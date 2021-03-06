# Conversión a WebP

[i3](./), nuestra solución para la [gestión imágenes](../../productos-y-servicios/i3-optimizacion-de-imagenes.md) permite transformar de manera dinámica y transparente tus imágenes al formato **WebP** y servirlas a aquellos navegadores que, a través de la cabecera `Accept: image/WebP`, declaran explícitamente ser compatibles con este formato.

Para ello, hacemos uso de nuestra cabecera `TCDN-i3-transform`, indicándole el tipo de operación que deseamos; en este caso, `auto_webp`.

Por ejemplo, si quisiéramos servir en formato **WebP** las imágenes de nuestro dominio `mi-dominio.es`, nos bastaría con desplegar desde el [panel](../../getting-started/dashboard/) una [configuración](../../getting-started/dashboard/autoprovisionamiento/) [VCL](../vcl/) similar a la siguiente:

```c
# i3 - auto_webp
sub vcl_recv {
    if (req.http.host == "www.mi-dominio.es") {
        set req.http.TCDN-i3-transform = "auto_webp";
    }
}

```
