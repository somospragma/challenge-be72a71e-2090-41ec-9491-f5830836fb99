# AGENTS.md

Instrucciones para el agente de IA que abra este repositorio (Claude Code, Cursor, Codex, Copilot, Gemini). Se cargan solas: no hay que pegar nada en ningun chat.

## Que es este repositorio

Es el codigo base de un reto de aprendizaje de Pragma: **Diseño y Creación de Artefactos Reusables en Arquitectura SOA**.

| | |
|---|---|
| Tema | creacion de artefactos |
| Nivel | senior-l2 |
| Chapter | Integración — Desarrollo |
| Especialidad | Api |
| Stack | Java / Spring Boot 3.5 |
| Patron arquitectonico | capas estándar con separación de dominio e infraestructura (SOA) |
| Tiempo estimado | 20 horas |

## Receta del stack

Esqueleto obligatorio:

- `openapi.yaml con paths, schemas y responses completos`
- `policies/ con las politicas del gateway (rate limit, auth, transformacion)`
- `environments/ con la configuracion por ambiente`
- `tests/ con la coleccion de contrato`
- `README.md con el contrato y los codigos de error`

Dependencias:

- org.springframework.boot:spring-boot-starter-web 3.5.6
- org.springframework.boot:spring-boot-starter-actuator 3.5.6
- org.apache.camel:camel-spring-boot-starter 4.4.0
- org.apache.camel:camel-jackson 4.4.0
- io.github.resilience4j:resilience4j-spring-boot2 2.1.0
- org.springframework.kafka:spring-kafka 3.2.0
- org.springframework.boot:spring-boot-starter-validation 3.5.6
- org.projectlombok:lombok 1.18.32
- org.springframework.boot:spring-boot-starter-test 3.5.6
- org.apache.camel:camel-test-spring 4.4.0
- org.mockito:mockito-core 5.5.0

## Tu tarea

Dejar este proyecto en estado **verificable**: que el comando de verificacion corra sin errores. Escribi los archivos en disco, en este repositorio. No generes ZIPs ni archivos adjuntos.

En orden:

1. Corre `npx --yes @redocly/cli lint openapi.yaml` y mira que falla.
2. Completa lo que falte de la lista de abajo: manifiesto de dependencias, punto de entrada, capa de interfaz y las capas del patron declarado.
3. Arregla SOLO los errores que impiden compilar o arrancar.
4. Volve a correr `npx --yes @redocly/cli lint openapi.yaml` hasta que pase.
5. Pará ahí.

## Regla dura: las fases son trabajo del humano

**PROHIBIDO implementar los entregables de las fases.** El valor del reto esta en que la persona los resuelva. Tu trabajo es que tenga un proyecto que arranca; el hueco pedagogico se queda como esta.

No resuelvas nada de esto:

- **Fase 1 — Identificación de Requisitos y Restricciones**: Documento de requisitos y restricciones del dominio.
- **Fase 2 — Diseño de Artefactos Reusables**: Documento de diseño de artefactos reusables.
- **Fase 3 — Implementación y Validación de Artefactos**: Artefactos implementados y validados, junto con el reporte de pruebas.
- **Fase 4 — Refactorización y Optimización**: Artefactos refactorizados y optimizados, junto con la documentación de los cambios realizados.

Distincion operativa:

- **Arreglar** (si): import faltante, tipo que no existe, dependencia sin declarar, error de sintaxis, archivo referenciado que no existe.
- **No tocar** (no): logica de negocio incompleta, validaciones ausentes, secretos hardcodeados, APIs deprecadas que funcionan, concurrencia insegura, patrones mejorables. Eso es lo que la persona tiene que encontrar.

## Superficie de practica (NO completes)

Estos archivos SON el ejercicio de la persona. No los implementes; deja stubs. No toques la logica que el reto pide completar.

- [ ] `src/main/java/com/pragma/pagos/infrastructure/config/CircuitBreakerConfig.java` — El topic pide resiliencia: este archivo es el ejercicio.

