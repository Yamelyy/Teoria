Santiago Hernández Yamely Naomi.

1) Suponga que T1 (n) y T2 (n) son el tiempo de ejecución para dos fragmentos de algoritmos A1 y A2 , respectivamente, tales que T1 (n) = O(f (n)) y T2 (n) = O(g(n)). Pruebe que T1 (n)T2 (n) es O(f (n)g(n)).

```{r}
Demostración:
Sabemos que:
t1(n) = O(f(n)), asi que existen c1 y N1 tales que para toda n>N1, t1(n) <= c1f(n).
t2(n) = O(g(n)), asi que existen c2 y N2 tales que para toda n>N2, t2(n) <= c2g(n).
Sea N = max{N1, N2}, como N es mayor o igual que N1, N2 simultanemaente, entonces para n > N se cumple:
        t1(n) <= c1 f(n)
        t2(n) <= c2 g(n)

Multiplicandolas obtenemos que para toda n>N = max{N1, N2}:
        t1(n)t2(n) <= c1c2f(n)g(n)

Ya encontramos N y c=c1c2 tales que, para toda n > N:
        t(n)=t1(n)t2(n) <= cf(n), g(n)

De acuerdo a la definicion, entonces
        t(n) = O(f(n)g(n))
```




2) Para cada uno de los siguientes fragmentos de programas, dé un análisis del tiempo de ejecución (O(n)). Justifique con sumas (sumatorias) y muestre la solución paso a paso de dichas sumas.

(a)
```{r}
sum = 0 ;                  -> O(1)
  for ( i =0; i <n ; i ++) -> O(n)
     sum++;                -> O(n)
```
-> O(n) + O(1) = O(n) - tiempo constante

(b)
```{r}
  sum = 0 ;                      -> O(1)
  f o r ( i =0; i <n ; i ++)     -> O(n)
      f o r ( j =0; j <n ; j ++) -> O(n)  
          sum++;                 -> O(n)
```
-> O(n) + O(n) = O(n^2) + O(1) = O(n^2)

  O(n^2) - complejidad cuadratica 

  (c)
```{r}
  sum = 0 ;                      -> O(1)
  f o r ( i =0; i <n ; i ++)     -> O(n)
    f o r ( j =0; j <n∗n ; j ++) -> O(n)
      sum++;                     -> O(n)
```
-> O(n) + O(n) = O(n^2) + O(1) + O(n) = O(n^2)

  O(n^2) - complejidad cuadratica 
  
(d)
```{r}
  sum = 0 ;                    -> O(1)
  f o r ( i =0; i <n ; i ++)   -> O(n)
    f o r ( j =0; j <i ; j ++) -> O(n)
      sum++;                   -> O(n)
```
-> O(n) + O(n) = O(n^2) + O(1) + O(n) = O(n^2)

  O(n^2) - complejidad cuadratica 

(e)
```{r}
  sum = 0 ;                        -> O(1)
  f o r ( i =0; i <n ; i ++)       -> O(n)
    f o r ( j =0; j <i ∗ i ; j ++) -> O(n)
      f o r ( k=0; k<j ; k++)      -> O(n)
        sum++;                     -> O(n)
```

-> O(n) + O(n) + O(n) = O(2^n) + O(n) + O(1) = O(2^n)

  O(2^n) - complejidad exponencial 


3. Defina un TDA para una Lista Ligada.

```{r}  
//clase Nodo
  class Nodo {
      int dato;
      Nodo siguiente:

      public Nodo(int dato) {
        this.dato = dato;
        this.siguiente = null;
      }
  }

//clase ListaLigada
  class ListaLigada {
      private Nodo cabeza;

      public ListaLigada(){
      this.cabeza = null;
      } 
  }

  public void agregar(int dato) {
      Nodo nuevoNodo = new Nodo(dato);
      nuevoNodo.siguiente = cabeza;
      cabeza = nuevoNodo;
  }
  Nodo temp = cabeza;
      while (temp.siguiente != null) {
        temp = temp.siguiente;
      }
      temp.siguiente = nuevoNodo;
```

4. Suponga que se desea almacenar eficientemente una matriz triangular inferior (incluyendo la diagonal) en la que, además, todas las entradas de los renglones de ı́ndice impar son cero. Obtenga el polinomio de direccionamiento para almacenar esta matriz en un arreglo unidimensional (Tip: la suma de los primeros k números naturales impares es  $k^2$ )

 Tn = n(n+1)/2 

 Dado que en una fila i hay i+1 elementos y qeu la suma de los primeros k numeros naturales impares es de  $k^2$ , entonces el numero total de elementos no nulos es:

 En = $(n/2 +1)^2$ (si n es par)
 En = c (si n es impar)

Encontramos f(i , j) i = filas y j = columnas

Si(i) = $(i/2)^2$ 
dentro de la fila i, el elemento (i , j) esta en la posicion j, entonces f( i,j ) =  $(i/2)^2+j$ con i par  

5. Calcular la complejidad del siguiente método, (Tip: Identifique casos para T(n) y luego vaya igualando en términos de T(n − 1), etc, hasta llegar al caso base):
```{r}
  int metodo ( i n t n ) {
    int x , i ;
    if( n <= 1 ) {
      return 1;
    }
    else{
      for( i =1; i<=n ; i++ ) {
        x = 1;
        while ( x < n ){
          x = x∗2;
        }
      }
      r e t u r n ( metodo ( n/2)+ metodo ( n / 2 ) ) ;
    }
  }
```
Bucle for: complejidad O(n)
Bucle while: complejidad O(log n) ya que se duplica despues de cada iteracion.
Recursion: metodo hace dos llamadas recursivas, metodo(n/2) y se da la recurrencia: T(n)=2T(n/2)+O(n log n)

-> T(n)=2T(n/2)+O(n log n) 
= 2(2T(n/4)+O(n/2log(n/2))) + O(n log n)
= 4T(n/4)+O(n/2log(n/2)) + O(n log n)

T(n) =  $2^kT(n/2^k)$ + (SUMA K-1, i=0) $O(n/2^ilog(n/2^i))$ 

Cuando $n/2^k=1$, tenemos k = log n, por lo que T(1) es constante:
$T(n)=O (n log^2 = n)$

Por lo tanto la complejidad es $O(n log^2 n)$


6. Dé los polinomios de direccionamiento para:

a) encontrar el elemento i-ésimo en:

f l o a t [ ] m i s F l o t a n t e s = new f l o a t [ 8 9 ] ;

i es el indice del elemento en el arreglo, (0 <= i < 89)
Dirección base es el primer elemento del arreglo.

Direccion = Dirección base + i * tamaño del tipo de dato.

Si i = 20.
El tamaño en bytes de float es 4 bytes, entonces:
= Dirección base + (20*4)
= Direccion base + 80
Entonces MisFlotantes[20] esta 80 bytes despues de la dirección del arreglo 


b) encontrar el elemento (i, j) en:

int [ ] [ ] m i s E n t e r o s = new i n t [ 1 0 ] [ 5 ] ;

Int = 4 bytes
Tamaño = tamaño de una referencia.
Dirección = dirección + i * tamaño + j * tamaño tipo de dato 

Si  m i s E n t e r o s[ 4 ] [ 3 ]

Dirección : direccion + 4 * 4 + 3 * 2 = 28
