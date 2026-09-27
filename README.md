# Diseño y Creación de Artefactos Reusables en Arquitectura SOA

Como desarrollador senior en un equipo de desarrollo distribuido, tu misión es diseñar y crear artefactos reusables que ayuden en el proceso de tareas complejas en una arquitectura de Servicios Orientados (SOA). El objetivo es desarrollar componentes que puedan ser reutilizados por diferentes equipos y proyectos, asegurando la consistencia y eficiencia en el proceso de integración. Los artefactos deben manejar flujos de datos entre múltiples servicios, validar entradas y salidas, y proporcionar mecanismos de recuperación ante fallos. El dominio es el de una plataforma de gestión de pagos en línea, donde los artefactos interactuarán con un motor de pagos, un sistema de autenticación y un servicio de notificación.

## Informacion General

| Campo | Valor |
|-------|-------|
| **Tema** | creacion de artefactos |
| **Nivel** | senior-l2 |
| **Tipo** | practical |
| **Tiempo estimado** | 20 horas |

## Fases del Reto

### Fase 0: Configuración del Proyecto

**Objetivo:** Obtener el proyecto base funcional enviando el Código Base a un asistente de IA, que lo analizará, corregirá errores y generará un ZIP listo para usar.

**Tiempo estimado:** 15-30 minutos

**Instrucciones:**

- Asegúrate de tener instalado para ejecutar el proyecto: JDK 17+, Maven 3.9+, IDE con soporte Java.
- Copia todo el contenido del campo **Código Base** de este reto — incluyendo el texto de instrucciones que aparece al inicio.
- Abre un asistente de IA (Claude en claude.ai, ChatGPT o Gemini — se recomienda Claude), pega el contenido copiado en el chat y envíalo.
- El asistente analizará los archivos, corregirá errores y generará un archivo ZIP descargable. Descárgalo y extráelo en la carpeta donde quieras trabajar.
- Ejecuta `mvn compile` en la raíz. Si no hay errores, estás listo.

**Entregable:** El proyecto compila/arranca sin errores.

<details>
<summary>Pistas de conocimiento</summary>

- Copia el Código Base completo incluyendo el texto de instrucciones al inicio — esas instrucciones le indican al asistente exactamente qué hacer con los archivos.
- Si el asistente no genera el ZIP automáticamente al terminar el análisis, escríbele: "genera el ZIP ahora".
- Si el proyecto tiene errores al arrancar, comparte el mensaje de error con el mismo asistente para que lo corrija.

</details>

### Fase 1: Identificación de Requisitos y Restricciones

**Objetivo:** Comprender los requisitos funcionales y no funcionales del dominio, así como las restricciones existentes.

**Tiempo estimado:** 4 horas

**Instrucciones:**

- Analiza el dominio de la gestión de pagos en línea para identificar los principales actores y sus interacciones.
- Documenta las restricciones operativas, como la latencia máxima aceptable para las transacciones y la disponibilidad del sistema.

**Entregable:** Documento de requisitos y restricciones del dominio.

<details>
<summary>Pistas de conocimiento</summary>

- Considera las interacciones entre el motor de pagos, el sistema de autenticación y el servicio de notificación.
- Evalúa cómo las restricciones operativas impactan en el diseño de los artefactos.

</details>

### Fase 2: Diseño de Artefactos Reusables

**Objetivo:** Diseñar artefactos que puedan ser reutilizados en diferentes contextos y que cumplan con los requisitos identificados.

**Tiempo estimado:** 8 horas

**Instrucciones:**

- Diseña un artefacto que maneje la validación de entradas en el proceso de pago, asegurando que los datos sean correctos y consistentes.
- Proporciona mecanismos de recuperación ante fallos, como reintentos con backoff exponencial.

**Entregable:** Documento de diseño de artefactos reusables.

<details>
<summary>Pistas de conocimiento</summary>

- Considera la idempotencia en las operaciones de pago para evitar duplicados.
- Evalúa diferentes estrategias de recuperación ante fallos y elige la más adecuada para el contexto.

</details>

### Fase 3: Implementación y Validación de Artefactos

**Objetivo:** Implementar los artefactos diseñados y validar su funcionamiento en el contexto del dominio.

**Tiempo estimado:** 6 horas

**Instrucciones:**

- Implementa los artefactos diseñados en la fase anterior, asegurándote de que cumplan con los requisitos funcionales y no funcionales.
- Realiza pruebas de integración para validar la interacción entre los artefactos y los servicios del dominio.

**Entregable:** Artefactos implementados y validados, junto con el reporte de pruebas.

<details>
<summary>Pistas de conocimiento</summary>

- Utiliza casos de prueba que cubran tanto los casos felices como los edge cases del dominio.
- Documenta cualquier desviación del diseño original y justifica las decisiones tomadas.

</details>

### Fase 4: Refactorización y Optimización

**Objetivo:** Refactorizar y optimizar los artefactos para mejorar su rendimiento y mantenibilidad.

**Tiempo estimado:** 2 horas

**Instrucciones:**

- Analiza el código implementado y realiza refactorizaciones necesarias para mejorar la legibilidad y mantenibilidad.
- Optimiza el rendimiento de los artefactos, considerando tanto la latencia como la utilización de recursos.

**Entregable:** Artefactos refactorizados y optimizados, junto con la documentación de los cambios realizados.

<details>
<summary>Pistas de conocimiento</summary>

- Considera patrones de diseño que puedan mejorar la estructura y la reutilización del código.
- Evalúa el impacto de las optimizaciones en el rendimiento y la mantenibilidad.

</details>

## Dimensiones Evaluadas

- **queEs**: ¿Qué son los artefactos reusables y por qué son importantes en una arquitectura SOA?
- **paraQueSirve**: ¿Cómo los artefactos diseñados en este reto ayudan en el proceso de tareas complejas en el dominio de la gestión de pagos en línea?
- **comoSeUsa**: ¿Cómo se utilizan los artefactos implementados en diferentes contextos y proyectos?
- **erroresComunes**: ¿Cuáles son los errores comunes que pueden ocurrir al diseñar y utilizar artefactos reusables, y cómo se pueden evitar?
- **queDecisionesImplica**: ¿Qué decisiones clave deben tomarse al diseñar y optimizar artefactos reusables en una arquitectura SOA?

## Criterios de Evaluacion

- Identificación correcta de los requisitos y restricciones del dominio.
- Diseño de artefactos reusables que cumplan con los requisitos funcionales y no funcionales.
- Implementación y validación efectiva de los artefactos en el contexto del dominio.
- Refactorización y optimización de los artefactos para mejorar su rendimiento y mantenibilidad.

## Como trabajar con un asistente de IA

Hay dos caminos, elegi uno:

- **AGENTS.md** (recomendado) — instrucciones nativas del repo. Abri esta carpeta con tu agente local (Claude Code, Cursor, Codex, Copilot, Gemini) y las carga solo. Sabe que archivos faltan y con que comando se verifica, y completa el scaffold escribiendo en disco.
- **PROMPT_MEJORA.md** — para copiar y pegar en un chat (claude.ai, ChatGPT). Devuelve un ZIP con el proyecto. Sirve si no tenes un agente en el IDE.

Ninguno de los dos resuelve las fases del reto: eso es tu trabajo.

## Verificacion

El proyecto esta listo para trabajar cuando este comando corre sin errores:

```bash
npx --yes @redocly/cli lint openapi.yaml
```

---

*Reto generado automaticamente por Challenge Generator - Pragma*
