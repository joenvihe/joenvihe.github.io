---
layout: post
title: Scrapeo a BVL
tags: [scraper,bvl,heroku, scheduler]
date: 2022-06-07 15:32 +0800
---

Estoy scrapeando el listado de las acciones de la bvl. Est

Me gustaria realizar un robot que me avise cuando comprar o cuando vender una accion.

Es por ello que busco las api's disponibles de la BVL, encontre varias, pero la que estoy utilizando es la que me dice la cotización del dia.

```bash
URL_HOME = "https://dataondemand.bvl.com.pe/v1/stock-quote/home"
payload = {
    "companyCode": "",
    "inputCompany": "",
    "isToday": "true",
    "sector": ""
}
```

Lo unico que hice fue encontrar el api, hacerle un request, obtener los datos y guardarlo en un BD.

Esto se esta ejecutando automaticamente en heroku batch:

- El proceso esta en su documentación:
https://devcenter.heroku.com/articles/clock-processes-python
- Las variables de entorno se guardan de la siguiente manera:
https://devcenter.heroku.com/articles/config-vars

Lo almaceno en una BD para saber el historico y generar alertas.






