# 🗣️ Chat with Your Database
## Natural Language to SQL using Oracle AI Database 26ai — Select AI

<div align="center">

![Oracle 26ai](https://img.shields.io/badge/Oracle_AI_Database-26ai-F80000?style=for-the-badge&logo=oracle&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.12-3776AB.svg?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o-412991?style=for-the-badge&logo=openai&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)


*Type plain English → Oracle writes the SQL → Results in seconds*

• [📓 Open Notebook](oracle_26ai_select_ai.ipynb) • [☁️ Oracle Free Tier](https://cloud.oracle.com)

</div>

---

## 🎯 What This Project Does

Every enterprise has critical data locked inside Oracle databases — accessible only to SQL-literate engineers. **Oracle AI Database 26ai's Select AI** eliminates this bottleneck.

This tutorial demonstrates a fully self-contained, reproducible demo where:

- 🏪 A realistic **retail sales database** is built from scratch (4 tables, ~1,750 rows)
- 🤖 An **LLM provider** (OpenAI GPT-4o or Cohere Command R+) is registered directly inside Oracle
- 💬 Business users **type plain English** and get instant, accurate SQL results
- 📊 All **4 Select AI modes** are demonstrated live in a Jupyter Notebook

> ✅ **100% free** — runs entirely on Oracle Cloud Always Free Tier. No credit card required.

---

## ✨ Oracle AI Database 26ai — Features Showcased

### 1. 🧠 Select AI — Natural Language to SQL
The core feature. Type any business question in plain English — Oracle generates and executes the SQL automatically.

```
You type  →  "What were the top 5 products by revenue last month?"

Oracle    →  SELECT p.name, SUM(oi.quantity * oi.unit_price * (1 - oi.discount)) AS revenue
             FROM products p
             JOIN order_items oi ON p.id = oi.product_id
             JOIN orders o ON oi.order_id = o.id
             WHERE o.status = 'completed'
             AND o.order_date >= ADD_MONTHS(TRUNC(SYSDATE,'MM'),-1)
             GROUP BY p.name
             ORDER BY revenue DESC
             FETCH FIRST 5 ROWS ONLY
```

### 2. 🔍 SHOWSQL Mode — Transparent AI
Reveals the generated SQL **without executing it**. The most educational moment — viewers see exactly how the AI interprets their question. Perfect for teaching SQL through real questions.

```sql
SELECT AI SHOWSQL which customers have not placed an order in the last 90 days?
```

### 3. 📝 NARRATE Mode — Insight as Prose
Returns a **human-readable business summary** instead of a raw data table. Non-technical stakeholders get direct answers without reading tables.

```sql
SELECT AI NARRATE summarize total sales by product category for Q1 2026
```
> *"Electronics led revenue at $47,832 (38% of total), followed by Home & Garden at $28,441 (23%)..."*

### 4. 💬 CHAT Mode — Conversational Data Exploration
Multi-turn conversation grounded in your live database. Oracle retains context across turns — previewing the **agentic AI direction** of 26ai.

```sql
SELECT AI CHAT what can you tell me about our customer base?
-- Follow-up:
SELECT AI CHAT which city has the most premium customers?
-- Context retained in next turn:
SELECT AI CHAT and what is the average order value for those customers?
```

### 5. 🔌 DBMS_CLOUD_AI — LLM Provider Flexibility
Demonstrates Oracle's **open ecosystem** — the same profile works with OpenAI GPT-4o **or** Cohere Command R+. Zero vendor lock-in. Switch providers by changing one parameter.

```python
# OpenAI
{"provider": "openai",  "model": "gpt-4o",          "credential_name": "OPENAI_CRED"}

# Cohere — same structure, zero other changes
{"provider": "cohere",  "model": "command-r-plus",   "credential_name": "COHERE_CRED"}
```

---

## 🗃️ Retail Sales Schema

A universally understood schema — rich enough for interesting queries, simple enough for any beginner.

| 📋 Table | 🔑 Key Columns | 🎯 Demo Purpose |
|---|---|---|
| `CUSTOMERS` | id, name, email, city, age, segment | Filter by region, demographics, Premium / Standard / Budget |
| `PRODUCTS` | id, name, category, unit_price, stock_quantity | Category analysis, pricing — 5 categories × 10 products |
| `ORDERS` | id, customer_id, order_date, status, total_amount | Time-series (Jan 2025 – Apr 2026), status breakdowns |
| `ORDER_ITEMS` | id, order_id, product_id, quantity, unit_price, discount | Revenue, top products, discount analysis |

**~1,750 rows** of realistic synthetic data generated with Python's Faker library.

---

## 🚀 Quick Start

```bash
# 1. Clone the repository
git clone https://github.com/ridash2005/Text-to-SQL-with-Oracle-AI-DB.git
cd oracle-26ai-select-ai

# 2. Install dependencies (Python 3.12 + uv required)
uv sync

# 3. Configure environment
cp .env.example .env
# Edit .env with your Oracle credentials and LLM API key

# 4. Extract wallet into ./wallet/
# Download from: ADB Console → Database Connection → Download Wallet

# 5. Launch
uv run jupyter notebook oracle_26ai_select_ai.ipynb
```

---

## 🛠️ Tech Stack

| Tool | Version | Purpose |
|---|---|---|
| 🐍 Python | 3.12 | Runtime |
| 📦 uv | latest | Package manager (replaces pip/conda) |
| 🗄️ oracledb | ≥ 3.4.2 | Oracle DB driver — thin mode, no Oracle Client needed |
| ☁️ Oracle ADB 26ai | 26ai | Autonomous Database Always Free Tier |
| 🤖 OpenAI | GPT-4o | LLM provider (primary) |
| 🤖 Cohere | Command R+ | LLM provider (alternative, free trial) |
| 🎭 Faker | ≥ 25.0.0 | Synthetic data generation |
| 🐼 pandas | ≥ 2.0.0 | DataFrame display |
| 🎨 rich | ≥ 14.0.0 | Beautiful notebook output |

---

## ⚙️ Full Environment Setup Guide

### 📋 Step 1 — Oracle Cloud Free Tier Account

1. Go to **https://cloud.oracle.com** → **"Start for free"**
2. Verify email + phone (SMS)
3. Choose your **Home Region** — pick the one closest to you
   ⚠️ *This cannot be changed later. Choose carefully.*
4. No credit card required

> 💡 Always Free resources are **permanent** — they don't expire after the 30-day trial period.

---

### 🗄️ Step 2 — Create Autonomous Database

Navigate: ☰ Hamburger Menu → Oracle Database → Autonomous Database → **Create Autonomous Database**

| ⚙️ Setting | ✅ Value |
|---|---|
| Display name | `oracle26ai-demo` |
| Database name | `ORACLE26AI` |
| Workload type | **Transaction Processing** |
| Always Free | ✅ **Toggle ON** |
| Database version | **26ai** ← select this, NOT 19c or 23ai |
| Admin password | Min 12 chars: uppercase + lowercase + digit + special char |
| Network access | Secure access from everywhere |

Wait ~2 minutes for status: 🟢 **Available**

---

### 💼 Step 3 — Download & Extract Wallet

```bash
# ADB Console → Database Connection → Download Wallet (Instance Wallet)
# Set a wallet password — this becomes WALLET_PASSWORD in .env

mkdir -p ./wallet
cd ./wallet
unzip ~/Downloads/Wallet_ORACLE26AI.zip

# Verify these files exist:
ls
# cwallet.sso  ewallet.p12  keystore.jks  ojdbc.properties
# sqlnet.ora   tnsnames.ora  truststore.jks
```

---

### 🔗 Step 4 — Find Your Connection String

In the **Database Connection** dialog → **Connection Strings**, copy the `_high` entry:

```bash
# Verify it exists in your wallet:
grep "oracle26ai_high" ./wallet/tnsnames.ora
# Expected: oracle26ai_high = (DESCRIPTION= ...
```

This becomes `DB_DSN=oracle26ai_high` in your `.env` file.

---

### 🔑 Step 5 — Get Your LLM API Key

**Option A — OpenAI (Recommended)**
1. Go to **https://platform.openai.com/api-keys**
2. Create new secret key → copy immediately (shown only once)
3. Cost estimate: **< $0.10 total** for the entire tutorial (~$0.005/query)

**Option B — Cohere (Free alternative)**
1. Go to **https://dashboard.cohere.com/api-keys**
2. Generate a Trial key (free, rate-limited — sufficient for tutorial)

---

### 📄 Step 6 — Configure `.env` File

```bash
cp .env.example .env
```

Fill in all values:

```env
# ── Oracle Autonomous Database ────────────────────────────────────────────────
DB_USER=ADMIN
DB_PASSWORD=YourStrongPassword123!

# From tnsnames.ora — use the _high service for best performance
DB_DSN=oracle26ai_high

# ⚠️ MUST be an absolute path — relative paths fail silently on some platforms
WALLET_DIR=/Users/yourname/projects/oracle-26ai-select-ai/wallet
WALLET_PASSWORD=YourWalletPassword

# ── LLM Provider — set ONE ────────────────────────────────────────────────────
OPENAI_API_KEY=sk-proj-xxxxxxxxxxxxxxxxxxxxxxxx
# COHERE_API_KEY=your-cohere-key-here
```

> 🔐 **Security:** `.env` is already in `.gitignore`. Never commit it. Never log it.

---

### 🐍 Step 7 — Python Environment with uv

```bash
# Install uv
curl -LsSf https://astral.sh/uv/install.sh | sh   # macOS / Linux
# brew install uv                                   # macOS Homebrew

# Install all project dependencies into .venv
uv sync

# Launch Jupyter
uv run jupyter notebook

# OR if you prefer JupyterLab
uv run jupyter lab
```

---

### ✅ Step 8 — Grant Network ACL (Required for Select AI)

Run once in **Database Actions → SQL** (accessible from your ADB console):

```sql
-- Allow ADMIN to call external LLM APIs (required for DBMS_CLOUD_AI)
BEGIN
  DBMS_NETWORK_ACL_ADMIN.APPEND_HOST_ACE(
    host       => 'api.openai.com',   -- or 'api.cohere.com' for Cohere
    lower_port => 443,
    upper_port => 443,
    ace        => xs$ace_type(
      privilege_list => xs$name_list('connect'),
      principal_name => 'ADMIN',
      principal_type => xs_acl.ptype_db
    )
  );
  COMMIT;
END;
/
```

---

## 📓 Notebook Walkthrough

| # | Section | What Happens | ⏱️ |
|---|---|---|---|
| 1 | 🔧 Environment Setup | Imports, `.env` validation, Oracle connection test, `DBMS_CLOUD_AI` availability check | ~5 min |
| 2 | 🏗️ Schema & Data | DDL for 4 tables, 200 customers + 50 products + 500 orders via Faker | ~4 min |
| 3 | 🔌 Select AI Profile | LLM credential, profile creation, `SET_PROFILE` activation | ~3 min |
| 4 | 🎬 Live Demo | All 4 modes: `SELECT AI` → `SHOWSQL` → `NARRATE` → `CHAT` | ~8 min |
| 5 | 🚀 Extensions | APEX, PL/SQL agents, BI integration, Python RAG teaser | ~3 min |

**Total runtime: ~19 minutes**

---

## 🔄 Fresh Kernel Checklist

> After kernel restart, always run these cells in order before any `SELECT AI` query:

```
✅  Cell 1  — Imports & package check
✅  Cell 2  — Load .env
✅  Cell 3  — Connect to Oracle ADB
✅  Cell 10 — DBMS_CLOUD_AI.SET_PROFILE  ← REQUIRED every session
```

The credential and profile **persist in Oracle** between sessions. Only `SET_PROFILE` must be re-run per kernel restart.

---

## 🔧 Troubleshooting

| ❌ Error | 🔍 Cause | ✅ Fix |
|---|---|---|
| `ORA-12154: TNS could not resolve` | `DB_DSN` doesn't match tnsnames.ora | `grep high wallet/tnsnames.ora` → copy exact prefix |
| `DPY-6003: wallet not found` | `WALLET_DIR` is relative or wrong | Use absolute path: `/Users/name/.../wallet` |
| `ORA-01017: invalid username/password` | Wrong `DB_PASSWORD` | ADB Console → More Actions → Reset Admin Password |
| `ORA-20000: ORA-24247: Network access denied` | ADMIN lacks ACL to call LLM APIs | Run `DBMS_NETWORK_ACL_ADMIN.APPEND_HOST_ACE` in DB Actions SQL (see Step 8) |
| `ORA-00923: FROM keyword not found` | `SET_PROFILE` not called this session | Re-run Cell 10 before any `SELECT AI` query |
| `DPY-4010: bind variable ":WORD" not provided` | Colon in SQL string parsed as bind var | Avoid passing text with `:word` patterns directly to `cur.execute()` |
| `ORA-00904: DBMS_CLOUD_AI invalid identifier` | Not on Autonomous Database | Select AI is ADB-only — must use ATP or ADW, not Oracle XE / Free Edition |
| `ModuleNotFoundError` | Packages not installed | Run `uv sync` in project directory |

---

## 💡 What is Oracle AI Database 26ai?

| Detail | Value |
|---|---|
| 📅 Announced | October 14, 2025 — Oracle AI World (Larry Ellison keynote) |
| 🚀 Cloud GA | October 2025 |
| 🖥️ On-Premises GA | January 2026 (Linux x86-64) |
| 🔢 Internal Version | `23.26.x.x.x` — built on Oracle 23c base ("26" = 2026 release generation) |
| 🆕 New vs 23ai | Native AI Agents · Enhanced Vector Search (HNSW + IVF) · AI-driven DB management |
| ☁️ Always Free Tier | ✅ Available — 20 GB, forever free |
| 📚 Documentation | https://docs.oracle.com/en/database/oracle/oracle-database/26/ |

---

## 🌍 Real-World Use Cases

```
📊  Executive Dashboards   →  "Show Q3 revenue vs last year by region"
👥  HR Analytics           →  "Which departments have the highest attrition this quarter?"
💰  Finance Reporting      →  "Summarize overdue invoices by customer segment"
📦  Supply Chain           →  "Which products are at risk of stockout in 30 days?"
🎯  Sales Intelligence     →  "Which customers haven't renewed in the past 6 months?"
📣  Marketing              →  "What is the average order value for premium customers in New York?"
```

---

## 🔮 Tutorial Series — What's Next

| # | Video | Topic | Status |
|---|---|---|---|
| 1 | **Select AI** | Natural Language to SQL | ✅ This video |
| 2 | **Vector Search** | Document Q&A inside Oracle 26ai | 🔜 Coming soon |
| 3 | **AI Agents** | Agentic loops with `DBMS_CLOUD_AI.GENERATE` | 🔜 Coming soon |
| 4 | **APEX + AI** | Build a full web app in minutes | 🔜 Coming soon |

---

## 📄 License

This project is licensed under the **MIT License** — free to use, modify, and distribute with attribution.

---

<div align="center">

**🚀 Built with ❤️ using Oracle AI Database 26ai**

**Rickarya Das | April 2026**

[☁️ Get Oracle Cloud Free Tier](https://cloud.oracle.com) &nbsp;•&nbsp; [▶️ Watch the Tutorial](#) &nbsp;•&nbsp; [⭐ Star this Repo](#)

</div>
