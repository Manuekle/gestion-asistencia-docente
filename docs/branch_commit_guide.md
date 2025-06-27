# Guía de Ramas y Commits por Historia de Usuario

Este documento define la convención de ramas y ejemplos de commits para cada Historia de Usuario (HU) según la estructura Git Flow y Conventional Commits.

> Formato de rama: `feature/<hu-id>-<slug>`  
> Formato de commit: `tipo(alcance): mensaje`

Tipos de commit más usados: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`.

---

## Tabla General

| Épica | HU | Título | Rama | Commits sugeridos |
|-------|----|--------|------|-------------------|
| **EPIC 1 – Usuarios y Autenticación** |
| | HU-001 | Registro masivo de usuarios | `feature/hu-001-registro-masivo-usuarios` | `feat(auth): bulk user import endpoint`  <br>`feat(ui): csv/xlsx upload component` <br>`test(auth): bulk import edge cases` <br>`docs(users): usage guide` |
| | HU-002 | Autenticación segura MFA | `feature/hu-002-autenticacion-mfa` | `feat(auth): oauth + password login` <br>`feat(auth): 2fa via totp/email` <br>`fix(auth): brute-force protection` <br>`test(auth): mfa flows` |
| | HU-003 | Gestión de perfil | `feature/hu-003-perfil-usuario` | `feat(profile): edit profile page` <br>`feat(profile): avatar upload` <br>`feat(profile): change-password flow` <br>`test(profile): validation` |
| **EPIC 2 – Gestión Académica** |
| | HU-004 | CRUD de asignaturas | `feature/hu-004-asignaturas-crud` | `feat(subjects): CRUD API` <br>`feat(ui): subjects admin page` <br>`test(subjects): api cases` |
| | HU-005 | Dashboard docente | `feature/hu-005-dashboard-docente` | `feat(ui): teacher dashboard widgets` <br>`chore(api): aggregate stats` <br>`test(ui): widget rendering` |
| | HU-006 | Estudiantes por asignatura | `feature/hu-006-estudiantes-por-asignatura` | `feat(students): enroll/unenroll` <br>`feat(ui): students table` <br>`test(students): enrollment rules` |
| **EPIC 3 – Programación de Clases** |
| | HU-007 | Programación de clases | `feature/hu-007-programacion-clases` | `feat(classes): schedule model` <br>`feat(ui): calendar view` <br>`test(classes): conflicts` |
| | HU-008 | Control de asistencia en tiempo real | `feature/hu-008-control-asistencia-tiempo-real` | `feat(attendance): live websocket` <br>`feat(ui): real-time panel` <br>`test(attendance): socket events` |
| | HU-009 | Cronograma académico | `feature/hu-009-cronograma-academico` | `feat(calendar): academic timeline` <br>`style(calendar): responsive design` <br>`docs(calendar): user guide` |
| **EPIC 4 – Sistema QR** |
| | HU-010 | Generación de QR seguros | `feature/hu-010-qr-generacion` | `feat(qr): secure code generator` <br>`chore(qr): crypto utils` |
| | HU-011 | Validación de QR | `feature/hu-011-qr-validacion` | `feat(qr): validate endpoint` <br>`test(qr): invalid/expired cases` |
| | HU-012 | Interfaz de escaneo | `feature/hu-012-qr-ui-escaner` | `feat(ui): qr scanner component` <br>`style(ui): camera overlay` <br>`test(ui): permissions` |
| **EPIC 5 – Registro de Asistencias** |
| | HU-013 | Registro de asistencia | `feature/hu-013-registro-asistencia` | `feat(att): save attendance record` <br>`test(att): duplicate prevention` |
| | HU-014 | Panel de asistencias | `feature/hu-014-panel-asistencias` | `feat(ui): attendance dashboard` <br>`chore(api): pagination` |
| | HU-015 | Asistencia manual | `feature/hu-015-asistencia-manual` | `feat(att): manual override` <br>`test(att): teacher override rules` |
| **EPIC 6 – Reportes y Analíticas** |
| | HU-016 | Reportes de asistencia | `feature/hu-016-reportes-asistencia` | `feat(report): attendance PDF` <br>`test(report): totals` |
| | HU-017 | Bitácoras docentes | `feature/hu-017-bitacoras-docentes` | `feat(log): teacher logs` <br>`docs(log): export format` |
| | HU-018 | Panel de estadísticas | `feature/hu-018-panel-estadisticas` | `feat(stats): student KPIs` <br>`test(stats): chart data` |
| | HU-019 | Dashboard institucional | `feature/hu-019-dashboard-institucional` | `feat(stats): institution metrics` <br>`style(ui): admin charts` |
| **EPIC 7 – Comunicación** |
| | HU-020 | Notificaciones | `feature/hu-020-notificaciones` | `feat(msg): notification service` <br>`test(msg): channels` |
| | HU-021 | Mensajería interna | `feature/hu-021-mensajeria-interna` | `feat(chat): inbox ui` <br>`feat(chat): message API` |
| | HU-022 | Recordatorios automáticos | `feature/hu-022-recordatorios` | `feat(reminder): cron scheduler` <br>`test(reminder): email flow` |
| **EPIC 8 – Administración** |
| | HU-030 | Carga masiva de datos (ejemplo) | `feature/hu-030-carga-masiva-ejemplo` | `feat(import): sample bulk loader` <br>`test(import): validation cases` |
| | HU-031 | Observación clases canceladas | `feature/hu-031-observacion-clases` | `feat(obs): cancellation observations` <br>`docs(obs): usage` |
| | HU-032 | Outlook calendar sync | `feature/hu-032-outlook-sync` | `feat(sync): outlook calendar events` <br>`test(sync): api errors` |
| **EPIC 8 – Administración** |
| | HU-023 | Usuarios y permisos | `feature/hu-023-usuarios-permisos` | `feat(admin): role management` <br>`test(admin): access control` |
| | HU-024 | Configuración del sistema | `feature/hu-024-configuracion-sistema` | `feat(settings): global settings ui` <br>`docs(settings): env vars` |
| | HU-025 | Auditoría | `feature/hu-025-auditoria` | `feat(audit): activity logs` <br>`test(audit): filter/query` |
| | HU-026 | Mantenimiento del sistema | `feature/hu-026-mantenimiento` | `feat(maintenance): cleanup scripts` <br>`docs(maintenance): runbook` |

---

## Flujo de trabajo recomendado

```bash
# 1. Crear rama
git checkout -b feature/hu-00X-descripcion develop

# 2. Commits frecuentes y atómicos
 git add .
 git commit -m "feat(<scope>): mensaje claro"

# 3. Subir la rama y abrir PR a develop
 git push -u origin feature/hu-00X-descripcion
```

Al finalizar la HU y aprobar el PR, mergear a `develop`. Al cierre del sprint, `develop` se integra a `main` mediante un Pull Request de release.
