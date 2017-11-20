# Ejercicio 1 de la Práctica del curso de git, gitHub y Sourcetree
### by Brais Moure

* ¿Qué comando utilizaste en el paso 11? ¿Por qué?
> He utilizado el comando `git reset --hard HEAD~1`
> 
> Con `git reset HEAD~1 ` dehago el último *commit* realizado. Si a mayores quiero modificar mi Working Copy, debo añadir `--hard`.
> De esta forma, **HEAD** y la rama **styled** apuntan al *commit* inmediatamente anterior, y mi Working Copy se modifica con el contenido del repositorio en ese punto. 

* ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?
> Uso el comando `git reflog` para visualizar la lista de operaciones realizadas sobre el repo (su rastro de migas), y así obtener el identificador SHA del *commit* que quiero rehacer.
> 
> A continuación identifico el *commit* que quiero rehacer (**c4fd31f HEAD@{1}: commit: Modifico el archivo git-nuestro.md para darle estilo.**) y me quedo con su identificador SHA.
> 
> Realizo un `git reset --hard c4fd31f` para modificar el contenido de mi Workig Copy, retornando al estado antes de deshacer este último *commit*.

* El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?
> En primer lugar hago en `git merge master` desde la rama **styled**.
> 
> La consola muestra el mensaje *Already up-to-date*. Esto es debido a que en la rama **styled** (creada a partir de **master**) hemos actualizado el archivo *git-nuestro.git*. En este lapso de tiempo, la rama **master** no ha avanzado, por lo que no existen modificaciones que mergear con nuestra rama actual **styled**. Es decir, no causa ningún conflicto.

* El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?
> Para hacer el *merge* me sitúo en la rama **styled** con `git checkout styled` y ejecuto `git merge htmlify`.
> Hecho esto, vemos que hay confictos. Las ramas **htmlify** y **styled** parten de **master**. En ambas se ha modificado el archivo *git-nuestro.md* con diferente contenido, por lo que si queremos incorporar el contenido de **htmlify** a **styled** deberemos elegir con cuál nos quedamos.

* El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?
> Para hacer este *merge* nos situamos en **master** con `git checkout master` y ejecutamos `git merge styled`.
> 
> El *merge* se realiza satisfactoriamente y sin conflictos ya que **styled** partió de **master**, y esta última no avanzó desde la creación de la rama. Por lo tanto, puede incorporar en ella los cambios de **styled** sin problema, aunque sean sobre código ya existente. Simplemente se trata de una versión más reciente del código, que no entra en conflicto con ninguna otra modificación realizada a posteriori sobre **master**. 

* ¿Qué comando o comandos utilizaste en el paso 25?
> Para dibujar el diagrama he utilizado el comando `git log --graph`.
> 
> También podría dibujar el diagrama resumido con` git log --pretty=oneline --graph`, por ejemplo. Así mostraría el grafo con sus *commit* en una única línea.

* El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?
> Sí que podría ser *fast-forward*, ya que, dado que la rama **title** ha partido del último *commit* de **master**, el puntero de **HEAD -> master** podría avanzar directamente hasta el de **title**, sin necesidad de realizar un *commit* adicional con las actualizaciones del fichero *git-nuestro.mg* (que es lo que hizo el *merge* *no fast-forward*).

* ¿Qué comando o comandos utilizaste en el paso 27?
> He utilizado el comando `git reset HEAD~1` sin `--hard` para deshacer el último *merge* sin perder los cambios de mi *Working Copy*. En realidad, lo que hago es retroceder al nodo del grafo inmeditamente anterior.

* ¿Qué comando o comandos utilizaste en el paso 28?
> Para descartar los cambios sobre el único archivo que tenemos ejecuto el comando `git checkout git-nuestro.md`.

* ¿Qué comando o comandos utilizaste en el paso 29?
> He eliminado la rama **title** con el comando `git branch -D title`.

* ¿Qué comando o comandos utilizaste en el paso 30?
> Para rehacer el *merge* lo primero que hago es ejecutar `git reflog` para buscar el identificador asociado al *merge* a rehacer. Una vez localizado, ejecuto `git reset --hard cbbc8e6` para actualizar mi Working Copy y volver al estado en el que habíamos añadido el título.

* ¿Qué comando o comandos usaste en el paso 32?
> Para regresar al *commit* inicial repito los pasos utilizados anteriormente. Busco el identificador deseado con `git reflog` y ejecuto `git reset 01344d7` para situarme en el *commit* deseado. Esta vez sin `--hard` ya que no me interesa actualizar mi *Working Copy*.

* ¿Qué comando o comandos usaste en el punto 33?
> Hago lo mismo que el en paso anterior. Esta vez ejecutando `git reset cbbc8e6` también sin `--hard` ya que actualmente ya poseo el *Working Copy* final.
