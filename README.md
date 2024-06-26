# Repositório Autoatendimento Lanchonete - Fiap Pós-Tech Arquitetura de Software

## Objetivo

O objetivo desse repositório é a apresentação da solução de autoatendimento proposta para o curso de pós gradução em *
*Arquitetura de Software**, aqui serão encontrados:

- Links de documentações ou entregáveis
- Código fonte da aplicação
- Código fonte de infraestrutura como código(caso necessário)
- Código fonte de Dockerfiles ou arquivos relacionados.

## DDD

A documentação referente a parte do DDD(Domain Driven Design).
Link de acesso: [Documentação via miro](https://miro.com/app/board/uXjVMnTeAN8=/?share_link_id=984815149799)

No miro há os seguintes elementos:

- Glossário de linguagem ubíqua com os termos utilizados no dominio
- Pictograma com os fluxos
- Storytelling escrito
- Event Storming com os eventos
- Event Storming com a definição dos agregados

## Pré requisitos para execução na aws

Definir as secrets abaixo no github para serem utilizadas no github actions.

```
DATABASE_HOST
DATABASE_USER
DATABASE_PASSWORD

AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_DEFAULT_REGION

COGNITO_POOL
COGNITO_CLIENT_ID
COGNITO_CLIENT_SECRET
```

## Execução no Kubernetes

### Configuracao de secrets

**fiap-secrets-db:**

- variável DATABASE_HOST
- variável DATABASE_USER
- variável DATABASE_PASSWORD
- variável DJANGO_KEY

**fiap-secrets-cobranca:**

- variável MERCADOPAGO_TOKEN
- variável MERCADOPAGO_EMAIL

obs.1: Será necessário rever e ajustar as variáveis utilizados pelos objetos de deployment.
obs.²: Caso não seja executado em ambiente AWS será necessário remover dos arquivos yaml as configurações referentes as
variáveis do cognito e secrets AWS.

**Para executar migrations do banco e carga de dados execute:(necessário executar manualmente somente uma vez)**

```bash
 #Fazer deployment dos objetos do kubernetes
 kubectl apply -f k8s/
 
 #Executar migrations do microservico de pedido
 kubectl exec deploy/app-autoatendimento -c fiap-pos-tech -- /bin/sh /app/carregar_dados.sh 
 
 #executar migrations do microservico de catalogo
 kubectl exec deploy/catalogo -c catalogo -- /bin/sh /app/carregar_dados.sh
 ```




