#¿Qué comando utilizaste en el paso 11? ¿Por qué?

- git reset --hard HEAD~1  Deshacer el último commit y lo que había en mi working copy de manera que todo quede como estaba antes. Nuestro staging area queda vacío.


    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git reset --hard HEAD~1
    HEAD is now at 9c91f87 Punto Numero 4`

- Veo el resultado con git log 

    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git log
    commit 9c91f87459b03ddc31610d307bf68c8ba6e52ada
    Author: Miguel Mingoarranz Perez <soymingo@gmail.com>
    Date:   Wed Apr 26 08:54:33 2017 +0200

    Punto Numero 4`


#¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?

- Utilizo ref log para ver los puntos en ni proyecto

    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git reflog
    9c91f87 HEAD@{0}: reset: moving to HEAD~1
    7fee194 HEAD@{1}: commit: Punto Numero 10
    9c91f87 HEAD@{2}: checkout: moving from master to styled
    9c91f87 HEAD@{3}: commit (initial): Punto Numero 4`


- Utilizo el comando git reset --hard + (hast 7 digitos) que me permite volver al comit anterior y ademas puedo recuperar los archivos del working copy de ese comit


    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git reset --hard 7fee194
    HEAD is now at 7fee194 Punto Numero 10`



- Compruebo cambios con git log

    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git log
    commit 7fee1943d5af84179e63391d8e2fccb1367b9fbb
    Author: Miguel Mingoarranz Perez <soymingo@gmail.com>
    Date:   Wed Apr 26 09:10:18 2017 +0200

    Punto Numero 10

    commit 9c91f87459b03ddc31610d307bf68c8ba6e52ada
    Author: Miguel Mingoarranz Perez <soymingo@gmail.com>
    Date:   Wed Apr 26 08:54:33 2017 +0200

    Punto Numero 4`



#El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?


    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git merge master
    Already up-to-date.`

- Este merge no realiza ningun cambio ya que la rama master ta conitene un comit que contiene la rama master
- Los archivos no entran en conflicto dado que mantiene las diferentes versiones en comits diferentes





#El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?

- Vuelvo a la rama styled

    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git checkout styled
    Switched to branch 'styled'`

- Realizo el merge

    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git merge htmlify
    Auto-merging git-nuestro.md
    CONFLICT (content): Merge conflict in git-nuestro.md
    Automatic merge failed; fix conflicts and then commit the result.`
    
- Causa un conflicto que arreglare editando el archivo nano git-nuestro.md quedandome con el contenido deseado. Despues realizare un git add git-nuestro y git commit. Al no pedir el punto 20 en esta practica no documento los cambios en este archivo



#El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?

- Cambio a la rama master

    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git checkout master
    Switched to branch 'master'`

- Realizo el merge  git merge styled. al ser un merge Fast-Forward se mueve el puntero de master a styled. Esta operacion no genera conflictos porque en cada comit existe una version diferente de nuestro archivo

    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git merge styled
    Updating 9c91f87..13ead6d
    Fast-forward
    git-nuestro.md | 20 ++++++++++----------
    1 file changed, 10 insertions(+), 10 deletions(-)`




#¿Qué comando o comandos utilizaste en el paso 25?

- git log graph

    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git log --graph
    *   commit 13ead6da5910752cbb6eb926d69e68e4c5bd5f6a
    |\  Merge: 7fee194 406cd69
    | | Author: Miguel Mingoarranz Perez <soymingo@gmail.com>
    | | Date:   Wed Apr 26 09:50:01 2017 +0200
    | | 
    | |     Merge branch 'htmlify' into styled
    | |   
    | * commit 406cd69430469fd22ea7323378d18ccb5dd20aa8
    | | Author: Miguel Mingoarranz Perez <soymingo@gmail.com>
    | | Date:   Wed Apr 26 09:41:06 2017 +0200
    | | 
    | |     Punto Numero 17
    | |   
    * | commit 7fee1943d5af84179e63391d8e2fccb1367b9fbb
    |/  Author: Miguel Mingoarranz Perez <soymingo@gmail.com>
    |   Date:   Wed Apr 26 09:10:18 2017 +0200
    |   
    |       Punto Numero 10
    |  
    * commit 9c91f87459b03ddc31610d307bf68c8ba6e52ada
    Author: Miguel Mingoarranz Perez <soymingo@gmail.com>
    Date:   Wed Apr 26 08:54:33 2017 +0200

    Punto Numero 4`

- Otras posibilidades son git log --decorate y git log --online


#El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?

- Uso el comando git merge --no-ff title. En este caso se crea se crea un nuevo comit que contiene los punteros de master. El puntero de title quedaria en su commit

   ` MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git merge --no-ff title
    Merge made by the 'recursive' strategy.
    git-nuestro.md | 1 +
    1 file changed, 1 insertion(+)`


    `   ........................
