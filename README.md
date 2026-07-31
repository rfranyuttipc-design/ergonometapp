# ErgonometApp v5.1

**Sistema de Evaluación Ergonómica Profesional**  
Métodos: Ley Silla DOF 17/07/2025 | REBA | LEST  
RFranyutti - Conciencia Verde y Laboral S.C.

---

## ✨ NOVEDADES EN v5.1

### 🎯 Reportes Word Completamente Rediseñados

La función `generate_docx()` fue completamente reescrita de **133 líneas → 620 líneas**:

✅ **Portada profesional** con encabezado corporativo  
✅ **Resumen ejecutivo** con tabla de riesgos coloreada  
✅ **11 secciones estructuradas** y bien organizadas  
✅ **Tablas profesionales** con colores dinámicos:
   - 🔴 Rojo para riesgo ALTO/MUY ALTO
   - 🟠 Naranja para riesgo MEDIO/MOLESTO
   - 🟢 Verde para riesgo BAJO/ACEPTABLE

✅ **Conclusiones dinámicas** generadas automáticamente  
✅ **Validación formal** con tabla de firmas estructurada  
✅ **Trazabilidad completa** con folio único  
✅ **Formato profesional** Calibri justificado, márgenes corporativos

---

## 🚀 Quick Start

### Requisitos
- Python 3.8+
- pip (gestor de paquetes)

### Instalación Local

```bash
# 1. Clonar repositorio
git clone https://github.com/rfranyuttipc-design/ergonometapp.git
cd ergonometapp

# 2. Crear ambiente virtual (opcional pero recomendado)
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate

# 3. Instalar dependencias
pip install -r requirements.txt

# 4. Crear carpetas necesarias
mkdir -p database reports uploads static/images

# 5. Ejecutar app
python app.py

# 6. Abrir navegador
# http://localhost:5000
```

---

## 🌐 Deploy a Render.com

### Opción 1: Conectar GitHub directamente (Recomendado)

1. **En tu repositorio GitHub:**
   - Asegúrate que `build.sh`, `render.yaml`, `requirements.txt` y `app.py` estén commiteados
   ```bash
   git add .
   git commit -m "v5.1: Reportes Word profesionales"
   git push origin main
   ```

