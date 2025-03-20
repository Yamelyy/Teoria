1. (2.5 ptos) Diseñe, en pseudocódigo, un método que reciba una lista ligada $L$
y una pila $P$ , el cual deberá modificar la lista original eliminando las posiciones indicadas por cada nodo de la pila. Use las operaciones propias de cada
estructura. Calcule la $O$.<br>
Ejemplo: Si $L = {2, 4, 6, 8, 9, 3}$ y $P = {2, 5}$ el método regresa $L = {2, 6, 8, 3}$

```{r}
Metodo EliminarPosicion(Lista L, Pila P){
  while {
    P=!null
    posicion = P.desapilar(); //obtiene la posicion a eliminar
    if(posicion>=1 && posicion <=longiyud(L)){
      L.eliminarLaPosicion(posicion -1) //elimina nodo en la posicion indicada
    } //fin if
  } // fin while
}

```
-Pila: contiene las posiciones a eliminar en la lista.

-Lista: se eliminan los nodos indicados en la pila.

-P.desapilar(): Extrae el elemento superior de la pila (FIFO)

-L.elimirLaPosicion(posicion): elimina el nodo indicado en la pila


COMPLEJIDAD:

Desapilar O(1)

Eliminar el nodo de l alista: O(n), en caso de que n sea la posicion a eliminar ya que puede ser necesario recorrer toda la lista.

Metodo EliminarPosicion: Si la pila tiene k elementos y la lista tiene n elemntos O(k*n) 
Si $L = {2, 4, 6, 8, 9, 3}$ y $P = {2, 5}$ el método regresa $L = {2, 6, 8, 3}$


2. (2.5 ptos)

   2.1 ¿Cuánto tarda la ejecución del método que inserta un elemento en un hash?
   O(n) ya que itera en varias ocasiones, priemro al buscar si no es vacío, al buscar la posicion e introducir un elemento, ademas de que recorre toda la tabla.

   2.2 Describa la estrategia lineal para resolver una colisión. Si se utiliza esta técnica ¿cómo se garantiza el mismo tiempo de ejecución mencionado en
el inciso anterior?

  -Se busca el siguiente espacion libre, pero esto no es tan optimo ya que si todos o casi todos los espacios estan ocupados, tiene que buscar uno por uno y recorrer todo, pero al ser asi, la complejidad O(n) se conserva.
  
  -Se asocia una lista enlazada a cada espacio de la tabla hash, donde tambien se almacenan los elementos y mantiene la complejidada O(n) ya que recorre tambien la lista enlazada y es mucho mas eficiente.

