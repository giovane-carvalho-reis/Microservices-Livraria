# Guia Docker Compose

Este guia explica como subir e gerenciar um ambiente containerizado utilizando Docker Compose.

## Pré-requisitos

Antes de começar, certifique-se de ter instalado:

- [Docker](https://docs.docker.com/get-docker/) (versão 20.10+)
- [Docker Compose](https://docs.docker.com/compose/install/) (versão 2.0+)

Para verificar as instalações:
```bash
docker --version
docker compose version
```

Dentro da pasta do projeto realize o comanhdo 
```bash
docker compose up -d
```
E os serviços inclusos irão ser criados no docker

## Token Keycloak

Com os serviços de pé, executar o seguinte curl para pegar o token:
```
curl --request post \
  --url http://localhost:8080/realms/master/protocol/openid-connect/token \
  --header 'content-type: application/x-www-form-urlencoded' \
  --data grant_type=password \
  --data client_id={CLIENTE ID QUE VC ADICIONOU} \
  --data client_secret={O SEU SECRET} \
  --data username={SEU USUARIO CRIADO} \
  --data password={SUSA SENHA}
```

Obs: Lembrando que para a requisição funcionar as informações acima devem ter sido
adicionadas no keycloak anteriormente