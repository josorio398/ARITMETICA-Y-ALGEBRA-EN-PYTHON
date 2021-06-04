

Descripción general
===================

Este módulo contiene algunas herramientas para la representación gráfica de vectores en el plano y en 
el espacio, diseñado para un curso de álgebra lineal con aplicaciones, contiene funciones para graficar
vectores con punto inicial y punto final dado, o anclados en el origen, para su realización se utilizó 
la librería de graficación interactiva **Plotly** y la librería de arreglos multidimensionales **NumPy**,
es compatible con vectores construidos como matriz columna en la librería **SymPy**. Puede servir como 
herramienta de visualización, para validar el conocimiento por parte de los estudiantes y para la 
resolución de problemas relacionados con conceptos vectoriales.

|travis| |lgtm| |coveralls| |libraries|

.. |travis| image:: https://img.shields.io/badge/python%20-%2314354C.svg?&style=flat&logo=python&logoColor=white
  :target: https://travis-ci.org/cdown/srt
  :alt: Tests

.. |lgtm| image::  https://img.shields.io/badge/plotly%20-%233B4D98.svg?&style=flat&logo=plotly&logoColor=white
  :target: https://lgtm.com/projects/g/cdown/srt/overview/
  :alt: LGTM

.. |coveralls| image:: https://img.shields.io/badge/numpy%20-%230095D5.svg?&style=flat&logo=numpy&logoColor=white
  :target: https://coveralls.io/github/cdown/srt?branch=develop
  :alt: Coverage

.. |libraries| image:: https://img.shields.io/badge/SymPy%20-%23239120.svg?&style=flat&logo=sympy&logoColor=white
  :target: https://libraries.io/github/cdown/srt
  :alt: Dependencies

Instalación
===========

Para utilizar el módulo de graficación **plotvectors** debe importarlo de la siguiente manera:

.. code:: python

    pip install PlotLinearAlgebra

.. code:: python

    from PlotLinearAlgebra.plotvectors import *

Funciones
=========

El submódulo **plotvectors** contiene las funciones **plotvectors2D** que permite realizar la visualización 
de vectores en el plano cartesiano y **plotvectors3D** que permite la visualización de vectores en el espacio
tridimensional, para definir puntos en estos módulos se usarán los objetos tipo tupla, por ejemplo el punto 
``P =(x,y)`` o ``P =(x,y,z)`` y para definir vectores se usarán listas, por ejemplo el vector unidimensional
``V =[x]``, bidimensional ``V =[x,y]`` o tridimensional ``V =[x,y,z]``,  también podemos definir vectores 
como una matriz columna, haciendo uso de la librería sympy, de la forma ``V =Matrix([x])``, ``V =Matrix([x,y])`` 
o ``V =Matrix([x,y,z])`` dependiendo de la dimensión del vector.

plotvectors2D
-------------

Permite visualizar múltiples vectores en el plano cartesiano, que pueden tener un punto inicial y un punto final 
dado, estar anclados en el origen del plano, o vectores equipolentes a otro que inicie en un punto dado (traslación de vectores),
y vectores en forma polar anclados en el origen o con un punto inicial dado, acepta como argumentos vectores unidimensionales o
bidimensionales definidos como matriz columna en la librería SymPy.

A continuación  se presenta la sintaxis adecuada para el manejo de esta función:

