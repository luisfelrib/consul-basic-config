# Configurar Consul para utilizar Service Discovery

## Documentação completa
- https://www.consul.io/docs

## Comandos via terminal para configurar o Consul
- Show Members
```bash
consul members
```
- Start Consul server without config file
```bash
consul agent -server -bootstrap-expect=3 -node=consulserver01 -bind=172.18.0.3 -data-dir=/var/lib/consul -config-dir=/etc/consul.d
```

- Start Consul server with JSON file
```bash
consul agent -config-dir=/etc/consul.d
```

- Generate encryption key
```bash
consul keygen
```

- Start client
```bash
consul agent -bind=172.18.0.5 -data-dir=/var/lib/consul -config-dir=/etc/consul.d -retry-join=172.18.0.3
```

- Consul join (servers and clients)
```bash 
# consul join [server-address]
consul join 172.18.0.3
```

- Reload services on agents container
```bash
consul reload
```
## Ferrmentas extras para testar e verificar funcionamento
- Pacote bind-tools para usar o DIG
```bash
apk -u add bind-tools
```
- Usando DIG para obter informações dos serviços
```bash
dig @localhost -p 8600 nginx.service.consul
```
- API Consul de catalogo de serviços
```bash
curl localhost:8500/v1/catalog/services
```