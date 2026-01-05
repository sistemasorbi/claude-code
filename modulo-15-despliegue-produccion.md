# Módulo 15: Despliegue a Producción

**Objetivo:** Lleva tus aplicaciones a producción con la asistencia de Claude Code

**Tiempo Estimado:** 60-90 minutos

---

## Lo Que Aprenderás en Este Módulo

Al final de este módulo, podrás:
- Entender fundamentos de despliegue
- Desplegar a varias plataformas (Vercel, Heroku, VPS)
- Usar Docker para containerización
- Configurar pipelines CI/CD
- Configurar entornos de producción
- Implementar monitoreo y logging
- Seguir mejores prácticas de seguridad
- Manejar migraciones de base de datos en producción

---

## Lección 1: Fundamentos de Despliegue

### ¿Qué es el Despliegue?

**Despliegue** significa hacer tu aplicación disponible en internet para que otros puedan usarla.

**Desarrollo vs Producción:**

**Desarrollo:**
- Ejecutándose en tu computadora
- Eres el único usuario
- Puedes romper cosas y arreglarlas
- Modo debug habilitado
- Datos de prueba

**Producción:**
- Ejecutándose en servidores
- Usuarios reales acceden
- Debe ser confiable y rápido
- Sin info de debug expuesta
- Datos reales

---

### Lista de Verificación de Despliegue

**Antes de desplegar, asegúrate:**
```
Ayúdame a preparar esta aplicación para producción:
1. Verificar que todas las variables de entorno estén documentadas
2. Verificar que no haya secretos en el código
3. Asegurar que el manejo de errores no exponga info sensible
4. Añadir logging apropiado
5. Configurar endpoint de health check
6. Configurar CORS apropiadamente
7. Añadir rate limiting
8. Configurar HTTPS
9. Minificar/bundlear código
10. Ejecutar todos los tests
```

---

## Lección 2: Desplegando a Vercel

### ¿Qué es Vercel?

**Vercel** es una plataforma optimizada para frameworks frontend (Next.js, React, etc.)

**Mejor para:**
- Aplicaciones Next.js
- Apps React/Vue/Svelte
- Funciones serverless
- Sitios estáticos

---

### Desplegando con Claude Code

```
Ayúdame a desplegar esta aplicación Next.js a Vercel:
1. Instalar Vercel CLI
2. Configurar vercel.json
3. Configurar variables de entorno
4. Desplegar a producción
5. Configurar dominio personalizado
```

**Claude Code hará:**

```bash
# Instalar Vercel CLI
npm install -g vercel

# Login
vercel login

# Desplegar
vercel --prod
```

**Crear vercel.json:**
```json
{
  "buildCommand": "npm run build",
  "outputDirectory": ".next",
  "devCommand": "npm run dev",
  "installCommand": "npm install",
  "framework": "nextjs",
  "env": {
    "DATABASE_URL": "@database-url",
    "API_KEY": "@api-key"
  }
}
```

---

## Lección 3: Desplegando a Heroku

### ¿Qué es Heroku?

**Heroku** es una plataforma para desplegar aplicaciones backend y full-stack.

**Mejor para:**
- APIs Node.js
- Apps Python/Django
- Ruby on Rails
- Aplicaciones full-stack

---

### Desplegando con Claude Code

```
Ayúdame a desplegar esta API Express a Heroku:
1. Crear Procfile
2. Configurar heroku.yml si es necesario
3. Configurar variables de entorno
4. Añadir base de datos PostgreSQL
5. Configurar despliegue
6. Configurar logging
```

**Claude Code crea:**

**Procfile:**
```
web: node dist/server.js
```

**Comandos de despliegue:**
```bash
# Instala Heroku CLI primero, luego:

# Login
heroku login

# Crear app
heroku create nombre-mi-app

# Añadir PostgreSQL
heroku addons:create heroku-postgresql:hobby-dev

# Configurar variables de entorno
heroku config:set NODE_ENV=production
heroku config:set API_KEY=tu-key

# Desplegar
git push heroku main

# Ver logs
heroku logs --tail
```

---

## Lección 4: Desplegando a VPS (Servidor Privado Virtual)

### ¿Qué es un VPS?

**VPS** = Tu propio servidor (ej. DigitalOcean, Linode, AWS EC2)

**Mejor para:**
- Control total necesario
- Configuraciones personalizadas
- Múltiples aplicaciones
- Aprender administración de servidores

---

### Configurando Despliegue en VPS

```
Ayúdame a desplegar esta app Node.js a un VPS Ubuntu:
1. Configurar el servidor (Node.js, PM2, Nginx)
2. Configurar firewall
3. Configurar SSL con Let's Encrypt
4. Configurar reverse proxy Nginx
5. Configurar PM2 para gestión de procesos
6. Configurar reinicios automáticos
7. Configurar script de despliegue
```

**Claude Code creará guía de despliegue:**

**En el servidor:**
```bash
# Actualizar sistema
sudo apt update && sudo apt upgrade -y

# Instalar Node.js
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs

# Instalar PM2
sudo npm install -g pm2

# Instalar Nginx
sudo apt install -y nginx

# Configurar firewall
sudo ufw allow 22
sudo ufw allow 80
sudo ufw allow 443
sudo ufw enable
```

