# PROYECTO FINAL CIENCIA DE DATOS

## 1. y 2. DATASETS PRIMERO Y SEGUNDO Y LIMPIEZA DE DATOS (duplicados – eliminación de columnas, etc).

Se realizó la elección de dos datasets ubicados en www.datos.gov.co los cuales se encuentran en los siguientes links:

* https://www.datos.gov.co/Trabajo/Disparidad-Salarial-Hombres-Mujeres/hf6d-emrx/about_data
* https://www.datos.gov.co/Trabajo/Disparidad-de-Horas-Trabajadas-Hombres-y-Mujeres/bee9-sdwx/about_data

El primer dataset trata acerca de la disparidad salarial en cuanto a hombres y mujeres, donde podemos visualizar esta disparidad relacionada respecto a los diferentes departamentos, mientras que el segundo dataset trata acerca de la disparidad de horas trabajadas en cuanto a hombres y mujeres.

Se realizó la descarga de los archivos en formato CSV, y se realizó la limpieza de datos con OpenRefine.

![image](https://github.com/jufe941209/Proyecto-final-ciencia-de-datos/assets/128336195/22ef2a79-2c52-440b-9117-de766fa5b014)
![image](https://github.com/jufe941209/Proyecto-final-ciencia-de-datos/assets/128336195/71d47ee1-7083-4779-985c-5917054c9ef0)

Después se realizó el proceso de limpieza de datos mediante Python, eliminando los valores vacíos, valores anormales y valores no relevantes para el estudio.

Se observa que en los datasets encontramos las siguientes columnas: 
* Indicador,Periocidad,Desagregación geográfica,Dominio geográfico,año,valor salarial
* Indicador,Periodicidad,Desagregación geográfica,Dominio geográfico,año,valor horas

De las cuales se eliminó la columna de periodicidad, ya que todas presentan periodos anuales de evaluación, adicionalmente se realiza el renombre de la columna indicador en cada dataframe, para que al realizar el proceso de merge, se pedan unir los valores de forma correcta.

values1 = values1.rename(columns={"Indicador": "Indicador salarial"})
values2 = values2.rename(columns={"Indicador": "Indicador horas trabajadas"})

Se realizó el proceso de normalización de datos, mediante Python, ya que se encontraron algunos datos en donde se encuentran valores de “Colombia” en el campo de departamento.

values1['Dominio geográfico'] = values1['Dominio geográfico'].replace('Colombia', 'N/A')
values2['Dominio geográfico'] = values2['Dominio geográfico'].replace('Colombia', 'N/A')

## 3. Realizar un cruce

Se realiza el merge de los valores dentro de las dos bases de datos, donde utilizamos las columnas comunes como claves para el merge.

datos_combinados = pd.merge(values1, values2, on=["Desagregación geográfica", "Dominio geográfico", "año"], how='outer')

Se realizó el proceso de normalización de datos, mediante Python, ya que se encontraron algunos datos en donde se encuentran valores de “Colombia” en el campo de departamento.

values1['Dominio geográfico'] = values1['Dominio geográfico'].replace('Colombia', 'N/A')
values2['Dominio geográfico'] = values2['Dominio geográfico'].replace('Colombia', 'N/A')

A continuación se realiza el proceso de conversión del merge, en un archivo CSV.

datos_combinados.to_csv('data/datos_combinados.csv', sep=',', index=False)


## 4. Cargar en Github - clevercloud del archivo CSV.

Se despliega en este repositorio el CSV

![image](https://github.com/jufe941209/Proyecto-final-ciencia-de-datos/assets/128336195/bfb73030-75ed-4bfa-b069-76abe7d73914)

## 5.	Google Colab análisis de datos (como están distribuidos, sacar unas conclusiones)

Se realiza el proceso de análisis en Google Colab, el cual encontramos en el siguiente link:

https://colab.research.google.com/drive/1d6GwpJ7gIWi5Qp6uAenFGKA_7CmjqxRs

## 6.	Hacíamos unas gráficas, sacar conclusiones

Estas las podemos encontrar en el archivo de Google Colab mencionado en el punto anterior.

## 7.	Opcional (si hay datos geográficos – Mapa) 

En este Dataset no se encuentran datos geográficos, por lo que no se realiza mapa.

## 8.	Dashboard en la herramienta LookerStudio

Encontramos el dashboard en el siguiente link.


