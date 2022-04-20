---
layout: post
title: Ejecutar Planificador de Tareas con Heroku
date: 2021-06-03 15:32 +0800
---

Necesito ejecutar un programita en python cada cierto periodo de tiempo. Sí, este programita es el que extrae los precios de los diferentes supermercados.

Deseo que se ejecute 1 vez a la semana y todos los lunes.

Para ello estoy utilizando, nuevamente [Heroku](https://www.heroku.com/), porque me permite programar 3 tareas, gratis.

Tambien me he guiado del siguiente tutorial en medium:
- [Tutorial](https://medium.com/analytics-vidhya/schedule-a-python-script-on-heroku-a978b2f91ca8)

Los pasos fueron:

1.- crear una carpeta con 3 archivos importantes:
- scheduler.py  (es el programita en python que deseas ejecutar)
- requirements.txt (son las dependencias que necesitas instalar en python)
- runtime.txt (la version del python, en este caso python-3.8.10)

2.- En heroku crear el pipeline

3.- Por linea de comandos crear app
`heroku create job-python-app`

4.- Desplegar por linea de comandos tu job a Heroku
```heroku git:clone -a job-python-app 
cd job-python-app
git add .
git commit -am "make it better"
git push heroku master
```

5.- Al pipeline creado en el paso 2 se adiciona el app creado en el paso 3

6.- Se adiociona al app "job-python-app" el resource "Advance Scheduler", donde se registra el Trigeer, colocandose el nombre del archivo python a ejecutar en este caso "scheduler.py"... la del punto 1