**Configuración Nginx:**
```nginx
server {
    listen 80;
    server_name tudominio.com;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

**Archivo ecosystem de PM2:**
```javascript
module.exports = {
  apps: [{
    name: 'mi-app',
    script: './dist/server.js',
    instances: 'max',
    exec_mode: 'cluster',
    env: {
      NODE_ENV: 'production',
      PORT: 3000
    }
  }]
};
```

---

## Lección 5: Despliegue con Docker

### ¿Por Qué Docker?

**Docker** empaqueta tu app con todo lo que necesita para ejecutarse.

**Beneficios:**
- Consistente entre entornos
- Fácil de desplegar en cualquier lugar
- Aísla dependencias
- Escala fácilmente

---

### Creando Configuración Docker

```
Crea configuración Docker para esta API Node.js:
1. Escribe Dockerfile
2. Crea .dockerignore
3. Escribe docker-compose.yml para desarrollo local
4. Añade docker-compose de producción
5. Incluye health checks
```

**Dockerfile:**
```dockerfile
# Etapa de build
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# Etapa de producción
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY --from=builder /app/dist ./dist

# Seguridad: ejecutar como non-root
USER node

# Health check
HEALTHCHECK --interval=30s --timeout=3s \
  CMD node healthcheck.js

EXPOSE 3000
CMD ["node", "dist/server.js"]
```

**.dockerignore:**
```
node_modules
npm-debug.log
.env
.git
.gitignore
README.md
.vscode
coverage
.DS_Store
```

**docker-compose.yml:**
```yaml
version: '3.8'

services:
  app:
    build: .
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production
      - DATABASE_URL=postgres://user:pass@db:5432/mydb
    depends_on:
      - db

  db:
    image: postgres:14-alpine
    environment:
      - POSTGRES_DB=mydb
      - POSTGRES_USER=user
      - POSTGRES_PASSWORD=pass
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

---

## Lección 6: Pipelines CI/CD

### ¿Qué es CI/CD?

**CI** = Integración Continua (testear código automáticamente)
**CD** = Despliegue Continuo (desplegar código automáticamente)

**Beneficios:**
- Testing automático
- Despliegue automático
- Detectar bugs temprano
- Desplegar más rápido y seguro

---

### GitHub Actions para CI/CD

```
Crea un workflow de GitHub Actions que:
1. Se ejecute en cada push a main
2. Ejecute todos los tests
3. Ejecute linter
4. Haga build de la aplicación
5. Despliegue a producción si los tests pasan
6. Envíe notificaciones si falla
```

**.github/workflows/deploy.yml:**
```yaml
name: Desplegar a Producción

on:
  push:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'

      - name: Instalar dependencias
        run: npm ci

      - name: Ejecutar linter
        run: npm run lint

      - name: Ejecutar tests
        run: npm test

      - name: Build
        run: npm run build

  deploy:
    needs: test
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main'
    steps:
      - uses: actions/checkout@v3

      - name: Desplegar a producción
        env:
          DEPLOY_KEY: ${{ secrets.DEPLOY_KEY }}
        run: |
          ./scripts/deploy.sh
```

---

## Lección 7: Configuración de Entorno

### Gestionando Variables de Entorno

```
Ayúdame a configurar gestión apropiada de entorno:
1. Crear plantilla .env.example
2. Documentar todas las variables de entorno
3. Configurar diferentes configs para dev/staging/prod
4. Añadir validación para variables requeridas
5. Asegurar valores sensibles
```

**config/env.ts:**
```typescript
import dotenv from 'dotenv';

dotenv.config();

interface Config {
  nodeEnv: string;
  port: number;
  databaseUrl: string;
  jwtSecret: string;
  apiKey: string;
}

function validateEnv(): Config {
  const required = [
    'DATABASE_URL',
    'JWT_SECRET',
    'API_KEY'
  ];

  for (const key of required) {
    if (!process.env[key]) {
      throw new Error(`Falta variable de entorno requerida: ${key}`);
    }
  }

  return {
    nodeEnv: process.env.NODE_ENV || 'development',
    port: parseInt(process.env.PORT || '3000'),
    databaseUrl: process.env.DATABASE_URL!,
    jwtSecret: process.env.JWT_SECRET!,
    apiKey: process.env.API_KEY!
  };
}

export const config = validateEnv();
```

---

## Lección 8: Monitoreo y Logging

### Configurando Logging de Producción

```
Añade logging de grado producción:
1. Usa logging estructurado (formato JSON)
2. Diferentes niveles de log (error, warn, info, debug)
3. Rotación de logs
4. Envía errores a servicio de monitoreo
5. No registres datos sensibles
```

