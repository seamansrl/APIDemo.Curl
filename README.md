# PROYECTO HORUS: Demo usando CURL

Esta demo muestra como usar la API del Proyecto Horus para decodificar un codigo PDF417, QR, EAN13, etc usando CURL. Si bien este ejemplo muestra la función de Codebar/Decoder se puede usar con todos los endpoints de Horus

# Obtener Token

```
curl -H "Content-Type: application/json" --data "{\"user\":\"ACA TU USUARIO HORUS\",\"password\":\"ACA TU CLAVE HORUS\",\"profileuuid\":\"ACA EL UUID DEL PERFIL EN HORUS\"}" -X POST "http://server1.proyectohorus.com.ar/api/v2/functions/login"
```

Obtendremos como respuesta:

```
 {
 "code" : "200",
 "token" : "jmGyTRbd7tMmoR7vasORDkFR9vbNeb/Z44JPfrwSqhH2VXsyP4damgBOyBEyHKjiSoXGHXI4Fei8EOb2B++5WWwYvTeU4BfiJWzYXq3rwnmPATN0tXs2ug+v1IRPrbRBHGvC5PdVBAHy3U=",
 "instance" : "b0bb3e88531511eaac4g90155d714f00"
 }

```

# Decodificar una imagen

```
curl -H "Authorization: Bearer ACA VA EL TOKEN" -H "Content-Type: multipart/form-data" -F "photo=@qrcode.jpg" -X POST "http://server1.proyectohorus.com.ar/api/v2/functions/codebar/decoder?responseformat=json"
```

Obtendremos como respuesta:

```
{
 "code" : "200",
 "value" : "ok",
 "y1" : "0.1784841075794621",
 "x1" : "0.2234513274336283",
 "y2" : "0.8117359413202934",
 "x2" : "0.7986725663716814",
 "detected_id" : "BEGIN:VCARD  VERSION:3.0  N:Stan NICKNAME:Smith SOUND:Stan Smith TEL:+7 (978) 571-91-44 TEL-AV: EMAIL:web.marshal.ru@gmail.com ADR:home BDAY: TITLE: ORG: URL: NOTE:  END:VCARD" (QRCODE)",
 "vector_id" : "0",
 "confidence" : "0.00"
}
```

Podemos con esto usar jq en linux BASH para decodificar el JSON y automatizar las consultas segun lo comentado en el presente link:

https://stedolan.github.io/jq/tutorial/

# Dentro de las funciones de la API podemos encontrar:

El Proyecto Horus consiste en una API REST que permite de forma simple identificar imagenes via redes neuronales.

- FACE ID
- OBJECT DETECTION
- QR DECODER
- ID DECODER
- APLR (AUTOMATIC PLATE LICENSE RECOGNITION)

al 01-02-2020 el proyecto estas en modo beta por lo cual para poder acceder y configurar la API se debera descargar la APP que permite a la administracion desde https://www.proyectohorus.com.ar/descargas/windows/admin.zip

La URL a usar en el codigo de ejemplo es:
https://server1.proyectohorus.com.ar

El usuario, Password y Perfil se obtienen en esta primer etapa desde el software descargable.

Ejemplo de como usar el administrador aca:

https://www.youtube.com/watch?v=R8AcntEprjE

