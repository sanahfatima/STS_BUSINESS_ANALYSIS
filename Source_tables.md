# Source tables/infrastructure
## System of record tables 

table names and columns to be added, what is the table answering mentioned
additions in tables, columns are welcome. 

### Clients: 
CREATE TABLE src_clients (
    id              BIGINT PRIMARY KEY,
    client_name     TEXT,
    industry        TEXT, (transport, non transport) 
    country         TEXT,
    state           TEXT,
    created_at      TIMESTAMP,
    status          TEXT); (active, not active) 
### Answers: 
- Is our client?
- When they joined 
- Their status/portal access (username for client is their client_id)

### Services: 
CREATE TABLE src_services (
    id              BIGINT PRIMARY KEY,
    service_name    TEXT,
    service_category TEXT,
    base_price      NUMERIC(12,2),
    active_flag     BOOLEAN, 
    created_at      TIMESTAMP);
### Answers: Service catalog (theory excluded) 

### Invoices: 
CREATE TABLE src_invoices (
    id              BIGINT PRIMARY KEY,
    client_id       BIGINT,
    invoice_date    DATE,
    invoice_status  TEXT,     -- paid / unpaid / canceled
    total_amount    NUMERIC(12,2),
    created_at      TIMESTAMP
    payment_date    DATE,
    amount_paid     NUMERIC(12,2),
    payment_method  TEXT
);
### Answers: (need to add more columns) 
- Over the year invoices paid info per client 
- Financial/revenue findings 
- Need to differentiate gov and sts fee

### Orders: 
CREATE TABLE src_order_services (
    id              BIGINT PRIMARY KEY,
    invoice_id      BIGINT,
    client_id       BIGINT,
    service_id      BIGINT,
    quantity        INT DEFAULT 1,
    unit_price     NUMERIC(12,2),
    created_at      TIMESTAMP);
### Answers: (need to add more columns)
Tracking services per client 
Tracking renewals 
Tracking late filings 
Need to differentiate gov and sts fee
Service performance 