**Usando Winston para logging:**
```typescript
import winston from 'winston';

const logger = winston.createLogger({
  level: process.env.LOG_LEVEL || 'info',
  format: winston.format.combine(
    winston.format.timestamp(),
    winston.format.errors({ stack: true }),
    winston.format.json()
  ),
  transports: [
    // Escribe todos los logs a consola
    new winston.transports.Console({
      format: winston.format.simple()
    }),
    // Escribe errores a error.log
    new winston.transports.File({
      filename: 'logs/error.log',
      level: 'error'
    }),
    // Escribe todos los logs a combined.log
    new winston.transports.File({
      filename: 'logs/combined.log'
    })
  ]
});

export default logger;
```

---

### Health Checks

```
Añade endpoints de health check:
1. /health - health check básico
2. /health/ready - readiness check (dependencias)
3. /health/live - liveness check
```

```typescript
app.get('/health', (req, res) => {
  res.json({ status: 'ok', timestamp: new Date().toISOString() });
});

app.get('/health/ready', async (req, res) => {
  try {
    // Verificar base de datos
    await db.query('SELECT 1');

    res.json({
      status: 'ready',
      checks: {
        database: 'ok'
      }
    });
  } catch (error) {
    res.status(503).json({
      status: 'not ready',
      checks: {
        database: 'failed'
      }
    });
  }
});
```

---

## Lección 9: Migraciones de Base de Datos en Producción

### Migraciones Seguras de Base de Datos

```
Crea una estrategia segura de migración de BD:
1. Versiona todos los cambios de esquema
2. Escribe migraciones up y down
3. Prueba migraciones en staging primero
4. Haz backup antes de migrar
5. Ten plan de rollback
```

**Usando herramienta de migración:**
```typescript
// migrations/001_create_users_table.ts
export async function up(db) {
  await db.schema.createTable('users', (table) => {
    table.increments('id').primary();
    table.string('email').notNullable().unique();
    table.string('password_hash').notNullable();
    table.timestamps(true, true);
  });
}

export async function down(db) {
  await db.schema.dropTable('users');
}
```

**Ejecutando migraciones:**
```bash
# ¡Haz backup de BD primero!
pg_dump mydb > backup_$(date +%Y%m%d).sql

# Ejecuta migraciones
npm run migrate:latest

# Si algo sale mal, rollback
npm run migrate:rollback
```

---

## Práctica Práctica

### Ejercicio 1: Desplegar App Full-Stack

**Tarea:** Despliega una aplicación completa

```
Toma el proyecto del Módulo 9 y:
1. Prepáralo para producción
2. Configura configuración de entorno
3. Añade endpoints de health check
4. Crea configuración Docker
5. Despliega a tu plataforma elegida
6. Configura monitoreo
7. Prueba en producción
```

---

### Ejercicio 2: Pipeline CI/CD

**Tarea:** Configura despliegue automatizado

```
Crea un pipeline CI/CD que:
1. Ejecute tests en cada PR
2. Despliegue a staging al merge a develop
3. Despliegue a producción al merge a main
4. Envíe notificaciones si falla
5. Incluya migraciones de BD
```

---

### Ejercicio 3: Despliegue Zero-Downtime

**Tarea:** Implementa rolling deployment

```
Configura estrategia de despliegue que:
1. Mantenga versión anterior durante despliegue
2. Cambie tráfico gradualmente a nueva versión
3. Monitoree errores
4. Haga rollback automático si detecta problemas
5. Asegure zero downtime
```

---

## Lista de Verificación del Módulo 15

¡Felicidades por completar el curso! Asegúrate de poder:

- [ ] Preparar aplicaciones para producción
- [ ] Desplegar a varias plataformas
- [ ] Usar Docker para containerización
- [ ] Configurar pipelines CI/CD
- [ ] Configurar entornos apropiadamente
- [ ] Implementar monitoreo y logging
- [ ] Manejar migraciones de BD de forma segura
- [ ] Seguir mejores prácticas de seguridad

---

## Mejores Prácticas de Despliegue a Producción

**Antes de Cada Despliegue:**
- ✅ Ejecutar todos los tests
- ✅ Revisar cambios
- ✅ Hacer backup de BD
- ✅ Tener plan de rollback
- ✅ Desplegar durante horas de bajo tráfico
- ✅ Monitorear después del despliegue

**Seguridad:**
- ✅ Usar HTTPS en todas partes
- ✅ Mantener dependencias actualizadas
- ✅ No exponer detalles de error
- ✅ Usar headers de seguridad
- ✅ Rate limit en APIs
- ✅ Validar toda entrada

**Rendimiento:**
- ✅ Minificar y bundlear assets
- ✅ Habilitar compresión
- ✅ Usar CDN para archivos estáticos
- ✅ Cachear apropiadamente
- ✅ Monitorear rendimiento

---

## ¡Felicidades!

¡Has completado el curso **Claude Code para Principiantes**!

Ahora tienes las habilidades para:
- Construir aplicaciones con Claude Code
- Escribir código limpio y profesional
- Testear y depurar efectivamente
- Desplegar a producción
- Seguir mejores prácticas

**¿Qué sigue?**
- Construye proyectos reales
- Contribuye a código abierto
- Comparte tu conocimiento
- ¡Sigue aprendiendo!

---

*¡Curso Completado! ¡Feliz construcción con Claude Code!*
