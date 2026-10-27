<p align="center">
  <img src="logo.svg" alt="Logo de VitaHogar" width="460">
</p>

<h1 align="center">VitaHogar</h1>
<p align="center"><b>Servicio médico en casa · Plan preventivo</b></p>

<p align="center">
  Proyecto académico de <b>Programación 1</b> · Segundo corte · Caso B<br>
  Desarrollado en <b>Java</b>
</p>

---

## Tabla de contenido

1. [Sobre la empresa](#1-sobre-la-empresa)
2. [Descripción del proyecto](#2-descripción-del-proyecto)
3. [Levantamiento de requerimientos](#3-levantamiento-de-requerimientos)
4. [Protección de datos personales](#4-protección-de-datos-personales-colombia)
5. [Del requerimiento al backlog](#5-del-requerimiento-al-backlog)
6. [Backlog del producto](#6-backlog-del-producto)
7. [Historias de usuario](#7-historias-de-usuario)
8. [Cómo ejecutar el programa](#8-cómo-ejecutar-el-programa)
9. [Estructura del repositorio](#9-estructura-del-repositorio)
10. [Autor y video](#10-autor-y-video)

---

## 1. Sobre la empresa

> Identidad generada con apoyo de inteligencia artificial (Claude), como pide el caso de estudio.

### Nombre

**VitaHogar**

Combina *vita* (vida, en latín) y *hogar*. Expresa la idea central del servicio: llevar el cuidado de la salud a la casa de las personas.

**Eslogan:** *Prevención que llega a tu puerta.*

### Logo

La casa representa el hogar y el techo en azul marino transmite protección. La cruz médica blanca en el centro indica que la atención de salud está dentro de la casa. Los colores son verde azulado (salud y bienestar) y azul marino (confianza y seriedad).

<p align="center">
  <img src="logo.svg" alt="Logo de VitaHogar" width="420">
</p>

| Elemento | Color |
|---|---|
| Verde azulado (salud) | `#0F9D8A` |
| Azul marino (confianza) | `#12355B` |
| Gris (texto secundario) | `#5B6B7A` |

### Misión

Brindar atención médica preventiva en el hogar de forma accesible, cercana y segura, con planes claros y adaptados a cada familia, cuidando siempre la privacidad de la información de nuestros usuarios.

### Visión

Para 2031, ser el servicio de medicina preventiva domiciliaria de referencia en Colombia, reconocido por la confianza de las familias, la calidad humana de su equipo y el uso responsable de la tecnología.

### Valores

| Valor | Significado |
|---|---|
| **Cercanía** | Vamos hasta donde está el paciente y lo tratamos con calidez. |
| **Prevención** | Cuidar antes de que se enferme es mejor que curar después. |
| **Confianza** | Planes y precios claros, sin sorpresas. |
| **Privacidad** | Los datos de salud se protegen y se usan solo con autorización. |
| **Responsabilidad** | Cumplimos la ley y respondemos por la calidad de lo que ofrecemos. |

---

## 2. Descripción del proyecto

VitaHogar es una empresa de servicio médico en casa que requiere un algoritmo en **Java** donde el cliente o usuario pueda observar y seleccionar las diferentes opciones de un plan preventivo.

### Planes

| Sigla | Plan | Costo |
|---|---|---|
| **PB** | Plan Básico | $275.325 COP |
| **PP** | Plan Premium | $325.650 COP |

### Datos que solicita el sistema

Nombre, cédula, síntomas, dirección de residencia, cantidad de personas cubiertas y tipo de plan.

### Funcionamiento general

- El sistema es **continuo**: permite registrar varios usuarios seguidos.
- Si el médico escribe la palabra **`medicamento`**, la factura actual termina y el sistema queda listo para el siguiente cliente.

### Menú del sistema

1. Registrar cliente (nombre, cédula, síntomas, dirección de residencia)
2. Tipo de plan (usar las siglas PB o PP)
3. Otros usuarios (debe ser un número entero)
4. Valor mensual (proceso = tipo de plan × otros usuarios)
5. Respaldo TXT
6. Descuento (si el síntoma es gripa o alergia, se aplica un descuento del 12,5 % en ambos planes)
7. Visualizar información
8. Salir

### Entregables del caso

- [x] Levantamiento de requerimientos en GitHub (este documento)
- [x] Paso a paso para llevar los requerimientos a un backlog y a historias de usuario
- [x] Algoritmo comentado (`ServicioMedicoCasa.java`)
- [x] Nombre, logo, misión y visión generados con apoyo de IA
- [ ] Video explicativo

---

## 3. Levantamiento de requerimientos

> Donde el enunciado es ambiguo, se dejó una **suposición** marcada para confirmarla con el docente.

### 3.1 Requerimientos funcionales (RF)

| ID | Nombre | Descripción | Funcionamiento |
|---|---|---|---|
| RF-01 | Mostrar planes preventivos | El cliente puede ver y elegir entre las opciones de plan. | Muestra Plan Básico (PB) a $275.325 COP y Plan Premium (PP) a $325.650 COP. |
| RF-02 | Menú principal | Presenta las 8 opciones y recibe la elección. | Bucle que muestra el menú, lee un número del 1 al 8 y ejecuta la opción. Si es inválida, avisa y vuelve a pedirla. |
| RF-03 | Registrar cliente (opción 1) | Captura los datos del cliente. | Pide nombre, cédula, síntomas y dirección de residencia, y los guarda en memoria para la factura actual. |
| RF-04 | Seleccionar tipo de plan (opción 2) | Define el plan contratado. | El usuario escribe **PB** o **PP**. El sistema asocia el valor del plan y rechaza cualquier otra sigla. |
| RF-05 | Registrar otros usuarios (opción 3) | Captura la cantidad de personas adicionales cubiertas. | Pide un número **entero** y rechaza decimales, texto y negativos. |
| RF-06 | Calcular valor mensual (opción 4) | Calcula el costo mensual. | Aplica la fórmula del caso: `valor = valor del plan × otros usuarios`. |
| RF-07 | Aplicar descuento (opción 6) | Reduce el valor si hay síntomas elegibles. | Si el síntoma es **gripa** o **alergia**, aplica 12,5 % a ambos planes: `valor_final = valor × 0,875`. |
| RF-08 | Respaldo en TXT (opción 5) | Guarda la información en un archivo de texto. | Escribe los datos y el valor de la factura en un `.txt`. |
| RF-09 | Visualizar información (opción 7) | Muestra los datos del cliente y su factura. | Imprime nombre, cédula, síntomas, dirección, plan, otros usuarios, descuento y valor final. |
| RF-10 | Salir (opción 8) | Termina el programa. | Rompe el bucle del menú y cierra de forma ordenada. |
| RF-11 | Operación continua | Permite registrar varios usuarios seguidos. | Al cerrar una factura, el sistema reinicia las variables y queda listo para el siguiente cliente sin cerrarse. |
| RF-12 | Cierre de factura por palabra clave | El médico termina la factura escribiendo "medicamento". | El sistema revisa lo que escribe el médico. Si detecta `medicamento` (sin distinguir mayúsculas), cierra la factura actual y vuelve al estado inicial. |
| RF-13 | Validación de datos | Evita datos incorrectos. | Valida que la cédula sea numérica, que los campos obligatorios no estén vacíos, que el plan sea PB o PP y que los otros usuarios sean enteros. |
| RF-14 | Autorización de datos personales | El cliente acepta el tratamiento de sus datos antes de registrarse. | Antes de RF-03 muestra el aviso de privacidad y pide "SI/NO". Si responde "NO", no se registran datos. |

**Suposiciones:**

- **Palabra "medicamento":** el enunciado no dice dónde la escribe el médico. Se asume como una entrada de texto en el menú, al final de la atención.
- **Fórmula del valor mensual:** el caso dice `tipo de plan × otros usuarios`. Si "otros usuarios" es 0, el valor da 0. Se implementó la fórmula tal cual el enunciado. Si el titular debe contar como persona cubierta, la fórmula sería `valor del plan × (otros usuarios + 1)`.

**Ejemplo de cálculo:** plan PB con 2 otros usuarios y síntoma "gripa":

| Paso | Operación | Resultado |
|---|---|---|
| Valor base | 275.325 × 2 | **$550.650** |
| Con descuento | 550.650 × 0,875 | **$481.818,75** |

### 3.2 Requerimientos no funcionales (RNF)

| ID | Categoría | Descripción | Cómo se cumple |
|---|---|---|---|
| RNF-01 | Lenguaje / portabilidad | Debe estar desarrollado en **Java**. | Código en Java estándar, ejecutable en cualquier sistema con JVM. |
| RNF-02 | Usabilidad | Menú claro y mensajes entendibles. | Opciones numeradas y mensajes de error que indican el formato esperado. |
| RNF-03 | Mantenibilidad | El algoritmo debe entregarse **comentado**. | Comentarios en cada bloque y método, y nombres claros de variables. |
| RNF-04 | Fiabilidad | El programa no debe cerrarse por datos erróneos. | Manejo de excepciones (`try/catch`) en las lecturas, por ejemplo `NumberFormatException`. |
| RNF-05 | Disponibilidad | Funcionamiento continuo mientras no se elija "Salir". | Ciclo `while` controlado por la opción 8. |
| RNF-06 | Integridad de datos | El respaldo TXT debe reflejar la información real. | Se escribe desde los mismos datos validados. |
| RNF-07 | Seguridad | Proteger los datos sensibles del respaldo y de la sesión. | Restringir el acceso al archivo, no dejar datos visibles entre clientes y, si es posible, cifrar el TXT. |
| RNF-08 | Rendimiento | Respuesta inmediata en consola. | Operaciones simples en memoria, sin esperas perceptibles. |
| RNF-09 | Codificación | Soportar tildes y ñ. | Guardar el TXT en UTF-8. |
| RNF-10 | Control de versiones | El levantamiento y el código deben estar en **GitHub**. | Repositorio con README, documentación de requerimientos y commits descriptivos. |
| RNF-11 | Cumplimiento legal | Cumplir la normativa de protección de datos. | Ver la sección 4. |

### 3.3 Requerimientos de dominio (RD)

Son las reglas del negocio médico y de facturación. Vienen del contexto del servicio y no de una preferencia técnica.

| ID | Requerimiento | Descripción |
|---|---|---|
| RD-01 | Planes y tarifas | Solo existen dos planes preventivos: Básico ($275.325 COP) y Premium ($325.650 COP). |
| RD-02 | Siglas de planes | Se identifican como **PB** y **PP**. |
| RD-03 | Moneda | Todos los valores están en pesos colombianos (COP). |
| RD-04 | Cobertura grupal | El plan cubre al cliente y a otras personas, y el valor depende de la cantidad de personas. |
| RD-05 | Regla de descuento | 12,5 % en ambos planes si el síntoma es gripa o alergia. |
| RD-06 | Cierre de factura | La palabra "medicamento" termina la factura. |
| RD-07 | Identificación del cliente | Se identifica con cédula, un número único por persona. |
| RD-08 | Servicio a domicilio | La dirección de residencia es obligatoria, porque la atención se presta en casa. |
| RD-09 | Información de salud | Los síntomas son información clínica y tienen **tratamiento legal especial** (sección 4). |

---

## 4. Protección de datos personales (Colombia)

Como el caso usa pesos colombianos y cédula, la norma aplicable es la **Ley 1581 de 2012** (Ley de Habeas Data), reglamentada por el **Decreto 1377 de 2013**, hoy compilado en el **Decreto 1074 de 2015**. La autoridad de control es la **Superintendencia de Industria y Comercio (SIC)**. También se apoya en el artículo 15 de la Constitución.

### Datos del caso y su clasificación

| Dato | Tipo | Por qué importa |
|---|---|---|
| Nombre | Personal | Identifica a la persona. |
| Cédula | Personal | Identificación única. |
| Dirección de residencia | Personal (privado) | Ubica a la persona en su domicilio. |
| **Síntomas** | **Sensible (salud)** | La ley los trata con especial protección porque su uso indebido puede generar discriminación. |
| Otros usuarios cubiertos | Personal de terceros | Si se piden sus datos, también necesitan autorización. Si solo se cuenta un número, no hay dato personal. |

### Qué exige la ley al sistema

| # | Exigencia | Cómo se refleja en VitaHogar |
|---|---|---|
| 1 | **Autorización previa, expresa e informada** | RF-14: aviso de privacidad y confirmación "SI/NO" antes de registrar. |
| 2 | **Finalidad clara** | El aviso indica que los datos se usan solo para prestar el servicio y facturar. |
| 3 | **Datos sensibles (síntomas)** | El cliente puede negarse a darlos escribiendo "ninguno". |
| 4 | **Derechos del titular** (conocer, actualizar, rectificar, suprimir y revocar) | El aviso los informa. Un sistema completo debería permitir corregir o borrar un registro. |
| 5 | **Política de tratamiento y aviso de privacidad** | La empresa debe tenerlos publicados y mostrarlos al cliente. |
| 6 | **Seguridad y confidencialidad** | El respaldo TXT guarda datos de salud en texto plano, por lo que conviene limitar su acceso o cifrarlo. |
| 7 | **Registro Nacional de Bases de Datos (RNBD)** | Según el tamaño de la empresa, puede ser obligatorio registrar la base de datos ante la SIC. |
| 8 | **Confidencialidad médica** | La información clínica también está cubierta por el secreto profesional y las normas de historia clínica (Ley 23 de 1981 y Resolución 1995 de 1999). |

> Esta sección es orientación académica y no constituye asesoría jurídica. En un proyecto real debe validarse con un asesor legal y revisar la normativa vigente en la SIC.

---

## 5. Del requerimiento al backlog

Paso a paso para llevar los requerimientos a un backlog y a historias de usuario:

1. **Numerar los requerimientos.** Cada uno queda con un identificador: RF, RNF o RD.
2. **Identificar los roles.** Aquí son el **cliente**, el **operador del sistema** (quien registra) y el **médico** (quien cierra la factura).
3. **Convertir cada RF en una historia** con la estructura: *Como [rol], quiero [funcionalidad], para [beneficio]*.
4. **Agregar criterios de aceptación.** Son condiciones verificables que indican cuándo la historia está terminada.
5. **Asignar prioridad** (Alta, Media o Baja) según qué tan indispensable es para que el sistema funcione.
6. **Ordenar el backlog** por prioridad y dependencias. Por ejemplo, no se puede calcular el valor sin antes registrar el plan.
7. **Repartir en sprints** o entregas pequeñas y revisar el backlog cuando cambien los requerimientos.

---

## 6. Backlog del producto

| Identificador | Historia de Usuario | Origen | Prioridad | Sprint |
|---|---|---|---|---|
| HU-01 | Mostrar planes preventivos | RF-01 | Alta | 1 |
| HU-02 | Menú principal | RF-02 | Alta | 1 |
| HU-03 | Autorización de datos personales | RF-14 | Alta | 1 |
| HU-04 | Registrar cliente | RF-03 | Alta | 1 |
| HU-05 | Seleccionar tipo de plan | RF-04 | Alta | 1 |
| HU-06 | Registrar otros usuarios | RF-05 | Alta | 1 |
| HU-07 | Calcular valor mensual | RF-06 | Alta | 2 |
| HU-08 | Validar datos ingresados | RF-13 | Alta | 1 |
| HU-09 | Aplicar descuento por síntoma | RF-07 | Media | 2 |
| HU-10 | Visualizar información | RF-09 | Media | 2 |
| HU-11 | Respaldo en TXT | RF-08 | Media | 3 |
| HU-12 | Cierre de factura con "medicamento" | RF-12 | Media | 2 |
| HU-13 | Operación continua | RF-11 | Media | 2 |
| HU-14 | Salir del sistema | RF-10 | Baja | 3 |
| HU-15 | Código comentado | RNF-03 | Media | 3 |
| HU-16 | Repositorio en GitHub | RNF-10 | Media | 3 |

### Organización por sprints

| Sprint | Enfoque | Historias |
|---|---|---|
| **Sprint 1** | Base del sistema | HU-01, HU-02, HU-03, HU-04, HU-05, HU-06, HU-08 |
| **Sprint 2** | Lógica de negocio | HU-07, HU-09, HU-10, HU-12, HU-13 |
| **Sprint 3** | Cierre y entrega | HU-11, HU-14, HU-15, HU-16 |

---

## 7. Historias de usuario

Cada historia sigue la estructura: **Como** [tipo de usuario] · **Quiero** [funcionalidad] · **Para** [beneficio u objetivo].

### HU-01: Mostrar planes preventivos

- **Como** cliente
- **Quiero** ver las opciones de plan con su costo
- **Para** decidir cuál me conviene

**Criterios de aceptación:** se muestran PB ($275.325 COP) y PP ($325.650 COP) con sus siglas.

### HU-02: Menú principal

- **Como** operador
- **Quiero** un menú numerado del 1 al 8
- **Para** navegar por las funciones sin confundirme

**Criterios de aceptación:** el menú reaparece tras cada acción. Una opción inválida muestra un aviso y no cierra el programa.

### HU-03: Autorización de datos personales

- **Como** cliente
- **Quiero** aceptar o rechazar el tratamiento de mis datos antes de registrarlos
- **Para** que mis datos de salud se usen solo con mi consentimiento (Ley 1581 de 2012)

**Criterios de aceptación:** antes del registro aparece el aviso de privacidad. Si responde "NO", no se guarda ningún dato.

### HU-04: Registrar cliente

- **Como** operador
- **Quiero** registrar nombre, cédula, síntomas y dirección de residencia
- **Para** identificar al cliente y saber dónde prestar el servicio

**Criterios de aceptación:** ningún campo obligatorio puede quedar vacío y la cédula debe ser numérica.

### HU-05: Seleccionar tipo de plan

- **Como** operador
- **Quiero** indicar el plan con las siglas PB o PP
- **Para** asignar el costo base correcto

**Criterios de aceptación:** solo acepta PB o PP, sin distinguir mayúsculas. Cualquier otro valor se rechaza y se vuelve a pedir.

### HU-06: Registrar otros usuarios

- **Como** operador
- **Quiero** ingresar la cantidad de otros usuarios cubiertos
- **Para** calcular el valor según el tamaño del grupo

**Criterios de aceptación:** solo acepta números enteros. Rechaza decimales, texto y negativos.

### HU-07: Calcular valor mensual

- **Como** cliente
- **Quiero** conocer cuánto pagaré cada mes
- **Para** decidir si contrato el servicio

**Criterios de aceptación:** `valor = valor del plan × otros usuarios`. Ejemplo: PB con 2 otros usuarios da $550.650.

### HU-08: Validar datos ingresados

- **Como** operador
- **Quiero** que el sistema avise cuando me equivoque al digitar
- **Para** no registrar información errónea ni que el programa se caiga

**Criterios de aceptación:** cualquier entrada inválida muestra un mensaje claro y permite reintentar.

### HU-09: Aplicar descuento por síntoma

- **Como** cliente
- **Quiero** recibir el descuento si mi síntoma es gripa o alergia
- **Para** pagar menos en esos casos

**Criterios de aceptación:** se aplica 12,5 % en ambos planes (`valor × 0,875`). Con cualquier otro síntoma no hay descuento.

### HU-10: Visualizar información

- **Como** operador
- **Quiero** ver los datos registrados y el valor final
- **Para** confirmarlos con el cliente antes de cerrar

**Criterios de aceptación:** muestra nombre, cédula, síntomas, dirección, plan, otros usuarios, descuento y valor final.

### HU-11: Respaldo en TXT

- **Como** operador
- **Quiero** guardar la información de la factura en un archivo de texto
- **Para** conservar un registro de la atención

**Criterios de aceptación:** el archivo se crea en UTF-8 y refleja los mismos datos validados. Debe tener acceso restringido por contener datos de salud.

### HU-12: Cierre de factura con "medicamento"

- **Como** médico
- **Quiero** cerrar la factura escribiendo la palabra "medicamento"
- **Para** terminar la atención de ese cliente

**Criterios de aceptación:** la palabra se detecta sin importar mayúsculas o minúsculas. Al detectarla se cierra la factura y se limpian los datos del cliente.

### HU-13: Operación continua

- **Como** operador
- **Quiero** atender a varios clientes seguidos sin reiniciar el programa
- **Para** agilizar el trabajo diario

**Criterios de aceptación:** tras cerrar una factura, el sistema queda listo para un nuevo registro.

### HU-14: Salir del sistema

- **Como** operador
- **Quiero** salir con la opción 8
- **Para** cerrar el programa de forma ordenada

**Criterios de aceptación:** termina el ciclo del menú y muestra un mensaje de despedida.

### HU-15: Código comentado

- **Como** docente evaluador
- **Quiero** que el algoritmo tenga comentarios en cada bloque
- **Para** entender la lógica sin tener que adivinarla

**Criterios de aceptación:** cada método tiene un comentario explicativo y las variables tienen nombres claros.

### HU-16: Repositorio en GitHub

- **Como** equipo de desarrollo
- **Quiero** subir el levantamiento de requerimientos y el código a GitHub
- **Para** mantener control de versiones y cumplir con la entrega

**Criterios de aceptación:** el repositorio tiene README, el documento de requerimientos, el backlog y commits descriptivos.

---

## 8. Cómo ejecutar el programa

### Requisitos

- **Java 11 o superior** (JDK instalado).

### Pasos

```bash
# 1. Compilar
javac -encoding UTF-8 ServicioMedicoCasa.java

# 2. Ejecutar
java ServicioMedicoCasa
```

> En Windows, si las tildes se ven mal en la terminal, ejecuta `chcp 65001` antes del programa.

### Prueba rápida

Ejecuta esta secuencia en el menú:

| Paso | Entrada |
|---|---|
| 1 | `1` → `SI` → nombre, cédula, síntoma `gripa`, dirección |
| 2 | `2` → `PB` |
| 3 | `3` → `2` |
| 4 | `4` (valor mensual esperado: **$550.650,00**) |
| 5 | `6` (valor con descuento esperado: **$481.818,75**) |
| 6 | `7` para ver la factura y `5` para guardar el respaldo |
| 7 | `medicamento` para cerrar la factura |

---

## 9. Estructura del repositorio

```text
VitaHogar/
├── README.md                 # Este documento
├── logo.svg                  # Logo de VitaHogar
├── ServicioMedicoCasa.java   # Algoritmo en Java (comentado)
└── respaldo_clientes.txt     # Se genera al usar la opción 5 (no subir a GitHub)
```

> **Importante:** `respaldo_clientes.txt` contiene datos personales y de salud. Agrégalo a un archivo `.gitignore` para no subirlo al repositorio.

---

## 10. Autor y video

- **Autor:** [Tu nombre completo]
- **Curso:** Programación 1 · Segundo corte · Caso B
- **Docente:** David Escobar Valencia
- **Video explicativo:** [Pega aquí el enlace]
