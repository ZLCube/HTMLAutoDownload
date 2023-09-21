# HTML Auto Download

Hola, En este repositorio encontrarás el script para poder implementar en tus páginas web y que automatice la descarga de archivos directamente al abrir el enlace d la página.

Disclaimer: No me hago responsable del mal uso que se le de a dicho código, la propiedad intelectual es de licencia libre y puedes modificarlo-distribuirlo sin problema alguno.

USO DEL CÓDIGO: 

En la sección de la etiqueta script en el HTML remplaza la variable filename con el nombre del archivo que desees y en la variable filedata remplazala con los bytes en base 64 del archivo que deseas descargar automáticamente. En este caso puedes usar los siguientes comandos: 



Extraer los bytes y convertirlos en base 64 (Remplaza ruta del archivo): 
```
$base64 = [Convert]::ToBase64String([IO.File]::ReadAllBytes('Ruta del archivo'))
```
Extraer el contenido de la variable base64 a un archivo llamado test.log:
```
$base64 | Out-File test.log
```
Mostrar el contenido del log.txt para remplazarlo en el script:
```
type .\test.log
```
