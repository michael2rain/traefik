# Instalar mkcert para crear certificados en local
Seguir las instrucciones para instalar mkcert en su dispositivo.
[text](https://github.com/FiloSottile/mkcert)

# Ejecutar el comando dentro de la carpeta /certs
mkcert mydomain.local

# Agregar archivo certs.yml dentro de esta misma carpeta /certs
Con el siguiente contenido:

tls:
  certificates:
    - certFile: "/certs/mydomain.local.pem"
      keyFile: "/certs/mydomain.local-key.pem"