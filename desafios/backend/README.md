# Desafio AWS Software Engineer, Back-end - Mimoo
> ~~Adotado~~ Inspirado no [Desafio: Desenvolvimento / Backend](https://www.notion.so/Back-end-0b2c45f1a00e4a849eefe3b1d57f23c6) da BossaBox

Sua tarefa é construir uma API e banco de dados para a aplicação VUTTR (Very Useful Tools to Remember). A aplicação é um simples repositório para gerenciar ferramentas com seus respectivos nomes, links, descrições e tags.

A aplicação deve ser construída utilizando a seguinte stack: AWS Cognito, AWS Api Gateway, AWS Lambda - escrito em TypeScript (ou JavaScript) e utilizando o [Serverless Framework](https://serverless.com/framework/docs/) com a lib [Middy](https://github.com/middyjs) - e AWS DynamoDB.

A API deverá ser documentada utilizando o formato [Swagger](https://swagger.io/docs/specification/basic-structure/).

## O que será avaliado

Queremos avaliar sua capacidade de desenvolver e documentar um back-end para uma aplicação. Serão avaliados:

- Código bem escrito e limpo;
- Quais ferramentas foram usadas, como e por quê, além do seu conhecimento das mesmas;
- Seu conhecimento em banco de dados, requisições HTTP, APIs REST, etc;
- Sua capacidade de se comprometer com o que foi fornecido;
- Sua capacidade de documentação da sua parte da aplicação.

## O mínimo necessário

- Uma aplicação contendo uma API real simples, com autenticação, que atenda os requisitos descritos abaixo, fazendo requisições à um banco de dados para persistência;
- README.md contendo informações básicas do projeto e como executá-lo;
- [Swagger](https://swagger.io/docs/specification/basic-structure/) da aplicação.

## Bônus

Os seguintes itens não são obrigatórios, mas darão mais valor ao seu trabalho (os em negrito são mais significativos para nós)

- Uso de ferramentas externas que facilitem o seu trabalho;
- Cuidados especiais com otimização, padrões, entre outros;
- Migrations ou script para configuração do banco de dados utilizado;
- **Testes**.

# Requisitos

## 0: Deve haver uma rota para listar todas as ferramentas cadastradas

`GET /tools`

Resposta:

    [
        {
            id: 1,
            title: "Notion",
            link: "https://notion.so",
            description: "All in one tool to organize teams and ideas. Write, plan, collaborate, and get organized. ",
            tags: [
                "organization",
                "planning",
                "collaboration",
                "writing",
                "calendar"
            ]
        },
        {
            id: 2,
            title: "json-server",
            link: "https://github.com/typicode/json-server",
            description: "Fake REST API based on a json schema. Useful for mocking and creating APIs for front-end devs to consume in coding challenges.",
            tags: [
                "api",
                "json",
                "schema",
                "node",
                "github",
                "rest"
            ]
        },
        {
            id: 3,
            title: "fastify",
            link: "https://www.fastify.io/",
            description: "Extremely fast and simple, low-overhead web framework for NodeJS. Supports HTTP2.",
            tags: [
                "web",
                "framework",
                "node",
                "http2",
                "https",
                "localhost"
            ]
        }
    ]

## 1: Deve ser possível filtrar ferramentas utilizando uma busca por tag

`GET /tools?tag=node`   (*node* é a tag sendo buscada neste exemplo)

Resposta:

    [
        {
            id: 2,
            title: "json-server",
            link: "https://github.com/typicode/json-server",
            description: "Fake REST API based on a json schema. Useful for mocking and creating APIs for front-end devs to consume in coding challenges.",
            tags: [
                "api",
                "json",
                "schema",
                "node",
                "github",
                "rest"
            ]
        },
        {
            id: 3,
            title: "fastify",
            link: "https://www.fastify.io/",
            description: "Extremely fast and simple, low-overhead web framework for NodeJS. Supports HTTP2.",
            tags: [
                "web",
                "framework",
                "node",
                "http2",
                "https",
                "localhost"
            ]
        }
    ]

## 2: Deve haver uma rota para cadastrar uma nova ferramenta

O corpo da requisição deve conter as informações da ferramenta a ser cadastrada, sem o ID (gerado automaticamente pelo servidor). A resposta, em caso de sucesso, deve ser o mesmo objeto, com seu novo ID gerado.

`POST /tools
Content-Type: application/json`

    {
        "title": "hotel",
        "link": "https://github.com/typicode/hotel",
        "description": "Local app manager. Start apps within your browser, developer tool with local .localhost domain and https out of the box.",
        "tags":["node", "organizing", "webapps", "domain", "developer", "https", "proxy"]
    }

Resposta:

`Status: 201 Created`

`Content-Type: application/json`

    {
        "title": "hotel",
        "link": "https://github.com/typicode/hotel",
        "description": "Local app manager. Start apps within your browser, developer tool with local .localhost domain and https out of the box.",
        "tags":["node", "organizing", "webapps", "domain", "developer", "https", "proxy"],
        "id":5
    }

## 3: O usuário deve poder remover uma ferramenta por ID

`DELETE /tools/:id`

Resposta:

`Status: 200 OK`

    {}

## Critérios de Aceitação

- A API deve ser real e escrita por você. Ferramentas que criam APIs automaticamente (Loopback, json-server, etc) não são aceitas;
- Todos os requisitos acima devem ser cumpridos, seguindo o padrão de rotas estabelecido;
- Deve haver um documento de OpenAPI (antigo Swagger) descrevendo sua API;
- Se você julgar necessário, adequado ou quiser deixar a aplicação mais completa (bônus!) você pode adicionar outras rotas, métodos, etc.

Ao término do desafio, você deve [agendar uma ligação](https://calendly.com/lucaskauer/challenge) com Lucas Kauer (Tech Lead da Mimoo) para falar sobre o que você construiu. A ligação ocorrerá via Hangouts, e o link estará presente no convite do evento. **Desconsiderar esse item se você chegou ao teste por outro canal**.
