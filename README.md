# 💈 Barber SaaS - App de Agendamentos

Um aplicativo híbrido completo para gerenciar agendamentos em barbearias e salões de beleza.

## 🎯 Funcionalidades

- ✅ **Agendamento de Clientes** - Reserve horários disponíveis
- ✅ **Gestão de Prestadores** - Controle barbeiros e cabeleireiros
- ✅ **Sistema de Pagamento** - Integração com Stripe
- ✅ **Histórico de Clientes** - Rastreie clientes e serviços
- ✅ **Painel Administrativo** - Controle completo do negócio
- ✅ **Notificações** - Lembretes automáticos
- ✅ **Avaliações** - Sistema de feedback de clientes
- ✅ **Multi-plataforma** - Web, iOS e Android

## 📱 Tecnologias

### Backend
- **Node.js** + Express
- **MongoDB** para banco de dados
- **JWT** para autenticação
- **Stripe API** para pagamentos
- **Firebase** para notificações

### Frontend Mobile
- **React Native** + Expo
- Funciona em iOS e Android
- Suporte offline

### Frontend Web
- **React** + Vite
- **Tailwind CSS** para estilos
- **Redux** para gerenciamento de estado

## 📁 Estrutura do Projeto

```
barber-saas/
├── backend/              # API Node.js
│   ├── src/
│   │   ├── controllers/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── middleware/
│   │   ├── services/
│   │   ├── config/
│   │   └── app.js
│   ├── .env.example
│   └── package.json
│
├── mobile/               # React Native + Expo
│   ├── app/
│   ├── screens/
│   ├── components/
│   ├── services/
│   ├── hooks/
│   ├── context/
│   └── app.json
│
├── web/                  # React Web
│   ├── src/
│   │   ├── pages/
│   │   ├── components/
│   │   ├── services/
│   │   ├── hooks/
│   │   ├── redux/
│   │   └── App.jsx
│   └── package.json
│
├── shared/               # Tipos e utilitários compartilhados
│   ├── types/
│   ├── utils/
│   └── constants/
│
└── docs/                 # Documentação
    ├── API.md
    ├── DATABASE.md
    └── DEPLOYMENT.md
```

## 🚀 Quick Start

### Backend
```bash
cd backend
npm install
npm run dev
```

### Mobile
```bash
cd mobile
npm install
npx expo start
```

### Web
```bash
cd web
npm install
npm run dev
```

## 🔐 Autenticação

- JWT (JSON Web Tokens)
- Refresh tokens para segurança
- Suporte para 3 tipos de usuários:
  - Cliente
  - Prestador de Serviço
  - Administrador

## 💳 Pagamentos

Integração com **Stripe** para:
- Pagamento de agendamentos
- Recebimentos do negócio
- Relatórios financeiros

## 📧 Notificações

**Firebase Cloud Messaging** para:
- Confirmação de agendamentos
- Lembretes 1 hora antes
- Cancelamento de agendamentos
- Promoções e ofertas

## 📊 Banco de Dados

**MongoDB** com as seguintes coleções:
- Users (clientes, prestadores, admin)
- Services (serviços oferecidos)
- Appointments (agendamentos)
- Reviews (avaliações)
- Payments (pagamentos)
- Businesses (dados da barbearia/salão)

## 📖 Documentação

- [API Documentation](./docs/API.md)
- [Database Schema](./docs/DATABASE.md)
- [Deployment Guide](./docs/DEPLOYMENT.md)

## 👤 Autor

[@gaudas541](https://github.com/gaudas541)

## 📝 Licença

MIT License - veja o arquivo LICENSE para detalhes
