## Passo a passo prático para fazer o deploy de uma API na nuvem da Azure:

### Passo 1: Preparar a API Localmente
1. **Crie a API**: Vamos usar Node.js e Express para este exemplo.
   ```bash
   mkdir minha-api
   cd minha-api
   npm init -y
   npm install express
   ```
2. **Crie o arquivo `app.js`**:
   ```javascript
   const express = require('express');
   const app = express();
   const port = 3000;

   app.get('/', (req, res) => {
       res.send('API na Nuvem funcionando!');
   });

   app.listen(port, () => {
       console.log(`API rodando na porta ${port}`);
   });
   ```
3. **Teste a API localmente**:
   ```bash
   node app.js
   ```
   Acesse `http://localhost:3000` no navegador para verificar se está funcionando.

### Passo 2: Configurar o Azure
1. **Crie uma conta no Azure**: Se ainda não tiver, crie uma conta no portal do Azure.
2. **Instale o Azure CLI**: Baixe e instale o Azure CLI a partir do site oficial.
3. **Faça login no Azure CLI**:
   ```bash
   az login
   ```

### Passo 3: Criar um App Service no Azure
1. **Crie um grupo de recursos**:
   ```bash
   az group create --name meuGrupoDeRecursos --location eastus
   ```
2. **Crie um App Service Plan**:
   ```bash
   az appservice plan create --name meuPlanoAppService --resource-group meuGrupoDeRecursos --sku FREE
   ```
3. **Crie um Web App**:
   ```bash
   az webapp create --resource-group meuGrupoDeRecursos --plan meuPlanoAppService --name minhaApiAzure
   ```

### Passo 4: Fazer o Deploy da API
1. **Configure o Git no projeto**:
   ```bash
   git init
   git add .
   git commit -m "Primeiro commit"
   ```
2. **Configure o repositório remoto**:
   ```bash
   az webapp deployment source config-local-git --name minhaApiAzure --resource-group meuGrupoDeRecursos
   ```
   O comando acima retornará uma URL Git. Adicione essa URL como remoto:
   ```bash
   git remote add azure <URL-GIT>
   ```
3. **Envie o código para o Azure**:
   ```bash
   git push azure master
   ```

### Passo 5: Verificar o Deploy
1. **Acesse a URL do Web App**: No portal do Azure, vá até o recurso do Web App e copie a URL. Acesse essa URL no navegador para verificar se a API está funcionando.

Pronto! Sua API deve estar rodando na nuvem da Azure. 
