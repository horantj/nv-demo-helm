# nv-demo-helm
Using this chart, will install some demo pods, as well as a menu based tool to trigger various activities.<br>
This chart can be installed in 1..n namespaces, and traffic etc... will be localized to that NS.

## Install helm chart:
exploit.image_tag: See valid tags at https://hub.docker.com/repository/docker/horantj/exploit

struts.ingress.enabled: bool to enable ingress for struts. not strictly required for the menu tool.
struts.ingress.host: Use a host or IP for ingress to struts. i.e. "struts.3.227.235.243.sslip.io"

```
git clone https://github.com/horantj/nv-demo-helm.git
helm install -n demo --create-namespace \
--set exploit.image_tag=0.4 --set struts.ingress.enabled=true \
--set struts.ingress.host=struts.3.227.235.243.sslip.io
```

## Using exploit tool:
Shell into the exploit pod and run the tool:
```
python3 exploit.py <admin user> <admin pass> neuvector-svc-controller.cattle-neuvector-system.svc
```