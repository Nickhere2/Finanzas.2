# Finanzas.2 - Gestor de Finanzas con Google Sheets

App web sencilla para gestionar movimientos de caja y guardar datos directamente en Google Sheets.

## ¿Qué necesitas?

1. Un Google Sheet (hoja de cálculos)
2. Un Google Apps Script conectado a ese Sheet
3. Esta web app (index.html)

## Paso 1: Crear el Google Sheet

1. Ve a [Google Sheets](https://sheets.google.com/)
2. Crea una nueva hoja
3. Copia el ID del Sheet (en la URL: `https://docs.google.com/spreadsheets/d/ID_AQUI/edit`)

## Paso 2: Crear el Google Apps Script

1. En tu Google Sheet, ve a: **Extensiones > Apps Script**
2. Reemplaza todo el código con esto:

```javascript
const SHEET_NAME = 'Movimientos';

function doGet() {
  return HtmlService.createHtmlOutput('Web app del Google Sheets conectada');
}

function doPost(e) {
  try {
    const sheet = SpreadsheetApp.getActiveSheet();
    const data = JSON.parse(e.postData.contents);
    
    // Añadir fila con los datos
    sheet.appendRow([
      data.date,
      data.type,
      data.amount,
      data.category,
      data.note
    ]);
    
    return ContentService.createTextOutput(JSON.stringify({ok: true})).setMimeType(ContentService.MimeType.JSON);
  } catch (error) {
    return ContentService.createTextOutput(JSON.stringify({ok: false, error: error.toString()})).setMimeType(ContentService.MimeType.JSON);
  }
}

function getData() {
  const sheet = SpreadsheetApp.getActiveSheet();
  const data = sheet.getDataRange().getValues();
  return data;
}
```

3. Guarda el proyecto
4. Ve a **Desplegar > Nuevo despliegue**
5. Selecciona "Aplicación web"
6. Elige "Ejecutar como: [tu email]"
7. "Ejecutar como: Cualquiera"
8. Copia la URL que te da (sera como: `https://script.google.com/macros/d/.../usercontent`)

## Paso 3: Configurar en la Web App

1. Abre el archivo `index.html` en tu navegador
2. Haz clic en el icono de engranaje (settings)
3. Pega:
   - **ID del Google Sheet**: El ID que copiaste en el Paso 1
   - **URL de Apps Script**: La URL del despliegue del Paso 2
4. Guarda

## Uso

- **+** Boton flotante: Agregar un nuevo movimiento
- **Resúmen**: Ve tu balance diario, mensual y proyección
- **Historial**: Tabla con todos los movimientos registrados
- **Engranaje**: Cambiar configuración

## Notas

- Los datos se guardan localmente primero y se sincronizan con Google Sheets
- Si Google Sheets no está disponible, los datos se mantienen localmente
- El Apps Script debe estar "Activo" para que funcione

## Customización

Puedes editar `index.html` para:
- Cambiar colores
- Agregar más campos
- Modificar categorías

---

**Creado por:** [Tu nombre]
**Última actualización:** Diciembre 2024
