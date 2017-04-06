:data-transition-duration: 300
:title: Introducción a Git
:venue: 8vas Jornadas de Software Libre de la UNNOBA
:author: Martín Gaitán
:css: slides.css
:skip-help: true

Introducción a
===============


.. image:: img/Git.png


Gastón Avila / `@AvilaGas <http://twitter.com/AvilaGas>`_ / CC-by-sa

(Mayoritariamente trabajo de Martín Gaitán)

--------

:data-reveal: 1

Quién soy
---------

- Dr. en Física, gravitación clásica, datos iniciales,
- Albañil del software, Python, Javascript,
- Activista en OpenDataCordoba,
- ¿Git? ex-principiante.

avila.gas@gmail.com

-----------



En el principio...
--------------------


.. image:: img/01-copies.png


.. note::

    * flujo totalmente lineal
    * impide colaboración
    * no hay historia.
    * dónde hice qué

--------

:data-rotate: 90
:data-y: r1400


.. code:: html

    From: Juan <juancho@todavianosegit.com>
    To: Pedro <pete@todavianosegit.com>
    Subject: Trabajo

    Peter, acá te mando el zip con la última versión
    que incluye mi parte del trabajo

    ----

.. code:: html

    From: Pedro <pete@todavianosegit.com>
    To: Juan <juancho@todavianosegit.com>
    Subject: Re: Trabajo

    Juancito, me olvidé de avisarte que yo ya había
    hecho esa parte y cambié la API!

-------

:data-rotate: 90
:data-x: r-1400

Algunos creyeron evolucionar
------------------------------

.. image:: img/dropbox.jpg

.. note::

     * soluciona la sincronizacion de la última versión
     * sin merge

-----

:data-rotate: 90
:data-x: r-1400


.. image:: img/meme1.jpg

---------

:data-rotate: 90
:data-y: r1400


CVS/SVN
--------

Todo un avance, pero...

- Centralizado

  - Cuello de botella y Talón de Aquiles
  - Dependiente de la red para casi todo
  - Commits "bomba"

- Ramas difíciles

  - Flujo lineal
  - Dificulta el cambio de contexto/colaboración


--------

Y llegaron los sistemas distribuídos
-------------------------------------

- Git / Mercurial / Bazaar
- Todas las copias son repositorios
- Dependen menos de la red
- múltiples flujos posibles
- Más respaldos
- Experimentación / Branching fácil

------

:data-rotate: 90
:data-x: r-1400


Git: un DVCS rapidísimo y potente
----------------------------------

*Muy bien diez felicitado* en...

- ¡Velocidad!
- Integridad de datos
- Poca depencia de red
- Redundancia: todos son clones
- Branching y merging fácil: flujo versátil
- Bancarse proyectos como Linux
- **Github**

----------

:data-rotate: 90
:data-y: r1400

Los peros
---------

- La documentación también es distribuída ;-)
- La UI está llena de *WTF!*
- No hay **una** manera obvia
- Muchos nombres para referirse a lo mismo

--------

:data-rotate: 90
:data-x: r-1400


Y no es tan fácil
-----------------

.. image:: img/img_0.png

-----

.. image:: img/img_2.png

-----

.. image:: img/img_5.png

----

.. image:: img/img_9.png

-----

:data-rotate: 0
:data-y: r1400


Instalación
-----------

**Windows**

*http://code.google.com/p/msysgit*

**Linux**

.. code:: bash

    apt-get install git

**OS X**

.. code:: bash

    brew install git

--------

:data-rotate: 90
:data-y: r1400


Configuración
-------------

Quién sos

.. code:: bash

    git config --global user.name "Gastón Avila"
    git config --global user.email avila.gas@gmail.com


Tu editor

.. code:: bash

    git config --global core.editor nano

--------


Escribamos un paper
--------------------

.. code:: bash

    $ mkdir un-paper
    $ cd un-paper
    $ git init
    Initialized empty Git repository in /home/gavila/un-paper/.git/

--------

Que estoy haciendo?
--------------------

.. code:: bash

    $ git status
    On branch master

    Initial commit

    nothing to commit (create/copy files and use "git add" to track)

--------



Ahora escribo
-------------

.. code:: bash

    $ nano readme.md
    $ cat readme.md
    Introducción a Git
    ==================

    Lorem Ipsum es simplemente el texto de relleno de las imprentas y archivos
    de texto.
    Lorem Ipsum ha sido el texto de relleno estándar de las industrias desde
    el año 1500, cuando un impresor (N. del T. persona que se dedica a la
    imprenta) desconocido usó una galería de textos y los mezcló de tal
    manera que logró hacer un libro de textos especimen. No sólo sobrevivió
    500 años, sino que tambien ingresó como texto de relleno en documentos
    electrónicos, quedando esencialmente igual al original.

--------


Donde estoy?
-------------

