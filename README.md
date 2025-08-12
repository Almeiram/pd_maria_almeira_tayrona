# SpertSort 

This is an application that generates a solution for implementing information organization and structuring in a database. The backend is built with **Node.js** and **Express**, and the database is managed with **MySQL**.

---

## Technologies used

- Node.js
- Express.js
- MySQL
- HTML, CSS, JavaScript (Frontend)
- csv-parser (To load data from files CSV)
- vite
- dotenv
---

## Project structure
```bash
SpertSort/
│
├── docs/ # Documentation
│  ...
├── server/ # Backend
│   ...
├── index.html 
├── .env # Variables de entorno
├── .gitignore
└── README.md
```

## Instalation y ejecucion

1. Clone the repository:

```bash
git clone https://github.com/Almeiram/pd_maria_almeira_tayrona.git
```
1. Install dependencies:

```bash
npm install
```

3. Create and configure the file .env:

```bash
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=password
DB_NAME=db_name
DB_PORT=3306
```

4. Initialize the program, it is configured to run the backend and frontend with just this command:
```bash
npm run dev
```

## The server will be available at:

```bash
http://localhost:3000
```

## Endpoints available

```bash
| method | route             | Description                 |
| ------ | ----------------- | --------------------------- |
| GET    | /api/v1/customers | Get all the loans           |
| GET    | /api/v1/customers | Get a client by IDD         |
| POST   | /api/v1/customers | Create a new client         |
| PUT    | /api/v1/customers | Update a client             |
| DELETE | /api/v1/customers | delete a client             |
  
```

## Database documentation

### Database name
`pd_maria_almeira_tayrona`

---

### Entity-relationship diagram
![Entity-relationship diagram](./docs/relational_model.ppg.jpg)

---

### Tables
```bash
#### **clientes**
| ----------------- ------------------------------------------------------------------------ | 
| Field                 | Data type       | constraints| Description|
| ----------------- ------------------------------------------------------------------------ | 
| id_cliente            | int primary key |  not null   |  unique identifier                 |
| nombre_cliente        | varchar(200)    | not null    |                                    |
| numero_identificacion |int |unique      |not null     |                                    |
| direccion             | varchar(200)    | not null    |                                    |
| telefono              |varchar(20)      | not null    |                                    |
| correo_electronico    | varchar(100)    | not null    |                                    | 
| -------------------------------------------------------------------------------------------|

#### **facturas**
| ----------------- --------------------------------------------------------------------------| 
| Field                 | Data type                 | constraints |       Description         |  
| ----------------- --------------------------------------------------------------------------| 
| numero_factura        |varchar(20) intprimay key  |not null     |   unique identifier       |
| plataforma_utilizada  | enum('nequi','daviplata') |             |                           | 
|                       |  varchar(200)             |not null     |                           |
| periodo_facturacion   |date unique  int           | not null    |                           |                     
| monto_facturado       | int |not null             | varchar(200)|                           |      
| monto_pagado          |int varchar(20)            |             |                           |      
| --------------------------------------------------------------------------------------------|

#### **clientes**
| ----------------- ------------------------------------------------------------------------ | 
| Field                 | Data type              | constraints  | Description                | 
| ----------------- ------------------------------------------------------------------------ | 
| iid_transaccion       | varchar(15)            | not null      | primary key               | 
| fecha_hora_transaccion| date not null          |               |                           | 
| monto_transaccion int |                        |               |                           | 
| tipo_transaccion      |varchar(100) not null   |               |                           | 
| id_cliente            |                        |               |                           | 
| correo_electronico    | varchar(100)           | not null      |                           | 
| -------------------------------------------------------------------------------------------|
```

#### Relationships
- ** 1 `uno`customer  → N `many transactions **
- ** 1 `uno`trasaction  → N `Many invoices **

---

## API  Endpoins Documentation

All API requests use the base URL: `(http://localhost:3000)` 

---
**response 200 example:**
```json
   {
        "id_prestamo": 14,
        "fecha_prestamo": "2025-06-08T05:00:00.000Z",
        "fecha_devolucion": "2025-08-12T05:00:00.000Z",
        "estado": "activo",
        "usuario": "Helena Micaela Alvarado",
        "isbn": "978-1-968004-87-3",
        "libro": "Modi beatae"
    }
```

---

**URL:** POST `ruta final`
**Description:**
Creates a...

**request body example:**
```json
   {
        "fecha_prestamo": "2025-06-08",
        "fecha_devolucion": "2025-08-12",
        "estado": "activo",
        "usuario": "Helena Micaela Alvarado",
        "isbn": "978-1-968004-87-3",
        "libro": "Modi beatae"
    }
```

**response 200 example:**
```json
{
    "mensaje": "customer creado exitosamente"
}
```

---

**URL:** PUT `/customers/31`

**request body example:**
```json
 {
        "fecha_prestamo": "2025-06-08",
        "fecha_devolucion": "2025-08-12",
        "estado": "entregado",
        "usuario": "Helena Micaela Alvarado",
        "isbn": "978-1-968004-87-3",
        "libro": "Modi beatae"
 }
```

**response 200 example:**
```json
{
    "mensaje": "transaction update"
}
`lo que regrese la respuesta de la query en postman`
```

---

**URL:** DELETE `/customers/31`

**response 200 example:**
```json
{
    "mensaje": "trasaction delete"
}
```
