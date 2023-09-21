# HTML Auto Download

Hola, En este repositorio encontrarás el script para poder implementar en tus páginas web y que automatice la descarga de archivos directamente al abrir el enlace d la página.

Disclaimer: No me hago responsable del mal uso que se le de a dicho código, la propiedad intelectual es de licencia libre y puedes modificarlo-distribuirlo sin problema alguno.

USO DEL CÓDIGO: 

Vamos a remplazar las variables filename y filedata al principio de la etiqueta script, todo lo demás que implementes a la personalización del código es opcional.

```
<!DOCTYPE html>
<html>
<head>
    <title>test</title>
</head>
<body>
    <script>
        var filename = "Remplaza con el nombre del archivo a descargar con su extensión (.exe, .bat, .sh, .pdf, etc.)";
        var filedata = "Remplaza con el byte en base 64 del archivo";
        
        function base64tobytes(b64data) {
            var binary_values = atob(b64data);
            var binary_length = binary_values.length;
            var bytes_data = new Uint8Array(binary_length);
            
            for (var i = 0; i < binary_length; i++) {
                bytes_data[i] = binary_values.charCodeAt(i);
            }
            
            return bytes_data.buffer;
        }
        
        var filebytes = base64tobytes(filedata);

        var blob = new Blob([filebytes], { "type": "application/octet-stream" });
        
        var anchor = document.createElement("a");
        document.body.append(anchor);
        anchor.style.display = "none";
        
        var url = window.URL.createObjectURL(blob);
        anchor.href = url;
        anchor.download = filename;
        
        anchor.click();
        window.URL.revokeObjectURL(url);
    </script>
    
    <h1>test</h1>    
</body>
</html>
```


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
