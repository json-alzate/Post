# Ionic-Angular adicionar ambiente.<!-- omit in toc -->

Adicionar un nuevo ambiente y utilizarlo para compilar 	`ionic build` y para ejecutar `ionic serve` un proyecto de ionic framework

### Tabla de Contenido<!-- omit in toc -->

- [1- Nuevo archivo](#1--nuevo-archivo)
- [2- Registrar ambiente](#2--registrar-ambiente)
- [3- Compilar](#3--compilar)
- [4- Ejecutar](#4--ejecutar)
- [5- Archivo](#5--archivo)
- [6- Sobre mi](#6--sobre-mi)

## 1- Nuevo archivo
Por defecto se tienen dos archivos para configurar los ambientes que alimentaran la aplicación. Que son:

- src/environments/environment.ts
- src/environments/environment.prod.ts

Entonces, vamos a crear uno nuevo para un ambiente llamado: 
'staging'

- src/environments/environment.staging.ts

## 2- Registrar ambiente
En el archivo:

- angular.json

Dentro de *`"build"`* ubica *`"configurations"`* y duplica el objeto *`"production"`*

Y ahora lo más importante es cambiar la ruta del archivo que se utiliza para remplazar el ambiente por defecto en *`"fileReplacements"`*:

```
...
    "fileReplacements": [
        {
            "replace": "src/environments/environment.ts",
            "with": "src/environments/environment.staging.ts"
        }
    ],
...
```

El valor de *`"configurations"`* queda asi:
```
...
          "configurations": {
            "production": {
              "fileReplacements": [
                {
                  "replace": "src/environments/environment.ts",
                  "with": "src/environments/environment.prod.ts"
                }
              ],
...
            },
            "staging": {
              "fileReplacements": [
                {
                  "replace": "src/environments/environment.ts",
                  "with": "src/environments/environment.staging.ts"
                }
              ],
...
          }
...
```

En todo caso el archivo angular.json final:
[angular.json](https://github.com/json-alzate/Tutoriales/blob/master/files/1/angular.json)

## 3- Compilar
Antes de compilar la aplicación de Ionic, tengamos en cuenta que para compilar en Angular por defecto se utiliza:
`ng build --prod` que es una abreviatura de `ng build -c=production`, es decir que para una aplicación netamente en angular, valdría con ejecutar `ng build -c=staging` para  compilar con el ambiente que configuramos previamente.

Pero como estamos utilizando Ionic framework, **no** valdría algo como `ionic build -c=staging`, puesto que tenemos una envoltura adicional: asi que el comando correcto para Ionic es:

```
ionic build -- -c=staging
```



## 4- Ejecutar
Para que también el proyecto pueda ejecutarse en el navegador ya sabes con el típico `ionic serve`, pero con el ambiente *staging*,
En el archivo:

- angular.json

Ubica *`"serve"`* y adiciona al objeto *`"configurations"`* esto:

```
...
  "staging": {
    "browserTarget": "app:build:staging"
  },
...
```

Y para ejecutar el ambiente staging utiliza:
```
ionic serve -- -c=staging
```

## 5- Archivo
[angular.json](https://github.com/json-alzate/Tutoriales/blob/master/files/1/angular.json)

## 6- Sobre mi
Soy [Json Alzate](https://www.jheison.com), si te ha servido regálame una estrella.

Si te gusta compartir tu código, dame una mano en el proyecto de [ChessColate](https://github.com/json-alzate/ChessColate) :).