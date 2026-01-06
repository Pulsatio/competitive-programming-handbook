# Sesión 1: Introducción y Primeros Pasos (2h)

Duración: 2 horas

Objetivos
- Entender qué es la programación competitiva y sus plataformas.
- Conocer la estructura típica de un problema competitivo.
- Aprender entrada/salida básica en C++ y usar una plantilla inicial.
- Resolver ejercicios simples: Hello World y A+B.

Materiales
- Ordenador con compilador C++ (g++, clang++)
- Acceso a internet para plataformas (Codeforces, AtCoder, CodeChef, LeetCode)
- Editor de código / terminal

Agenda (2h)
- 00:00–00:10 — Presentación: ¿qué es programación competitiva? Plataformas y reglas.
- 00:10–00:30 — Estructura de un problema (entrada, salida, restricciones, ejemplos).
- 00:30–00:50 — Entrada/Salida básica: `cin`, `cout`, `endl`.
- 00:50–01:10 — I/O rápido: `ios::sync_with_stdio(false); cin.tie(nullptr);` y lectura de múltiples casos.
- 01:10–01:40 — Ejemplos prácticos: Hello World y problema A+B.
- 01:40–02:00 — Mini-práctica y preguntas.

Ejemplos de código

Hello World
```cpp
// ejemplo: Hello World
#include <bits/stdc++.h>
using namespace std;
int main() {
    cout << "Hello World\n";
    return 0;
}
```

A + B (entrada: dos enteros en una línea)
```cpp
// ejemplo: A+B
#include <bits/stdc++.h>
using namespace std;
int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    long long a, b;
    if (cin >> a >> b) {
        cout << (a + b) << '\n';
    }
    return 0;
}
```

Plantilla básica para competiciones
```cpp
// plantilla-clase: helper de I/O y ejemplo práctico
#include <bits/stdc++.h>
using namespace std;

struct CP {
    CP() { ios::sync_with_stdio(false); cin.tie(nullptr); }
    int nextInt() { int x; cin >> x; return x; }
    long long nextLong() { long long x; cin >> x; return x; }
    string nextToken() { string s; cin >> s; return s; }
    template<typename T> vector<T> nextVec(int n) { vector<T> v(n); for (int i=0;i<n;++i) cin>>v[i]; return v; }
    void printLn(long long x) { cout << x << '\n'; }
    void printLn(const string &s) { cout << s << '\n'; }
};
 
// Ejemplo: resolver A+B con múltiples casos usando la clase
struct ExampleSolver {
    CP io;
    void run() {
        int T = 1;
        if (!(cin >> T)) return; // leer número de casos si existe
        while (T--) {
            long long a = io.nextLong();
            long long b = io.nextLong();
            io.printLn(a + b);
        }
    }
};

int main() {
    ExampleSolver solver;
    solver.run();
    return 0;
}
```

Ejercicios propuestos (para la práctica de la sesión)
- Escribir y ejecutar el programa Hello World.
- Resolver A+B con enteros pequeños.
- Modificar A+B para leer hasta EOF (múltiples líneas con pares de enteros).
- Revisar la plantilla y comentar cada línea.

Notas
- Reforzar el hábito de probar con casos borde y ejemplos.
- Recordar límites de tipos (usar long long cuando haya posibilidad de overflow).
