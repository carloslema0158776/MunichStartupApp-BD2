# Notas de publicación

- El código Java original incluía una contraseña de PostgreSQL. En el paquete preparado fue sustituida por la variable de entorno `MUNICH_DB_PASSWORD`.
- Las transformaciones Pentaho contenían credenciales cifradas; se sustituyeron por variables de entorno. Configura esas variables antes de ejecutar Spoon.
- Se retiraron archivos compilados, configuración privada de NetBeans y rutas absolutas de dependencias. Reconfigura las bibliotecas PostgreSQL JDBC y PDFBox al abrir el proyecto.
- El script de población OLTP no se incluyó en el paquete público porque contiene nombres y contactos de personas cuyo carácter ficticio no se ha confirmado.
- La ejecución integral de la aplicación y de los procesos ETL no se ha verificado.
