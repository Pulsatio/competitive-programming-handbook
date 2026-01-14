# Sesión 1: Introducción y Primeros Pasos (2h)

Docente: Gustavo Orosco Zavala

## Objetivos

- Entender qué es la programación y qué es C++
- Conocer qué es la programación competitiva y el calendario de competiciones
- Comprender los conceptos fundamentales de programación
- Aprender la plantilla básica de C++
- Conocer los tipos de variables básicos
- Dominar entrada/salida con cin y cout

## 1. ¿Qué es Programación?

La **programación** es el proceso de diseñar y escribir instrucciones que una computadora puede ejecutar para resolver problemas o realizar tareas específicas. Es como darle una receta detallada a la computadora para que sepa exactamente qué hacer.

**Conceptos clave:**

- Un **programa** es un conjunto de instrucciones escritas en un lenguaje que la computadora entiende
- Los programas transforman **datos de entrada** en **resultados de salida**
- La programación requiere pensamiento lógico y resolución de problemas

## 2. ¿Qué es C++?

**C++** es un lenguaje de programación de propósito general, creado por Bjarne Stroustrup en 1979. Es uno de los lenguajes más utilizados en programación competitiva por su:

- **Velocidad:** C++ es muy rápido, ideal para problemas con límites de tiempo estrictos
- **Control:** Permite control preciso sobre la memoria y recursos
- **STL (Standard Template Library):** Biblioteca con estructuras de datos y algoritmos ya implementados
- **Versatilidad:** Se usa desde sistemas operativos hasta videojuegos

**¿Por qué C++ en competitiva?**

- Ejecución rápida (crucial para pasar los límites de tiempo)
- Bibliotecas potentes (`vector`, `set`, `map`, algoritmos, etc.)
- Ampliamente aceptado en todas las plataformas de competición

## 3. ¿Qué es Programación Competitiva?

La **programación competitiva** es un deporte mental donde los participantes resuelven problemas algorítmicos en un tiempo limitado.

**Características:**

- Problemas con entrada/salida bien definidas
- Límites de tiempo y memoria estrictos
- Se evalúa corrección y eficiencia del código
- Competiciones individuales o en equipo

**Plataformas populares:**

- **Codeforces** - Competiciones regulares, muy activo
- **AtCoder** - Competiciones japonesas con buenos problemas
- **CodeChef** - Competiciones mensuales y práctica
- **LeetCode** - Enfocado en entrevistas técnicas
- **CSES Problem Set** - Excelente para aprendizaje
- **OmegaUp** - Plataforma latinoamericana

## 4. Calendario de Competiciones

### Competiciones Importantes

**CPIO - Competencia Peruana de Informática Olímpica**

- Competición nacional de Perú
- Etapa clasificatoria para competiciones internacionales
- Formato: Problemas algorítmicos en 5 horas

**OII - Olimpiada Iberoamericana de Informática**

- Competición regional para países iberoamericanos
- Participan países de habla hispana y portuguesa
- Generalmente en septiembre

**IOI - International Olympiad in Informatics**

- Olimpiada mundial de informática
- El evento más prestigioso para estudiantes de secundaria
- Anual, rota entre países
- Formato: 2 días, 3 problemas por día, 5 horas cada día

**Otras competiciones:**

- ICPC (para universitarios)
- Google Code Jam
- Meta Hacker Cup
- Competiciones semanales en Codeforces y AtCoder

## 5. Aprendiendo a Programar (No el Lenguaje)

Antes de dominar la sintaxis de C++, es crucial entender los **conceptos fundamentales** de programación. Estos conceptos son universales y se aplican a cualquier lenguaje.

### Conceptos Fundamentales

**1. Entrada y Salida**

- **Entrada:** Datos que recibe el programa (del teclado, archivo, etc.)
- **Salida:** Resultados que produce el programa (pantalla, archivo, etc.)

**2. Datos**

- Información que manipula el programa
- Pueden ser números, texto, valores verdadero/falso, etc.

**3. Variables**

- "Cajas" donde guardamos datos
- Tienen un nombre y un tipo
- Pueden cambiar su valor durante la ejecución

**4. Condicionales**

- Permiten tomar decisiones (`if`, `else`)
- El programa ejecuta diferentes acciones según condiciones

**5. Bucles**

- Permiten repetir acciones (`for`, `while`)
- Evitan escribir el mismo código muchas veces

**6. Funciones**

- Bloques de código reutilizable
- Reciben parámetros y pueden devolver resultados
- Organizan el código en partes lógicas

> 💡 **Filosofía:** Primero piensa en _qué_ quieres hacer (algoritmo), luego en _cómo_ escribirlo en C++.

## 6. Plantilla Inicial de C++

### Plantilla Básica

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(nullptr);

    // Tu código aquí

    return 0;
}
```

### Explicación de la Plantilla

**`#include <bits/stdc++.h>`**

- Incluye **todas** las bibliotecas estándar de C++
- Útil en competitiva (no tienes que recordar qué incluir)
- Incluye: iostream, vector, algorithm, string, map, set, queue, etc.
- ⚠️ No usar en proyectos profesionales (solo en competitiva)

**`using namespace std;`**

- Permite usar `cout` en lugar de `std::cout`
- Ahorra tiempo al escribir código
- Evita el prefijo `std::` en todas las funciones

