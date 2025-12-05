# Finanzas.2 - Gestor de Finanzas con Google Sheets

App web sencilla para gestionar movimientos de caja y guardar datos **PERMANENTEMENTE** en Google Sheets.

## ✨ CARACTERÍSTICAS

✅ Interfaz bonita y responsive
✅ Agregar ingresos y egresos
✅ Calcular balance del día en tiempo real
✅ **Datos guardados PERMANENTEMENTE en Google Sheet**
✅ Sin problemas de CORS
✅ Funciona en cualquier navegador

## 🚀 CÓMO EMPEZAR

### Opción 1: Usar la app directamente (sin configuración)

Va a https://nickhere2.github.io/Finanzas.2/ y empieza a agregar movimientos. **NOTA:** Los datos se guardarán en memoria local pero SE PERDERÁN si limpias el cache.

### Opción 2: Configurar para guardar en Google Sheets (RECOMENDADO)

Para que los datos se guarden **PERMANENTEMENTE** en tu Google Sheet:

1. Lee el archivo `SETUP_GOOGLE_FORM.md` en este repositorio
2. Sigue los pasos para crear un Google Form
3. Actualiza el código con tus IDs
4. ¡Listo! Los datos se guardarán automáticamente

**⏱️ Tiempo estimado: 10 minutos**

## 📋 Requisitos

- Una cuenta de Google (para Google Sheets y Forms)
- Un navegador moderno
- Nada más

## 🔧 Configuración

Ver archivo: `SETUP_GOOGLE_FORM.md`

Este archivo contiene:
- Paso a paso para crear el Google Form
- Cómo obtener los Entry IDs
- Cómo actualizar la app
- Solución de problemas

## 📁 Estructura del proyecto

```
Finanzas.2/
├── index.html              # App principal
├── README.md               # Este archivo
└── SETUP_GOOGLE_FORM.md    # Guía de configuración (LÉEME PRIMERO)
```

## 🔐 Privacidad y Seguridad

- Los datos se guardan en TU Google Sheet personal
- La app NO guarda datos en servidores externos
- Usamos Google Forms para enviar datos (método seguro y confiable)
- Todo el código es JavaScript - puedes revisar qué hace

## 💡 Cómo funciona

1. **Frontend (tu navegador):** Interfaz para agregar movimientos
2. **Google Form:** Recibe y procesa los datos
3. **Google Sheet:** Almacena los datos de forma permanente

Este método **EVITA problemas de CORS** y garantiza que los datos se guarden siempre.

## 🆘 Problemas Comunes

**P: ¿Los datos se pierden si cierro el navegador?**
R: SÍ, a menos que hayas configurado el Google Form. Lee `SETUP_GOOGLE_FORM.md`

**P: ¿Puedo usar mi Google Sheet existente?**
R: SÍ, crea un Google Form, conéctalo a tu Sheet y luego copia los Entry IDs

**P: ¿Qué hago si aparece un error?**
R: Abre la consola (F12) y busca mensajes de error. Verifica que los Entry IDs sean correctos.

## 📞 Soporte

Si tienes problemas:
1. Verifica que todos los Entry IDs estén correctos
2. Abre la consola del navegador (F12) y busca errores
3. Asegúrate de que el Google Form esté conectado al Sheet

## 📄 Licencia

MIT - Usa libremente para tus proyectos