.. code:: bash

    $ git status
    On branch master

    Initial commit

    Untracked files:
      (use "git add <file>..." to include in what will be committed)

        readme.md

    nothing added to commit but untracked files present (use "git add" to track)

--------


Agregar al stage
--------------------

.. code:: bash

    $ git add readme.md
    $ git status
    On branch master

    Initial commit

    Changes to be committed:
      (use "git rm --cached <file>..." to unstage)

    	new file:   readme.md

--------

Commit!
--------------------

.. code:: bash

    $ git commit -m "Crear primer párrafo"
    $ git status
    [master (root-commit) 0d0f711] Crear primer commit
     1 file changed, 11 insertions(+)
     create mode 100644 readme.md

--------


Que hice?
--------------------

.. code:: bash

    $ git log

    commit 0d0f711aa32c21b0ac790c638463e540f02a6f78
    Author: Gaston Avila <avila.gas@gmail.com>
    Date:   Wed Apr 5 23:36:49 2017 -0300

        Crear primer commit

--------


Agregar varios archivos
------------------------

.. code:: bash

    $ git status
    On branch master
    Untracked files:
      (use "git add <file>..." to include in what will be committed)

    	bibtex.tex
    	imagenes/

    nothing added to commit but untracked files present (use "git add" to track)

---------

Agregar varios archivos
------------------------

.. code:: bash

    $ git add .
    $ git status
    On branch master
    Changes to be committed:
      (use "git reset HEAD <file>..." to unstage)

    	new file:   bibtex.tex
    	new file:   imagenes/Git.png
    	new file:   imagenes/dropbox.jpg


---------


Commit de varios archivos
---------------------------

.. code:: bash

    $ git commit -m 'Imágenes y bibtex.tex'
    [master 542f7e2] Imágenes y bibtex.tex
     3 files changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 bibtex.tex
     create mode 100644 imagenes/Git.png
     create mode 100644 imagenes/dropbox.jpg

---------


Como vamos?
------------------------

.. code:: bash

    $ git log

    commit 542f7e203d3f68d41c8c98fff2a6dea27130bbaa
    Author: Gaston Avila <avila.gas@gmail.com>
    Date:   Wed Apr 5 23:57:15 2017 -0300

        Imágenes y bibtex.tex

    commit 0d0f711aa32c21b0ac790c638463e540f02a6f78
    Author: Gaston Avila <avila.gas@gmail.com>
    Date:   Wed Apr 5 23:36:49 2017 -0300

        Crear primer commit

---------


Deshaciendo
-------------

Corregir el último commit


.. code:: bash

    $ git commit --amend

Restaurar archivo

.. code:: bash

    git checkout file.java  # por defecto ``HEAD``
    git checkout [REV] -- file.java     # SHA1, tag, rama

Revertir commit

.. code:: bash

    git revert 1776f5

--------


Borrando
---------

*Unstage* (quitar del proximo commit)

.. code:: bash

    git rm --cached file.py

Dejar de *trackear*:

.. code:: bash

    git rm file.py

------------


¿Qué cambié?
------------

