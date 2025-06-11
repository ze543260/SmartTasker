# SmartTasker

Este projeto é um sistema completo de gerenciamento de tarefas, desenvolvido como desafio técnico. Ele demonstra integração entre frontend (React + TypeScript + TailwindCSS), backend (Node.js + Express) e um microsserviço Python (FastAPI + Gemini API) para sugestões inteligentes de títulos e descrições de tarefas.

---

## ✨ Funcionalidades

- **Criar tarefas** com título, descrição e data de término
- **Editar tarefas** (título, descrição e data)
- **Listar tarefas** cadastradas
- **Marcar tarefas** como concluídas ou incompletas
- **Excluir tarefas** com confirmação
- **Sugerir título** de tarefa usando IA (Gemini)
- **Sugerir descrição** de tarefa usando IA (Gemini)
- Interface responsiva, moderna e acessível

---

## 🛠️ Tecnologias Utilizadas

- **Frontend:** React, TypeScript, TailwindCSS
- **Backend:** Node.js, Express, Axios
- **Microsserviço:** Python, FastAPI, Google Gemini API
- **Outros:** dotenv, CORS

---

## 📦 Estrutura do Projeto

```
desafio/
├── backend/         # API Node.js/Express (tarefas)
│   ├── index.js
│   ├── package.json
│   └── routes/
│       └── tasks.js
├── frontend/        # Aplicação web React/TypeScript
│   ├── src/
│   │   ├── App.tsx
│   │   ├── components/
│   │   │   └── TaskItem.tsx
│   │   └── types.ts
│   ├── package.json
│   └── ...
└── python-service/  # Microsserviço Python para sugestões IA
    ├── suggestion_service.py
    ├── .env
    └── ...
```

---

## 🚀 Como Executar

### 1. Backend (Node.js + Express)

```bash
cd backend
npm install
npm run dev
```

A API estará disponível em `http://localhost:3001`

### 2. Frontend (React + TypeScript + TailwindCSS)

```bash
cd frontend
npm install
npm start
```

O app web estará rodando em `http://localhost:3000`

### 3. Microsserviço Python (FastAPI + Gemini)

**Pré-requisitos:** Python 3.10+, `.env` com sua chave da API Gemini  
Obtenha sua chave em: [https://ai.google.dev/gemini-api/docs/api-key?hl=pt-br](https://ai.google.dev/gemini-api/docs/api-key?hl=pt-br)

```bash
cd python-service
pip install -r requirements.txt
uvicorn suggestion_service:app --reload --port 5000
```

A rota estará disponível em `http://localhost:5000/suggest-title` e `http://localhost:5000/suggest-description`

---

## 🔗 Integração

- O **frontend** se comunica com o **backend** em `localhost:3001`
- O **backend** acessa `/tasks/suggest-title` e `/tasks/suggest-description`, que chamam o microsserviço Python (`localhost:5000`), usando a API do Gemini para gerar sugestões

---

## 🧪 Testando as Sugestões IA

### Sugestão de Título

```http
POST http://localhost:5000/suggest-title
Content-Type: application/json

{
  "titles": ["Estudar React", "Fazer compras", "Lavar o carro"]
}
```

Resposta esperada:

```json
{ "title": "Organizar material de estudo" }
```

### Sugestão de Descrição

```http
POST http://localhost:5000/suggest-description
Content-Type: application/json

{
  "title": "Estudar React"
}
```

Resposta esperada:

```json
{
  "description": "Revisar os principais conceitos e hooks do React para aprimorar o desenvolvimento de interfaces."
}
```

---

## 🖥️ Uso da Interface

- Preencha o **título**, **descrição** (opcional) e **data de término** (opcional)
- Use os botões para **criar tarefa**, **sugerir título** ou **sugerir descrição**
- Edite qualquer tarefa clicando no ícone de lápis
- Marque como concluída/incompleta ou exclua tarefas facilmente

---

## ℹ️ Observações

- Os dados das tarefas são armazenados apenas em memória (não persistem após reiniciar o backend)
- O projeto é totalmente local, sem necessidade de deploy externo
- O código é modular, limpo e fácil de entender
- O microsserviço Python depende de uma chave válida da API Gemini (Google Generative AI)

---

## 👨‍💻 Feito com

- Node.js + Express
- React + TypeScript
- Tailwind CSS
- FastAPI + Python
- Gemini API (Google Generative AI)

---
