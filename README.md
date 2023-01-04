# TicketService 🎫

El presente proytecto es un **Microservicio** desarrollado en el lenguaje de programacion C#, utilizando una **arquitectura Hexagonal** para brindar una **API**, capaz de gestionar la intomacion de un **Sistema de Tickets**.

El mismo se ha desarrollado mediante el uso de **Entity Framework** como ORM.

El actual microservicio en conjunto con [AuthService](https://github.com/diloretoignacio/AuthService) son consumidos por la aplicacion web [TicketsFrontend](https://github.com/diloretoignacio/TicketsFrontend)

A continuacion se demuestran los principales endopoints para realizar acciones sobre la informacion:
## Crear Ticket
### Request
```
POST /api/Tickets
```
### Body
```
{
  "PriorityId": 1,
  "CategoryId": 3,
  "title": "Titulo del ticket",
  "description": "Descripcion del ticket",
  "fileAdjunt": "url"
}
```

## Obtener Ticket por ID
```
GET /api/tickets/:id
```
### Response
```
{
    "idTicket": 1,
    "ticketComments": [
        {
            "idComment": 1,
            "idUser": 5,
            "idTicket": 1,
            "comment": "Se ha reparado el mouse",
            "file": "",
            "dateComment": "2023-01-04T15:16:31.235637"
        }
    ],
    "ticketLogs": [
        {
            "idTicketLog": 1,
            "idTicket": 1,
            "idUser": 4,
            "dateAction": "2023-01-04T15:12:42.00712",
            "action": "Creado"
        },
        {
            "idTicketLog": 2,
            "idTicket": 1,
            "idUser": 5,
            "dateAction": "2023-01-04T15:16:15.1319622",
            "action": "Actualizado el estado"
        }
    ],
    "ticketStatus": {
        "idTicketStatus": 3,
        "description": "Finalizado"
    },
    "ticketPriority": {
        "idPriority": 3,
        "description": "Alta"
    },
    "ticketBody": {
        "idTicketBody": 1,
        "title": "No funciona el mouse",
        "description": "¡Hola equipo!\n\nEl mouse de mi PC no se encuentra funcionando correctamente",
        "file": ""
    },
    "ticketCount": {
        "idTicketCount": 1,
        "countOpen": 0,
        "countApproved": 0,
        "countDisapproved": 0
    },
    "ticketCategory": {
        "idTicketCategory": 3,
        "name": "Reparacion Hardware",
        "description": "Categoria responsable de gestionar las reparaciones de Hardware",
        "reqApproval": true,
        "minApprovers": 1,
        "idAreadestino": 3,
        "active": true
    },
    "user": {
        "userId": 1,
        "userName": "admin",
        "firstName": "Cosme",
        "lastName": "Fulanito",
        "email": "psgrupointer@gmail.com"
    }
}
```
## Obtener ticket por ID
```
GET /api/tickets/:id
```
### Response
```
{
    "idTicket": 1,
    "ticketComments": [
        {
            "idComment": 1,
            "idUser": 5,
            "idTicket": 1,
            "comment": "Se ha reparado el mouse",
            "file": "",
            "dateComment": "2023-01-04T15:16:31.235637"
        }
    ],
    "ticketLogs": [
        {
            "idTicketLog": 1,
            "idTicket": 1,
            "idUser": 4,
            "dateAction": "2023-01-04T15:12:42.00712",
            "action": "Creado"
        },
        {
            "idTicketLog": 2,
            "idTicket": 1,
            "idUser": 5,
            "dateAction": "2023-01-04T15:16:15.1319622",
            "action": "Actualizado el estado"
        }
    ],
    "ticketStatus": {
        "idTicketStatus": 3,
        "description": "Finalizado"
    },
    "ticketPriority": {
        "idPriority": 3,
        "description": "Alta"
    },
    "ticketBody": {
        "idTicketBody": 1,
        "title": "No funciona el mouse",
        "description": "¡Hola equipo!\n\nEl mouse de mi PC no se encuentra funcionando correctamente",
        "file": ""
    },
    "ticketCount": {
        "idTicketCount": 1,
        "countOpen": 0,
        "countApproved": 0,
        "countDisapproved": 0
    },
    "ticketCategory": {
        "idTicketCategory": 3,
        "name": "Reparacion Hardware",
        "description": "Categoria responsable de gestionar las reparaciones de Hardware",
        "reqApproval": true,
        "minApprovers": 1,
        "idAreadestino": 3,
        "active": true
    },
    "user": {
        "userId": 1,
        "userName": "admin",
        "firstName": "Cosme",
        "lastName": "Fulanito",
        "email": "cosmefulanito@gmail.com"
    }
}
```
## Crear Comentario
### Request
```
POST /api/TicketComment
```
### Body
```
{
  "idTicket": 1,
  "comment": "comentario",
  "file": "url"
}
```



## Crear Categoria
### Request
```
POST /api/TicketCategory
```
### Body
```
{
  "name": "string",
  "description": "string",
  "reqApproval": true,
  "minApprovers": 0,
  "idAreadestino": 1
}
```

Ademas se permite:

* Crear un area de la empresa
* Derivar Ticket a otra categoria
* Cambiar el estado de un Ticket
* Cambiar la prioridad de un Ticket
* Obtener tickets de un estado en particular

Todos los endpoints correspondientes se encuentran en el archivo **Collección Postman ServiceTickets.json** que contiene la coleccion de Postamn utilizada
