# Ejercicio_Frases_GabrielOrtiz


### Explicación Función `create_markov_chain`
---

La función `create_markov_chain` es responsable de crear la cadena de Markov.

Pasos que realiza la función:

* Elimina los signos de puntuación de todas las frases, utilizando la funcion `re.sub()` de la libreria re

* Divide el texto en palabras individuales, utilizando `text.split()`.

* Crea un diccionario vacío llamado `markov_chain`.

* Itera a través de cada palabra en el texto.

* Para cada palabra, se guarda la palabra actual en la variable `current_word` y la siguiente palabra en `next_word`.
  
* Si `current_word` ya existe en el diccionario `markov_chain`, se agrega `next_word` a la lista de palabras siguientes asociadas con `current_word`.

* Si `current_word` no existe en el diccionario, se crea una nueva entrada para él con una lista que solo contiene `next_word`.

* Devuelve el diccionario `markov_chain` al final del bucle.  
  

### Explicación Función `generate_text`

---

La función `generate_text` recibe dos parámetros: un diccionario `markov_chain` que representa una cadena de Markov, y 
un entero `length` que indica cuántas palabras se deben generar.

La función comienza seleccionando una palabra al azar como la primera palabra de la frase generada. 

Esta palabra se selecciona de entre las claves del diccionario `markov_chain` y debe cumplir la condición de que su primera letra esté en mayúscula.

Luego, se entra en un bucle que se ejecutará length veces. En cada iteración, se busca en el diccionario `markov_chain`  la lista de palabras siguientes a la palabra actual. Si la palabra actual está en el diccionario, se selecciona una 
palabra siguiente al azar de esa lista, y se añade a la frase generada. La nueva palabra se convierte en la palabra actual para la próxima  iteración. Si la palabra actual no está en el diccionario, el bucle se detiene.

Finalmente, la función devuelve la frase generada como una cadena de texto.

### Explicación App

---

Esta sección del código abre un archivo de texto llamado `"frases/frases_informatica.txt"` en modo lectura (el "r" significa lectura). 

El método readlines() lee todas las líneas del archivo y las devuelve como una lista de cadenas. La función join() toma una lista de cadenas y las une en una única cadena, separándolas con el separador que se le pasa como argumento. En este caso, el separador es una cadena vacía '', por lo que las líneas se unen sin separación alguna.

Luego, todo el texto del archivo se almacena en la variable `"text"`.

Después, se llama a la función `"create_markov_chain"` y se pasa como argumento la variable `"text"`,  para crear una cadena de Markov. El resultado se almacena en la variable `"markov_chain"`.

Luego, se pide al usuario que introduzca un número para indicar el número de frases que desea generar, y se almacena en la variable `"number_of_sentences"`.

A continuación, se utiliza un bucle for que se ejecuta `"number_of_sentences"` veces. En cada iteración, se llama a la función `"generate_text"` y se pasa como argumentos `"markov_chain"` y 10 (que representa el número máximo de palabras que se deben generar en cada frase). La frase generada se almacena en la variable `"generated_text"`. Finalmente, se imprime `"generated_text"`.

En resumen, este código abre un archivo de texto, crea una cadena de Markov con su contenido, pide al usuario el número de frases que desea generar y luego genera y muestra esas frases.