# 🏆 TorneoHub

Plataforma SaaS multiusuario para organizar torneos deportivos: inscripción de equipos, generación automática de calendarios, resultados y clasificaciones en tiempo real.

> **Estado:** 🚧 en desarrollo 

## Problema que resuelve

Muchos clubes y ligas amateur gestionan sus torneos con hojas de cálculo y grupos de mensajería. TorneoHub centraliza la inscripción, el calendario, los resultados y la clasificación en una sola aplicación.

## Funcionalidades previstas

- [ ] Registro y autenticación con JWT
- [ ] Roles: organizador, árbitro, capitán de equipo, espectador
- [ ] Multi-tenant: cada organización gestiona sus propios torneos
- [ ] CRUD de torneos, equipos y jugadores
- [ ] Generación automática de calendario (liga todos contra todos y eliminatorias)
- [ ] Registro de resultados y cálculo de clasificación
- [ ] Actualización de resultados en tiempo real (WebSockets)
- [ ] Notificaciones por correo
- [ ] Suscripción de pago para organizaciones (Stripe, modo test)
- [ ] API REST documentada con OpenAPI/Swagger
- [ ] Despliegue en producción con Docker y CI/CD

## Stack

| Capa | Tecnología |
|------|-----------|
| Backend | Java 21, Spring Boot 3 |
| Seguridad | Spring Security + JWT |
| Persistencia | Spring Data JPA, PostgreSQL, Flyway |
| Tiempo real | Spring WebSocket (STOMP) |
| Frontend | [React / Thymeleaf: por decidir] |
| Tests | JUnit 5, Mockito, Testcontainers |
| DevOps | Docker, GitHub Actions |

## Arquitectura

Arquitectura por capas (controller → service → repository) con DTOs y manejo centralizado de errores. Los diagramas se añadirán en `/docs`.

## Estructura del proyecto

```
torneohub/
├── backend/
│   └── src/
│       ├── main/
│       │   ├── java/com/torneohub/
│       │   │   ├── config/         # Configuración (CORS, OpenAPI, beans)
│       │   │   ├── security/       # Spring Security, filtros y JWT
│       │   │   ├── controller/     # Endpoints REST
│       │   │   ├── service/        # Lógica de negocio
│       │   │   ├── repository/     # Spring Data JPA
│       │   │   ├── domain/         # Entidades JPA
│       │   │   ├── dto/            # Objetos de entrada/salida de la API
│       │   │   ├── mapper/         # Conversión entidad ↔ DTO
│       │   │   ├── exception/      # Excepciones y manejo global de errores
│       │   │   ├── websocket/      # Configuración y mensajes STOMP
│       │   │   ├── notification/   # Envío de correos
│       │   │   └── billing/        # Integración con Stripe
│       │   └── resources/
│       │       └── db/migration/   # Migraciones Flyway
│       └── test/java/com/torneohub/
│           ├── controller/
│           ├── service/
│           ├── repository/
│           └── integration/        # Tests con Testcontainers
├── docs/
│   ├── architecture/               # Diagramas y decisiones de diseño
│   └── api/                        # Documentación de la API
├── .github/workflows/              # CI/CD con GitHub Actions
└── README.md
```

## Cómo ejecutarlo

> Pendiente: se completará cuando exista la primera versión ejecutable.

```bash
git clone https://github.com/Panchitis311/TorneoHub.git
cd torneohub
docker compose up
```

## Hoja de ruta

1. **Fase 1:** modelo de datos, autenticación y CRUD básico
2. **Fase 2:** generación de calendarios y clasificación
3. **Fase 3:** tiempo real y notificaciones
4. **Fase 4:** pagos, documentación y despliegue

## Licencia

MIT
