## Bienvenidos a la investigación de las comorbilidades del Covid 19

# 0. INTRODUCCIÓN.

La estructuración del proyecto tiene como fin la evaluación del impacto que ha tenido la reciente pandemia del **SARS-CoV-2 (COVID-19)**, en los servicios hospitalarios y en la tasa de muertes para pacientes con enfermedades crónicas como la DIABETES MELLITUS, para llegar a los resultados esperados los estudios se realizaran bajo los datos estadísticos de entidades como El Instituto Nacional de Salud INS, Departamento Administrativo Nacional de Estadística (DANE), Sistema Integral de Información de la Protección Social (SISPRO), la ORGANIZACIÓN MUNDIAL DE LA SALUD (OMS), entre otros.

# 1. OBJETIVOS:
1. Identificar las bases de datos pertinentes para la creación de Modelos de datos.
1.2. estudio generalizado de los indicadores de gestion del sector de salúd pública.
1.3. desarrollar un modelo estadistico para conocer las variables que intervienen en la muerte por covid.
1.4. Evaluar el desempeño de las entidades públicas con respecto a los tratamientos para el manejo de la pandemia.
1.5. Evaluar el impacto de la llegada del COVID-19 en la salud de comorbilidades tales como DIABETES MELLITUS. 

# 2. MARCO TEORICO

Para el desarrrollo de nuestra investigación, se utilizarán los siguientes componentes:
1.  **Dataset del instituto nacional de salud colombia INS**
2. **Dataset del instituno nacional de salud de los Estados unidos CDC**
3. **Python**
4. **EXCEL**
5. **Power Bi**
5. **STATSMODEL**
6.  **FACEBOOK PROPHET MODEL**
7. **CODIGOS  INTERNACIONALES DE ENFERMEDADES CD10**

# 3. PLANTEAMIENTO DEL PROBLEMA.

##3.1 Poblemas con los datos.
###3.1.1 Problemas con los sets de datos

dado que los datasets son demasiado grandes para poderlos abrir con herramientas como excel, demasiado incongruentes como para poder trabajarlos con power bi, realizaremos todo un trabajo de mineria de datos que va desde una limpieza de datos hasta la reducción en pequeños dataframes por medio de Python y los grabaremos en excel, para que pedan ser analizados por otros investigadores.

### 3.1.2  Errores de Origen.

