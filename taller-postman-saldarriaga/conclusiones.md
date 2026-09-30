# Conclusiones del taller de Postman

## 1. Idempotencia

La idempotencia es una propiedad de una operación en la que realizarla varias veces con los mismos datos produce el mismo efecto final que realizarla una sola vez.

### Clasificación de los métodos HTTP

| Método | ¿Es idempotente? |
|---|---|
| GET | Sí |
| POST | No |
| PUT | Sí |
| PATCH | No garantizado |
| DELETE | Sí |

### Prueba realizada con PUT

Se ejecutó varias veces la petición PUT `/posts/1` utilizando los mismos datos.

La respuesta mantuvo el mismo resultado, por lo que el comportamiento observado fue consistente con una operación idempotente.

### Prueba realizada con POST

Se ejecutó varias veces la petición POST `/posts`.

En las pruebas realizadas, JSONPlaceholder devolvió el mismo ID, 101, en las diferentes ejecuciones. Sin embargo, este resultado corresponde al comportamiento observado en esta API de prueba y no permite concluir que POST sea idempotente.

---

## 2. Headers de respuesta

Durante las pruebas se observaron diferentes headers en las respuestas de la API.

### Content-Type

Indica el tipo de contenido que está siendo enviado en la respuesta. En las pruebas se observó:

`application/json; charset=utf-8`

Es importante porque permite saber que la respuesta contiene información en formato JSON y conocer la codificación utilizada.

### Cache-Control

Indica directivas relacionadas con el almacenamiento en caché de la respuesta.

En la prueba se observó:

`max-age=43200`

Este tipo de información es útil para analizar cómo una respuesta puede ser almacenada temporalmente.

### Connection

Indica información relacionada con la conexión utilizada para la comunicación.

En la respuesta se observó:

`keep-alive`

Los headers son importantes en las pruebas de API porque proporcionan información adicional sobre cómo se entrega y procesa la respuesta, además del código de estado y el cuerpo.

---

## 3. Importancia de las pruebas automáticas

Las pruebas automáticas permiten verificar de manera repetible que una respuesta cumple determinadas condiciones.

En este taller se creó inicialmente una prueba para comprobar que el estado de la respuesta fuera 200:

```javascript
pm.test("El estado es 200", function () {
    pm.response.to.have.status(200);
});