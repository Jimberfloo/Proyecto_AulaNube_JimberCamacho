# Proyecto_AulaNube_JimberCamacho
avance de proyecto para la entrega de la evaluación 1 de Java, esto se creo para los enlaces.
# AulaNube — Plataforma LMS Cloud-Native

Proyecto de diseño e implementación de arquitectura basada en microservicios para la plataforma e-learning **AulaNube**, desarrollado para la asignatura **JVY0101: Diseño y Construcción de Soluciones Nativas en Nube** (Duoc UC).

---

## 1. Integrantes del Equipo
* **Estudiante 1:** [Jimber Camacho]
* **Sección / Asignatura:** JVY0101

---

## 2. Descripción del Proyecto
AulaNube es una plataforma de e-learning distribuida diseñada bajo una arquitectura cloud-native en AWS. Satisface los requerimientos de alta demanda durante periodos de inicio de semestre mediante escalabilidad por dominio, desacoplamiento de pagos y mensajería asíncrona orientada a eventos.

---

## 3. Arquitectura del Sistema
![Diagrama de Arquitectura](./INFRAESTRUCTURA-DIAGRAMA%20DE%20LA%20NUBE.png)

### Componentes Clave de Infraestructura (AWS)
* **API & Borde:** AWS WAF, Amazon Cognito (JWT / Roles), Amazon API Gateway.
* **Cómputo:** Microservicios Spring Boot en Amazon ECS (Fargate) + Funciones AWS Lambda para procesos asíncronos y batch.
* **Mensajería & Desacoplamiento:** Amazon SQS (Event-Driven Architecture).
* **Descubrimiento & Resiliencia:** AWS Cloud Map (Service Registry) y Circuit Breaker (Resilience4j).
* **Persistencia:** DynamoDB (Bases de datos por dominio) y Amazon S3 (Materiales de cursos y Certificados PDF).
* **Observabilidad & Seguridad:** AWS CloudWatch, AWS X-Ray, AWS KMS y AWS Secrets Manager.

---

## 4. Estructura de Microservicios
| Microservicio | Puerto Local | Dominio & Responsabilidad |
|---|---|---|
| `ms-usuarios` | 8081 | Identidad, perfiles y autenticación (JWT) |
| `ms-cursos` | 8082 | Gestión de catálogo, unidades, foros y materiales |
| `ms-matriculas` | 8083 | Inscripciones, control de cupos e integración con SQS |
| `ms-evaluaciones` | 8084 | Cuestionarios, entregas, notas e historial auditable |
| `ms-pagos` | 8085 | Procesamiento de pagos desacoplado con Circuit Breaker |
| `ms-certificados` | 8086 | Registro y emisión criptográfica de certificados |

---

## 5. Requisitos de Ejecución Local
* Java 17 LTS
* Apache Maven 3.8+
* Docker Desktop & LocalStack (para simular servicios AWS)