## Lo que falta y tenes que completar

### 1. Referencias colgando (23)

Salieron de un analisis estatico del codigo que SI esta en el repo. Cada una rompe la compilacion:

- [ ] `src/main/java/com/pragma/pagos/application/OrquestadorPago.java` — `org.slf4j`
      El import org.slf4j.Logger pertenece a org.slf4j, pero ninguna dependencia declarada en el pom.xml cubre ese paquete. Falta agregar la dependencia o el import esta mal (libreria equivocada).
- [ ] `src/main/java/com/pragma/pagos/infrastructure/client/MotorPagosClient.java` — `org.slf4j`
      El import org.slf4j.Logger pertenece a org.slf4j, pero ninguna dependencia declarada en el pom.xml cubre ese paquete. Falta agregar la dependencia o el import esta mal (libreria equivocada).
- [ ] `src/main/java/com/pragma/pagos/infrastructure/client/SistemaAutenticacionClient.java` — `org.slf4j`
      El import org.slf4j.Logger pertenece a org.slf4j, pero ninguna dependencia declarada en el pom.xml cubre ese paquete. Falta agregar la dependencia o el import esta mal (libreria equivocada).
- [ ] `src/main/java/com/pragma/pagos/infrastructure/client/ServicioNotificacionClient.java` — `org.slf4j`
      El import org.slf4j.Logger pertenece a org.slf4j, pero ninguna dependencia declarada en el pom.xml cubre ese paquete. Falta agregar la dependencia o el import esta mal (libreria equivocada).
- [ ] `src/main/java/com/pragma/pagos/application/OrquestadorPago.java` — `EventoPagoProducer.publicarEventoPago`
      Se invoca `publicarEventoPago` sobre `EventoPagoProducer`, pero esa clase no declara ese metodo. Agregalo con su implementacion real, o usa uno de los que si declara.
- [ ] `src/main/java/com/pragma/pagos/application/OrquestadorPago.java` — `ServicioNotificacionClient.enviarNotificacion`
      Se invoca `enviarNotificacion` sobre `ServicioNotificacionClient`, pero esa clase no declara ese metodo. Agregalo con su implementacion real, o usa uno de los que si declara.
- [ ] `src/main/java/com/pragma/pagos/application/OrquestadorPago.java` — `RecuperacionFalloService.registrarFallo`
      Se invoca `registrarFallo` sobre `RecuperacionFalloService`, pero esa clase no declara ese metodo. Agregalo con su implementacion real, o usa uno de los que si declara.
- [ ] `src/main/java/com/pragma/pagos/application/OrquestadorPago.java` — `RecuperacionFalloService.programarReintento`
      Se invoca `programarReintento` sobre `RecuperacionFalloService`, pero esa clase no declara ese metodo. Agregalo con su implementacion real, o usa uno de los que si declara.
- [ ] `src/main/java/com/pragma/pagos/infrastructure/client/ServicioNotificacionClient.java` — `NotificacionPago.tipo`
      Se invoca `tipo` sobre `NotificacionPago`, pero esa clase no declara ese metodo. Agregalo con su implementacion real, o usa uno de los que si declara.
- [ ] `src/main/java/com/pragma/pagos/infrastructure/client/ServicioNotificacionClient.java` — `NotificacionPago.destinatario`
      Se invoca `destinatario` sobre `NotificacionPago`, pero esa clase no declara ese metodo. Agregalo con su implementacion real, o usa uno de los que si declara.
- [ ] `src/main/java/com/pragma/pagos/infrastructure/client/ServicioNotificacionClient.java` — `NotificacionPago.correlationId`
      Se invoca `correlationId` sobre `NotificacionPago`, pero esa clase no declara ese metodo. Agregalo con su implementacion real, o usa uno de los que si declara.
- [ ] `src/main/java/com/pragma/pagos/infrastructure/client/ServicioNotificacionClient.java` — `NotificacionPago.titulo`
      Se invoca `titulo` sobre `NotificacionPago`, pero esa clase no declara ese metodo. Agregalo con su implementacion real, o usa uno de los que si declara.
