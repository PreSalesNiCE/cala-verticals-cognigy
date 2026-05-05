# Integration Guide - One Seguro

Este guia explica como conectar o One Seguro com seus sistemas reais (backend, databases, APIs).

**O que é integração?** Conectar o agente IA com os sistemas que guardam dados (seguradoras, bancos de dados, etc).

---

## 📋 Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Available Integrations](#available-integrations)
- [Step-by-Step Setup](#step-by-step-setup)
- [Testing](#testing)
- [Troubleshooting](#troubleshooting)

---

## Overview

### Sem Integração (Demo Mode)

```
Customer → AI Agent → Simulated Response
                      (no data saved)

Exemplo:
User: "I want to report a claim"
Agent: "Claim registered! Number: SIN-2025-001847"
       ↑ Este número é gerado fake, não salva em nada
```

### Com Integração (Production Mode)

```
Customer → AI Agent → Your Backend APIs → Your Database
                      ↓
                      Saves claim
                      Sends email
                      Updates status
                      Generates real ID

Exemplo:
User: "I want to report a claim"
Agent: "Claim registered! Number: SIN-2025-001847"
       ↑ Número real, guardado no seu banco de dados
       ↑ Email enviado
       ↑ Pode ser consultado depois
```

---

## Architecture

### Data Flow

```
┌─────────────────────────────────────────────────────────────┐
│                     COGNIGY AGENT                           │
│  (One Seguro AI flows)                                      │
└──────┬──────────────────────────────────────────────────────┘
       │
       │ HTTP REST calls
       ↓
┌──────────────────────────────────────────────────────────────┐
│              YOUR BACKEND APIS                               │
│  ├── POST /claims/create                                    │
│  ├── GET /claims/{id}                                       │
│  ├── POST /notifications/email                              │
│  └── GET /customers/{cpf}                                   │
└──────┬──────────────────────────────────────────────────────┘
       │
       │ Query/Update
       ↓
┌──────────────────────────────────────────────────────────────┐
│              YOUR DATABASE                                   │
│  ├── Claims table                                           │
│  ├── Customers table                                        │
│  ├── Documents table                                        │
│  └── Status history                                         │
└──────────────────────────────────────────────────────────────┘
```

---

## Available Integrations

### Integration 1: Claims Management API

**Purpose:** Criar, ler, atualizar sinistros

**What it does:**
- Cria novo sinistro no banco
- Gera ID único
- Salva informações
- Retorna confirmação

**Endpoints needed:**
```
POST /api/v1/claims/create
GET /api/v1/claims/{claim_id}
PUT /api/v1/claims/{claim_id}
```

**Example:**

```javascript
// Request
POST http://seu-backend.com/api/v1/claims/create
Content-Type: application/json
Authorization: Bearer YOUR_API_KEY

{
  "customer_cpf": "12345678901",
  "claim_type": "accident",
  "date": "2025-05-04",
  "location": "Avenida Paulista",
  "description": "Car collision"
}

// Response
{
  "success": true,
  "claim_id": "SIN-2025-001847",
  "created_at": "2025-05-04T10:30:00Z"
}
```

---

### Integration 2: Email Notification API

**Purpose:** Enviar confirmações por email

**What it does:**
- Envia email de confirmação
- Inclui número do sinistro
- Anexa documentos
- Rastreia envio

**Endpoints needed:**
```
POST /api/v1/notifications/email
```

**Example:**

```javascript
// Request
POST http://seu-backend.com/api/v1/notifications/email
Content-Type: application/json
Authorization: Bearer YOUR_API_KEY

{
  "recipient": "customer@email.com",
  "claim_id": "SIN-2025-001847",
  "template": "claim_confirmation",
  "language": "pt-BR"
}

// Response
{
  "success": true,
  "email_sent": true,
  "message_id": "MSG-12345"
}
```

---

### Integration 3: Customer API

**Purpose:** Buscar dados do cliente

**What it does:**
- Valida CPF
- Retorna dados do cliente
- Verifica se é cliente
- Obtém histórico

**Endpoints needed:**
```
GET /api/v1/customers/{cpf}
```

**Example:**

```javascript
// Request
GET http://seu-backend.com/api/v1/customers/12345678901
Authorization: Bearer YOUR_API_KEY

// Response
{
  "success": true,
  "customer": {
    "name": "João Silva",
    "cpf": "12345678901",
    "phone": "+55 11 98765-4321",
    "email": "joao@email.com",
    "is_active": true,
    "has_claims": 2
  }
}
```

---

### Integration 4: Document Upload API

**Purpose:** Guardar documentos (fotos, PDFs)

**What it does:**
- Recebe arquivo
- Armazena no S3/cloud
- Retorna URL
- Vincula ao sinistro

**Endpoints needed:**
```
POST /api/v1/claims/{claim_id}/documents
```

**Example:**

```javascript
// Request
POST http://seu-backend.com/api/v1/claims/SIN-2025-001847/documents
Content-Type: multipart/form-data
Authorization: Bearer YOUR_API_KEY

Files:
- damage-photo-01.jpg
- damage-photo-02.jpg
- police-report.pdf

// Response
{
  "success": true,
  "documents": [
    {
      "id": "DOC-001",
      "filename": "damage-photo-01.jpg",
      "url": "https://cdn.seu-domain.com/claims/SIN-2025-001847/damage-photo-01.jpg"
    }
  ]
}
```

---

## Step-by-Step Setup

### Step 1: Configure API Endpoint in Cognigy

**In Cognigy Dashboard:**

1. Go to **Settings** → **Integrations** (or **Connections**)
2. Click **New Integration** / **Add Connection**
3. Choose **REST API** or **HTTP**

### Step 2: Create Connection for Claims API

**Name:** `One Seguro - Claims Management`

**Configuration:**

```
Base URL: https://api.seu-backend.com
Port: 443 (HTTPS)
Protocol: REST API
Authentication: Bearer Token
API Key: YOUR_API_KEY_HERE
```

### Step 3: Create Connection for Email API

**Name:** `One Seguro - Notifications`

**Configuration:**

```
Base URL: https://api.seu-backend.com
Endpoint: /api/v1/notifications/email
Authentication: Bearer Token
```

### Step 4: Connect to Flow Nodes

**In Cognigy flow editor:**

1. Drag **Execute REST Call** node (or similar)
2. Select integration: `Claims Management`
3. Set method: `POST`
4. Set endpoint: `/api/v1/claims/create`
5. Map input data:
   ```
   customer_cpf: input.cpf
   claim_type: input.claimType
   date: input.date
   ```

### Step 5: Handle Response

**In your flow:**

```
REST Call Node
├── On Success
│   ├── Extract claim_id
│   ├── Save to context
│   ├── Send confirmation email
│   └── Reply to user
│
└── On Error
    ├── Log error
    ├── Escalate to human
    └── Apologize to user
```

---

## Testing

### Test Claims API

**Via Cognigy Debug Mode:**

1. Open flow in Cognigy
2. Click **Debug** button
3. Start conversation:
   - User: "I want to report a claim"
   - Watch the REST call execute
   - Check response in logs

**Via Postman (API Testing Tool):**

```
Method: POST
URL: https://api.seu-backend.com/api/v1/claims/create
Headers:
  Authorization: Bearer YOUR_API_KEY
  Content-Type: application/json

Body:
{
  "customer_cpf": "12345678901",
  "claim_type": "accident",
  "date": "2025-05-04",
  "location": "Test Location"
}

Expected Response:
{
  "success": true,
  "claim_id": "SIN-2025-001847"
}
```

### Test End-to-End

1. **Start conversation:** "I want to report a claim"
2. **Provide information:** Answer agent questions
3. **Submit:** Confirm details
4. **Check backend:** Verify claim created in database
5. **Check email:** Verify confirmation sent
6. **Check status:** Verify claim appears in status check

---

## Integration Checklist

Before going to production:

**Setup**
- [ ] API endpoints documented
- [ ] Authentication working
- [ ] Endpoints accessible from Cognigy
- [ ] API keys secure (use environment variables)

**Testing**
- [ ] Create claim flow works
- [ ] Read claim flow works
- [ ] Email sends correctly
- [ ] File upload works
- [ ] Error handling tested
- [ ] All languages tested

**Security**
- [ ] Using HTTPS
- [ ] API keys in environment, not hardcoded
- [ ] Rate limiting configured
- [ ] Validation on all inputs
- [ ] Sensitive data not logged

**Monitoring**
- [ ] Logs configured
- [ ] Error alerts set up
- [ ] Performance monitored
- [ ] Health checks in place

---

## Common Integration Patterns

### Pattern 1: Synchronous (Real-time)

```
User submits → Agent calls API → Gets response immediately → Confirms to user

Best for: Quick operations (validation, simple lookups)
Risk: If API is slow, user waits
```

### Pattern 2: Asynchronous (Delayed)

```
User submits → Agent queues job → Confirms immediately → Backend processes later

Best for: Long operations (document processing, email sending)
Risk: User doesn't get result immediately
```

### Pattern 3: Hybrid

```
User submits → Immediate confirmation → Backend processes async → Email with result

Best for: Claims (fast confirmation, email with details)
```

---

## Troubleshooting

### Issue: API not responding

**Symptoms:**
- Flow hangs after REST call
- User times out
- No error message

**Solutions:**
1. Check API endpoint URL (typo?)
2. Verify authentication token
3. Check firewall/network access
4. Add timeout handling
5. Check API logs

### Issue: Invalid response format

**Symptoms:**
- REST call succeeds but flow breaks
- "Cannot read property X"
- Claim not created

**Solutions:**
1. Check API response format matches expected
2. Add response validation
3. Log full response for debugging
4. Test with Postman first

### Issue: Emails not sending

**Symptoms:**
- Claim created OK
- No email received
- No error in logs

**Solutions:**
1. Verify email API is connected
2. Check recipient email address
3. Check email template
4. Look in spam folder
5. Test email API separately

---

## Example: Complete Claims Flow with Integrations

```
START
  ↓
Agent: "What type of claim?"
User: "Car accident"
  ↓
[Decision Node - Validate Claim Type]
  ↓
Agent: "When did it happen?"
User: "Yesterday"
  ↓
[Collect all information]
  ↓
Agent: "Confirming details..."
  ↓
[REST Call: POST /claims/create]
  ├─ Success:
  │   ├─ Claim ID: SIN-2025-001847
  │   ├─ [REST Call: POST /notifications/email]
  │   ├─ Agent: "Claim registered! Check your email."
  │   └─ END
  │
  └─ Error:
      ├─ Log error
      ├─ Agent: "System error, connecting human agent"
      └─ Escalate to human
```

---

## Environment Variables

**Best practice:** Never hardcode API keys

**Instead, use environment variables:**

```javascript
// In Cognigy (Execution Settings or Settings)
CLAIMS_API_KEY = your-secret-key
CLAIMS_API_URL = https://api.seu-backend.com
NOTIFICATION_API_KEY = your-secret-key
```

**In REST nodes:**

```
Authorization: Bearer {{CLAIMS_API_KEY}}
URL: {{CLAIMS_API_URL}}/api/v1/claims/create
```

---

## Monitoring & Logging

### What to Log

✅ API requests (method, URL, status)
✅ Request timing (how long each API call takes)
✅ Response status (success/error)
✅ Claim IDs created
✅ Escalations (when human needed)

❌ API keys
❌ CPFs (unless necessary)
❌ Full email addresses
❌ Password data

### Example Log

```
[2025-05-04 10:30:15] CLAIM_CREATED
  Claim ID: SIN-2025-001847
  Type: accident
  Customer: CPF masked (****78901)
  API Response Time: 234ms
  Email Sent: Yes

[2025-05-04 10:30:45] EMAIL_SENT
  Message ID: MSG-12345
  Recipient: customer@email.com
  Template: claim_confirmation
  Status: Success
```

---

## Performance Tips

1. **Use caching** - Don't call API for same customer twice
2. **Set timeouts** - Don't wait forever for API response
3. **Async operations** - Send email in background, don't wait
4. **Batch requests** - If uploading multiple files, batch them
5. **Monitor latency** - Track which APIs are slow

---

## Rollback Plan

If integration breaks in production:

1. **Immediately:** Fall back to demo mode (no API calls)
2. **Quick fix:** Update API endpoint/key
3. **If unfixable:** Escalate all claims to human agents
4. **Communicate:** Notify customers of issue
5. **Post-mortem:** Investigate what went wrong

---

## Next Steps

1. **Document your APIs** - What endpoints exist?
2. **Get API credentials** - Keys, URLs, auth method
3. **Test with Postman** - Verify APIs work standalone
4. **Create Cognigy connections** - One per API
5. **Build flow nodes** - REST call nodes with proper mapping
6. **Test end-to-end** - Full conversation with real data
7. **Deploy to production** - Monitor closely first week

---

## Resources

- **Cognigy REST API Docs:** [docs.cognigy.com/rest](https://docs.cognigy.com)
- **Postman Tutorial:** [postman.com/learning](https://learning.postman.com/)
- **API Best Practices:** [restfulapi.net](https://www.restfulapi.net/)

---

**Last Updated:** May 4, 2025  
**Version:** 1.0