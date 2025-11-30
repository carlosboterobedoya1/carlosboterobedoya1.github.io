##**Tarea 2 - Ejercicios Unidad 1**

**#Primer ejercicio hacer que ujna tortuga camine hacia delante:**

```python
def adelante(n):
    print("-" * n + ">")
    return
```

```python
adelante(50)
```

```
-------------------------------------------------->
```


**#Segundo ejercicio simulacion de la tortuga bajando**

```python
def abajo(n):
    print("\n".join("|" * n + "V"))  # Le pedi ayuda a chat con este concepto "\n".join sirve para unir varios elementos
                                     # de una lista o iterables en un solo texto.
    return
```

```python
abajo(5)
```

```
|
|
|
|
|
V
```


**#Tercer ejercicio que es hacer que la tortuga simule hacer un giro de 90 grados.**


```python
def adelante(n):
    print("-" * n + ">")
    return

def abajo(n, m, actual=0):  # En este caso se utilizo recursion ya que hace el papel de un ciclo, actual=0 controla cuantas 
    if actual > m:         # veces se llama a si misma y cuando se debe detener.
        return
    espacios = " " * n
    if actual < m:         
        print(espacios + "|")
    else:
        print(espacios + "V")
    abajo(n, m, actual + 1)  # lo malo de esto es que se debe poner n tambien cuando se va a llamar m, va a quedar asi abajo(n,m)
                             # lo que se quiere es abajo(m).
```

```python
adelante(5)
abajo(5, 2)
```

```
----->
     |
     |
     V
```

**#Cuarto ejercicio simucacion de una tortuga baje escalones.**

**primera solucion.**


```python
def adelante(n, movilidad=0):  # Movilidad hace que la flecha se mueva hacia la derecha.
    print(" " * movilidad + "-" * n + ">")  # el "-" * n es el largo de la flecha.

def abajo(m, movilidad=0, actual=0):  # como vimos anteriormente actual es un contador.
    if actual > m:                   
        return
    
    if actual < m:
        print(" " * movilidad + "|")  # Cuando actual es < n imprime "|"
    else:
        print(" " * movilidad + "v")  # cuando actual == n imprime V.
    
    abajo(m, movilidad, actual + 1)

def escalon(n, m, repeticiones, nivel=0):  # Nivel empieza en cero y va subiendo para cada nivel.
    if nivel == repeticiones:
        return
    
    movilidad = nivel * (n + 2)

    adelante(n, movilidad)
    abajo(m, movilidad + n)

    escalon(n, m, repeticiones, nivel + 1)  # en este caso solo se tiene que poner al ejecutar escalon(n, m y el numero de escalones)
                                            # quedaria asi escalon(5,2,3)
```

```python
escalon(5, 2, 3)
```

```
----->
     |
     |
     v
       ----->
            |
            |
            v
              ----->
                   |
                   |
                   v
```


**segunda solucion del cuarto ejercicio**

```python
posicion = 0  # Posicion es una variable que guarda cuantos espacios hay que poner antes de dibujar, y queda fuera para declarar las dos sentencias.

def adelante(n):
    global posicion 
    print(" " * posicion + "-" * n + ">")
    posicion += n  # Aumenta la posiscion para que el siguiente dibujo quede más a la derecha.

def abajo(n):
    global posicion
    vertical = posicion  # se usa vertical = posicion para alinear la línea justo debajo de la flecha.
    if n >= 1:  # Dependiendo del número n, imprime la cantidad de "|".
        print(" " * vertical + "|")
    if n >= 2:
        print(" " * vertical + "|")
    if n >= 3:
        print(" " * vertical + "|")
    if n >= 4:
        print(" " * vertical + "|")
    if n >= 5:
        print(" " * vertical + "|")
    print(" " * vertical + "V")  # Al final se imprime la cabeza "V"
```

```python
adelante(5)
abajo(2)

adelante(5)
abajo(2)

adelante(5)
abajo(2)
```

```
----->
     |
     |
     V
     ----->
          |
          |
          V
          ----->
               |
               |
               V
```



