---
layout: post
title: Captura de precios de supermercados
---

Un dia hace mas de 6 años, estaba en mi cama viendo las paginas web de diferentes supermercados del Perú, necesitaba realizar las compras de la semana, en ese momento solo habia 3 paginas web que tenian su carrito de compras, Wong, Plaza Vea y Tottus, todos con una baja calidad de desarollo, pareciera que nunca lo actualizaban, su version eran de los 2000, estando en ese momento en el 2015.

Se me ocurrio la gran idea, de hacer un programita que compare los precios de los supermercados, sentí en ese momento que era la idea mas genial del mundo y que nadie lo habia hecho antes y me iba hacer millonario, en los minutos siguientes volvi a la realidad busque por google y en europa y eeuu ya existian dichas páginas con las mismas temáticas.

Igual, me enrumbe en hacerlo, porque en Perú, hasta ahorita, no hay una web que compare precios de supermercados o al menos que yo haya encontrado por google.

La web que realice lo llame "Compra Ahorro", que original verdad? bueno la idean era comprar y ahorra XD.

Hice mi lista de actividades:
- Analizar web's de supermercados donde podría extraer precios (3 en ese momento, ahora gracias a la pandemia son 5)
- Aprender a extraer datos de paginas web. La técnica se llama escrapeo o scraping, en internet existe mucha info sobre la misma, pero lo dare solo 3 tips que les ayudaran un montón:
    * Google chrome y sus herramientas para desarrollo (el F12), tab network, tab All o XHR, en esas vistas veran todos los request que realiza la web
    * Viendo todos los request, lo que debemos buscar es el api que extraiga toda la información
    * Utilizar python y la libreria request para extraer la info json que devuelve el api.
- Una vez ya tienes el json y la data en tu poder, hay que guardarlo en una bd que tenga un modelo de datos sencillo donde puedas almacenar  la data que arroja el json. Otro tip. 
    * La BD puede ser "posstgres" y pueden utilizar "heroku" que te da almacenamiento gratis para hacer tus pruebas
- Por ultimo viene lo más complicado y trabajoso, estandarizar los nombres de los productos. Obvio, en el supermercado 1 un producto puede estar en la categoria "Alacena" y en el supermercado 2 en "Despensa", en una puedes encontrar el texto "Arroz Blanco" y en el otro "Arroz Blanco Costeño 500 mg". Los tips:
    * UTilizar tecnicas de limpieza de datos: extraer las "marcas", el "embase", la "unidad de medidad" de los nombres de los productos, colocarlo todo en minuscula, la cosa que al final te quedara "arroz blanco" contra "arroz blanco"
    * La idea es limpiar lo mejor posible la oracion para que solo te quede una pequeña descripcion, ha de verdad las limpieza lo hice con "expreciones regulares".
    * 




