# 🔌 API Documentation

## Base URL
```
http://localhost:5000/api
```

## Authentication
Todas as requisições devem incluir o header:
```
Authorization: Bearer <jwt_token>
```

## Endpoints

### Auth

#### Register
```
POST /auth/register
Content-Type: application/json

{
  "name": "João Silva",
  "email": "joao@example.com",
  "phone": "(11) 99999-9999",
  "password": "senha123",
  "role": "client" // ou "provider"
}

Response: 200 OK
{
  "token": "jwt_token",
  "refreshToken": "refresh_token",
  "user": { ... }
}
```

#### Login
```
POST /auth/login
Content-Type: application/json

{
  "email": "joao@example.com",
  "password": "senha123"
}

Response: 200 OK
{
  "token": "jwt_token",
  "refreshToken": "refresh_token",
  "user": { ... }
}
```

#### Refresh Token
```
POST /auth/refresh-token
Content-Type: application/json

{
  "refreshToken": "refresh_token"
}

Response: 200 OK
{
  "token": "new_jwt_token"
}
```

### Users

#### Get Profile
```
GET /users/:id
Headers: Authorization: Bearer <token>

Response: 200 OK
{
  "user": { ... }
}
```

#### Update Profile
```
PUT /users/:id
Headers: Authorization: Bearer <token>
Content-Type: application/json

{
  "name": "novo nome",
  "bio": "nova bio",
  "avatar": "url"
}

Response: 200 OK
{
  "user": { ... }
}
```

### Services

#### List Services
```
GET /services?businessId=<id>

Response: 200 OK
{
  "services": [ ... ]
}
```

#### Get Service
```
GET /services/:id

Response: 200 OK
{
  "service": { ... }
}
```

#### Create Service
```
POST /services
Headers: Authorization: Bearer <token>
Content-Type: application/json

{
  "name": "Corte de Cabelo",
  "description": "Corte moderno",
  "category": "haircut",
  "price": 50,
  "duration": 30,
  "businessId": "id"
}

Response: 201 Created
{
  "service": { ... }
}
```

### Appointments

#### List Appointments
```
GET /appointments?status=scheduled&businessId=<id>
Headers: Authorization: Bearer <token>

Response: 200 OK
{
  "appointments": [ ... ]
}
```

#### Create Appointment
```
POST /appointments
Headers: Authorization: Bearer <token>
Content-Type: application/json

{
  "clientId": "id",
  "providerId": "id",
  "serviceId": "id",
  "businessId": "id",
  "startTime": "2024-01-15T10:00:00Z",
  "notes": "opcional"
}

Response: 201 Created
{
  "appointment": { ... }
}
```

#### Get Available Slots
```
GET /appointments/available-slots/:providerId?date=2024-01-15&serviceId=<id>

Response: 200 OK
{
  "slots": [
    "10:00",
    "10:30",
    "11:00",
    ...
  ]
}
```

#### Cancel Appointment
```
POST /appointments/:id/cancel
Headers: Authorization: Bearer <token>
Content-Type: application/json

{
  "reason": "motivo do cancelamento"
}

Response: 200 OK
{
  "appointment": { ... }
}
```

### Reviews

#### Create Review
```
POST /reviews
Headers: Authorization: Bearer <token>
Content-Type: application/json

{
  "appointmentId": "id",
  "rating": 5,
  "comment": "Excelente serviço!",
  "serviceQuality": 5,
  "professionalism": 5,
  "timeliness": 5,
  "cleanliness": 5,
  "value": 5
}

Response: 201 Created
{
  "review": { ... }
}
```

#### Get Reviews
```
GET /reviews?providerId=<id>&businessId=<id>

Response: 200 OK
{
  "reviews": [ ... ],
  "avgRating": 4.8
}
```

### Payments

#### Create Payment Intent
```
POST /payments/create-payment-intent
Headers: Authorization: Bearer <token>
Content-Type: application/json

{
  "appointmentId": "id",
  "amount": 5000, // em centavos
  "currency": "brl"
}

Response: 200 OK
{
  "clientSecret": "pi_secret",
  "paymentIntentId": "pi_123"
}
```

#### Webhook
```
POST /payments/webhook

Stripe enviará eventos:
- payment_intent.succeeded
- payment_intent.payment_failed
```

### Businesses

#### Get Business
```
GET /businesses/:id

Response: 200 OK
{
  "business": { ... }
}
```

#### Create Business
```
POST /businesses
Headers: Authorization: Bearer <token>
Content-Type: application/json

{
  "name": "Barbearia do João",
  "phone": "(11) 98765-4321",
  "email": "contato@barbearia.com",
  "address": { ... },
  "operatingHours": { ... }
}

Response: 201 Created
{
  "business": { ... }
}
```

## Status Codes

- `200 OK` - Sucesso
- `201 Created` - Criado com sucesso
- `400 Bad Request` - Erro na requisição
- `401 Unauthorized` - Não autenticado
- `403 Forbidden` - Acesso negado
- `404 Not Found` - Recurso não encontrado
- `500 Internal Server Error` - Erro do servidor
