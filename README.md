# sql-loyalty-card-analysis
Analisis masivo de tarjetas de cliente distinguido - sql server
# Loyalty Card Purchase Analysis — SQL Server

**Author:** Abraham Zaragoza  
**Role target:** Data Analyst / Analista de Datos  
**Tech stack:** SQL Server, SAP Business One, TruPos POS

---

## Business Problem

The company had a loyalty card system for distinguished customers, but there was **no way to analyze all customers at once**. The only option was to look up each customer **one by one** through a Crystal Reports interface.

This meant:
- ❌ No visibility of monthly performance across all customers
- ❌ No way to identify which customers were close to activation
- ❌ No mass reporting for business decisions

---

## Solution

I developed a SQL query that extracts and summarizes **all customers' loyalty card purchases in a single result**, broken down by month, allowing the business to:

- See every customer's monthly spending in one view
- Identify **ACTIVE** customers (≥ $4,000 MXN/month)
- Identify **INACTIVE** customers and how much they need to activate
- Filter by any date range

---

## Files

| File | Description |
|------|-------------|
| `queries/movimientos_por_cliente_y_mes.sql` | Main query — monthly summary for all customers |

---

## Key SQL Concepts Used

- `JOIN` between POS and ERP tables (TruPos + SAP B1)
- `GROUP BY` with date range filtering
- `CASE WHEN` for business logic (active/inactive status)
- Aggregate functions: `SUM`, `COUNT`, `MIN`
- Date conversion with `CONVERT`

---

## Sample Output

| Periodo | Cliente | Tarjeta | TotalMes | Estatus | LeFalta |
|---------|---------|---------|----------|---------|---------|
| 202602 | Juan Pérez | 1073 | $3,500 | INACTIVO | $500 |
| 202603 | Juan Pérez | 1073 | $6,856 | ACTIVO | $0 |
| 202604 | María López | 1052 | $4,200 | ACTIVO | $0 |

---

##  Impact

> Transformed a one-by-one manual lookup into a **mass analysis report**, enabling data-driven decisions on customer loyalty performance for the first time.

---

*Built from a real business need — no existing report covered this use case.*
