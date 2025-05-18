# 🏥 Sistema Tunomático — Modelado Arquitectónico Profesional

## 📋 Descripción General

El **Sistema Tunomático** es una solución digital orientada a la gestión de turnos médicos en centros de salud. Su propósito es optimizar la experiencia de pacientes y personal administrativo, asegurando trazabilidad, disponibilidad en tiempo real y sincronización con sistemas hospitalarios externos (ERP). El sistema incorpora control de agenda médica, emisión de confirmaciones, y una arquitectura escalable basada en patrones de diseño.

Este proyecto sigue una transición profesional desde la **visión funcional** hasta el **modelo físico de implementación**, incluyendo la aplicación de patrones de diseño claves para asegurar modularidad, mantenimiento y escalabilidad del sistema.

---

## 🔹 1. Diagrama de Casos de Uso UML

![Diagrama de Casos de Uso](imagenes/casos_de_uso.png)

### Descripción general

El análisis funcional permitió identificar actores clave y funcionalidades principales del sistema. Se aplicaron correctamente relaciones `<<include>>` y `<<extend>>` para representar procesos obligatorios y opcionales en el flujo del sistema.

#### Actores identificados:
- **Paciente**: Solicita, consulta y cancela turnos.
- **Recepcionista**: Interactúa con el sistema para registrar o modificar turnos de forma asistida.
- **Administrador**: Gestiona agendas y controla la auditoría del sistema.
- **Sistema ERP**: Sincroniza información crítica del entorno hospitalario.

#### Casos de uso y relaciones:
- **Solicitar Turno**
  - `<<extend>>` **Emitir Confirmación de Turno**: puede ser accionado como respuesta opcional.
- **Gestionar Agenda Médica**
  - `<<include>>` **Sincronizar con ERP**: operación obligatoria al modificar la agenda.
- **Auditoría de Acciones**: exclusivo del Administrador.
- **Consultar Disponibilidad**, **Cancelar Turno**: acceso tanto para pacientes como recepcionistas.

La claridad de los flujos asegura comprensión desde la perspectiva del usuario final y promueve trazabilidad en auditorías internas.

---

## 🔹 2. Diagrama de Clases UML con Patrones Aplicados

![Diagrama de Clases](imagenes/diagrama_clases.png)

### Patrones Aplicados

#### **1. Singleton – `ConfiguracionSistema`**
Permite el acceso global y controlado a parámetros clave del sistema (duración de turno, máximo diario, etc.), evitando múltiples instancias y errores de configuración dispersa.

#### **2. Prototype – `PlantillaTurno`**
Facilita la clonación de formatos repetitivos de turnos (ej. atención general, pediatría, controles), optimizando el trabajo administrativo y manteniendo homogeneidad.

#### **3. Adapter – `AdaptadorERP`**
Abstrae la lógica de comunicación entre el sistema interno y el ERP hospitalario. Garantiza independencia tecnológica y facilita futuras integraciones o migraciones.

#### **4. Bridge – `InterfazUsuario`**
Permite separar la lógica de visualización según el dispositivo utilizado (web, móvil), mejorando experiencia de usuario y permitiendo escalar hacia nuevas plataformas sin romper la lógica de negocio.

Cada patrón fue aplicado en respuesta a una necesidad arquitectónica real, no como adorno teórico. Se usaron estereotipos (`<<Singleton>>`, `<<Adapter>>`, etc.) y se respetaron buenas prácticas de modelado orientado a objetos.

---

## 🔹 3. Diagrama de Implementación UML

![Diagrama de Implementación](imagenes/diagrama_implementacion.png)

### Despliegue Físico y decisiones técnicas

- **Servidor Web** aloja la interfaz de usuario para pacientes y personal (web y móvil), facilitando escalabilidad horizontal.
- **Servidor de Aplicaciones** contiene la lógica principal, patrones aplicados y servicios internos.
- **Servidor ERP** representa el sistema hospitalario externo al cual se sincronizan datos vía el `AdaptadorERP`.

Se garantizó la separación de responsabilidades, la posibilidad de escalar componentes de manera independiente y la independencia tecnológica. Esta estructura modular permite mantener la calidad del servicio y reducir la complejidad operativa.

---

## 🧩 Reflexiones Finales del Modelado

Este trabajo representa una aproximación profesional al modelado arquitectónico de sistemas. La transición clara desde la funcionalidad hasta la implementación permite diseñar soluciones robustas, comprensibles por múltiples perfiles (desarrolladores, operaciones, stakeholders) y fácilmente mantenibles.

El uso intencional de patrones de diseño asegura un equilibrio entre flexibilidad y control, entregando una arquitectura alineada a los estándares reales de la industria.

---

## ✅ Estructura del Repositorio Esperada

```
Tunomatic/
│
├── README.md
├── imagenes/
│   ├── casos_de_uso.png
│   ├── diagrama_clases.png
│   └── diagrama_implementacion.png
└── .gitignore (opcional)
```

---

## 📤 Entrega

- Repositorio público en GitHub con la estructura descrita.
- Todos los diagramas deben estar exportados en formato `.png`.
- El archivo `README.md` debe mantener redacción profesional y formato exacto como el presente.
- Enlace enviado por correo institucional antes del plazo indicado.

---

## 📌 Notas Finales

El objetivo no es solo cumplir con una actividad, sino adoptar el **rol de un arquitecto profesional de software**. Este ejercicio consolida tu capacidad para transformar requerimientos en soluciones técnicas claras, sostenibles y reales.
