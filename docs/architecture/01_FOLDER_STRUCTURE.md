# Arquitectura de Carpetas (Detallada)

```
sistema-asistencias/
├── app/                                # Código fuente de la aplicación Next.js
│   ├── api/                            # Endpoints de la API (Backend)
│   │   ├── admin/                      # Rutas exclusivas para Administradores
│   │   ├── attendances/                # Rutas para la gestión de asistencias (ej. escaneo)
│   │   ├── auth/                       # Rutas de autenticación (Login, Register, NextAuth)
│   │   ├── docente/                    # Rutas exclusivas para Docentes
│   │   ├── estudiante/                 # Rutas exclusivas para Estudiantes
│   │   ├── profile/                    # Rutas para la gestión del perfil de usuario
│   │   └── users/                      # Rutas para la gestión de usuarios
│   ├── dashboard/                      # Vistas protegidas del dashboard
│   │   ├── admin/                      # Páginas del panel de Administrador
│   │   ├── docente/                    # Páginas del panel de Docente
│   │   ├── estudiante/                 # Páginas del panel de Estudiante
│   │   └── profile/                    # Página de perfil de usuario
│   ├── emails/                         # Plantillas de correo transaccional (React Email)
│   ├── (auth_pages)/                   # Agrupación de rutas públicas de autenticación
│   │   ├── forgot-password/
│   │   ├── login/
│   │   ├── register/
│   │   └── reset-password/
│   ├── globals.css                     # Estilos globales
│   ├── layout.tsx                      # Layout principal de la aplicación
│   └── page.tsx                        # Página de inicio (Landing page)
├── components/                         # Componentes reutilizables de React
│   ├── ui/                             # Componentes base de UI (shadcn)
│   └── shared/                         # Componentes complejos compartidos
├── lib/                                # Librerías, helpers y utilidades
│   ├── auth.ts                         # Configuración de NextAuth
│   ├── prisma.ts                       # Cliente Prisma exportado como 'db' (importar SIEMPRE como { db } from '@/lib/prisma')
│   └── utils.ts                        # Funciones de utilidad
├── prisma/                             # Configuración de la base de datos con Prisma
│   ├── migrations/                     # Archivos de migración de la BD
│   ├── seed.ts                         # Script para poblar la BD con datos iniciales
│   └── schema.prisma                   # Esquema de la base de datos
└── public/                             # Archivos estáticos (imágenes, fuentes, etc.)
```
