# Taller de API REST con Postman

## Información del estudiante

**Estudiante:** Marcela Saldarriaga  
**Código:** [1114148782]  
**Asignatura:** Ingeniería de Software II  

---

# Marco conceptual

## ¿Qué es una API REST?

Una API REST es una interfaz que permite que diferentes aplicaciones se comuniquen mediante solicitudes HTTP. REST utiliza recursos y operaciones HTTP para consultar, crear, modificar o eliminar información.

Un **recurso** es un elemento que una API permite consultar o manipular. Por ejemplo, en JSONPlaceholder, un post es un recurso.

Un **endpoint** es la dirección específica mediante la cual se accede a un recurso de la API. Por ejemplo:

`https://jsonplaceholder.typicode.com/posts/1`

En este caso, `/posts/1` identifica el recurso correspondiente al post con ID 1.

### Ejemplo en una aplicación cotidiana

Una aplicación de compras puede utilizar una API para consultar los productos disponibles, registrar nuevos pedidos o consultar el estado de una compra.

### Fuente

JSONPlaceholder: https://jsonplaceholder.typicode.com/

---

# Métodos HTTP y CRUD

| Método HTTP | Operación CRUD | Descripción |
|---|---|---|
| GET | Read | Consultar información o recursos. |
| POST | Create | Crear un nuevo recurso. |
| PUT | Update | Actualizar un recurso. |
| PATCH | Update | Modificar parcialmente un recurso. |
| DELETE | Delete | Eliminar un recurso. |

---

# Códigos de estado HTTP

Los códigos de estado HTTP permiten conocer el resultado de una solicitud.

| Familia | Significado | Ejemplo |
|---|---|---|
| 1xx | Información | 100 Continue |
| 2xx | Solicitud procesada correctamente | 200 OK |
| 3xx | Redirección | 301 Moved Permanently |
| 4xx | Error relacionado con la solicitud del cliente | 404 Not Found |
| 5xx | Error relacionado con el servidor | 500 Internal Server Error |

## Diferencia entre 4xx y 5xx

Los códigos 4xx generalmente indican que existe un problema con la solicitud realizada por el cliente, mientras que los códigos 5xx indican que ocurrió un problema al procesar la solicitud en el servidor.

---

# Cómo reproducir el taller

Para reproducir las pruebas se debe utilizar Postman y realizar las solicitudes contra la API JSONPlaceholder:

`https://jsonplaceholder.typicode.com`

La colección utilizada en el taller se encuentra en el archivo `coleccion.json`.

Las principales peticiones realizadas fueron:

1. GET `/posts/1`
2. GET `/posts`
3. GET `/posts/9999`
4. POST `/posts`
5. PUT `/posts/1`
6. PATCH `/posts/1`
7. DELETE `/posts/1`

También se exploraron otros recursos:

- GET `/users`
- GET `/comments`
- GET `/posts/1/comments`

Durante el taller se realizaron pruebas automáticas en Postman para comprobar diferentes características de las respuestas.

---

# Resultados principales

Durante las pruebas se obtuvieron diferentes códigos de estado según la operación realizada.

- GET `/posts/1` → 200 OK
- GET `/posts` → 200 OK
- GET `/posts/9999` → 404 Not Found
- POST `/posts` → 201 Created
- DELETE `/posts/1` → 200 OK

También se realizaron pruebas con PUT y PATCH para observar las diferencias entre ambas operaciones.

Se probaron valores límite mediante `/posts/100` y `/posts/101`, obteniendo 200 OK y 404 Not Found respectivamente.

---

# Archivos del repositorio

El repositorio contiene los siguientes archivos y carpetas:

```text
taller-postman-tuapellido/
│
├── README.md
├── hallazgos.md
├── conclusiones.md
├── coleccion.json
│
└── evidencias/
    ├── 01-get-recurso.png
    ├── 02-get-coleccion.png
    ├── 03-error-404.png
    ├── 04-post-creacion.png
    └── 05-test-automatico.png