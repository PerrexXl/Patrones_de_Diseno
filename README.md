# Patrones_de_Diseño
Repositorio usado para almacenar archivos necesarios para la entrega de Patrones de Diseño

# Sistema para gestionar Turnos Digitales - [Tunomático]

## 1. Descripción

El proyecto corresponde al modelado arquitectónico de un Sistema para la gestión de Turnos Digitales, Llamado Tunomático. El objetivo principal es permitir la solicitud, administración, visualización y seguimiento de turnos dentro de una Empresa que atiende de cara al publico de manera presencial y semipresencial.

El sistema tiene en cuenta la interacción entre clientes, recepcionistas, administradores, pantallas digitales y servicios de notificación. A través del modelado UML se muestra la evolución desde una vista funcional del sistema, mediante casos de uso, hasta una propuesta física, mediante diagramas de clases e implementación.

El diseño considera buenas prácticas de orientación a objetos y la aplicación de patrones de diseño populares, específicamente Singleton, Prototype, Adapter y Bridge, con el propósito de mejorar la organización, reutilización, mantenibilidad y escalabilidad de la solución.

## 2. Diagrama de Casos de Uso

[Diagrama de Casos de Uso]
<img width="421" height="756" alt="image" src="https://github.com/user-attachments/assets/7691e067-7ff9-4c33-9cc3-f623b38d362b" />


El diagrama de casos de uso representa las principales funciones del sistema desde la vista de los actores que interactúan con él.

### Actores identificados

- Cliente: el usuario que solicita su turno y consulta su estado.
- Recepcionista: el encargado de llamar, atender, reasignar o finalizar turnos.
- Administrador: responsable de gestionar los servicios, módulos de atención y reportes.
- Pantalla de Turnos: un dispositivo encargado de mostrar los turnos correspondientes.
- Sistema de Notificación: servicio externo que informa al cliente sobre el estado de su turno.

### Justificación de relaciones

Se utilizaron relaciones `<<include>>` en los casos donde una funcionalidad siempre requiere la ejecución de otra. Por ejemplo, solicitar un turno incluye seleccionar un servicio y generar un ticket digital.

También se aplicaron relaciones `<<extend>>` para representar comportamientos opcionales o alternativos. Por ejemplo, cancelar turno extiende la consulta de estado, ya que no siempre el cliente querra cancelará su turno, pero puede hacerlo desde esa funcionalidad.

## 3. Diagrama de Clases

![Diagrama de Clases]
<img width="2397" height="619" alt="image" src="https://github.com/user-attachments/assets/66b3524c-8f12-4f26-aab4-426993fc5601" />


El diagrama de clases ejemplifica la estructura lógica del sistema, considerando atributos, métodos, relaciones, cardinalidades y patrones de diseño aplicados.

### Patrón Singleton

La clase `SistemaTurnos` aplica el patrón de `<<Singleton>>`, ya que el sistema debe contar con una única instancia central encargada de administrar el resto de turnos, servicios y procesos principales. Esto evita inconsistencias generadas por múltiples objetos controlando simultáneamente la lógica del sistema.

### Patrón Prototype

La clase `Turno` aplica el patrón `<<Prototype>>`, permitiendo clonar una estructura base de turno para generar nuevos tickets digitales de forma más eficiente. Este patrón resulta útil cuando los turnos comparten una estructura similar, pero cambian datos como código, estado, fecha, hora o servicio asociado.

### Patrón Adapter

La clase `AdaptadorEmail` aplica el patrón `<<Adapter>>`, permitiendo que el sistema se comunique con un servicio externo de correo electrónico sin depender directamente de su implementación. Esto facilita reemplazar el proveedor de notificaciones en el futuro sin modificar la lógica principal del sistema.

### Patrón Bridge

El patrón `<<Bridge>>` se aplica en la relación entre `CanalVisualizacion` y `DispositivoVisual`. Esta separación permite que la lógica de visualización de turnos sea independiente del tipo de dispositivo utilizado, como pantallas LED, LCD o monitores web.

## 4. Diagrama de Implementación

![Diagrama de Implementación]
<img width="1732" height="452" alt="image" src="https://github.com/user-attachments/assets/db93acbb-5147-46fc-a829-17e185ed1289" />


El diagrama de implementación representa la distribución física y tecnológica del sistema.

### Decisiones arquitectónicas

El sistema se organiza en un cliente o kiosko digital, un servidor de aplicaciones, una base de datos, un servicio externo de notificaciones y dispositivos físicos de visualización.

El servidor de aplicaciones concentra la lógica principal del sistema, incluyendo la gestión de turnos, aplicación de patrones y conexión con servicios externos. La base de datos almacena información sobre turnos, servicios y módulos de atención.

El sistema de notificaciones se representa como un nodo externo, lo que permite mantener desacoplada la lógica interna del sistema respecto de proveedores específicos de correo o mensajería.

La pantalla de atención se representa como un nodo físico independiente, conectado al sistema mediante red o conexión local, permitiendo mostrar los turnos llamados en tiempo real.

---

## 5. Reflexiones Finales

El modelado del Sistema de Gestión de Turnos Digitales permite comprender lo importante que es diseñar una solución desde distintas perspectivas: funcional, estructural y física.

El uso de casos de uso facilita la tarea de identificar las necesidades reales de los actores. El diagrama de clases permite organizar idea logica mediante principios de orientación a objetos, mientras que el diagrama de implementación permite visualizar cómo los componentes se distribuyen en una arquitectura real.

La aplicación de patrones de diseño fortalece la calidad del sistema. Singleton permite centralizar el control, Prototype mejora la creación de turnos, Adapter facilita la integración con servicios externos y Bridge permite separar la visualización de los dispositivos físicos.

En conclusión, Tunomático representa una solución escalable a futuro, mantenible y coherente con buenas prácticas de diseño de software tal como fueron enseñadas.
