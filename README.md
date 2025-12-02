# Contagia Frontend - Aplicação Next.js com HeroUI

Frontend desenvolvido em Next.js 15 com TypeScript, utilizando HeroUI v2 para componentes de interface, Tailwind CSS para estilização e integração com a API backend para upload e identificação de músicas.

## 📋 Índice

- [Como Instalar](#como-instalar)
- [Variáveis de Ambiente](#variáveis-de-ambiente)
- [Dependências](#dependências)
- [Como Iniciar o Servidor](#como-iniciar-o-servidor)
- [Como Rodar](#como-rodar)
- [Estrutura de Pastas](#estrutura-de-pastas)

## 🚀 Como Instalar

### Pré-requisitos

- **Node.js** (versão 18 ou superior recomendada)
- **npm**, **yarn**, **pnpm** ou **bun** para gerenciamento de dependências
- **Backend rodando** (Contagia_Back) na porta 8000 ou configurada

### Passos de Instalação

1. **Navegue até a pasta do frontend:**
```powershell
cd Contagia_Front
```

2. **Instale as dependências:**
```powershell
npm install
```

ou com pnpm:
```powershell
pnpm install
```

⚠️ **Nota para usuários de pnpm**: Se estiver usando `pnpm`, adicione ao arquivo `.npmrc`:
```
public-hoist-pattern[]=*@heroui/*
```

Depois, execute `pnpm install` novamente.

## 🔐 Variáveis de Ambiente

Crie um arquivo `.env.local` na raiz da pasta `Contagia_Front` com as seguintes variáveis:

```env
# URL da API Backend
NEXT_PUBLIC_API_URL=http://localhost:8000

# Ambiente de execução
NODE_ENV=development
```

### Variáveis Disponíveis

- **NEXT_PUBLIC_API_URL**: URL base da API backend (padrão: `http://localhost:8000`)
  - Esta variável é exposta ao cliente (prefixo `NEXT_PUBLIC_`)
  - Certifique-se de que o backend está rodando nesta URL

⚠️ **IMPORTANTE**: 
- Variáveis com prefixo `NEXT_PUBLIC_` são expostas ao navegador
- Nunca commite o arquivo `.env.local` no repositório
- Para produção, configure as variáveis no ambiente de deploy

## 📦 Dependências

### Dependências Principais

- **next** (^15.5.4) - Framework React para produção
- **react** (18.3.1) - Biblioteca React
- **react-dom** (18.3.1) - Renderização React no DOM
- **@heroui/\*** - Componentes UI do HeroUI v2
  - Accordion, Alert, Autocomplete, Avatar, Badge, Button, Card, etc.
- **framer-motion** (11.18.2) - Animações
- **next-themes** (0.4.6) - Gerenciamento de temas (claro/escuro)
- **lucide-react** (^0.545.0) - Ícones
- **clsx** (2.1.1) - Utilitário para classes CSS condicionais

### Dependências de Desenvolvimento

- **typescript** (5.6.3) - Linguagem TypeScript
- **tailwindcss** (4.1.11) - Framework CSS utility-first
- **@tailwindcss/postcss** (4.1.11) - PostCSS para Tailwind
- **eslint** (^9.37.0) - Linter de código
- **prettier** (3.5.3) - Formatador de código
- **@types/node** (^20.5.7) - Tipos do Node.js
- **@types/react** (18.3.3) - Tipos do React
- **@types/react-dom** (18.3.0) - Tipos do React DOM

## 🖥️ Como Iniciar o Servidor

### Modo Desenvolvimento

```powershell
npm run dev
```

Este comando:
- Inicia o servidor de desenvolvimento na porta 3000
- Habilita hot-reload automático
- Usa Turbopack para compilação rápida
- Acesse em `http://localhost:3000`

### Modo Produção

1. **Compile o projeto:**
```powershell
npm run build
```

2. **Inicie o servidor de produção:**
```powershell
npm start
```

O servidor estará disponível em `http://localhost:3000`.

### Outros Comandos

```powershell
# Executar linter e corrigir problemas
npm run lint

# Build para produção
npm run build
```

## 🏃 Como Rodar

### Verificação Inicial

1. **Certifique-se de que o backend está rodando:**
   - Backend deve estar em `http://localhost:8000` (ou URL configurada)
   - Verifique com: `GET http://localhost:8000/`

2. **Inicie o frontend:**
```powershell
npm run dev
```

3. **Acesse no navegador:**
   - Abra `http://localhost:3000`

### Funcionalidades Principais

- **Home**: Página inicial do sistema
- **Dashboard**: Painel principal com estatísticas
- **Upload**: Upload de arquivos MXF para identificação
- **Relatórios**: Visualização de relatórios e validações
- **Validação**: Validação de músicas identificadas

### Rotas Disponíveis

- `/` - Página inicial
- `/home` - Home do sistema
- `/dashboard` - Dashboard principal
- `/upload` - Upload de arquivos
- `/relatorios` - Lista de relatórios
- `/relatorios/validacao/[id]` - Validação de relatório específico

## 📁 Estrutura de Pastas

```
Contagia_Front/
├── app/                      # App Router do Next.js 15
│   ├── (login-routes)/       # Grupo de rotas de login
│   │   ├── home/
│   │   │   └── page.tsx      # Página home
│   │   └── layout.tsx        # Layout para rotas de login
│   ├── (navbar-routes)/      # Grupo de rotas com navbar
│   │   ├── dashboard/
│   │   │   └── page.tsx      # Página dashboard
│   │   ├── upload/
│   │   │   └── page.tsx      # Página de upload
│   │   ├── relatorios/
│   │   │   ├── page.tsx      # Lista de relatórios
│   │   │   └── validacao/
│   │   │       └── [id]/
│   │   │           └── page.tsx  # Validação por ID
│   │   └── layout.tsx        # Layout com navbar
│   ├── error.tsx             # Página de erro global
│   ├── layout.tsx             # Layout raiz
│   ├── page.tsx               # Página inicial
│   └── providers.tsx         # Providers do React
├── components/                # Componentes reutilizáveis
│   ├── approvalButtons.tsx   # Botões de aprovação
│   ├── BackgroundImage.tsx   # Componente de imagem de fundo
│   ├── ClientOnly.tsx        # Componente apenas cliente
│   ├── coloredFooter.tsx     # Rodapé colorido
│   ├── counter.tsx           # Contador
│   ├── edlDownloadModal.tsx  # Modal de download EDL
│   ├── errorState.tsx        # Estado de erro
│   ├── GlassCard.tsx         # Card com efeito glass
│   ├── HomeContent.tsx       # Conteúdo da home
│   ├── HomeHeader.tsx        # Cabeçalho da home
│   ├── icons.tsx             # Ícones customizados
│   ├── inputFile.tsx         # Input de arquivo
│   ├── inputSearch.tsx       # Input de busca
│   ├── loadingScreen.tsx     # Tela de carregamento
│   ├── musicCharts.tsx       # Gráficos de música
│   ├── musicCounter.tsx      # Contador de músicas
│   ├── musicPlayer.tsx       # Player de música
│   ├── musicStats.tsx        # Estatísticas de música
│   ├── navbar.tsx            # Barra de navegação
│   ├── navigationControl.tsx # Controle de navegação
│   ├── notification.tsx      # Notificações
│   ├── PageLayout.tsx        # Layout de página
│   ├── primitives.ts         # Componentes primitivos
│   ├── theme-switch.tsx      # Alternador de tema
│   ├── UploadHistory.tsx     # Histórico de uploads
│   ├── validationCard.tsx    # Card de validação
│   ├── validationPainel.tsx  # Painel de validação
│   ├── videoCard.tsx         # Card de vídeo
│   ├── videoCarossel.tsx     # Carrossel de vídeos
│   ├── videoPlayer.tsx       # Player de vídeo
│   ├── watchFolderSimulator.tsx  # Simulador de pasta watch
│   └── watchUtils.ts         # Utilitários de watch
├── config/                    # Configurações
│   ├── api.ts                # Configuração da API
│   ├── fonts.ts              # Configuração de fontes
│   └── site.ts               # Configurações do site
├── data/                      # Dados mockados
│   ├── musicMock.ts          # Dados mock de música
│   └── videoMocks.ts         # Dados mock de vídeo
├── public/                    # Arquivos estáticos
│   ├── fonts/                # Fontes customizadas
│   │   └── Globotipo-Texto.woff2
│   ├── Home.png              # Imagem da home
│   ├── logoGlobo.png         # Logo Globo
│   ├── logoGlobo.svg         # Logo Globo SVG
│   ├── logoWhiteGlobo.ico    # Ícone Globo branco
│   └── logoWhiteGlobo.png    # Logo Globo branco
├── styles/                    # Estilos globais
│   └── globals.css           # CSS global
├── types/                     # Definições de tipos
│   └── index.ts              # Tipos TypeScript
├── .env.local                # Variáveis de ambiente (não versionado)
├── .gitignore
├── eslint.config.mjs         # Configuração ESLint
├── next.config.js            # Configuração Next.js
├── package.json
├── package-lock.json
├── postcss.config.js         # Configuração PostCSS
├── tailwind.config.js        # Configuração Tailwind
├── tsconfig.json             # Configuração TypeScript
└── README.md
```

### Descrição das Pastas

- **app/**: App Router do Next.js 15 (rotas baseadas em arquivos)
  - `(login-routes)/`: Grupo de rotas que compartilham layout de login
  - `(navbar-routes)/`: Grupo de rotas que compartilham layout com navbar
  - Rotas dinâmicas: `[id]` para parâmetros dinâmicos

- **components/**: Componentes React reutilizáveis
  - Componentes de UI (cards, botões, modais)
  - Componentes de funcionalidade (player, upload, validação)
  - Componentes de layout (navbar, footer)

- **config/**: Configurações centralizadas
  - `api.ts`: Configuração de endpoints e cliente HTTP
  - `fonts.ts`: Configuração de fontes customizadas
  - `site.ts`: Configurações gerais do site

- **data/**: Dados mockados para desenvolvimento e testes

- **public/**: Arquivos estáticos servidos diretamente
  - Imagens, ícones, fontes

- **styles/**: Estilos globais e configurações CSS

- **types/**: Definições de tipos TypeScript compartilhados

## 🔧 Problemas Comuns

### Erro de conexão com backend
**Erro**: `Failed to fetch` ou `Não foi possível conectar ao backend`

**Solução**: 
- Verifique se o backend está rodando em `http://localhost:8000`
- Confirme a variável `NEXT_PUBLIC_API_URL` no `.env.local`
- Verifique CORS no backend

### Erro de módulo não encontrado
**Erro**: `Module not found` ou `Cannot find module`

**Solução**: 
- Execute `npm install` novamente
- Delete `node_modules` e `.next`, depois `npm install`
- Verifique se está usando a versão correta do Node.js

### Erro de build
**Erro**: Erros de TypeScript ou ESLint durante o build

**Solução**: 
- Execute `npm run lint` para verificar problemas
- Corrija os erros de TypeScript
- Verifique se todos os tipos estão corretos

### Porta 3000 já em uso
**Erro**: `Port 3000 is already in use`

**Solução**: 
- Encerre o processo na porta 3000
- Ou use outra porta: `npm run dev -- -p 3001`

## 📚 Documentação Adicional

- **Next.js**: [Documentação oficial](https://nextjs.org/docs)
- **HeroUI**: [Documentação oficial](https://heroui.com/)
- **Tailwind CSS**: [Documentação oficial](https://tailwindcss.com/docs)
- **TypeScript**: [Documentação oficial](https://www.typescriptlang.org/docs/)

## 🚧 Próximos Passos Recomendados

- [ ] Adicionar testes (Jest, React Testing Library)
- [ ] Implementar autenticação completa
- [ ] Adicionar tratamento de erros global
- [ ] Implementar cache de requisições
- [ ] Adicionar PWA (Progressive Web App)
- [ ] Otimizar performance e SEO
- [ ] Adicionar internacionalização (i18n)
