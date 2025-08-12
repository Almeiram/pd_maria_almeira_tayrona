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
biblioteca/
│
├── docs/ # Documentation
│       ...
├── app/ # Frontend (HTML, CSS, JS)
│       ...
├── server/ # Backend
│       ...
├── index.html 
├── .env # Variables de entorno
├── .gitignore
└── README.md
```

## Instalation y ejecucion

1. Clone the repository:

```bash
git clone 
cd 
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
| GET    | /api/v1/preos     | Obtener todos los préstamos |
| GET    | /api/v1/prestamos | Obtener un préstamo por ID  |
| POST   | /api/v1/prestamos | Crear un nuevo préstamo     |
| PUT    | /api/v1/prestamos | Actualizar un préstamo      |
| DELETE | /api/v1/prestamos | Eliminar un préstamo        |
  
```

## Database documentation

### Database name
`pd_maria_almeira_tayrona`

---

### Entity-relationship diagram
![Entity-relationship diagram](./docs/relational_model.ppg.jpg)

---

### Tables

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
| ----------------- ------------------------------------------------------------------------ | 
| Field                 | Data type          | constraints| Description|
| ----------------- ---------------------------------------------------------------------------- 
| numero_factura        |varchar(20) intprimay key  |not null     |  not null   |  unique identifier|
| plataforma_utilizada  | enum('nequi','daviplata') |not null     | varchar(200)        | not null  |
| periodo_facturacion   |date unique  int           | not null    |             |      |                     
| monto_facturado       | int |not null             | varchar(200)|     | not null              |      
| monto_pagado          |int varchar(20)            |             |   not null                  |      
| ----------------------------------------------------------------------------------------------|

#### **clientes**
| ----------------- ------------------------------------------------------------------------ | 
| Field                 | Data type       | constraints| Description|
| ----------------- ------------------------------------------------------------------------ | 
| iid_transaccion _varchar(15) not null primary key
| fecha_hora_transaccion date not null                        |
| monto_transaccion int                                |
| tipo_transaccion varchar(100) not null                               |
| id_cliente                                |
| correo_electronico    | varchar(100)    | not null    |                                    | 
| -------------------------------------------------------------------------------------------|






some descriptions
 PRIMARY KEY → Unique identifier for the `nombre de lo que identifica`,
 FOREING KEY → References `tabla.campo que referencia`
 `campo` name
 `campo` date
 `campo` description
 national identification number 
 `campo` email address
 gender

----

#### Relationships
- ** 1 `uno`eje: un profesor  → N `muchos`puede tenemos muchos estudiantes **

---

## API  Endpoins Documentation

All API requests use the base URL: `(http://localhost:3000)` 

---

### **ejemplo :  Historial de un libro por su ISBN**
**URL:** GET `/prestamos/historial/:isbn` 
**Description:**
retruns a ...

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
    "mensaje": "prestamo creado exitosamente"
}
```

---

**URL:** PUT `/prestamos/31`
**Description:**
Updates a...

**Path Paramenters:**
| Name | Type | Required | Description |
| id---- | int---- | yes-------- | id to update----------- |

some description:
`campo` to update


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
`lo que envias en el body de la query en postman`
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
**Description:**



**response 200 example:**
```json
{
    "mensaje": "trasaction delete"
}
`lo que regrese la respuesta de la query en postman`
```