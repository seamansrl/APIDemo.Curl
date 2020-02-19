# PROYECTO HORUS: Demo usando CURL

Esta demo muestra como usar la API del Proyecto Horus para decodificar un codigo PDF417, QR, EAN13, etc usando CURL. Si bien este ejemplo muestra la función de Codebar/Decoder se puede usar con todos los endpoints de Horus

# Obtener Token

```
curl -H "Content-Type: application/json" --data "{\"user\":\"ACA TU USUARIO HORUS\",\"password\":\"ACA TU CLAVE HORUS\",\"profileuuid\":\"ACA EL UUID DEL PERFIL EN HORUS\"}" -X POST "http://server1.proyectohorus.com.ar/api/v2/functions/login"
```

Obtendremos como respuesta:

```
{
"global" :
    {
     "data" : [
         {
         "code" : "200",
         "token" : "jmGyTRbd7tMmoR7vasORDkFR9vbNeb/Z44JPfrwSqhH2VXsyP4damgBOyBEyHKjiSoXGHXI4Fei8EOb2B++5WWwYvTeU4BfiJWzYXq3rwnmPATN0tXs2ug+v1IRPrbRBHGvC5PdVBAHy3U=",
         "instance" : "b0bb3e88531511eaac4g90155d714f00"
         }
      ]
    }
}
```

# Obtener Token

```
curl -H "Content-Type: application/json" --data "{\"user\":\"ACA TU USUARIO HORUS\",\"password\":\"ACA TU CLAVE HORUS\",\"profileuuid\":\"ACA EL UUID DEL PERFIL EN HORUS\"}" -X POST "http://server1.proyectohorus.com.ar/api/v2/functions/login"
```

Decodificar una imagen:

```
curl -H "Authorization: Bearer ACA VA EL TOKEN" -H "Content-Type: multipart/form-data" -F "photo=@qrcode.jpg" -X POST "http://server1.proyectohorus.com.ar/api/v2/functions/codebar/decoder?responseformat=json"
```

Obtendremos como respuesta:

```
{
"global" :
    {
     "data" : [
         {
         "code" : "200",
         "token" : "jmGyTRbd7tMmoR7vasORDkFR9vbNeb/Z44JPfrwSqhH2VXsyP4damgBOyBEyHKjiSoXGHXI4Fei8EOb2B++5WWwYvTeU4BfiJWzYXq3rwnmPATN0tXs2ug+v1IRPrbRBHGvC5PdVBAHy3U=",
         "instance" : "b0bb3e88531511eaac4g90155d714f00"
         }
      ]
    }
}
```
