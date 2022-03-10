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
