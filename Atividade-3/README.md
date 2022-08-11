<h1 align="center"> Atividade Kubernetes </h1>


## Atividade realizada no Windows e com o Docker for Windows.
## Criando um namespace chamado labwordpress no Kubernetes:
Criando um novo namespace com o comando:
```bash
kubectl create namespace labwordpress
```



## Realizando a criação do arquivo de service do MySQL mudando a porta padrão do banco MySQL para 3308:
Criando o arquivo mysql-service.yaml com as configurações necessárias:
```bash
apiVersion: v1
kind: Service
metadata:
  name: wordpress-mysql
  labels:
    app: wordpress
spec:
  ports:
    - port: 3308
  selector:
    app: wordpress
    tier: mysql
  clusterIP: None
```



## Realizando a criação do arquivo secret do MySql e definindo a senha:
Criando o arquivo mysql-secret.yaml com as configurações necessárias:
```bash
apiVersion: v1
kind: Secret
metadata:
  name: mysql-pass
type: Opaque
stringData:
  password: 49#31LAAm92
```



## Realizando a criação do arquivo de PersistentVolumeClaim do MySQL para um capacity de 3GB:
Criando o arquivo mysql-pvc.yaml e definindo o capacity para 3GB:
```bash
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: mysql-pv-claim
  labels:
    app: wordpress
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 3Gi
```



## Realizando a criação do arquivo de deployment do MySQL, criando um volume mount no deployment do MySQL chamado “mysql-persistent-storage-lab" apontando-o para /var/lib/mysql e criando volume com o mesmo nome do volume mount:
Criando o arquivo mysql-deeployment.yaml e definindo o volume mount com o nome solicitado e o ponto de montagem com o mesmo nome:
```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: wordpress-mysql
  labels:
    app: wordpress
spec:
  selector:
    matchLabels:
      app: wordpress
      tier: mysql
  strategy:
    type: Recreate
  template:
    metadata:
      labels:
        app: wordpress
        tier: mysql
    spec:
      containers:
      - image: mysql:5.6
        name: mysql
        env:
        - name: MYSQL_ROOT_PASSWORD
          valueFrom:
            secretKeyRef:
              name: mysql-pass
              key: password
        ports:
        - containerPort: 3308
          name: mysql
        volumeMounts:
        - name: mysql-persistent-storage-lab
          mountPath: /var/lib/mysql
      volumes:
      - name: mysql-persistent-storage-lab
        persistentVolumeClaim:
          claimName: mysql-pv-claim
```



## Realizando a criação do arquivo de service do Wordpress alterando para a TCP Port 80:
Criando o arquivo wp-service.yaml e definindo a porta TCP:
```bash
apiVersion: v1
kind: Service
metadata:
  name: wordpress
  labels:
    app: wordpress
spec:
  type: NodePort
  ports:
    - port: 80
      protocol: TCP
  selector:
    app: wordpress
    tier: frontend
```



## Realizando a criação do arquivo de PersistentVolumeClaim do Wordpress e definindo um capacity de 3GB:
Criando o arquivo wp-service.yaml e definindo o capacity de 3GB:
```bash
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: wp-pv-claim
  labels:
    app: wordpress
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 3Gi
```



## Definindo no arquivo de deployment do Wordpress um volume mount chamado “wordpresspersistent-storage-lab", apontando para /var/www/html, criando o volume em si com o mesmo nome do volume mount e inserindo secret criado anteriormente:
```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: wordpress
  labels:
    app: wordpress
spec:
  selector:
    matchLabels:
      app: wordpress
      tier: frontend
  strategy:
    type: Recreate
  template:
    metadata:
      labels:
        app: wordpress
        tier: frontend
    spec:
      containers:
      - image: wordpress:4.8-apache
        name: wordpress
        env:
        - name: WORDPRESS_DB_HOST
          value: wordpress-mysql
        - name: WORDPRESS_DB_PASSWORD
          valueFrom:
            secretKeyRef:
              name: mysql-pass
              key: password
        ports:
        - containerPort: 80
          name: wordpress
        volumeMounts:
        - name: wordpress-persistent-storage-lab
          mountPath: /var/www/html
      volumes:
      - name: wordpress-persistent-storage-lab
        persistentVolumeClaim:
          claimName: wp-pv-claim
```


## Realizando o apply de todos os arquivos:
Realizando o apply com o comando:
```bash
kubectl apply -f ./ --namespace=labwordpress
```



## Realizando a verificação da criação dos arquivos:
Realizando a verificação com o comando:
```bash
kubectl get all --namespace=labwordpress
```


## Verificando a URL:
Verificando a URL com o comando:
```bash
kubectl -n ingress get svc wordpress --namespace=labwordpress
```
