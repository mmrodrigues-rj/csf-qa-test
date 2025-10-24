# 🧪 CSF-QA-TEST — API Test Automation (Banco Carrefour Challenge)

![API Tests](https://github.com/mmrodrigues-rj/CSF-QA-TEST/actions/workflows/api-tests.yml/badge.svg)
![Negative API Tests](https://github.com/mmrodrigues-rj/CSF-QA-TEST/actions/workflows/negative-tests.yml/badge.svg)

Automação de testes de API desenvolvida como parte do **Desafio Banco Carrefour – QA Automation**.  
O projeto cobre autenticação JWT, operações CRUD em `/users`, validação de contratos, limites de requisição (Rate Limit) e cenários negativos, utilizando **Postman**, **Newman** e **GitHub Actions**.

---

## 🧰 Stack Técnica
| Componente | Descrição |
|-------------|------------|
| **Postman** | Criação e organização dos testes de API |
| **Newman** | Execução automatizada da coleção no terminal e CI |
| **Node.js 20+** | Ambiente de execução |
| **GitHub Actions** | Pipeline de integração contínua (CI) |
| **newman-reporter-htmlextra** | Geração de relatórios HTML detalhados |

---

## 🧩 Estrutura do Projeto

```
CSF-QA-TEST/
│
├── .github/
│   └── workflows/
│       ├── api-tests.yml           # Executa toda a suíte de testes
│       └── negative-tests.yml      # Executa apenas os cenários negativos
│
├── postman/
│   ├── collection.json             # Coleção completa de testes (CRUD, negativos, rate limit)
│   ├── environment.json            # Variáveis de ambiente (base_url, jwt, credenciais)
│   └── schemas/                    # (Opcional) JSON Schemas para validação de contrato
│
├── reports/                        # Relatórios gerados automaticamente (HTML, JUnit)
│
├── README.md                       # Este arquivo 😄
└── Banco Carrefour - Desafio de Automação de Testes de API.pdf
```

---

## ⚙️ Execução Local

### 1️⃣ Instale as dependências
```bash
npm install -g newman newman-reporter-htmlextra
```

### 2️⃣ Execute a suíte completa
```bash
newman run postman/collection.json \
  -e postman/environment.json \
  --reporters cli,htmlextra,junit \
  --reporter-htmlextra-export reports/report.html \
  --reporter-junit-export reports/junit.xml
```

### 3️⃣ Execute apenas os testes negativos
```bash
newman run postman/collection.json \
  -e postman/environment.json \
  --folder "Negative Tests" \
  --reporters cli,htmlextra,junit \
  --reporter-htmlextra-export reports/negative-report.html \
  --reporter-junit-export reports/negative-junit.xml
```

---

## 🚀 Execução Automática (GitHub Actions)

O pipeline é disparado automaticamente a cada **push** ou **pull request** no branch `main`.  
Ele realiza:
1. Instalação do Node.js e dependências  
2. Execução dos testes via **Newman**  
3. Geração dos relatórios HTML e JUnit  
4. Upload dos relatórios como artefatos no GitHub Actions  

Você pode acompanhar os resultados em:  
📍 **GitHub → Actions → [API Tests - CSF-QA-TEST](https://github.com/mmrodrigues-rj/CSF-QA-TEST/actions)**

---

## 📊 Relatórios

Após a execução:
- **HTML Report:** `reports/report.html`  
- **JUnit Report:** `reports/junit.xml`

Nos testes negativos:
- **HTML Report:** `reports/negative-report.html`  
- **JUnit Report:** `reports/negative-junit.xml`

---

## 🧠 Casos de Teste Principais

| Categoria | Descrição |
|------------|------------|
| **Auth** | Login e geração de token JWT |
| **Users (CRUD)** | Criação, listagem, busca, atualização e exclusão de usuários |
| **Rate Limit** | Execução de múltiplas requisições para validar limite da API |
| **Negative Tests** | E-mail duplicado, campos obrigatórios, ID inexistente, payload inválido |

---

## ✨ Autor

**Marcelo Rodrigues**  
👨‍💻 QA Automation Engineer  
📫 [LinkedIn](https://www.linkedin.com/in/marcelo-rodrigues)  
📦 Projeto: [CSF-QA-TEST](https://github.com/mmrodrigues-rj/CSF-QA-TEST)
