Based on: https://github.com/openfaas/workshop/blob/master/lab3.md 




```
curl -sSL https://cli.openfaas.com | sudo sh
faas login --gateway https://openfaas.tatzan.com/ --password <password>
faas-cli template pull
faas-cli new --list

```

```
faas-cli new --lang python3 hello-openfaas --prefix="kfirfer" --gateway https://openfaas.tatzan.com/
```


```
faas-cli new --lang python3 astronaut-finder --prefix="kfirfer" --gateway https://openfaas.tatzan.com/
faas-cli build -f ./astronaut-finder.yml
faas-cli push -f ./astronaut-finder.yml
faas-cli deploy -f ./astronaut-finder.yml

echo | faas-cli invoke astronaut-finder --gateway https://openfaas.tatzan.com/
```


```
kubectl logs deployment/astronaut-finder -n openfaas-fn
```