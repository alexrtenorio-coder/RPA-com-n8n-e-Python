# RPA-com-n8n-e-Python
RPA com n8n e Python
# 🤖 RPA com n8n e Python

Automação de processos utilizando **n8n + Python**, desenvolvida para demonstrar a integração entre ferramentas de automação, processamento de dados e APIs.

## 📌 Sobre o projeto

Este projeto implementa um processo de **RPA (Robotic Process Automation)** utilizando o **n8n como orquestrador** e **Python para processamento e validação dos dados**.

A automação recebe informações, realiza validações e processamento utilizando regras de negócio e retorna o resultado ao fluxo do n8n.

## 🎯 Objetivo

Demonstrar na prática como integrar:

* 🔄 Automação de processos
* 🐍 Python
* ⚙️ n8n
* 🌐 APIs
* 🔗 Webhooks
* 🐳 Docker
* 📊 Processamento e validação de dados
* 📝 Logs e tratamento de erros

## 🔄 Fluxo da automação

```text
┌──────────────┐
│    Webhook   │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│     n8n      │
│ Orquestração │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│    Python    │
│ Processamento│
│ e validação  │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│ Resultado da │
│ automação    │
└──────┬───────┘
       │
       ▼
┌──────────────┐
│     n8n      │
│ Notificação  │
└──────────────┘
```

## 🛠️ Tecnologias utilizadas

| Tecnologia       | Utilização                |
| ---------------- | ------------------------- |
| **n8n**          | Orquestração do workflow  |
| **Python**       | Processamento e validação |
| **Webhook**      | Recebimento de dados      |
| **HTTP Request** | Integração com APIs       |
| **Docker**       | Ambiente de execução      |
| **Git/GitHub**   | Versionamento             |

## 📁 Estrutura do projeto

```text
rpa-n8n-python/
│
├── README.md
│
├── workflow/
│   └── rpa_workflow.json
│
├── python/
│   ├── process_data.py
│   └── requirements.txt
│
├── data/
│   └── exemplo.json
│
├── docker-compose.yml
│
└── .gitignore
```

## 🐍 Processamento em Python

O Python recebe os dados enviados pelo fluxo e executa as regras de validação.

Exemplo:

```python
import sys
import json


def processar_dados(dados):
    nome = dados.get("nome", "").strip()
    email = dados.get("email", "").strip()
    valor = dados.get("valor", 0)

    if not nome or not email:
        return {
            "status": "ERRO",
            "mensagem": "Nome ou e-mail não informado."
        }

    if valor <= 0:
        return {
            "status": "ERRO",
            "mensagem": "Valor inválido."
        }

    return {
        "status": "PROCESSADO",
        "nome": nome,
        "email": email,
        "valor": valor,
        "mensagem": "Dados processados com sucesso."
    }


if __name__ == "__main__":
    entrada = sys.stdin.read()
    dados = json.loads(entrada)

    resultado = processar_dados(dados)

    print(json.dumps(resultado, ensure_ascii=False))
```

## 📥 Exemplo de entrada

```json
{
  "nome": "Alex",
  "email": "alex@example.com",
  "valor": 150
}
```

## 📤 Resultado

```json
{
  "status": "PROCESSADO",
  "nome": "Alex",
  "email": "alex@example.com",
  "valor": 150,
  "mensagem": "Dados processados com sucesso."
}
```

## 🚀 Como executar

### 1. Clonar o repositório

```bash
git clone https://github.com/SEU-USUARIO/rpa-n8n-python.git
```

### 2. Entrar no diretório

```bash
cd rpa-n8n-python
```

### 3. Executar o ambiente

```bash
docker compose up -d
```

### 4. Acessar o n8n

Após iniciar o container, acesse o endereço configurado para o n8n no ambiente local.

### 5. Importar o workflow

No n8n:

```text
Import Workflow
        ↓
workflow/rpa_workflow.json
```

## 🔐 Segurança

Informações sensíveis não devem ser armazenadas diretamente no código.

Utilize:

* Variáveis de ambiente
* Credentials do n8n
* Tokens protegidos
* `.env`
* `.gitignore`

Exemplo de `.gitignore`:

```text
.env
__pycache__/
*.pyc
node_modules/
```

## 📈 Possíveis melhorias

O projeto pode ser expandido para incluir:

* [ ] Banco de dados
* [ ] Integração com APIs externas
* [ ] Dashboard de acompanhamento
* [ ] Sistema de logs
* [ ] Tratamento avançado de exceções
* [ ] Retry automático
* [ ] Notificações via Telegram ou WhatsApp
* [ ] Integração com e-mail
* [ ] Agendamento automático
* [ ] Monitoramento das execuções
* [ ] Docker Compose completo
* [ ] Testes automatizados

## 💡 Aplicações práticas

A mesma arquitetura pode ser utilizada em processos como:

* Processamento de cadastros
* Validação de documentos
* Atualização de sistemas
* Processamento de planilhas
* Integração entre APIs
* Notificações automáticas
* Processos financeiros
* Automação de atendimento
* ETL e tratamento de dados

## 👨‍💻 Autor

**Alex Rogério Soares Tenório**

Projeto desenvolvido para estudos e demonstração prática de conhecimentos em:

**RPA • n8n • Python • APIs • Automação • Integração de Sistemas • Docker • Dados**

---

⭐ Se este projeto foi útil, considere deixar uma estrela no repositório.
