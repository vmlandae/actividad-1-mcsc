
# Actividad 1

Instrucciones

## 1. Pasos básicos en Git y GitHub. 

Completa los siguientes pasos (10 minutos):

(a) Asegúrense de tener instalado git en cada una de sus máquinas locales. Saquen un screenshot del comando `$ git --version`, o en su defecto, de GitHub Desktop.

(b) Los que no tengan una cuenta de GitHub, [háganse una cuenta personal acá](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home).

(c) Ingresen al github de la ayudantía 1 [github.com/vmlandae/actividad-1-mcsc], y vayan a los issues.  Ahí estará posteada una lista de asignación de grupos sin llenar, llamada "Usuarios de GitHub para la actividad 1". Escriban un comentario con su nombre-nickname y con el link de su usuario de GitHub.

(d) Hagan click en "Watch" (arriba a la derecha), con lo cual se inscriben para recibir notificaciones cuando hayan cambios en el repo. 

(e)  Hagan un "Fork" del repositorio, con lo cual crean una copia de este repositorio en su cuenta de GitHub personal. 

## 2. Actividad grupal con Git y GitHub

 Cada uno de ustedes que haya hecho el comentario del item (c) será asignado a un grupo, de 2 o 3 personas. Tendrá también asignado un rol, el cual puede ser *Core Developer*, *Contributor 1* o *Contributor 2*. Para los grupos de 2, el *Contributor 1* tomará las labores adicionales del *Contributor 2*. La evaluación es grupal, así que la idea es que puedan ayudarse en las tareas de cada uno. Hagan los siguientes pasos:

(a) El Core Developer crea un repositorio nuevo, llamado `DescrStats` en su 
GitHub personal. Seleccione las opciones de  "Public repository" y de "Initialize
this repository with a README". NO SELECCIONE la opción "Add .git-
ignore" o "Add a license". OJO: NO clone este repositorio dentro de otro repositorio de Git.

(b) Core Developer añade al Contributor 2 como un "contributor" al repositorio. Esto le da los mismos privilegios de "merge" que tiene el Core Developer.
(c) El Contributor 1 y el Contributor 2 le hacen fork a este repositorio.

(d) El Core Developer crea un branch llamado "python" y envía un *pull request* al "main" branch, en el que haya añadido el archivo `DescrStats.py`, los datos `datafile.txt`, y el archivo `.gitignore` al repositorio, en el `root`. Estos archivos están en el repositorio de la ayudantía, en la carpeta Actividad1. 

(e) El Contributor 2 hace un merge a este pull request, con el comentario "Todo OK, @CoreDeveloper ." donde @CoreDeveloper es el usuario de GitHub del mismo, para que quede etiquetado. 

(f) Contributor 1 crea un branch en su fork, llamado `read` , en el que actualiza el README.md para que tenga lo siguiente:
> # Documentación para `DescrStats.py` y la función `DescrStats()`
> Este repositorio contiene el módulo de Python `DescrStats.py`, que define
> la función `DescrStats()`. Esta función puede ser usada importando el módulo, 
> y usándola con un archivo de texto (de extensión `.txt`), que sea delimitado por comas,
> y que tenga una única variable.
> 
> ```python
> import DescStats as ds
> ds.DescrStats(`datafile.txt')
> ```
> Hemos puesto un archivo de datos de ejemplo en el repositorio (`datafile.txt`), 
> el cual puede ser usado para testear el módulo.

El Contributor 1 envía este cambio al "main" del repositorio principal con un pull request.

(g) Core Developer hace el merge con el comentario "Gracias por la actualización al `README.md`!"
(h) El Contributor 1 encuentra un error en el código de `DescrStats.py`, donde la función `data.variance()`
está incorrecta. Luego, el Contributor 1 crea un branch llamado "varfix" y cambia la línea 17, haciendo:
> data_var = data.var()
y hace un submit de un pull request al "main" del Core Developer, con el comentario "encontré este error en la función, con el cambio queda bien."
(i) El Contributor 2 hace el merge con el comentario "check".
(j) El Contributor 2 crea el siguiente issue, llamado "Mejoras para DescrStats()", con el label "enhancement", que use "check boxes" para una lista de nuevas características para añadir a `DescrStats.py`.
> Creo que podríamos añadir más funcionalidad a `DescrStats()`, en el módulo `DescrStats.py`.
> - [] Que retorne la estadística descriptiva como una tupla de escalares. 
> - [] Añadir `minimum` y `maximum`.
> - [] Incluir como argumento a un Booleano que diga si la función plotea un histograma de los datos. 

(k) El Core Developer crea un branch llamado "returnvals" y hace el siguiente cambio a `DescrStats.py`.

> def DescrStat(datafile):
>   data = np.loadtxt(datafile)
>   data_mean = data.mean()
>   data_std = data.std()
>   data_var = data.var()
> 
>   print('Mean of the data is:', data_mean)
>   print('Standard deviation of the data is:', data_std)
>   print('Variance of the data is:', data_var)
> 
>   return data_mean, data_std, data_var
Y envía este cambio al "main" repository directamente. 

(l) El Contributor 2 hace un check en la primera caja. 

(m) El Core Developer nota que la documentación interna no es buena, y crea un branch llamado "docstr", y hace los siguientes cambios:

```python
def DescrStat(datafile):
    '''
    --------------------------------------------------------------------
    Esta función imprime y retorna estadística descriptiva de un archivo de texto delimitado por comas, de una sola variable
    --------------------------------------------------------------------
    INPUTS:
    datafile = string, path del archivo de datos a usar en la función.
    OTRAS FUNCIONES Y ARCHIVOS LLAMADOS POR ESTA FUNCIÓN: None
    OBJETOS CREADOS EN LA FUNCIÓN:
    data = (N,) vector, data de datafile
    data_mean = scalar, promedio de los datos
    data_std = scalar >= 0, desviación estándar de la data
    data_var = scalar >= 0, varianza de la data
    ARCHIVOS CREADOS PRO ESTA FUNCIÓN: None
    RETURNS: data_mean, data_std, data_var
    --------------------------------------------------------------------
    '''
    data = np.loadtxt(datafile)
    data_mean = data.mean()
    data_std = data.std()
    data_var = data.var()
    print('Promedio de los datos es de:', data_mean)
    print('Desviación Estándar de los datos es de:', data_std)
    print('Varianza de los datos es de:', data_var)
    return data_mean, data_std, data_var

```
Envía estos cambios como un pull request al "main".

(n) El Contributor 2 hace el merge con el comentario: "Gracias, quedó mucho mejor documentado, y en español :)"
