# Hallazgos del taller de Postman

## 1. GET /posts/1

### Resultado
- Estado esperado: 200 OK
- Estado obtenido: 200 OK
- Tipo de respuesta: recurso individual
- Campos encontrados: userId, id, title y body.

### Criterio de aceptación
Para un recurso individual se espera que exista un único objeto con la información correspondiente al ID solicitado.

---

## 2. GET /posts

### Resultado
- Estado esperado: 200 OK
- Estado obtenido: 200 OK
- Tipo de respuesta: colección de recursos.
- Cantidad de elementos: 100.
- Campos principales: userId, id, title y body.

### Criterio de aceptación
Para una colección se espera recibir una lista de recursos y comprobar que la estructura de los elementos sea la esperada.

---

## 3. GET /posts/9999 – Recurso inexistente

### Resultado
- Estado esperado: 404 Not Found
- Estado obtenido: 404 Not Found.

La respuesta indica que el recurso solicitado no existe.

### ¿El test pasó o falló?

El test pasó porque el resultado obtenido coincide con el resultado esperado.

Un código 404 no representa necesariamente un defecto. En este caso es una respuesta correcta porque se solicitó un recurso que no existe.

### ¿Qué pasaría si devolviera 200 con un cuerpo vacío?

Sería necesario analizarlo como un posible defecto, porque la respuesta no estaría comunicando correctamente que el recurso solicitado no existe.

---

## 4. POST /posts – Creación

Se ejecutó cinco veces la petición POST utilizando el siguiente cuerpo:

```json
{
  "title": "Mi primera prueba",
  "body": "Taller de Ingeniería de Software II",
  "userId": 1
}