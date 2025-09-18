# Lab Supabase - Práctica de Creación de Tablas

Este laboratorio te guiará paso a paso para crear una cuenta en Supabase y configurar una base de datos con dos tablas relacionadas: **Usuarios** y **Mascotas**.

## 📋 Objetivos del Lab

Al completar este laboratorio serás capaz de:
- Crear y configurar una cuenta en Supabase
- Diseñar y crear tablas con relaciones (Foreign Keys)
- Configurar tipos de datos apropiados
- Establecer relaciones entre tablas
- Documentar tu trabajo con capturas de pantalla

## 🚀 Prerrequisitos

- Una dirección de correo electrónico válida
- Navegador web actualizado
- Conocimientos básicos de bases de datos relacionales

## 📝 Instrucciones del Laboratorio

### Paso 1: Crear una cuenta en Supabase

1. Ve a [https://supabase.com](https://supabase.com)
2. Haz clic en **"Start your project"** o **"Sign Up"**
3. Puedes registrarte usando:
   - GitHub (recomendado)
   - Google
   - Email y contraseña
4. Completa el proceso de verificación si es necesario
5. Una vez logueado, verás el dashboard de Supabase

**📸 Captura requerida:** Pantalla principal del dashboard de Supabase después del login

### Paso 2: Crear un nuevo proyecto

1. En el dashboard, haz clic en **"New Project"**
2. Selecciona tu organización (o crea una nueva)
3. Configura tu proyecto:
   - **Name:** `lab-practica-supabase`
   - **Database Password:** Crea una contraseña segura (¡guárdala!)
   - **Region:** Selecciona la región más cercana
4. Haz clic en **"Create new project"**
5. Espera a que el proyecto se configure (puede tomar unos minutos)

**📸 Captura requerida:** Pantalla de configuración del nuevo proyecto

### Paso 3: Acceder al Editor de Tablas

1. Una vez que el proyecto esté listo, ve a la sección **"Table Editor"** en el menú lateral
2. Aquí crearemos nuestras dos tablas

### Paso 4: Crear la tabla "Usuarios"

1. En el Table Editor, haz clic en **"Create a new table"**
2. Configura la tabla con los siguientes datos:
   - **Name:** `usuarios`
   - **Description:** `Tabla para almacenar información de usuarios`
3. Configura las columnas:

| Nombre | Tipo | Configuración |
|--------|------|---------------|
| `id` | `int8` | Primary Key, Auto-increment (viene por defecto) |
| `nombre` | `text` | No nulo |
| `edad` | `int4` | No nulo |
| `email` | `text` | No nulo, Único |

4. Haz clic en **"Save"** para crear la tabla

**📸 Captura requerida:** Pantalla de configuración de la tabla "usuarios"

#### Pasos detallados para crear columnas:

**Columna "nombre":**
- Name: `nombre`
- Type: `text`
- Default Value: (vacío)
- ✅ Is Nullable: desmarcar (No nulo)

**Columna "edad":**
- Name: `edad`  
- Type: `int4`
- Default Value: (vacío)
- ✅ Is Nullable: desmarcar (No nulo)

**Columna "email":**
- Name: `email`
- Type: `text`
- Default Value: (vacío)
- ✅ Is Nullable: desmarcar (No nulo)
- ✅ Is Unique: marcar

### Paso 5: Crear la tabla "Mascota"

1. Crea una nueva tabla con el nombre `mascota`
2. Configura las columnas:

| Nombre | Tipo | Configuración |
|--------|------|---------------|
| `id` | `int8` | Primary Key, Auto-increment (viene por defecto) |
| `nombre` | `text` | No nulo |
| `edad` | `int4` | No nulo |
| `chip_num` | `text` | No nulo, Único |
| `usuario_id` | `int8` | Foreign Key → usuarios(id) |

#### Pasos para crear la Foreign Key:

**Para la columna usuario_id:**
1. Name: `usuario_id`
2. Type: `int8`
3. ✅ Is Nullable: desmarcar (No nulo)
4. En **"Foreign Key Relation":**
   - Table: `usuarios`
   - Column: `id`
   - On Update: `CASCADE`
   - On Delete: `CASCADE`

**📸 Capturas requeridas:** 
- Pantalla de configuración de la tabla "mascota"
- Pantalla mostrando la configuración de la Foreign Key

### Paso 6: Verificar las tablas creadas

1. En el Table Editor, deberías ver ambas tablas: `usuarios` y `mascota`
2. Haz clic en cada tabla para verificar que las columnas están correctamente configuradas
3. Verifica que la relación Foreign Key esté establecida

**📸 Captura requerida:** Vista general del Table Editor mostrando ambas tablas

### Paso 7: Agregar datos de prueba (Opcional)

Para verificar que todo funciona correctamente, puedes agregar algunos datos de prueba:

**En la tabla usuarios:**
```sql
INSERT INTO usuarios (nombre, edad, email) VALUES 
('Juan Pérez', 25, 'juan@example.com'),
('María García', 30, 'maria@example.com');
```

**En la tabla mascota:**
```sql
INSERT INTO mascota (nombre, edad, chip_num, usuario_id) VALUES 
('Rex', 3, 'CHIP001', 1),
('Luna', 2, 'CHIP002', 2);
```

**📸 Captura requerida:** Tablas con datos de prueba insertados

## 📸 Resumen de Capturas Requeridas

Para completar el laboratorio, debes incluir las siguientes capturas de pantalla:

1. **Dashboard principal de Supabase** después del login
2. **Configuración del nuevo proyecto**
3. **Configuración de la tabla "usuarios"** con todas sus columnas
4. **Configuración de la tabla "mascota"** con todas sus columnas
5. **Configuración de la Foreign Key** (relación entre mascota y usuarios)
6. **Vista general del Table Editor** mostrando ambas tablas
7. **Tablas con datos de prueba** (opcional pero recomendado)

## 🔗 Entrega

1. Sube todas las capturas de pantalla a tu repositorio (carpeta `screenshots/` o `imagenes/`)
2. Asegúrate de que este README.md esté actualizado con tus capturas
3. Entrega la URL de tu repositorio GitHub

## 📋 Estructura Final de la Base de Datos

```
usuarios
├── id (int8, PK, auto-increment)
├── nombre (text, not null)
├── edad (int4, not null)
└── email (text, not null, unique)

mascota
├── id (int8, PK, auto-increment)
├── nombre (text, not null)
├── edad (int4, not null)
├── chip_num (text, not null, unique)
└── usuario_id (int8, FK → usuarios.id)
```

## ✅ Criterios de Evaluación

- [ ] Cuenta de Supabase creada exitosamente
- [ ] Proyecto configurado correctamente
- [ ] Tabla "usuarios" creada con las columnas especificadas
- [ ] Tabla "mascota" creada con las columnas especificadas
- [ ] Foreign Key establecida correctamente entre mascota.usuario_id y usuarios.id
- [ ] Capturas de pantalla incluidas y bien organizadas
- [ ] Documentación clara y completa
- [ ] Repositorio GitHub entregado con URL válida

## 🆘 Solución de Problemas

### Error al crear Foreign Key
- Asegúrate de que la tabla "usuarios" esté creada antes que "mascota"
- Verifica que los tipos de datos coincidan (int8 en ambas columnas)

### Error al insertar datos
- Verifica que el usuario_id en la tabla mascota corresponda a un id existente en usuarios
- Asegúrate de que el email sea único en la tabla usuarios

### No puedes acceder a Supabase
- Verifica tu conexión a internet
- Intenta usar un navegador diferente
- Limpia la caché del navegador

---

**¡Éxito en tu laboratorio!** 🎉
