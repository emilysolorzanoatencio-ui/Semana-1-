| <div align="right"><img src="../../Logo-UNA-Rojo_FondoTransparente%20(2).png" width="120" alt="Logo UNA" /></div> | | <p align="right"><img src="../../images.jpeg" width="120" alt="Logo EscINF" /></p> |
|:----------------------------------------------------|:-------------------------------------------------------------:|------------------------------------------------------------:|

**Programa de curso** · **Programación II**  
**Carrera:** Ingeniería de Sistemas de Información con grado en Bachillerato y salida lateral de Diplomado en Programación de Aplicaciones Informáticas.

---

# Semana 1 – Sección general: Relaciones entre clases y Upcast

Material de apoyo para la Sesión 1.

---

## 1. Relaciones entre clases en POO (repaso)

### Herencia – “Es-un”

- Una clase derivada hereda atributos y métodos de una clase base.
- Se interpreta como relación **“es-un”**.

**Ejemplos conceptuales:**

- Automóvil **es un** Vehículo  
- Perro **es un** Mamífero  

### Asociación – “Tiene-un”

Puede ser:

- **Agregación** (rombo blanco) → relación débil  
- **Composición** (rombo negro) → relación fuerte  

**Ejemplos:**

- Casa **tiene** Habitaciones (composición)  
- Universidad **tiene** Estudiantes (agregación)  

### Dependencia – “Usa-a”

- Es una relación **temporal**.
- Una clase utiliza otra como parámetro o variable local.

**Ejemplo:**

```cpp
void imprimir(Persona p);
```

No hay almacenamiento permanente.

---

## 2. Upcast (conversión ascendente)

**Definición formal:**  
El upcast ocurre cuando convertimos un objeto de una clase derivada en una referencia o puntero a su clase base.

**Ejemplo:**

```cpp
Automovil a;
Vehiculo* p = &a;  // Upcast
```

- ✔ Es seguro  
- ✔ Es implícito  
- ✔ No requiere cast explícito  
- ✔ Es la base del polimorfismo  

### ¿Por qué es seguro?

Porque todo objeto derivado contiene la parte base dentro de su estructura en memoria.

---

## 3. Conexión directa con polimorfismo

Cuando usamos:

```cpp
Vehiculo* p = &a;
p->describir();
```

Si el método es **virtual**, el programa decide en **tiempo de ejecución** qué versión ejecutar.

👉 Eso es **polimorfismo dinámico**.

---

## Explicación didáctica para clase

Puedes decirlo así a los estudiantes:

*“El upcast permite que yo trate muchos tipos distintos como si fueran uno solo. Eso es exactamente lo que hace posible el polimorfismo.”*

---

## Pregunta conceptual para evaluar en clase

Explique por qué el siguiente código compila y es seguro:

```cpp
Perro p;
Animal* a = &p;
```

---

## Idea para reforzar en pizarra

Dibujar la jerarquía:

```
Animal
   ↑
Mamifero
   ↑
Perro
```

Y luego mostrar:

**Perro → Mamifero → Animal** (Upcast)

---

**Referencia (APA):** (Savitch, 2018). Savitch, capítulos sobre herencia y clases base/derivadas; uso de punteros/referencias a clase base.