- [ ] `src/main/java/com/pragma/pagos/infrastructure/client/ServicioNotificacionClient.java` — `NotificacionPago.mensaje`
      Se invoca `mensaje` sobre `NotificacionPago`, pero esa clase no declara ese metodo. Agregalo con su implementacion real, o usa uno de los que si declara.
- [ ] `src/main/java/com/pragma/pagos/infrastructure/client/ServicioNotificacionClient.java` — `NotificacionPago.pagoId`
      Se invoca `pagoId` sobre `NotificacionPago`, pero esa clase no declara ese metodo. Agregalo con su implementacion real, o usa uno de los que si declara.
- [ ] `src/main/java/com/pragma/pagos/infrastructure/client/ServicioNotificacionClient.java` — `NotificacionPago.monto`
      Se invoca `monto` sobre `NotificacionPago`, pero esa clase no declara ese metodo. Agregalo con su implementacion real, o usa uno de los que si declara.
- [ ] `src/main/java/com/pragma/pagos/infrastructure/client/ServicioNotificacionClient.java` — `NotificacionPago.estado`
      Se invoca `estado` sobre `NotificacionPago`, pero esa clase no declara ese metodo. Agregalo con su implementacion real, o usa uno de los que si declara.
- [ ] `src/main/java/com/pragma/pagos/infrastructure/producer/EventoPagoProducer.java` — `EstadoPago.name`
      Se invoca `name` sobre `EstadoPago`, pero esa clase no declara ese metodo. Agregalo con su implementacion real, o usa uno de los que si declara.
- [ ] `src/test/java/com/pragma/pagos/domain/service/ValidacionPagoServiceTest.java` — `ValidacionPagoService.validar`
      Se invoca `validar` sobre `ValidacionPagoService`, pero esa clase no declara ese metodo. Agregalo con su implementacion real, o usa uno de los que si declara.
- [ ] `src/test/java/com/pragma/pagos/application/OrquestadorPagoTest.java` — `OrquestadorPago.ejecutar`
      Se invoca `ejecutar` sobre `OrquestadorPago`, pero esa clase no declara ese metodo. Agregalo con su implementacion real, o usa uno de los que si declara.
- [ ] `src/test/java/com/pragma/pagos/infrastructure/client/MotorPagosClientTest.java` — `MotorPagosClient.consultarEstado`
      Se invoca `consultarEstado` sobre `MotorPagosClient`, pero esa clase no declara ese metodo. Agregalo con su implementacion real, o usa uno de los que si declara.
- [ ] `src/test/java/com/pragma/pagos/infrastructure/client/MotorPagosClientTest.java` — `MotorPagosClient.procesarReembolso`
      Se invoca `procesarReembolso` sobre `MotorPagosClient`, pero esa clase no declara ese metodo. Agregalo con su implementacion real, o usa uno de los que si declara.
- [ ] `src/test/java/com/pragma/pagos/infrastructure/client/MotorPagosClientTest.java` — `CircuitBreakerConfig.getMotorPagosUrl`
      Se invoca `getMotorPagosUrl` sobre `CircuitBreakerConfig`, pero esa clase no declara ese metodo. Agregalo con su implementacion real, o usa uno de los que si declara.
- [ ] `pom.xml` — `org.apache.camel:camel-spring-boot-bom@4.4.0`
      org.apache.camel:camel-spring-boot-bom declara la version 4.4.0, pero Maven Central respondio que esa version no existe. Es una version inventada: reemplazala por una version publicada real, o si no se conoce con certeza, usa el mecanismo centralizado del ecosistema (BOM/parent/platform/version catalog) y no declares una version individual.

### Presentes (23)

