# HELM v3 Demo for OpenShift 4
This is a quick demo about how to use Helm with OpenShift 4. It is based on the following [article in opensource.com][1].

## Prepare your environment
Setup your OpenShift cluster (use[code-ready/crc][2]), login into it with the user developer and create a new project

```bash
$> crc setup && crc start
$> oc login -u developer -p developer https://api.crc.testing:6443/
$> oc new-project helm-demo
```

### Setup helm on Mac
If you want to play locally, you have to setup helm. Either download it from the official website or install it via [homebrew][3].
```bash
$> brew install helm
```

### Other OS'ses
Just read here: https://helm.sh

## Demo
A simple demo guide
### Explain local files
```bash
$ tree
.
├── Chart.yaml
├── README.md
├── charts
├── templates
│   ├── NOTES.txt
│   ├── _helpers.tpl
│   ├── configMap.yaml
│   ├── deployment.yaml
│   ├── hpa.yaml
│   ├── ingress.yaml
│   ├── route.yaml
│   ├── service.yaml
│   ├── serviceaccount.yaml
│   └── tests
│       └── test-connection.yaml
└── values.yaml

3 directories, 13 files
```

### Install the chart
```bash
$> helm install my-app-chart ./helm-demo --values ./helm-demo/values.yaml
```

### Make a simple update
Don’t forget to update Chart.yaml versions and then
```bash
$> helm upgrade my-app-chart ./helm-demo --values ./helm-demo/values.yaml
```

[1]:	https://opensource.com/article/20/5/helm-charts "article in opensource.com"
[2]:	https://github.com/code-ready/crc
[3]:	https://brew.sh