2. **En Render.com:**
   - Ve a [render.com](https://render.com)
   - Conecta tu cuenta GitHub
   - Crea nuevo "Web Service"
   - Selecciona tu repositorio `ergonometapp`
   - Render detectará automáticamente `render.yaml`
   - Click en "Deploy"

3. **Listo:**
   - Tu app estará en vivo en minutos
   - Puedes generar reportes Word desde la UI

### Opción 2: Deploy manual

```bash
# En tu máquina local:
git add .
git commit -m "v5.1: Reportes Word profesionales"
git push heroku main
# (O usa Render CLI)
```

---

## 📊 Estructura de Archivos

```
ergonometapp/
├── app.py                 ← App principal (1813 líneas, mejorado)
├── requirements.txt       ← Dependencias Python
├── build.sh              ← Script de build para Render
├── render.yaml           ← Configuración Render
├── README.md             ← Este archivo
├── database/             ← Base de datos SQLite (creado auto)
├── reports/              ← Reportes generados (creado auto)
├── uploads/              ← Archivos subidos (creado auto)
└── static/
    └── images/           ← Imágenes estáticas (creado auto)
```

---

## 🔑 Características Principales

### Evaluación Ergonómica

✅ **Métodos soportados:**
- Ley Silla DOF 17/07/2025 (Bipedestación)
- REBA (Rapid Entire Body Assessment)
- LEST (List of Ergonomic Tasks)

✅ **Análisis técnico:**
- Captura de pose con MediaPipe
- Cálculo automático de ángulos corporales
- Puntuación integrada de riesgos
- Recomendaciones inteligentes

### Generación de Reportes

✅ **Formatos exportables:**
- 📄 **DOCX** (Word profesional) ← MEJORADO EN v5.1
- 📊 **XLSX** (Excel con gráficos)
- 📑 **PDF** (Formato imprimible)

✅ **Reportes Word v5.1 incluyen:**
- Portada corporativa con información general
- Resumen ejecutivo de riesgos
- Sección datos generales del trabajador
- Espacio para fotografías del puesto
- Evaluación Ley Silla con detalles
- Evaluación REBA (Grupo A + Grupo B)
- Evaluación LEST (5 dimensiones)
- Tabla comparativa de métodos
- Recomendaciones por prioridad (coloreadas)
- Conclusiones dinámicas basadas en resultados
- Tabla de validación con firmas
- Folio único para trazabilidad

### Seguridad

✅ **Autenticación:**
- Código de registro maestro
- Roles: Director | Auditor
- Sesiones seguras (HTTPONLY, SAMESITE)

✅ **Datos:**
- Base de datos SQLite encriptada
- Permisos por usuario
- Auditoría de cambios

---

## 📝 Uso

### 1. Registro

```
URL: http://localhost:5000/register
Código: RFRANYUTTI2025  (Cambiar en app.py línea 18)
```

### 2. Login

```
Usuario: [el que registraste]
Contraseña: [la que creaste]
```

### 3. Crear Evaluación

- Dashboard → "Nueva Evaluación"
- Llenar datos generales
- Capturar pose con cámara (MediaPipe)
- Evaluar métodos: Ley Silla, REBA, LEST
- Generar reporte Word/Excel/PDF

### 4. Descargar Reportes

- Dashboard → Historial
- Seleccionar evaluación
- Botón "Descargar DOCX" / "XLSX" / "PDF"

---

## 🎨 Personalización

### Cambiar código de registro

Línea 18 en `app.py`:
```python
MASTER_REGISTRATION_CODE = 'TU_CODIGO_AQUI'
```

### Cambiar nombre de empresa

En función `generate_docx()` (línea ~850):
```python
run = p_company.add_run('TU EMPRESA S.C.')
```

### Cambiar colores corporativos

En función `generate_docx()` (líneas ~33-36):
```python
COLOR_PRIMARY = 'FFE7E6E6'        # Tu color
COLOR_HEADER_DANGER = 'FFCB2028'  # Rojo alto riesgo
COLOR_HEADER_WARNING = 'FFFFB84D' # Naranja medio riesgo
COLOR_HEADER_SUCCESS = 'FF70AD47' # Verde bajo riesgo
```

---

## 🔧 Tecnología

- **Backend:** Flask 2.3.3
- **Base de datos:** SQLite
- **Reportes:** python-docx, openpyxl, reportlab
- **Análisis pose:** MediaPipe
- **Server:** Gunicorn (Render.com)

---

## 📋 Cambios v5.1 vs v5.0

| Característica | v5.0 | v5.1 |
|---|---|---|
| **generate_docx()** | 133 líneas | 620 líneas |
| **Portada** | Básica | Profesional |
| **Secciones** | 5 | 11 |
| **Colores** | NO | Dinámicos (R/A/V) |
| **Conclusiones** | NO | Auto-generadas |
| **Imagen** | "Casero" | Profesional |
| **Compatibilidad** | - | 100% backward |

---

## 🐛 Troubleshooting

### Error: "ModuleNotFoundError: No module named 'docx'"

```bash
pip install python-docx --break-system-packages
pip install -r requirements.txt
```

### Error: "Permission denied: build.sh"

```bash
chmod +x build.sh
```

### Reporte no genera

Verifica que:
- ✅ Database folder existe: `mkdir -p database`
- ✅ Reports folder existe: `mkdir -p reports`
- ✅ Evaluación tiene datos completos
- ✅ No hay campos NULL en base de datos

### Colores en Word no se ven

- Usa Word 2010+ o versión moderna de LibreOffice
- Algunos navegadores pueden no renderizar colores en preview

---

## 📞 Soporte

Para problemas o sugerencias:
1. Revisa logs: `tail -f app.log` (si existe)
2. Verifica structure: `ls -la database reports uploads`
3. Prueba localmente primero antes de desplegar a Render

---

## 📄 Documentación Técnica

Ver código comentado en `app.py`:
- Líneas 1-100: Configuración e importaciones
- Líneas 700-1330: Función `generate_docx()` profesional
- Líneas 1330+: Rutas Flask y endpoints

---

## 📜 Licencia

Conciencia Verde y Laboral S.C.  
Derechos reservados. Uso profesional.

---

## ✅ Checklist de Deploy

- [ ] Git repo está actualizado
- [ ] `app.py` tiene 1813 líneas
- [ ] `requirements.txt` está presente
- [ ] `render.yaml` está presente
- [ ] `build.sh` es ejecutable
- [ ] Código de registro es secreto (no en GitHub)
- [ ] Probé localmente: `python app.py`
- [ ] Generé reporte Word test
- [ ] Subí a GitHub: `git push origin main`
- [ ] Render detectó cambios y desplegó
- [ ] App funciona en Render: `https://tu-app.onrender.com`

---

**Versión:** 5.1  
**Fecha:** 30/07/2026  
**Status:** ✅ Producción  

🎉 **¡Lista para usar!**

