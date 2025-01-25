# Projeto de Gerenciamento de Filmes com Azure Functions

Este projeto é uma aplicação de exemplo que utiliza o Azure Functions para gerenciar um banco de dados de filmes. A aplicação foi desenvolvida com .NET 8 e utiliza o Azure Cosmos DB para o armazenamento de dados.

## Pré-requisitos

- [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
- [Azure Functions Core Tools](https://docs.microsoft.com/azure/azure-functions/functions-run-local)
- [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/)

## Configuração

1. Clone o repositório para sua máquina local:

```bash
git clone <URL_DO_REPOSITORIO>
cd <NOME_DO_REPOSITORIO>
```

2. Configure as variáveis de ambiente no arquivo `local.settings.json`:

```json
{
    "IsEncrypted": false,
    "Values": {
        "AzureWebJobsStorage": "UseDevelopmentStorage=true",
        "FUNCTIONS_WORKER_RUNTIME": "dotnet-isolated",
        "CosmoDBConnection": "AccountEndpoint=https://<SEU_COSMOS_DB_ENDPOINT>;AccountKey=<SEU_COSMOS_DB_KEY>;"
    },
    "Host": {
        "CORS": "*"
    }
}
```

3. Certifique-se de que o Azure Cosmos DB está configurado corretamente e que as credenciais no arquivo `local.settings.json` estão corretas.

## Executando o Projeto

1. Inicie o Azure Functions Core Tools com o seguinte comando:

```bash
func start
```

2. Acesse a URL fornecida pelo Azure Functions Core Tools para interagir com as funções.

## Estrutura do Projeto

- **`fnGetAllMovies`**: Função que recupera todos os filmes do banco de dados Cosmos DB.
- **`local.settings.json`**: Arquivo de configuração local para o Azure Functions.

## Funcionalidades

### Obter Todos os Filmes

Recupera todos os filmes armazenados no Azure Cosmos DB.

- **Endpoint**: `GET /api/GetAllMovies`
- **Descrição**: Retorna uma lista de todos os filmes no banco de dados.

### Adicionar um Novo Filme

Adiciona um novo filme ao banco de dados Azure Cosmos DB.

- **Endpoint**: `POST /api/AddMovie`
- **Descrição**: Adiciona um novo filme ao banco de dados.
- **Corpo da Requisição**:

```json
{
    "id": "string",
    "title": "string",
    "director": "string",
    "releaseYear": "int"
}
```

### Atualizar um Filme

Atualiza os detalhes de um filme existente no Azure Cosmos DB.

- **Endpoint**: `PUT /api/UpdateMovie`
- **Descrição**: Atualiza um filme existente no banco de dados.
- **Corpo da Requisição**:

```json
{
    "id": "string",
    "title": "string",
    "director": "string",
    "releaseYear": "int"
}
```

### Deletar um Filme

Deleta um filme do banco de dados Azure Cosmos DB.

- **Endpoint**: `DELETE /api/DeleteMovie`
- **Descrição**: Remove um filme do banco de dados.
- **Parâmetros da Requisição**:

```json
{
    "id": "string"
}
```

## Contribuição

1. Faça um fork do projeto.
2. Crie uma nova branch para a sua funcionalidade (`git checkout -b feature/nova-funcionalidade`).
3. Faça commit das suas alterações (`git commit -am 'Adiciona nova funcionalidade'`).
4. Faça push para a branch (`git push origin feature/nova-funcionalidade`).
5. Abra um Pull Request.