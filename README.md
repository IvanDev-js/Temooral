# Lenguajes y Automatas I

##  
Este contenido mostrara diversos codigos realizados en el lenguaje python, principalmente uno que se realizo con automatas finitos denominado FADO, de la materia de Lenguajes y Automatas I

<a id='contents'></a>
## Contenido.
<ul>
<li><a href="#intro">Introdución.</a></li>
<li><a href="#wrangling">Tutorial para FAdo.</a></li>
<li><a href="#eda">Ejemplo de Aplicacion de FAdo</a></li>
<li><a href="#conclusions">Conclusions</a></li>
<li><a href="#reference">Referencias</a></li>
</ul>
  
<a id='intro'></a>

### Introdución.

En este documento llevaremos a cabo el desarrollo de un codigo en python de automatas finitos utilizando FADO, el cual nos ayudara a crear transiciones para poder identificar una direccion IP la cual ingresaremos por consola y nos dira si la IP que ingresamos es verdadera o falsa, de acuerdo a las declaraciones hechas en las transiciones.
 
<a id='wrangling'></a>
### Tutorial para FAdo

El sistema FAdo es un conjunto de herramientas para la manipulación de lenguajes regulares.

Los lenguajes regulares pueden representarse mediante expresiones regulares (regexp) o autómatas finitos, entre otros formalismos. Los autómatas finitos pueden ser deterministas (DFA) o no deterministas (NFA). En FAdo, estas representaciones se implementan como clases de Python. La documentación completa de todas las clases y métodos está disponible aquí.

Para trabajar con FAdo, después de la instalación, importe los siguientes módulos en un intérprete de Python:

```
1  from FAdo.fa import *
2  from FAdo.reex import *
3  from FAdo.fio import *
```

El módulo fa implementa las clases para autómatas finitos y el módulo reex, las clases para expresiones regulares. El módulo fio implementa métodos para la entrada/salida de autómatas y modelos relacionados.

### Automatas finitos.

La clase superior para autómatas finitos es la clase FA, que tiene dos subclases principales: OFA para autómatas finitos unidireccionales y la clase TFA para autómatas finitos bidireccionales. La clase OFA implementa la estructura básica de un autómata finito compartida por los DFA y los NFA. Esta clase define los siguientes atributos:

<ol>
<li>Sigma: es el alfabeto de entrada (conjunto)</li>
<li>States: lista de estados, es una lista que cada estado se referencia por su indice cada vez que se utiliza(transiciones, dinal, etc)</li>
<li>Initial: el estado inicial (o un conjunto de estados iniciales para NFA). Es un indice o una lista de indices</li>
<li>Final: el estado inicial (o un conjunto de estados iniciales para NFA). Es un indice o una lista de indices</li>
</ol>

En general, no se deben crear instancias (objetos) de la clase OFA. Las clases DFA y NFA implementan DFA y NFA, respectivamente. La clase GFA implementa NFA generalizados que se utilizan en la conversión entre autómatas finitos y expresiones regulares. Las tres clases heredan de la clase OFA.

Para cada clase hay métodos especiales para agregar/eliminar/modificar símbolos del alfabeto, estados y transiciones.

### DFAs

El siguiente ejemplo muestra como crear un DFA que acepte las palabras de {0,1}* que sean multiplos de 3.

```
 1   m3 = DFA()
 2   m3.setSigma(['0','1'])
 3   m3.addState('s1')     
 4 	 m3.addState('s2')     
 5   m3.addState('s3')          
 6   m3.setInitial(0)      
 7   m3.addFinal(0)          
 8   m3.addTransition(0, '0', 0)  
 9   m3.addTransition(0, '1', 1)   
 10  m3.addTransition(1, '0', 2) 
 11  m3.addTransition(1, '1', 0) 
 12  m3.addTransition(2, '0', 1) 
 13  m3.addTransition(2, '1', 2)    
```
Ahora es posible, por ejemplo, ver la estructura del autómata o probar si éste acepta una palabra.

```
1  m3.evalWordP("011") -> Verdadero 
2  m3.evalWordP("1011") -> Falso
```

<h4>Ejemplo de DFA</h4>

<a href="#contents">Ir a Contenido.</a>

<a id='eda'></a>
### Ejemplo de Aplicacion de FAdo

Vamos a realizar un ejercicio donde utilizaremos el ejemplo de FAdo pero esta vez realizaremos un codigo mas reducido para poder ahorrarnos codigo, en este caso utilizaremos un for en el cual uniremos el inicio, entrada y final, dentro del mismo for para poder realizar las transiciones.

### Ejemplo de codigo

```
1 def procesar_ip():
2    ipData = input("Teclea la Dirección IP: ")
3    ipEsperada = "192168155125"
4    es_valida = m3.evalWordP(ipData)  # Evalúa la IP ingresada
5    print(f"\nIP ingresada: {ipData}")
6    print(f"IP esperada: {ipEsperada}")
7    if ipData == ipEsperada:
8        print("Comparación con IP esperada: VERDADERA")
9    else:
10        print("Comparación con IP esperada: FALSA")
```

<a href="#contents">Ir a Contenido.</a>

<a id='conclusions'></a>
### Conclusiones.

Se llevo a cabo la realizacion del codigo utilizando FADO, el cual nos muestra y evalua la direccion IP que le ingresemos por consola, esta direccion IP nos dira si es verdadera o falsa dependiendo de la evaluacion que le indiquemos en el codigo de las transciones.

<a href="#contents">Ir a Contenido.</a>

<a id='reference'></a>
### Referencias

[1] “A small tutorial for FAdo — FAdo 2.1.2 documentation,” Fc.up.pt, 2023. 
https://www.dcc.fc.up.pt/~rvr/FAdoDoc/notebooks/FAdoTutorial.html (accedio May 22, 2025).

<a href="#contents">Ir a Contenido.</a>