.. code:: bash

    $ git diff

    diff --git a/readme.md b/readme.md
    index c1a4618..cbdc480 100644
    --- a/readme.md
    +++ b/readme.md
    @@ -4,8 +4,10 @@ Introducción a Git
     Lorem Ipsum es simplemente el texto de relleno de las imprentas y archivos
     de texto.
     Lorem Ipsum ha sido el texto de relleno estándar de las industrias desde
    -el año 1500, cuando un impresor (N. del T. persona que se dedica a la
    +el año 1500, cuando un impresor (N. del T. tipo que se dedica a la
     imprenta) desconocido usó una galería de textos y los mezcló de tal
     manera que logró hacer un libro de textos especimen. No sólo sobrevivió
     500 años, sino que tambien ingresó como texto de relleno en documentos
     electrónicos, quedando esencialmente igual al original.
    +
    +Además esto debía tratarse de git, quizá deba incluir más texto robado.

------------


¿Qué cambié?
------------

Cambios en stage

.. code:: bash

    git diff --cached

Respecto a una revision

.. code:: bash

    git diff 1776f5

Visualmente

.. code:: bash

    meld .  # winmerge, kdiff3, otros...

--------

:data-rotate: 90
:data-x: r-1400


.gitignore
----------

No queremos control de **todo**

.. code:: bash

    *.pyc
    *.swp
    /build/
    /doc/[abc]*.txt
    .pypirc
    *.egg-info

.. note::

    • Blank lines or lines starting with # are ignored
    • Standard glob patterns work
    • End pattern with slash (/) to specify a directory
    • Negate pattern with exclamation point (!)

---------

:data-rotate: 90
:data-y: r1400


Ramas (Branches)
----------------

- Cambio de contexto indoloro (locales y rápidos)
- Son *punteros móviles* a un commit
- La rama por omisión se llama **master**

.. note::

     Factores externos necesitan inevitablemente de cambios de contexto.

     - Un bug severo se manifiesta en la última versión sin previo aviso.
     - El plazo para alguna presentación se acorta.
     - Un desarrollador que tiene que ayudar en una sección indispensable
       del proyecto está por tomar licencia.
     - Simplemente necesitas probar una idea

     En cualquier caso, debes soltar abruptamente lo que estás haciendo y enfocarte en una tarea completamente diferente.

-------

:data-rotate: 90
:data-x: r-1400


Creando una rama
----------------

.. code:: bash

    git branch experimento_loco
    git checkout experimento_loco

o directamente:

.. code:: bash

    git checkout -b experimento_loco

----------

Más comandos para ramas
------------------------

Cambiar de rama

.. code:: bash

    git checkout NOMBRE_RAMA

``checkout`` requiere todo *limpio*.
``stash`` es nuestra alfombra para esconder por un rato

.. code:: bash

    git stash
    git checkout NOMBRE_RAMA
    ...
    git checkout NOMBRE_RAMA_ORIGINAL
    git stash pop

----------


:data-rotate: 90
:data-y: r1400


Mezclar
--------

Desde otra rama. Ej: master

.. code:: bash

    git merge [--no-ff] experimento_loco

.. image:: img/merge1.png

------


:data-rotate: 90
:data-x: r-1400


En general hace magia
----------------------


.. image:: img/baby-git.png


-----------

Pero a veces no alcanza (conflictos)
------------------------------------

Corregimos a mano

.. code:: bash

    [corregimos los conflictos en el editor]
    git add file.rb
    git commit -m 'mezclando la rama X. corregi a mano el merge ...'

O forzamos lo nuestro / lo de ellos

.. code:: bash

    git checkout --ours file.rb  # o --theirs
    git add file.rb
    git commit

-----

:data-rotate: 0
:data-y: r1400


Rebase
--------

- Mover el origen de la rama
- Muy útil para *reescribir la historia*
- Recomendado antes de un *merge* a **master**

.. image:: img/merge2.png

.. image:: img/merge3.png

.. code:: bash

    # en feature-xyz
    git rebase master

------

:data-rotate: 90
:data-y: r1400


Listo, dónde subo mi código?
----------------------------

- Bitbucket / Gitorius
- Server del trabajo / facu
- Pero especialmente...

.. image:: img/github_logo.jpg

---------


Remotos
----------

Luego se pueden declarar repos remotos

.. code:: bash

    git remote add origin https://github.com/avilaton/un-paper.git

O directamente clonar un repositorio

.. code:: bash

    git clone https://github.com/avilaton/un-paper.git .

Son técnicamente iguales a nuestra copia de trabajo.
Pueden ser locales o remotos (ssh, https, etc.)

.. code:: bash

    $ git remote -v
    origin git://github.com/avilaton/un-paper.git (fetch)
    origin git://github.com/avilaton/un-paper.git (push)

-------

:data-rotate: 90
:data-x: r-1400


Empujando al remoto
-------------------

Sin default

.. code:: bash

   $ git push <remote> <rbranch>

O definimos default remoto para la rama actual

.. code:: bash

    git push -u <remote> <rbranch>

Y luego

.. code:: bash

    git push

-------

:data-rotate: 90
:data-y: r1400


Traeme lo nuevo (pull)
-----------------------


.. code:: bash

    git pull [<remote> <rbranch>]

``pull == fetch + merge``

---------------

Crear tags
-----------

Ponerle "nombre" a una revisión.

.. code:: bash

    git tag v0.1.0

Los tags son locales, pero se pueden pushear

.. code:: bash

    git push --tags

----------------


:data-rotate: 90
:data-x: r-1400


Github
-------

- No es sólo **hosting** git gratis (para software libre)
- Es una **plataforma social y profesional**
- ¡Colaborar con OSS nunca fue tan fácil!
- Gestión de proyectos / comunicación / revisión / etc.
- Enterarse de tendencias y aprender de cracks


-------

:data-rotate: 90
:data-y: r1400



Más info / práctica
--------------------

- Progit
- Git magic
- Githug
- Github help
- Esta charla: http://github.com/mgaitan/intro-git


---------

:data-rotate: 90
:data-rotate-y: 180
:data-y: r1400


Preguntas?
----------


----------


(Muchas gracias)
-----------------

.. note::

    Bibliografía

    http://dbrgn.ch/slides/20130207_getting_git/
    http://www.slideshare.net/CarlosTaborda/why-git-sucks-and-youll-use-it-anyways
    http://www.slideshare.net/leo.soto/introduccin-a-git
    https://speakerdeck.com/schacon/introduction-to-git
    http://www.slideshare.net/mickaeltr/git-github-leverage-your-open-source-projects
    http://www.slideshare.net/anildigital/git-introduction
