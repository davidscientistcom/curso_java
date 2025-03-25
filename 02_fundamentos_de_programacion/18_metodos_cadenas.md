
Métodos útiles de la clase String en Java

A continuación se presenta una recopilación de métodos comunes de la clase String en Java, con su descripción y un ejemplo de uso práctico.

Acceso y manipulación de caracteres
	•	charAt(int index)
Devuelve el carácter situado en la posición especificada (comenzando desde 0).
Ejemplo:

"Hola".charAt(1);  // Devuelve 'o'


	•	length()
Devuelve la longitud (número de caracteres) de la cadena.
Ejemplo:

"Hola".length();  // Devuelve 4


	•	substring(int beginIndex)
Devuelve una subcadena desde el índice especificado hasta el final de la cadena.
Ejemplo:

"Hola".substring(1);  // Devuelve "ola"


	•	substring(int beginIndex, int endIndex)
Devuelve una subcadena desde beginIndex hasta endIndex (sin incluir este último).
Ejemplo:

"Hola".substring(1, 3);  // Devuelve "ol"



Búsqueda de contenido
	•	indexOf(String str)
Devuelve la posición de la primera aparición de la subcadena especificada.
Ejemplo:

"Hola mundo".indexOf("mundo");  // Devuelve 5


	•	lastIndexOf(String str)
Devuelve la posición de la última aparición de la subcadena especificada.
Ejemplo:

"Hola mundo mundo".lastIndexOf("mundo");  // Devuelve 11


	•	contains(CharSequence s)
Indica si la cadena contiene la secuencia de caracteres especificada.
Ejemplo:

"Hola mundo".contains("mundo");  // Devuelve true


	•	startsWith(String prefix)
Comprueba si la cadena comienza con el prefijo indicado.
Ejemplo:

"Hola mundo".startsWith("Hola");  // Devuelve true


	•	endsWith(String suffix)
Comprueba si la cadena termina con el sufijo indicado.
Ejemplo:

"Hola mundo".endsWith("mundo");  // Devuelve true



Transformación de cadenas
	•	toLowerCase()
Convierte todos los caracteres de la cadena a minúsculas.
Ejemplo:

"Hola Mundo".toLowerCase();  // Devuelve "hola mundo"


	•	toUpperCase()
Convierte todos los caracteres de la cadena a mayúsculas.
Ejemplo:

"Hola Mundo".toUpperCase();  // Devuelve "HOLA MUNDO"


	•	trim()
Elimina los espacios en blanco al principio y al final de la cadena.
Ejemplo:

"  Hola  ".trim();  // Devuelve "Hola"



Reemplazo y división
	•	replace(char oldChar, char newChar)
Reemplaza todas las apariciones de un carácter por otro.
Ejemplo:

"Hola".replace('o', 'a');  // Devuelve "Hala"


	•	replaceAll(String regex, String replacement)
Reemplaza todas las apariciones que coincidan con una expresión regular.
Ejemplo:

"Hola mundo".replaceAll("\\s", "");  // Devuelve "Holamundo"


	•	split(String regex)
Divide la cadena en un array de subcadenas usando el delimitador especificado.
Ejemplo:

"uno,dos,tres".split(",");  // Devuelve ["uno", "dos", "tres"]



Comparación de cadenas
	•	equals(Object anObject)
Compara si dos cadenas son exactamente iguales, distinguiendo mayúsculas de minúsculas.
Ejemplo:

"Hola".equals("hola");  // Devuelve false


	•	equalsIgnoreCase(String anotherString)
Compara dos cadenas ignorando diferencias entre mayúsculas y minúsculas.
Ejemplo:

"Hola".equalsIgnoreCase("hola");  // Devuelve true


	•	compareTo(String anotherString)
Compara dos cadenas lexicográficamente (orden alfabético según código Unicode).
Ejemplo:

"Hola".compareTo("hola");  // Devuelve un número negativo


	•	compareToIgnoreCase(String str)
Compara dos cadenas lexicográficamente sin tener en cuenta mayúsculas o minúsculas.
Ejemplo:

"Hola".compareToIgnoreCase("hola");  // Devuelve 0



Validación de cadenas
	•	isEmpty()
Devuelve true si la cadena está vacía (sin caracteres).
Ejemplo:

"".isEmpty();  // Devuelve true