*   commit ea32a9a28045a6cc3c18fda9e7a061cebd23c9bd
    |\  Merge: 13ead6d 11cc2ae
    | | Author: Miguel Mingoarranz Perez <soymingo@gmail.com>
    | | Date:   Wed Apr 26 10:24:18 2017 +0200
    | | 
    | |     Merge branch 'title'
    | |   
    | * commit 11cc2aeee032083552e8aa0ebac18db40714c379
    |/  Author: Miguel Mingoarranz Perez <soymingo@gmail.com>
    |   Date:   Wed Apr 26 10:11:58 2017 +0200
    |   
    |       Punto Numero 23
    `

- Si podria ser fast-forward, porque title ya tenia la informacion de master

#¿Qué comando o comandos utilizaste en el paso 27?

    - git reset HEAD~1 dado que no quiero perder los datos del working copy



#¿Qué comando o comandos utilizaste en el paso 28?

- git checkot --gitnuestro.md

    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git checkout -- git-nuestro.md
    MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$` 

#¿Qué comando o comandos utilizaste en el paso 29?

- git branch -D title

    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git branch -D title
    Deleted branch title (was 11cc2ae).`



#¿Qué comando o comandos utilizaste en el paso 30?

- git reflog para ver los ultmos cambios

    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git reflog

    13ead6d HEAD@{1}: reset: moving to HEAD~1
    ea32a9a HEAD@{2}: merge title: Merge made by the 'recursive' strategy.
    13ead6d HEAD@{3}: checkout: moving from title to master
    11cc2ae HEAD@{4}: commit: Punto Numero 23`

- git reset --hard + HEAD{2}

    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git reset --hard ea32a9a
    HEAD is now at ea32a9a Merge branch 'title'`


#¿Qué comando o comandos usaste en el paso 32?


- Saco todos los commits con el comando git log

    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git log
    commit ea32a9a28045a6cc3c18fda9e7a061cebd23c9bd
    Merge: 13ead6d 11cc2ae
    Author: Miguel Mingoarranz Perez <soymingo@gmail.com>
    Date:   Wed Apr 26 10:24:18 2017 +0200

    Merge branch 'title'

    commit 11cc2aeee032083552e8aa0ebac18db40714c379
    Author: Miguel Mingoarranz Perez <soymingo@gmail.com>
    Date:   Wed Apr 26 10:11:58 2017 +0200

    Punto Numero 23

    commit 13ead6da5910752cbb6eb926d69e68e4c5bd5f6a
    Merge: 7fee194 406cd69
    Author: Miguel Mingoarranz Perez <soymingo@gmail.com>
    Date:   Wed Apr 26 09:50:01 2017 +0200

    Merge branch 'htmlify' into styled

    commit 406cd69430469fd22ea7323378d18ccb5dd20aa8
    Author: Miguel Mingoarranz Perez <soymingo@gmail.com>
    Date:   Wed Apr 26 09:41:06 2017 +0200

    Punto Numero 17

    commit 7fee1943d5af84179e63391d8e2fccb1367b9fbb
    Author: Miguel Mingoarranz Perez <soymingo@gmail.com>
    Date:   Wed Apr 26 09:10:18 2017 +0200

    Punto Numero 10

    commit 9c91f87459b03ddc31610d307bf68c8ba6e52ada
    Author: Miguel Mingoarranz Perez <soymingo@gmail.com>
    Date:   Wed Apr 26 08:54:33 2017 +0200

    Punto Numero 4`

- Me desplazo al comit deseado ejecutando "git checkout <commit deseado>  

    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git checkout 9c91f87459b03ddc31610d307bf68c8ba6e52ada
    HEAD is now at 9c91f87... Punto Numero 4`


- Tambien puedo moverme entre comit usando git reset --hard <commit deseado>  

    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git reset --hard 9c91f87459b03ddc31610d307bf68c8ba6e52ada
    HEAD is now at 9c91f87 Punto Numero 4`





#¿Qué comando o comandos usaste en el punto 33?

- Me desplazo al comit deseado ejecutando "git checkout <commit deseado> 

    `MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git checkout ea32a9a28045a6cc3c18fda9e7a061cebd23c9bd
    Previous HEAD position was 9c91f87... Punto Numero 4
    HEAD is now at ea32a9a... Merge branch 'title'`


- Tambien puedo moverme entre comit usando git reset --hard <commit deseado> 
    ` MacBook-Air-de-Miguel:practicaGitMiguel mingoarranz$ git reset --hard ea32a9a28045a6cc3c18fda9e7a061cebd23c9bd
    HEAD is now at ea32a9a Merge branch 'title'`

