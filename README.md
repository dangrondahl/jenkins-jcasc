# jenkins-master

Setting up Jenkins master in Docker

## How to run

```bash
docker-compose up -d
```

- Jenkins: http://localhost:8080 (`demoAdmin` / `passw0rd`)

## Getting Jenkins plugins

```bash
JENKINS_HOST=demoAdmin:passw0rd@localhost:8080
curl -sSL "http://$JENKINS_HOST/pluginManager/api/xml?depth=1&xpath=/*/*/shortName|/*/*/version&wrapper=plugins" | perl -pe 's/.*?<shortName>([\w-]+).*?<version>([^<]+)()(<\/\w+>)+/\1 \2\n/g'|sed 's/ /:/' > plugins.txt
```