- `pom.xml`
- `src/main/java/com/pragma/pagos/PagosApplication.java`
- `src/main/resources/application.yml`
- `src/main/java/com/pragma/pagos/domain/model/Pago.java`
- `src/main/java/com/pragma/pagos/domain/model/EstadoPago.java`
- `src/main/java/com/pragma/pagos/domain/exception/PagoInvalidoException.java`
- `src/main/java/com/pragma/pagos/domain/exception/ServicioNoDisponibleException.java`
- `src/main/java/com/pragma/pagos/domain/service/ValidacionPagoService.java`
- `src/main/java/com/pragma/pagos/domain/service/RecuperacionFalloService.java`
- `src/main/resources/schemas/pago-request.xsd`
- `src/main/resources/schemas/pago-response.xsd`
- `src/main/java/com/pragma/pagos/application/OrquestadorPago.java`
- `src/main/java/com/pragma/pagos/infrastructure/client/MotorPagosClient.java`
- `src/main/java/com/pragma/pagos/infrastructure/client/SistemaAutenticacionClient.java`
- `src/main/java/com/pragma/pagos/infrastructure/client/ServicioNotificacionClient.java`
- `src/main/java/com/pragma/pagos/infrastructure/producer/EventoPagoProducer.java`
- `src/main/java/com/pragma/pagos/infrastructure/consumer/EventoPagoConsumer.java`
- `src/main/java/com/pragma/pagos/infrastructure/config/CircuitBreakerConfig.java`
- `src/test/java/com/pragma/pagos/domain/service/ValidacionPagoServiceTest.java`
- `src/test/java/com/pragma/pagos/application/OrquestadorPagoTest.java`
- `src/test/java/com/pragma/pagos/infrastructure/client/MotorPagosClientTest.java`
- `openapi.yaml`
- `README.md`

### Capas del patron declarado

Cada una tiene que existir como directorio real con al menos un archivo. Codigo plano en la raiz no satisface el patron.

- `src/main/java/com/pragma/pagos`
- `src/main/java/com/pragma/pagos/domain`
- `src/main/java/com/pragma/pagos/domain/model`
- `src/main/java/com/pragma/pagos/domain/service`
- `src/main/java/com/pragma/pagos/domain/exception`
- `src/main/java/com/pragma/pagos/infrastructure`
- `src/main/java/com/pragma/pagos/infrastructure/client`
- `src/main/java/com/pragma/pagos/infrastructure/config`
- `src/main/java/com/pragma/pagos/infrastructure/producer`
- `src/main/java/com/pragma/pagos/infrastructure/consumer`
- `src/main/java/com/pragma/pagos/application`
- `src/main/resources`
- `src/main/resources/schemas`
- `src/test/java/com/pragma/pagos`

## Verificacion

```bash
npx --yes @redocly/cli lint openapi.yaml
```

El comando tiene que pasar SIN implementar los archivos de la superficie de practica: solo andamiaje.

Ese comando pasando es la definicion de "terminado" para vos.

## Convenciones que tenes que respetar

- Un solo ecosistema: no declares librerias de otro lenguaje ni mezcles gestores de paquetes.
- Toda libreria que uses tiene que estar declarada en el manifiesto de dependencias.
- Todo import declarado tiene que usarse; todo tipo usado tiene que existir o venir de una dependencia declarada.
- El patron es **capas estándar con separación de dominio e infraestructura (SOA)**: los contratos (interfaces, puertos) los define la capa interna y los implementa la externa, nunca al revés.
- Los archivos que crees llevan implementacion real, no stubs: sin `TODO`, sin cuerpos vacios, sin `// getters y setters`.

## Contexto del candidato

Sirve para calibrar el nivel del codigo, no para resolver las fases.

- Perfil: Chapter Integración, Especialidad Desarrollador, Tecnología API, Senior
- Brecha que el reto ataca: Implementa y crea artefactos reutilizable para el equipo que ayuda en proceso de tareas complejas
- Mision: Candidato con experiencia en arquitectura SOA y patrones de integración, trabaja en equipo de desarrollo distribuido

---

*Generado por Challenge Generator — Pragma. `README.md` tiene el enunciado completo del reto para la persona. `PROMPT_MEJORA.md` es la variante para pegar en un chat, si se prefiere ese flujo.*
