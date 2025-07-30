# 🗄️ Configuração do Supabase

## 📋 Pré-requisitos

1. Conta no [Supabase](https://supabase.com)
2. Projeto criado no Supabase

## 🔧 Passo a Passo

### 1. Criar Projeto no Supabase

1. Acesse [supabase.com](https://supabase.com)
2. Clique em "Start your project"
3. Faça login ou crie uma conta
4. Clique em "New Project"
5. Escolha sua organização
6. Preencha:
   - **Name**: sophia-gourmet
   - **Database Password**: (crie uma senha forte)
   - **Region**: South America (São Paulo)
7. Clique em "Create new project"

### 2. Obter as Chaves de API

1. No painel do seu projeto, vá para **Settings** > **API**
2. Copie as seguintes informações:
   - **Project URL** (algo como: https://xxxxx.supabase.co)
   - **anon public** (chave pública)
   - **service_role** (chave privada - mantenha secreta!)

### 3. Configurar Variáveis de Ambiente

Crie um arquivo `.env.local` na raiz do seu projeto:

\`\`\`env
# Supabase Configuration
NEXT_PUBLIC_SUPABASE_URL=https://seu-projeto.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=sua-chave-publica-aqui
SUPABASE_SERVICE_ROLE_KEY=sua-chave-privada-aqui
\`\`\`

**⚠️ IMPORTANTE:**
- Substitua os valores pelos seus dados reais
- Nunca compartilhe a `SUPABASE_SERVICE_ROLE_KEY`
- Adicione `.env.local` no seu `.gitignore`

### 4. Executar os Scripts SQL

1. No painel do Supabase, vá para **SQL Editor**
2. Execute o script `scripts/01-create-tables.sql`
3. Execute o script `scripts/02-insert-sample-data.sql`

Ou use os botões de execução aqui no v0!

### 5. Verificar se Funcionou

1. Reinicie seu servidor de desenvolvimento
2. Abra o site
3. Selecione um estado
4. Verifique no console se aparece: "Localização salva no banco de dados e localStorage"
5. No Supabase, vá para **Table Editor** > **user_locations** para ver os dados

## 🔍 Verificação de Problemas

### Erro: "supabaseUrl is required"
- ✅ Verifique se o arquivo `.env.local` existe
- ✅ Confirme se as variáveis estão corretas
- ✅ Reinicie o servidor após criar o `.env.local`

### Erro: "Invalid API key"
- ✅ Verifique se copiou as chaves corretas
- ✅ Confirme se não há espaços extras nas variáveis

### Tabela não existe
- ✅ Execute os scripts SQL no Supabase
- ✅ Verifique se a tabela `user_locations` foi criada

## 🚀 Funcionalidades Após Configuração

✅ **Localização salva permanentemente**
✅ **Usuário não precisa inserir estado novamente**
✅ **Dados sincronizados entre dispositivos**
✅ **Backup automático no banco**

## 💡 Dicas

- O site funciona mesmo sem Supabase (usa apenas localStorage)
- Configure o Supabase quando quiser dados permanentes
- Use o painel do Supabase para ver estatísticas de usuários
\`\`\`

Agora vou criar um componente para mostrar o status da configuração:
