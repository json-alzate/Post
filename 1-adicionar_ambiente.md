# Ionic-Angular adicionar ambiente.<!-- omit in toc -->

Adicionar un nuevo ambiente y utilizarlo para compilar 	`ionic build` y para ejecutar `ionic serve` un proyecto de ionic framework

### Tabla de Contenido<!-- omit in toc -->

- [1- Nuevo archivo](#1--nuevo-archivo)
- [2- Registrar ambiente](#2--registrar-ambiente)
- [3- Compilar](#3--compilar)
- [4- Ejecutar](#4--ejecutar)
- [5- Sobre mi](#5--sobre-mi)

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

Ubica *`"configurations"`* y duplica el objeto *`"production"`*

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
[angular.json](https://www.example.com)

## 3- Compilar



## 4- Ejecutar



## 5- Sobre mi
Soy [Json Alzate](https://www.jheison.com)