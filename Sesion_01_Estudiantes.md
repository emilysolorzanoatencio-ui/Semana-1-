| <div align="right"><img src="../Logo-UNA-Rojo_FondoTransparente%20(2).png" width="120" alt="Logo UNA" /></div> | | <p align="right"><img src="../images.jpeg" width="120" alt="Logo EscINF" /></p> |
|:----------------------------------------------------|:-------------------------------------------------------------:|------------------------------------------------------------:|

**Programa de curso** · **Programación II**  
**Carrera:** Ingeniería de Sistemas de Información con grado en Bachillerato y salida lateral de Diplomado en Programación de Aplicaciones Informáticas.

---

# Semana 1 – Sesión 1 (Estudiantes)

**Duración:** 2 horas  
**Tema:** Relaciones – repaso y Upcast

---

## Explicación (resumen)

- **Relaciones entre clases:** Generalización (herencia), dependencia y asociación (agregación/composición). Distinga "es-un" de "tiene-un".
- **Upcast:** Conversión de puntero o referencia de clase derivada a clase base. Es segura e implícita; permite polimorfismo.

---

## Espacio para tu código

Escriba su implementación en los bloques siguientes. El profesor validará que esté bien escrito.

### Ejercicio 1: Vehiculo y Automovil – upcast

Defina `Vehiculo` (base) y `Automovil` (derivada). En `main` cree un `Automovil` y asígnelo a un puntero (o referencia) a `Vehiculo`. Justifique en comentarios por qué es upcast y es seguro.

```cpp
#include <iostream>
using namespace std;

class Vehiculo{
protected:
string marca;
public:
Vehiculo (string m){
marca=m;}
void mostrar(){
cout<<"Marca: "<<marca<<endl;}

// Escriba aquí la clase Automovil
class Automovil: public Vehiculo{
private:
int puertas;
public:
Automovil(string m,int p):Vehiculo (m){
puertas=p;}
void infro(){
cout<<"Automovil de"<<puertas<<"puertas"<<endl;}
};

int main() {
    // Escriba aquí: crear Automovil y upcast a Vehiculo*

Automovil a("Toyota",4);
Vehiculo* v=&a;
 //Upcast: Automovil->Vehiculo*, es seguro porque automovil ES-UN vehiculo
v->mostrar();

    return 0;
}
```

### Ejercicio 2: Jerarquía de 3 niveles

Escriba una jerarquía base → derivada1 → derivada2. En `main` realice upcast en cada nivel a la clase base y llame un método definido en la base.

```cpp
// Escriba aquí las tres clases y main con upcast

#include <iostream>
using namespace std;

class Base {
public:
    void mensaje() {
        cout<<"Metodo de la clase Base" << endl;}
};

class Derivada1 : public Base {};

class Derivada2 : public Derivada1 {};

int main() {

    Derivada2 obj;

    // Upcast nivel 2 → base
    Base* p1 = &obj;
    p1->mensaje();

    // Upcast nivel 2 → derivada1
    Derivada1* p2 = &obj;

    // Upcast derivada1 → base
    Base* p3 = p2;
    p3->mensaje();

    return 0;
}

### Ejercicio 3: Array de punteros a base

Defina una clase base abstracta `Figura` (con `double area() = 0`) y derive `Circulo` y `Rectangulo`. En `main` use un **array** de punteros `Figura* figuras[MAX]`, agregue figuras y recorra el array mostrando el área. No use `vector`.

```cpp
// Escriba aquí: Figura, Circulo, Rectangulo y main con array Figura* figuras[MAX]

#include <iostream>
using namespace std;

#define MAX 10

class Figura {
public:
    virtual double area() = 0;  
};



class Circulo : public Figura {
private:
    double radio;

public:
    Circulo(double r) {
        radio = r; }

    double area() {
        return 3.1416 * radio * radio;}
};




class Rectangulo : public Figura {
private:
    double base;
    double altura;

public:
    Rectangulo(double b, double h) {
        base = b;
        altura = h; }

    double area() {
        return base * altura;}
};

int main() {

    Figura* figuras[MAX];

    figuras[0] = new Circulo(5);
    figuras[1] = new Rectangulo(4, 6);

    for (int i = 0; i < 2; i++) {
        cout<<"Area: "<<figuras[i]->area()<<endl; }

    for (int i = 0; i < 2; i++) {
        delete figuras[i];}

    return 0;
}

---

## Criterios de validación (para el profesor)

- [ ] Uso de `using namespace std;`
- [ ] Upcast correcto (puntero/referencia derivada → base)
- [ ] Uso de **array** de punteros (no vector) en el ejercicio 3
- [ ] Constructores sin sintaxis `b(base), h(alt)`; usar asignación en el cuerpo si aplica
