# Configuración de SSL
Para agregar el certificado de cada sitio web, es necesario crear un archivo por sitio web "mysite-local.yml" donde indicarás donde se puede encontrar el certificado dentro del contenedor de traefik, asegurate de montar la carpeta de tu espacio de trabajo el el archivo "compose.yml".

# Ejemplo:

# --- SECCIÓN 1: CERTIFICADOS SSL ---
tls:
  certificates:
    - certFile: /var/projects_root/mysite/ssl/_wildcard.mysite.local.pem
      keyFile: /var/projects_root/mysite/ssl/_wildcard.mysite.local-key.pem

# --- SECCIÓN 2: Middlewares ---
http:
  middlewares:
    # 1. Headers de Seguridad: Protege tu WP de ataques básicos (XSS, iframes maliciosos)
    mis-headers-seguros:
      headers:
        frameDeny: true
        browserXssFilter: true
        contentTypeNosniff: true
        forceSTSHeader: true
        stsIncludeSubdomains: true
        stsSeconds: 15552000

    # 2. Compresión Gzip: Hace que tu sitio cargue más rápido comprimiendo el HTML/CSS
    compresion-gzip:
      compress: {}
