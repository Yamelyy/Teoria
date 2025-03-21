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

  3. (2.5 ptos) Redefina el TDA de ListaLigada, de tal manera que garantice que el tiempo de ejecución de la operación size es $O(1)$.(Basta con reescribir sólo aquellas partes del TDA que se ven afectadas). Mencione lasventajas y desventajas.

Incluimos un atributo adicional que almacene el tamaño actual de la lista, este se actualizara cada que se agregue o elimine un elemnto de la lista.

  pseudocodigo:

  
  ```{r}
  Atributos:
    int tamaño: almacena el numero de elementos de la lista
    
    //constructor
    ListaLigada():
    cabeza = null
    tamaño = 0

    agregaAlFinal(elemento) //metodo que agrega un elemento al final de la lista
      nuevoNodo = Nodo(elemento)
      if ( cabeza = null) {
          cabeza = nuevoNodo
      } else {
          actual = cabeza
          while(actual.siguiente =! null){
              actual = actual.siguiente
          }
          actual.siguiente = nuevoNodo
      tamaño = tamaño + 1
      }

    elimiarEnLaPosicion(posicion) //elimina un elmento en la posicion especificada
        if (posicion < 0 o posicion >= tamaño) {
            error "posición inválida"
        }else if (posicion == 0){
            cabeza = cabeza.siguiente
        }else {
            actual = cabeza
            for(i=1 hasta posicion -1){
                actual = actual.siguiente
            }
            actual.siguiente = actual.siguiente.siguiente
        tamaño = tamaño -1
        }
 
  ```

Atrubuto tamaño: incrementa o decrementa cada vez que se agrega o elimina un elemnto de la lista, que se utiliza en los metodos AgregarAlFinal y eliminarEnLaPosicion.

size: regresa el valor del atributo tamaño que garantiza un tiempo de ejecucion $O(1)$ 

VENTAJAS:

-Se ejecuta en tiempo constante $O(1)$ que es mas eficiente que el tiempo lineal $O(n)$, ya que recorre toda la lista.

-No necesita recorrer toda la lista para obtener el tamaño

DESVENTAJAS:

-Uso de memoria: se requiere de más espacio de memoria para almacenar el atributo tamaño.

-Mantenimiento del atributo: en cada operacion o metodo que modifica la lista se debe actualizar correctamente el valor de tamaño, aunque ocasiona un pequeño overhead en menoria no afecta tanto el rendimiento.

4. (2.5 pts) Redefina el TDA de Celda (que represente a la celda para una lista doblemente ligada), de manera tal que cada una tenga nombre y posición. Defina sus operaciones e incluya los axiomas necesarios para garantizar el correcto funcionamiento de la estructura.
  

