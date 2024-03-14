# Repositório Autoatendimento Lanchonete - Fiap Pós-Tech Arquitetura de Software

## Objetivo
O objetivo desse repositório é a apresentação da solução de autoatendimento proposta para o curso de pós gradução em **Arquitetura de Software**, aqui serão encontrados:
- Links de documentações ou entregáveis
- Código fonte da aplicação
- Código fonte de infraestrutura como código(caso necessário)
- Código fonte de Dockerfiles ou arquivos relacionados.

## DDD
A documentaração referente a parte do DDD(Domain Driven Design).
Link de acesso: [Documentação via miro](https://miro.com/app/board/uXjVMnTeAN8=/?share_link_id=984815149799)

No miro há os seguintes elementos:
- Glossário de linguagem ubíqua com os termos utilizados no dominio
- Pictograma com os fluxos
- Storytelling escrito
- Event Storming com os eventos
- Event Storming com a definição dos agredados

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

Tanto a criação da infraestrutura do kubernetes quanto a aplicação do dos arquivos yaml do kubernetes serão executadas por github actions após algum push.


**Para executar migrations do banco e carga de dados execute:(necessário executar manualmente somente uma vez)**

``` kubectl exec deploy/app-autoatendimento -c fiap-pos-tech -- /bin/sh /app/carregar_dados.sh ```


## Arquitetura da solução
![arquitetura](https://github.com/rafaelbgil/fiap-autoatendimento/assets/13522522/ec957ea0-8f1e-4acd-93bc-907e953f2a8b)