dado que los datasets son consultas generalizadas que vienen de diferentes fuentes de información en el caso colombiano, son más de 1032 municipios, con sus entidades p{ublicas y privadas reportando EPS e IPS, se genera diferencias entre las formas en las que fueron estandarizadas las bases de datos, por lo que algunas variables vienen en diferentes formatos.

## 3.1.3 Normalización

para algunos datos realizaremos normalización booleana que consta de 0 para no y 1 para si, dado que constan de dos o más variables, en otras realizaremos normalización para rangos entre 0 y 1, para que las variables grandes no reduzcan a la minimima expresión a la más pequeñas.

## 3.2. Problemas de salud pública.

Una de las mayores problemáticas actuales en el Colombia, es el sector salud y no solo por el déficit que se presenta de personal de la salud, su alta demanda de usuarios, el poco tiempo de atención con el que cuentan los profesionales de la salud, para evaluar el estado real de los pacientes, la infraestructura deficiente, la alineación de subredes, si no que a todo lo anterior se suma la crisis sanitaria generada por la pandemia del COVID-19, situación que al 30 de Abril de 2021, lo posiciona en el ranking mundial de
contagios de Número 12 y a nivel de Latinoamérica en el tercer lugar[24].

## 4.0 INVESTIGACION DE LAS ESTADISTICAS
[Casos positivos de COVID-19 en Colombia](https://www.datos.gov.co/Salud-y-Protecci-n-Social/Casos-positivos-de-COVID-19-en-Colombia/gt2j-8ykr/data "Casos positivos de COVID-19 en Colombia")
Como ya lo mencionamos anteriormente iniciaremos realizando un estudio de las estadisticas generadas por el sistema de salud con el dataset del instituto nacional de salud INS.
generando pequeños datasets en los cuales podemos investigar el comportamiento de las diferentes variables encontradas.
### 4.1 Variables encontradas.
1.  Edad
2.  Genero
3.  Ubicación del caso.
4.  Sitio de aislamiento
5.  Diferencias entre el inicio de sintomas y el reporte
6.  Diferencias entre las series temporales.
7.  Estado de salud del caso.
8.   Velocidad de difusión del virus.
9.   Tipo de Recuperación.
10. Numero de muertes diarias.
11. Tiempos de Diagnostico.
12. Numero de Muertes por edad.
13. Quienes se contagian más.
14. Tiempo de Muerte.
15. Periodicidad con la que se debe realizar la evaluación de casos.
### Forma de obtención de datos.
de forma muy general enseñaremos la forma más fácil y eficiente de obtener los diferentes datos.

Como ejemplo utlizaremos la columna Sexo, que cuenta con 2 variables. F o M 	por medio de la funcion def, crearemos un nuevo dataframe normalizado de forma booleana de los generos.
        #Creando la columna Femenino
    # Funcion generar genero femenino
        def generof(fila): 
            sexf=fila['Sexo'] # en columna sexo le pedimos que analice la fila 
            if sexf =='F': # si en la fila esta la F
                resultado=1 # porque es mujer
                return resultado # Retorne 1
            else: # Sino
                resultado=0 # resultado es 0 porque no es mujer
                return resultado # Retorne 0 porque es hombre
        df_cases['Femenino']=df_cases.apply(generof,axis=1) #crea una nueva columna en el dataframe #llamada Femenino 
        
        #Creando la columna Masculino.
        def generom(fila):
            sexm=fila['Sexo']
            if sexm =='M':
                respuesta=1
                return respuesta
            else:
                respuesta=0
                return respuesta
        df_cases['Masculino']=df_cases.apply(generom,axis=1)
    
```python
#Creando la columna edad
def cluster_edad(fila):
    decil=fila['Edad']
    if decil<=10:
        resultado="Cluster_0"
        return resultado
    else:
        if decil>=11 and decil<=19:
            resultado="Cluster_1"
            return resultado
        else:
            if decil>=20 and decil<=29:
                resultado="Cluster_2"
                return resultado
            else:
                if decil>=30 and decil<=39:
                    resultado="Cluster_3"
                    return resultado
                else:
                    if decil>=40 and decil<=49:
                        resultado="Cluster_4"
                        return resultado
                    else:
                        if decil>=50 and decil<=59:
                            resultado="Cluster_5"
                            return resultado
                        else:
                            if decil>=60 and decil<=69:
                                resultado="Cluster_6"
                                return resultado
                            else:
                                if decil>=70 and decil<=79:
                                    resultado="Cluster_7"
                                    return resultado
                                else:
                                    if decil>=80 and decil<=89:
                                        resultado="Cluster_8"
                                        return resultado
                                    else:
                                        if decil>=90 and decil<=99:
                                            resultado="Cluster_9"
                                            return resultado
                                        else:
                                            if decil>=100:
                                                resultado="Cluster_10"
                                                return resultado
                                 
   # return resultado
#Nueva Columna Rango Edad
df_gen_edad['Rango_Edad']=df_gen_edad.apply(cluster_edad,axis=1)


```
```python
#Creando el nuevo Dataframe
df_gen_edad=df_gen_edad[['Rango_Edad','Edad','Sexo','Femenino','Masculino','Recuperado','Alentados','Activos','Fallecidos']]
df_gen_edad.head()
```

```python
#Salida #link
[Encabezado del dataframe de salida](http://github.com/milenabb88/Anteproyecto-Parte1/tree/master/Imagenes/) and ![DataFrameGeneroEdad.png]("Encabezado del dataframe de salida")

[![Encabezado del dataframe de salida](Imagenes "Encabezado del dataframe de salida")](http://github.com/milenabb88/Anteproyecto-Parte1/tree/master/Imagenes/DataFrameGeneroEdad.png "Encabezado del dataframe de salida")

Por ultimo creamos un nuevo dataframe en el cual por medio del cual consolidamos la información.
##Link
[![Dataframe de salida](imagenes Anteproyecto "Dataframe de salida")](http://https://github.com/milenabb88/Anteproyecto-Parte1/tree/master/Imagenes/Df_Recuperados.png "Dataframe de salida")

[Dataframe de salida](http://https://github.com/milenabb88/Anteproyecto-Parte1/tree/master/Imagenes/Df_Recuperados.png) and ![Df_Recuperados.png]("Dataframe de salida")

[Link](url) and ![Image](src)

```
