# Introduccion
Durante la ejecución de un programa, las variables
declaradas se ubican en memoria, c++ posee una sintaxis
especial para obtener la dirección en memoria que ocupa
la variable, para este cometido se hace uso del simbolo ```&```.

La sintaxis del lenguaje es variada para el uso de este
símbolo y no todo el tiempo se interpreta de la misma
manera por el compilador por lo que a continuación se
presentarán algunos ejemplos:


# Obteniendo la dirección de una variable

Si se quiere saber la dirección de una variable
se puede obtener de la siguiente manera, en el ejemplo 6.1

```cpp
#include <iostream>
int main(){
	int var = 999;
	std::cout << "La direccion de var es: " << &var << std::endl;
	return 0;
}
```

# Aspectos importantes de las direcciones.

El siguiente código asigna valores a dos variables de tipo ```int``` en el ejemplo 6.2:
```cpp
#include <iostream>

int main(){
	int a = 1;
	int b = 2;

	std::cout << "Valor de a: " << a << std::endl;
	std::cout << "Direccion de a: " << &a << std::endl;
	std::cout << "Valor de b: " << b << std::endl;
	std::cout << "Direccion de b: " << &b << std::endl;

	return 0;
}
```
La salida del código es la siguiente:
```
Valor de a: 1
Direccion de a: 0x7ffc80b3c640
Valor de b: 2
Direccion de b: 0x7ffc80b3c644
```

Se recalca lo siguiente:

* Las direcciones se presentan como números en hexadecimal.
* El tamaño de un int son 4 bytes.
* La dirección después de la de a es a + 4.

Es decir las variables se posicionan una después de otra según el tamaño en bytes
utilizando la estructura de datos conocido como pila (stack), el manejo de memoria
como tal es un tema que rebasa el alcance de los temas a tratar en la unidad.

Por esta razón, solo se proveeran referencias a contenidos que ayuden en la adquisición
de este conocimiento, una guía no exhaustiva que puede ser revisada según sea necesario
puede ser consultada en [[1]](1) y [[2]](2).

# Funciones

Otro caso particular es el de las funciones, estas tambien poseen direcciones, sin embargo,
su sintaxis es un poco distinta, considere el ejemplo 6.3:

```cpp
#include "ejemplo.hpp"
#include <iostream>

int main(){
	std::cout << "Referencia de foo: " << (void*)&ejemplo::foo << std::endl;
	return 0;
}
```
La salida esperada es la siguiente:
```
Referencia de foo: 0x559b9b7e51c9
```
Note que antes del operador ```&``` estamos usando
```cpp
(void*)
```
para establecer la referencia como un puntero este es un tema que se tratará más adelante
en esta unidad. Por ahora se recomienda al lector revisar el siguiente material [[3]](3).
# Referencias

<a id="1">[1]</a>
https://isocpp.org/wiki/faq/freestore-mgmt


<a id="2">[2]</a>
http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#S-resource

<a id="3">[3]</a>
https://cplusplus.com/doc/tutorial/typecasting/
