---
layout: post
title: Captura de precios de supermercados
tags: [clustering,precios-supermercado,comparador,nlp]
date: 2021-06-02 15:32 +0800
---

Un dia hace más de 6 años, estaba en mi cama viendo las páginas web de diferentes supermercados del Perú, necesitaba realizar las compras de la semana, en ese momento solo habia 3 paginas web que tenian su carrito de compras, Wong, Plaza Vea y Tottus, todos con una baja calidad de desarollo, pareciera que nunca lo actualizaban, su versión eran de los 2000, estando en ese momento en el 2015.

Se me ocurrio la gran idea, de hacer un programita que compare los precios de los supermercados, sentí en ese momento que era la idea mas genial del mundo y que nadie lo habia hecho antes y me iba hacer millonario, en los minutos siguientes volvi a la realidad busque por google y en europa y eeuu ya existian dichas páginas con las mismas temáticas.

Igual, me enrumbe en hacerlo, porque en Perú, hasta ahorita, no hay una web que compare precios de supermercados o al menos que yo haya encontrado por google.

La web que realice lo llame "Compra Ahorro", que original verdad? bueno la idea era comprar y ahorrar, comparando los precios.

Hice mi lista de actividades:

- Analizar web's de supermercados donde podría extraer precios (3 en ese momento, ahora gracias a la pandemia son 5)

- Aprender a extraer datos de paginas web. La técnica se llama escrapeo o scraping, en internet existe mucha info sobre la misma, pero les daré 3 tips que les ayudaran un montón:
    * Google chrome y sus herramientas para desarrollo (el F12), tab network, tab All o XHR, en esas vistas veran todos los request que realiza la web
    * Viendo todos los request, lo que debemos buscar es el api que extraiga toda la información
    * Utilizar python y la libreria request para extraer la info json que devuelve el api.

    ![_config.yml]({{ site.baseurl }}/images/plaza_vea.png)

- Una vez ya tienes el json y la data en tu poder, hay que guardarlo en una bd que tenga un modelo de datos sencillo donde puedas almacenar  la data que arroja el json. Tip en este punto: 
    * La BD puede ser "posstgres" y pueden utilizar [Heroku](https://www.heroku.com/) que te da almacenamiento gratis para hacer tus pruebas

- Por ultimo viene lo más complicado y trabajoso; estandarizar los nombres de los productos. Obvio, en el supermercado 1 un producto puede estar en la categoria "Alacena" y en el supermercado 2 en "Despensa", en una puedes encontrar el texto "Arroz Blanco" y en el otro "Arroz Blanco Costeño 500 mg". Los tips:
    * UTilizar tecnicas de limpieza de datos: extraer las "marcas", el "embase", la "unidad de medidad" de los nombres de los productos, colocarlo todo en minuscula, la cosa que al final te quedara "arroz blanco" contra "arroz blanco"
    * La idea es limpiar lo mejor posible la oracion para que solo te quede una pequeña descripcion, ha de verdad las limpieza lo hice con "expreciones regulares".
    * Pero tambien habia productos como "Arroz Blanco Graneado", "Arroz Blanco", "Arroz Blanco Selecta", "Arroz Blanco Superior". Como hice para saber si un producto era igual al de otro supermercado o era similar? En este punto utilize 2 técnicas, uno era de machine learning "clustering" para juntar en un grupo palabras iguales o similares y luego dentro de ese grupo utilice algoritmos de similaridad (ejm. el coseno de similaridad) y todos los items que estaban dentro de ese gruppo los comparaba, y si tenia una probabilidad alta de simillaridad, identificaba la igualdad.

- Bueno, ya teniendo la data comparada y almacenada en la BD, como lo muestro?; para ello lo quize mostrar de la manera mas sencilla posible, asi que busque un diseño de web sencilla y encontre una Tabla Pibotal, que me ayudo a comparar de manera sencilla. Tips:
    * Denuevo utilice "Heroku" para montar mi web ya que tiene espacio gratis
    * Utilice node.js para el desarrollo de la web.


Como resultado, esta es la web [Compra Ahorro](https://aqueous-meadow-07874.herokuapp.com/), no tiene precios actualizados hasta la fecha, lo hice por una sola vez y luego no tube tiempo de actualizar....

Sencillo verdad? pues me tomo varios años realizarlo entre idas y venidas, baches y tropiezos. De hecho que esta web si le doy el mayor de mis tiempos puedo hacerlo crecer mucho más, pero por ahora lo he dejado hasta ahi.





