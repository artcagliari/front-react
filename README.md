# Front React — Lista de Tarefas

Interface front-end de uma aplicação de gerenciamento de tarefas, construída com React e Vite. O projeto foi preparado para consumir uma API Laravel e inclui um protótipo visual completo que serve como referência para a implementação dos componentes.

## Visão geral

A proposta é oferecer uma experiência simples e acessível para organizar tarefas. A interface utiliza a estética de uma folha de caderno, adapta-se automaticamente ao tema claro ou escuro do sistema e respeita preferências de redução de movimento.

O repositório está dividido em duas partes:

- uma aplicação React em `src/`, atualmente com a estrutura inicial da tela;
- um protótipo estático em `prototipo/`, com exemplos dos principais estados da interface.

## Tecnologias

- React 19
- Vite 8
- React Compiler
- Axios
- ESLint
- CSS moderno e responsivo

## Funcionalidades planejadas

- listar tarefas cadastradas;
- adicionar uma tarefa com título e descrição opcional;
- editar tarefas existentes;
- marcar tarefas como concluídas;
- excluir tarefas;
- exibir estados de carregamento, lista vazia e erro;
- integrar o front-end a uma API REST em Laravel.

## Protótipo visual

O protótipo estático apresenta os estados que deverão ser reproduzidos na aplicação React:

- tarefa normal;
- tarefa concluída;
- tarefa em edição;
- operação aguardando resposta da API;
- carregamento inicial;
- lista vazia;
- falha de comunicação com o back-end.

Após iniciar o servidor de desenvolvimento, acesse:

```text
http://localhost:5173/prototipo/
```

## Pré-requisitos

Antes de começar, instale:

- Node.js compatível com o Vite 8;
- npm;
- uma API Laravel disponível em `http://localhost:8081`, caso queira testar a integração.

## Instalação

Clone o repositório e instale as dependências:

```bash
git clone https://github.com/artcagliari/front-react.git
cd front-react
npm install
```

Inicie o ambiente de desenvolvimento:

```bash
npm run dev
```

A aplicação estará disponível em:

```text
http://localhost:5173
```

## Scripts disponíveis

| Comando | Descrição |
| --- | --- |
| `npm run dev` | Inicia o servidor de desenvolvimento |
| `npm run build` | Gera a versão otimizada para produção |
| `npm run preview` | Executa localmente a versão de produção |
| `npm run lint` | Analisa o código com o ESLint |

## Integração com a API

Durante o desenvolvimento, as requisições iniciadas por `/api` são redirecionadas pelo proxy do Vite para:

```text
http://localhost:8081
```

A configuração pode ser alterada em `vite.config.js` para acompanhar a porta exposta pelo back-end.

### Contrato esperado

Cada tarefa deve seguir uma estrutura semelhante a esta:

```json
{
  "id": 1,
  "titulo": "Criar os componentes React",
  "descricao": "Implementar a interface a partir do protótipo",
  "concluida": false
}
```

Rotas REST esperadas:

| Ação | Método | Rota |
| --- | --- | --- |
| Listar tarefas | `GET` | `/api/tarefas` |
| Criar tarefa | `POST` | `/api/tarefas` |
| Atualizar tarefa | `PATCH` | `/api/tarefas/{id}` |
| Excluir tarefa | `DELETE` | `/api/tarefas/{id}` |

O proxy atual remove o prefixo `/api` antes de encaminhar a requisição. Caso as rotas do back-end mantenham esse prefixo, remova a opção `rewrite` de `vite.config.js`.

## Estrutura do projeto

```text
front-react/
├── prototipo/
│   └── index.html       # Referência visual com todos os estados
├── public/
│   └── favicon.svg      # Ícone da aplicação
├── src/
│   ├── App.jsx          # Componente principal
│   ├── index.css        # Tema, layout e estados visuais
│   └── main.jsx         # Ponto de entrada do React
├── eslint.config.js     # Regras de qualidade de código
├── index.html           # Documento principal
├── package.json         # Dependências e scripts
└── vite.config.js       # Plugins, servidor e proxy da API
```

## Design e acessibilidade

A folha de estilos já contempla:

- layout responsivo para telas menores;
- suporte automático aos temas claro e escuro;
- foco visível para navegação por teclado;
- textos auxiliares para leitores de tela;
- estados semânticos com `role="status"`, `role="alert"` e `aria-busy`;
- respeito à preferência `prefers-reduced-motion`.

Ao implementar os componentes, mantenha rótulos acessíveis nos campos e use descrições específicas nos checkboxes, como `Concluir: nome da tarefa`.

## Desenvolvimento

Antes de enviar alterações, execute:

```bash
npm run lint
npm run build
```

O React Compiler já está configurado para otimizar componentes compatíveis. Por isso, priorize componentes puros, não altere props ou estado diretamente e mantenha os Hooks no nível superior dos componentes.

## Autor

Desenvolvido por [Artur Cagliari](https://github.com/artcagliari).
