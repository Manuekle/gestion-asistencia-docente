# 2. Especificación de la API (Sincronizada)

> **Convención técnica:** Todos los endpoints que interactúan con la base de datos deben importar el cliente Prisma como `db` desde `@/lib/prisma`. Nunca uses `prisma` directamente para evitar múltiples instancias y posibles errores en desarrollo.

Esta especificación refleja la estructura de endpoints actual del proyecto, agrupada por rol de usuario.

---

## 🔑 Endpoints de Autenticación y Perfil (Generales)

#### `POST /api/auth/register`

Registra un nuevo usuario.

#### `POST /api/auth/login` (manejado por NextAuth)

Inicia sesión y obtiene un token de sesión.

#### `POST /api/auth/forgot-password`

Inicia el proceso de recuperación de contraseña.

#### `POST /api/auth/verify-reset-token`

Verifica que el token de reseteo sea válido.

#### `POST /api/auth/reset-password`

Establece una nueva contraseña usando un token válido.

#### `GET /api/profile`

Obtiene los datos del perfil del usuario autenticado.

#### `PUT /api/profile`

Actualiza los datos del perfil del usuario autenticado.

#### `POST /api/profile/change-password`

Cambia la contraseña del usuario autenticado.

---

## 👤 Endpoints de Administrador (`/api/admin`)

#### `GET /api/users`

Obtiene una lista paginada de todos los usuarios.

#### `POST /api/users/bulk`

Crea múltiples usuarios a partir de un archivo CSV.

#### `GET, POST /api/admin/asignaturas`

Obtiene o crea nuevas asignaturas.

#### `GET, POST /api/admin/clases`

Obtiene o crea nuevas clases.

#### `GET, POST /api/admin/matriculas`

Obtiene o crea nuevas matrículas (asociar estudiante a asignatura).

---

## 👨‍🏫 Endpoints de Docente (`/api/docente`)

#### `GET /api/docente/dashboard`

Obtiene estadísticas y datos para el dashboard del docente.

#### `GET /api/docente/dashboard/live`

Obtiene datos en tiempo real para una clase activa.

#### `GET, POST /api/docente/asignaturas`

Obtiene las asignaturas del docente o crea una nueva.

#### `GET, POST /api/docente/asignaturas/[id]/reportes`

- **GET**: Lista los reportes generados previamente para una asignatura.
- **POST**: Genera un nuevo reporte de asistencia en formato PDF para una asignatura. El cuerpo de la petición debe incluir las fechas de inicio y fin para el reporte.

#### `GET, POST /api/docente/clases`

Obtiene las clases de un docente o programa una nueva.

#### `GET, PUT /api/docente/clases/[classId]`

Obtiene o actualiza los detalles de una clase específica.

#### `POST /api/docente/clases/[classId]/generar-qr`

Inicia la clase y genera un código QR para la asistencia.

#### `GET /api/docente/clases/[classId]/asistencia`

Obtiene el estado de asistencia de todos los estudiantes para una clase.

#### `PUT /api/docente/asistencia`

Modifica manualmente el estado de asistencia de un estudiante.

#### `GET, POST /api/docente/eventos`

Gestiona eventos del calendario para el docente.

#### `PUT, DELETE /api/docente/eventos/[id]`

Actualiza o elimina un evento específico.

---

## 🎓 Endpoints de Estudiante (`/api/estudiante`)

#### `POST /api/attendances/scan`

Registra la asistencia de un estudiante escaneando un QR.

#### `GET /api/estudiante/dashboard`

Obtiene los datos para el dashboard del estudiante.

#### `GET /api/estudiante/historial`

Obtiene el historial de asistencias del estudiante.

#### `GET /api/estudiante/eventos`

Obtiene los eventos (clases) del calendario para el estudiante.

#### `GET /api/estudiante/reportes/asistencia`

Genera un reporte de asistencia personal.
