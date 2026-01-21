````markdown
# Sesión 2: Condicionales — `if`, `else if`, `else` (2h)

Docente: Gustavo Orosco Zavala

## Objetivos

- Aprender a usar `if`, `else if` y `else` en C++
- Entender y aplicar los operadores de comparación
- Construir expresiones lógicas complejas y anidar condicionales
- Practicar con ejemplos y ejercicios comunes en competitiva

## 1. ¿Qué es una estructura condicional?

Las estructuras condicionales permiten ejecutar código sólo cuando se cumple una condición.
Son fundamentales para tomar decisiones en un programa.

Tipos básicos en C++:

- `if (condición) { /* ... */ }` — ejecuta el bloque si la condición es verdadera
- `else if (otra_condición) { /* ... */ }` — evalúa si la primera fue falsa
- `else { /* ... */ }` — ejecuta si ninguna condición previa fue verdadera

## 2. Sintaxis y ejemplos básicos

### 2.1 `if` simple

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(nullptr);

    int x; cin >> x;
    if (x > 0) {
        cout << "x es positivo\n";
    }

    return 0;
}
```

### 2.2 `if` — `else`

```cpp
int n; cin >> n;
if (n % 2 == 0) {
    cout << "par\n";
} else {
    cout << "impar\n";
}
```

### 2.3 `if` — `else if` — `else`

```cpp
int a; cin >> a;
if (a < 0) {
    cout << "negativo\n";
} else if (a == 0) {
    cout << "cero\n";
} else {
    cout << "positivo\n";
}
```

## 3. Operadores de comparación

- `==` : igualdad
- `!=` : desigualdad
- `<` : menor que
- `>` : mayor que
- `<=` : menor o igual
- `>=` : mayor o igual

Ejemplo de uso:

```cpp
int x, y; cin >> x >> y;
if (x <= y) cout << "x <= y\n";
```

## 4. Operadores lógicos y expresiones complejas

- `&&` (AND): verdadero si ambas condiciones son verdaderas
- `||` (OR): verdadero si al menos una condición es verdadera
- `!` (NOT): invierte el valor lógico

Combinaciones y cortocircuito:

- En `cond1 && cond2`, si `cond1` es `false`, `cond2` no se evalúa (cortocircuito)
- En `cond1 || cond2`, si `cond1` es `true`, `cond2` no se evalúa

Ejemplo — rango válido:

```cpp
int x; cin >> x;
if (x >= 1 && x <= 100) {
    cout << "x está en [1,100]\n";
}
```

Ejemplo — múltiples condiciones:

```cpp
int a, b, c; cin >> a >> b >> c;
if ((a > b && a > c) || (a == b && a > c)) {
    cout << "a es el mayor o hay empate en el mayor\n";
}
```

## 5. Precedencia y paréntesis

- `!` tiene mayor precedencia
- `&&` tiene mayor precedencia que `||`
- Use paréntesis para aclarar intenciones y evitar errores

Ejemplo ambigüo (mejor clarificar):

```cpp
// Evitar: if (a && b || c)
if ((a && b) || c) { /* ... */ }
```

## 6. Ejemplos prácticos

### 6.1 Par o impar

```cpp
int n; cin >> n;
if (n % 2 == 0) cout << "PAR\n";
else cout << "IMPAR\n";
```

### 6.2 Máximo de tres números

```cpp
int a, b, c; cin >> a >> b >> c;
int mx = a;
if (b > mx) mx = b;
if (c > mx) mx = c;
cout << mx << '\n';
```

Alternativa con `if` anidados:

```cpp
int a, b, c; cin >> a >> b >> c;
if (a >= b && a >= c) cout << a << '\n';
else if (b >= a && b >= c) cout << b << '\n';
else cout << c << '\n';
```

### 6.3 Clasificación por nota (ejemplo con `else if`)

```cpp
int nota; cin >> nota;
if (nota < 0 || nota > 100) {
    cout << "Nota inválida\n";
} else if (nota >= 90) {
    cout << "A\n";
} else if (nota >= 80) {
    cout << "B\n";
} else if (nota >= 70) {
    cout << "C\n";
} else if (nota >= 60) {
    cout << "D\n";
} else {
    cout << "F\n";
}
```

### 6.4 Año bisiesto (ejemplo con condiciones compuestas)

```cpp
int y; cin >> y;
if ((y % 4 == 0 && y % 100 != 0) || (y % 400 == 0)) {
    cout << "Bisiesto\n";
} else {
    cout << "No bisiesto\n";
}
```

### 6.5 Operador ternario (forma compacta)

```cpp
int x; cin >> x;
cout << (x % 2 == 0 ? "PAR\n" : "IMPAR\n");
```

> Nota: El operador ternario `cond ? expr1 : expr2` es útil para expresiones simples, pero no para lógicas complejas.

## 7. Buenas prácticas

- Prefiere condiciones claras y con paréntesis cuando hay dudas
- Evita condiciones demasiado largas en una sola línea — extrae a variables con nombre si hace falta
- Usa `else if` cuando las ramas son mutuamente excluyentes
- Considera tablas de decisión o comentarios para casos con muchas ramas

## 8. Errores comunes

- Usar `=` en vez de `==` en la condición (`if (x = 5)` asigna y siempre es verdadera si no es cero)
- Olvidar paréntesis en comparaciones encadenadas incorrectas: `if (a < b < c)` NO funciona en C++
- No tener en cuenta el cortocircuito cuando se esperan efectos secundarios en la segunda condición

## 9. Ejercicios propuestos

1. Escribe un programa que lea un entero y diga si es positivo, negativo o cero.
2. Lee tres números y muestra el mayor (aplica lo aprendido en el ejemplo). Probar con empates.
3. Determina si un año es bisiesto.
4. Dado un entero N, imprime si está en el rango [A,B] dados por entrada.
5. Implementa un menú simple: lee una opción (1-3) y muestra una acción distinta para cada opción; incluye manejo de opción inválida.

## Recursos y consejos finales

- Practica combinando operadores lógicos y de comparación en problemas pequeños
- Usa `cout` con `\n` para I/O rápido
- Revisa casos borde: límites del rango, valores negativos, empates

## Ejemplos de pruebas rápidas

- Par/Impar: `4` → `PAR`, `7` → `IMPAR`
- Máximo: `3 5 5` → `5`
- Año bisiesto: `2000` → `Bisiesto`, `1900` → `No bisiesto`, `2012` → `Bisiesto`
````
