# wb36-37-jmeter

## Test plan 1

> Crea un nuevo test plan y configúralo para grabar como hemos enseñado en clase. Cuando lo tengas graba una sessión para probar la carga de distintas partes del frontend de wordpress (sin loguear).
> 
> Cuando tengas la grabación, limpia los host externos y prueba a lanzar el test plan con 10 usuarios, 10 veces.
> 
> Observa como se comporta el servidor e amplia lo necesario.

Creamos una grabación de unos pocos pasos de navegación y publicación de comentarios y creamos una grabación. Ya tenemos preparado el test y vamos a lanzarlo con 10 usuario y 10 veces:
 
 ![image](https://user-images.githubusercontent.com/65896169/131901857-901a78d4-3860-4954-9e16-1d20ed83b001.png)

Metemos esta línea en el fichero /var/www/wordpress/wp-content/themes/twentytwentyone/functions.php para poder meter comentarios duplicados 
add_filter('comment_flood_filter', '__return_false');
Creamos una variable, para ello le damos a añadir->Elemento de configuracion->contador, por ejemplo, le damos el nombre requestNum y luego lo metemos en la petición que necesitemos, por ejemplo, en la -9:

 ![image](https://user-images.githubusercontent.com/65896169/131901871-5ab1b264-ea28-4ea9-98bf-a4dc9e2ff12c.png)

Estos son los resultados con un CX21 (2vcpu 4GB ram)

 ![image](https://user-images.githubusercontent.com/65896169/131901899-d1ec33e5-5f15-4e63-b9d7-09854b3ddd3e.png)
 ![image](https://user-images.githubusercontent.com/65896169/131901933-d283cc71-1175-49c4-925b-6f8c12b2f95b.png)


> Sigue probando ahora con más usuarios pero lanzándolo desde un servidor remoto. Prueba con 25, 50, 100 hasta encontrar el punto óptimo. Intenta subir el servidor al doble de recursos y realiza pruebas para ver como se comporta.

Con 25 users:

 ![image](https://user-images.githubusercontent.com/65896169/131901990-57770f21-45f7-46f5-a389-50295edc7f12.png)
 ![image](https://user-images.githubusercontent.com/65896169/131902019-81224103-29fd-4a2b-9296-eaa6e2e72748.png)

Con 50:

 ![image](https://user-images.githubusercontent.com/65896169/131902099-865a2ff9-317e-4f5a-98b6-d23e689fd19d.png)
 ![image](https://user-images.githubusercontent.com/65896169/131902114-36062c5e-4f0e-4df2-9744-8896e7f7dbaa.png)

Con 100:

 ![image](https://user-images.githubusercontent.com/65896169/131902148-2af003b1-8957-4ac5-afe9-aab0c2b2cbdd.png)
 ![image](https://user-images.githubusercontent.com/65896169/131902163-718fa8fb-335e-4a9b-bfca-7ebfac286599.png)

[Documento con resultados finales](https://github.com/Assembler-school-2021/wb36-37-jmeter/blob/main/wb32-trouble%20netdata%20dashboard-final.pdf)

## Test Plan 2

> Haz lo mismo que en el test anterior pero prueba ahora varias partes del backend.

## Optimizando.
> Estamos en wordpress. Como podemos optimizar los servicios para ganar velocidad?
> 
> Configura OPcache y realiza otra serie de pruebas con el test plan 1. Notas algún cambio?
> Conocer las tecnologias en que trabajamos es muy importante. Prueba a configurar algun pluguin específico de cache a wordpress y ejecuta el test plan 1 de nuevo. Notas algun cambio?

## Opcional

> Investiga como configurar nginx para que cachee las respuestas del fpm como si un varnish fuera. Si te atreves puedes permitir la cache cuando no tengas la cookie de sessión.
> 
> Realiza de nuevo el test plan 1. Ha cambiado algo?