- ``plotvectors2D([x,y])`` permite graficar un vector con punto inicial ``(0,0)`` y punto final ``(x,y)``.
- ``plotvectors2D([x])`` permite graficar un vector unidimensional en la recta numérica con punto inicial  en el origen y punto final ``(x)``.
- ``plotvectors2D(V)`` permite graficar un vector definido como ``V = [x,y]`` o  ``V = [x]``, usando la librería **sympy** se pueden definir como ``V = Matrix([x,y])`` o ``V = Matrix([x])``.
- ``plotvectors2D([P,Q])`` permite graficar un vector con punto inicial ``P = (x1,y1)`` y punto final ``Q = (x2,y2)``.
- ``plotvectors2D([P,V])`` permite graficar un vector equipolente a un vector definido como: ``V = [x,y]``, ``V = [x]``, ``V = Matrix([x,y])`` o ``V = Matrix([x])`` con punto inicial en ``P = (x0,y0)``.
- ``plotvectors2D([a,"b"])`` permite graficar un vector con magnitud ``a`` y ángulo en grados respecto al eje x positivo ``b``.
- ``plotvectors2D([P,a,"b"])`` permite graficar un vector con punto inicial en ``P = (x0,y0)``, magnitud ``a`` y ángulo en grados respecto al eje x positivo ``b``.
- ``plotvectors2D([v1],[v2],...,[v3])`` permite graficar múltiples vectores en el plano definidos de diferente forma.

Como ejemplo, podemos presentar el siguiente código donde A,B,C,D se definen como vectores y P y Q se definen como puntos:

.. code:: python

    from sympy import Matrix
   
    A = Matrix([-3,8])
    B = Matrix([3])

    C = [3,10]
    D = [-4]
   
    P = (7,5)
    Q = (2,12)

    plotvectors2D([4,6],[6],A,B,C,D,[P,Q],[P,A],[P,C],[(7,2),C],[(-4,12),D],[8,"300"],[(4,-6.928),6,"90"]) 
    
plotvectors3D
-------------

Permite visualizar multiples vectores en el espacio tridimensional, que pueden tener un punto inicial y un punto final dado, estar 
anclados en el origen del espacio, o vectores equipolentes a otro que inicie en un punto dado (traslación de vectores), y vectores
desde una magnitud y un vector director unitario dado, acepta como argumentos vectores columna tridimensionales definidos en la librería SymPy.

A continuación  se presenta la sintaxis adecuada para el manejo de esta función:

- ``plotvectors3D([x,y])`` permite graficar un vector con punto inicial ``(0,0,0)`` y punto final ``(x,y,z)``.
- ``plotvectors3D(V)`` permite graficar un vector definido como ``V = [x,y,z]`` o en la librería **sympy** como ``V = Matrix([x,y,z])``.
- ``plotvectors3D([P,Q])`` permite graficar un vector con punto inicial ``P = (x1,y1,z1)`` y punto final ``Q = (x2,y2,z2)``.
- ``plotvectors3D([P,V])`` permite graficar un vector equipolente al vector  definido como ``V = [x,y,z]`` o  ``V = Matrix([x,y,z])`` con punto inicial en ``P = (x0,y0,z0)``.
- ``plotvectors3D([a,U])`` permite graficar un vector con magnitud ``a`` y vector director unitario definido como ``U = [x,y,z]`` o ``U = Matrix([x,y,z])``.
- ``plotvectors3D([P,a,U])`` permite graficar un vector con punto inicial en ``P = (x0,y0,z0)``, magnitud ``a`` y vector director unitario definido como ``U = [x,y,z]`` o ``U = Matrix([x,y,z])``.
- ``plotvectors3D ([v1],[v2],...,[v3])`` permite graficar múltiples vectores en el espacio definidos de diferente forma.

Como ejemplo, podemos presentar el siguiente código donde A,B se define como vectores, i,j,k como vectores unitario y P y Q como puntos:

.. code:: python
    from sympy import Matrix

    A = Matrix([6,2,3])
    B = [3,4,5]

    P = (-4,2,3)
    Q = (5,4,6)

    i = [1,0,0]
    j = [0,1,0]
    K = [0,0,1]

    norm = A.norm()
  
    U = (1/norm)*A
  
    plotvectors3D([1,2,3],B,A, [P,Q],[P,B],[(6,3,5),A],[(1,-2,3),(5,-4,-6)],[3,i],[(1,2,3),3,j],[5,K],[(4,5,6),8,U]) 

Colaboradores
=============

Jhonny Osorio Gallego


