# kubernetes-postgres

```bash
kubectl apply -f - << EOF
> apiVersion: v1
> kind: Pod
> metadata:
>   name: postgres
> spec:
>   containers:
>   - name: postgres
>     image: postgres
>     env:
>     - name: POSTGRES_PASSWORD
>       value: postgres
> EOF

```


```bash
kubectl get po
kubectl describe po postgres
```

```bash
kubectl exec -it postgres -- bash
```

```bash
PGPASSWORD=postgres
psql -U postgres
```



```bash
helm install postgresql bitnami/postgresql --set postgresqlPassword=postgres --set postgresqlDatabase=magma 
```


```bash
NAME: postgresql
LAST DEPLOYED: Thu Mar 10 13:01:07 2022
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
CHART NAME: postgresql
CHART VERSION: 11.0.3
APP VERSION: 14.1.0

** Please be patient while the chart is being deployed **

PostgreSQL can be accessed via port 5432 on the following DNS names from within your cluster:

    postgresql.default.svc.cluster.local - Read/Write connection

To get the password for "postgres" run:

    export POSTGRES_PASSWORD=$(kubectl get secret --namespace default postgresql -o jsonpath="{.data.postgres-password}" | base64 --decode)

To connect to your database run the following command:

    kubectl run postgresql-client --rm --tty -i --restart='Never' --namespace default --image docker.io/bitnami/postgresql:14.1.0-debian-10-r80 --env="PGPASSWORD=$POSTGRES_PASSWORD" \
      --command -- psql --host postgresql -U postgres -d postgres -p 5432

To connect to your database from outside the cluster execute the following commands:

    kubectl port-forward --namespace default svc/postgresql 5432:5432 &
    PGPASSWORD="$POSTGRES_PASSWORD" psql --host 127.0.0.1 -U postgres -d postgres -p 5432

```
