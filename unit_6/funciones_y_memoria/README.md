# Introduccion
El símbolo ```&``` no solo es utilizado en c++ para obtener una dirección
de memoria, este tambien es utilizado para declaraciones de tipo.
Esta característica tiene distintos usos, para este caso en específico
se detallará su uso en el caso de las funciones.

# Pasar por valor
Considere el siguiente código:
```cpp
#include <iostream>
#include "ejemplo.hpp"

int main(){
	int valor = 1;
	std::cout << "Dato de valor :" << valor << std::endl;

	std::cout << "Dato obtenido al llamar a pasarPorValor: " << ejemplo::pasarPorValor(valor) << std::endl;

	std::cout << "Dato de valor despues de la llamada de pasarPorValor: " << valor << std::endl;
	return 0;
}
```
La salida esperada es:
```
Dato en valor : 1
Dato obtenido al llamar a pasarPorValor: 3
Dato de valor después de la llamada de pasarPorValor: 1
```

Como puede notar el dato en la variable no cambia, esto significa que dentro
de la función existe una copia de la variable independiente de las variables
en main.

# Pasar por referencia

Considere el siguiente código en ejemplo_6.4:

```cpp
#include <iostream>
#include "ejemplo.hpp"

int main(){
	int valor = 1;
	std::cout << "Dato en valor :" << valor <<std::endl;

	std::cout << "Dato obtenido al llamar a pasarPorValor: " << ejemplo::pasarPorValor(valor) << std::endl;

	std::cout << "Dato de valor despues de la llamada de pasarPorValor: " << valor << std::endl;

	ejemplo::pasarPorReferencia(valor);

	std::cout << "Dato de valor despues de llamada a pasarPorReferencia: " << valor << std::endl;
	return 0;
}

```
Con salida:

```
Dato en valor : 1
Dato obtenido al llamar a pasarPorValor: 3
Dato de valor después de la llamada de pasarPorValor: 1
Dato de valor después de llamada a pasarPorReferencia: 2
```
Si se examina el código de la librería se encontrará lo siguiente:

```cpp

namespace ejemplo {
	int pasarPorValor(int arg){
		arg += 2;
		return arg;
	}
	void pasarPorReferencia(int& p){
		p = 2;
		return;
	}

}
```
Note que los tipos cambian para ambas funciones,
en el caso de pasarPorReferencia se hace uso de el tipo
referencia a un entero, esto permite que esta función
comparta la dirección de memoria de este argumento
con su dirección en main, de esta forma los cambios
en main se ven reflejados en la variable dentro main,
evitando una duplicación de variables.

Si se requiere compartir la información sin modificarla,
es buena práctica hacer del argumento pasado por referencia
una constante de la siguiente manera:
```cpp
	int referenciaInmutable(const int& a){
		return 0;
	}
```
