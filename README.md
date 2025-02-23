# Resumen de Tipos en TypeScript 🚀

Este documento es un resumen completo de los principales tipos y estructuras que ofrece TypeScript, con ejemplos y explicaciones de cada uno.

---

## 1. Tipos Primitivos 🏗️

Los tipos primitivos son los básicos en JavaScript y TypeScript:

- **string**
- **number**
- **boolean**
- **null**
- **undefined**
- **symbol**
- **bigint**

**Ejemplo:**

```typescript
let nombre: string = "Juan";
let edad: number = 30;
let activo: boolean = true;
```

---

## 2. Interfaces 📝

Las interfaces definen la estructura de un objeto. Son ideales para describir objetos, especialmente cuando se espera que otros objetos extiendan o implementen esta estructura.

**Ejemplo:**

```typescript
export interface Person {
  name: string;
  age: number;
  email?: string; // Propiedad opcional
}

const persona: Person = {
  name: "María",
  age: 25
};
```

### ¿Cuándo utilizarlas?

Utiliza interfaces cuando quieras definir la forma de objetos y aprovechar la capacidad de extensión y herencia, especialmente en proyectos orientados a objetos o cuando trabajas con clases.

---

## 3. Type Aliases 🔗

Los alias de tipo asignan un nombre a un tipo, ya sea simple o complejo. Pueden representar uniones, intersecciones o combinaciones de tipos.

**Ejemplo:**

```typescript
export type CommonPerson = Pick<Person, "name" | "age">;

const personaComun: CommonPerson = {
  name: "Carlos",
  age: 40
};
```

### ¿Cuándo utilizarlos?

Usa alias de tipo para simplificar tipos complejos, para trabajar con uniones o intersecciones, o cuando quieras crear tipos derivados a partir de otros.

---

## 4. Uniones (Union Types) 🔀

Permiten que una variable pueda tomar valores de distintos tipos.

**Ejemplo:**

```typescript
let id: number | string;
id = 10;
id = "10";
```

### ¿Cuándo utilizarlas?

Emplea uniones cuando una variable o parámetro pueda ser de diferentes tipos (por ejemplo, un ID que puede ser numérico o alfanumérico).

---

## 5. Intersecciones (Intersection Types) 🤝

Combinan múltiples tipos en uno solo, requiriendo que el valor cumpla con todas las estructuras combinadas.

**Ejemplo:**

```typescript
interface Business {
  company: string;
}

export type Employee = Person & Business;

const empleado: Employee = {
  name: "Ana",
  age: 28,
  company: "TechCorp"
};
```

### ¿Cuándo utilizarlas?

Utiliza intersecciones para fusionar distintas interfaces o tipos cuando un objeto deba cumplir con múltiples requisitos a la vez.

---

## 6. Enums 📊

Los enums definen un conjunto de constantes con nombre, facilitando el uso de valores fijos y legibles.

**Ejemplo:**

```typescript
export enum Direction {
  Up,
  Down,
  Left,
  Right
}

const dir: Direction = Direction.Up;
```

### ¿Cuándo utilizarlas?

Usa enums cuando necesites un conjunto limitado de valores predefinidos, como direcciones, estados o categorías.

---

## 7. Generics 📦

Los genéricos permiten crear componentes reutilizables y flexibles que pueden trabajar con distintos tipos sin perder la información de tipos.

**Ejemplo:**

```typescript
function identity<T>(arg: T): T {
  return arg;
}

let output = identity<string>("Hola Generics");
```

### ¿Cuándo utilizarlas?

Utiliza genéricos cuando desees escribir funciones, clases o interfaces que sean independientes del tipo y puedan reutilizarse con distintos tipos de datos.

---

## 8. Tipos Avanzados ⚙️

### a. Tipos Condicionales

Definen un tipo basado en una condición sobre otro tipo.

**Ejemplo:**

```typescript
export type IsString<T> = T extends string ? "Es string" : "No es string";

type Test1 = IsString<string>; // "Es string"
type Test2 = IsString<number>; // "No es string"
```

### b. Tipos Mapeados

Crean nuevos tipos iterando sobre las propiedades de otro tipo.

**Ejemplo:**

```typescript
export type ReadonlyPerson = {
  readonly [K in keyof Person]: Person[K];
};

const readonlyPerson: ReadonlyPerson = {
  name: "Luis",
  age: 32
};

// readonlyPerson.age = 33; // Error: propiedad de solo lectura
```

### c. Tipos de Índice

Definen tipos para objetos con claves dinámicas.

**Ejemplo:**

```typescript
export interface StringDictionary {
  [key: string]: string;
}

const diccionario: StringDictionary = {
  key1: "valor1",
  key2: "valor2"
};
```

---

## 9. Utilidades Incorporadas 🔧

TypeScript incluye varios tipos de utilidad que ayudan a transformar y manipular tipos existentes:

- `Partial<T>`: Todas las propiedades de `T` se vuelven opcionales.
- `Required<T>`: Todas las propiedades de `T` se vuelven requeridas.
- `Readonly<T>`: Todas las propiedades de `T` son de solo lectura.
- `Record<K, T>`: Crea un objeto con claves de tipo `K` y valores de tipo `T`.
- `Pick<T, K>`: Selecciona un subconjunto de propiedades de `T`.
- `Omit<T, K>`: Excluye ciertas propiedades de `T`.

**Ejemplo:**

```typescript
interface Todo {
  title: string;
  description: string;
  completed: boolean;
}

export type TodoPreview = Pick<Todo, "title" | "completed">;

const todo: TodoPreview = {
  title: "Aprender TS",
  completed: false
};
```

### ¿Cuándo utilizarlas?

Utiliza estas utilidades para evitar la repetición de código y para transformar tipos existentes de manera rápida y segura.

---

## Conclusión 🎯

TypeScript ofrece una estructura de tipos muy robusta que permite:

- **Interfaces**: Definir la forma de objetos y aprovechar la herencia.
- **Type Aliases**: Simplificar y combinar tipos complejos.
- **Uniones e Intersecciones**: Flexibilizar y combinar estructuras de tipos.
- **Enums**: Manejar conjuntos de valores fijos.
- **Generics**: Crear componentes reutilizables y seguros.
- **Tipos Avanzados y Utilidades**: Transformar y manipular tipos para adaptar el código a diversas necesidades.

