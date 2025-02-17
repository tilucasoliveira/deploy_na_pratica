
Passo a passo prático para fazer o deploy de uma API na nuvem da Azure


# Minha API

Uma API simples criada com Node.js e Express para demonstrar o deploy na Azure.

## Descrição

Esta API é um exemplo básico que responde com uma mensagem simples quando acessada. O objetivo é mostrar como fazer o deploy de uma API na nuvem da Azure.

## Estrutura do Projeto

- `app.js`: Arquivo principal da aplicação que configura o servidor Express.
- `package.json`: Arquivo de configuração do projeto Node.js, incluindo dependências e scripts.

## Como Usar

### Pré-requisitos

- Node.js instalado na máquina.
- Conta no Azure.
- Repositório no GitHub.

### Instalação

1. Clone o repositório:
   ```bash
   git clone https://github.com/SEU_USUARIO/minha-api.git
   cd minha-api


2. Instale as dependências:
   ```bash
   npm install


### Executar Localmente

3. Inicie o servidor:
```bash
npm start
```


4. Acesse http://localhost:3000 no navegador para ver a API em funcionamento.

### Deploy na Azure

5. Configure o Azure CLI e faça login:
```bash
az login
```

6. Crie um grupo de recursos:
```bash
az group create --name meuGrupoDeRecursos --location eastus
```

7. Crie um App Service Plan:
```bash
az appservice plan create --name meuPlanoAppService --resource-group meuGrupoDeRecursos --sku FREE
```

8. Crie um Web App:
```bash
az webapp create --resource-group meuGrupoDeRecursos --plan meuPlanoAppService --name minhaApiAzure
```

9. Configure o repositório remoto do Azure:
```bash
az webapp deployment source config --name minhaApiAzure --resource-group meuGrupoDeRecursos --repo-url https://github.com/SEU_USUARIO/minha-api --branch master --manual-integration
```

10. Acesse a URL do Web App no portal do Azure para verificar se a API está funcionando.

### Contribuição
Sinta-se à vontade para contribuir com melhorias para este projeto. Faça um fork do repositório, crie uma branch para suas alterações e envie um pull request.

### Licença
Este projeto está licenciado sob a licença MIT. Veja o arquivo LICENSE para mais detalhes.