**`int main() { ... }`**

- Función principal del programa
- Todo programa en C++ debe tener una función `main()`
- Es el punto de entrada donde empieza la ejecución

**`ios_base::sync_with_stdio(false);`**

- Desactiva la sincronización entre C y C++ I/O
- Hace que `cin` y `cout` sean **mucho más rápidos**
- Importante cuando hay mucha entrada/salida

**`cin.tie(nullptr);`**

- Desvincula `cin` de `cout`
- Mejora aún más la velocidad de I/O
- Evita que `cout` se vacíe automáticamente antes de cada `cin`

**`return 0;`**

- Indica que el programa terminó correctamente
- El sistema operativo recibe este código de retorno

## 7. Tipos de Variables

En C++ debemos declarar el **tipo** de cada variable antes de usarla.

### Tipos Básicos

**Enteros**

```cpp
int x = 10;              // Entero (-2×10⁹ a 2×10⁹ aprox.)
long long y = 1000000000000LL; // Entero grande (-9×10¹⁸ a 9×10¹⁸ aprox.)
short z = 100;           // Entero pequeño (-32768 a 32767)
```

**Decimales**

```cpp
float pi = 3.14f;        // Decimal con precisión simple
double e = 2.718281828;  // Decimal con doble precisión (preferido)
```

**Caracteres y Texto**

```cpp
char letra = 'A';        // Un solo carácter
string palabra = "Hola"; // Cadena de caracteres (texto)
```

**Booleanos**

```cpp
bool esCierto = true;    // Verdadero o falso
bool esFalso = false;
```

### Tabla de Rangos

| Tipo        | Tamaño  | Rango Aproximado              |
| ----------- | ------- | ----------------------------- |
| `int`       | 4 bytes | -2×10⁹ a 2×10⁹                |
| `long long` | 8 bytes | -9×10¹⁸ a 9×10¹⁸              |
| `double`    | 8 bytes | ±1.7×10³⁰⁸                    |
| `char`      | 1 byte  | -128 a 127 o caracteres ASCII |
| `bool`      | 1 byte  | true o false                  |

### ¿Cuál usar?

- **`int`**: Para la mayoría de problemas con números ≤ 10⁹
- **`long long`**: Cuando haya multiplicaciones o números > 10⁹
- **`double`**: Para problemas con decimales
- **`string`**: Para texto

> ⚠️ **Tip importante:** En competitiva, cuando tengas duda, usa `long long` para evitar overflow.

## 8. Entrada y Salida de Datos

### Uso de `cin` (Entrada)

**`cin`** lee datos desde la entrada estándar (teclado o archivo).

**Leer un entero:**

```cpp
int n;
cin >> n;
```

**Leer múltiples valores:**

```cpp
int a, b, c;
cin >> a >> b >> c;  // Lee tres números separados por espacios
```

**Leer un string (palabra):**

```cpp
string palabra;
cin >> palabra;  // Lee hasta el primer espacio
```

**Leer una línea completa:**

```cpp
string linea;
getline(cin, linea);  // Lee toda la línea, incluyendo espacios
```

### Uso de `cout` (Salida)

**`cout`** escribe datos en la salida estándar (pantalla).

**Imprimir un valor:**

```cpp
cout << 42;
```

**Imprimir múltiples valores:**

```cpp
int x = 10, y = 20;
cout << "x = " << x << ", y = " << y;
```

**Salto de línea:**

```cpp
cout << "Hola" << endl;   // Opción 1 (más lento)
cout << "Hola\n";         // Opción 2 (más rápido, preferido)
```

### Ejemplos Completos

**Ejemplo 1: Hello World**

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(nullptr);

    cout << "Hello World\n";

    return 0;
}
```

**Ejemplo 2: Suma de dos números (A + B)**

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(nullptr);

    long long a, b;
    cin >> a >> b;
    cout << a + b << '\n';

    return 0;
}
```

**Ejemplo 3: Múltiples casos de prueba**

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(nullptr);

    int t;
    cin >> t;  // Número de casos

    while (t--) {
        long long a, b;
        cin >> a >> b;
        cout << a + b << '\n';
    }

    return 0;
}
```

## Ejercicios Propuestos

1. **Hello World**: Escribe un programa que imprima "Hello World"
2. **A + B**: Lee dos enteros y muestra su suma
3. **Tres números**: Lee tres enteros a, b, c y muestra su suma y producto
4. **Tu nombre**: Lee un nombre y muestra "Hola, [nombre]!"
5. **Par o impar**: Lee un número y determina si es par o impar
6. **Múltiples sumas**: Lee T casos, cada uno con dos números, y muestra sus sumas

## Notas y Consejos

- **Prueba siempre con casos borde:** 0, números negativos, números muy grandes
- **Usa `long long` cuando hay multiplicaciones** para evitar overflow
- **Prefiere `'\n'` sobre `endl`** para salida más rápida
- **Lee el problema completo** antes de empezar a programar
- **Verifica los límites** de entrada en la descripción del problema

## Recursos Adicionales

- [CSES Problem Set](https://cses.fi/problemset/) - Excelente para practicar
- [Codeforces](https://codeforces.com/) - Competiciones y práctica
- [CP Algorithms](https://cp-algorithms.com/) - Referencia de algoritmos
