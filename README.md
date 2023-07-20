# sealed-secrets
```
https://github.com/bitnami-labs/sealed-secrets.git
helm repo add sealed-secrets https://bitnami-labs.github.io/sealed-secrets
```
# Creating Secret with DRY-RUN
```
 kubectl create secret generic mysecret --dry-run=client --from-literal=foo=bar -o json > mysecret.json
```
# Creating Sealed Secret < mandatory > 
```
kubeseal --scope namespace-wide --cert mycert.pem < mysecret.json > mysealedsecret.json
```
# Check the logs of the kubeseal controller to get the certificate
```
kubectl logs <pod_name> -n kube-system
kubeseal --fetch-cert > mycert.pem
```
