# CONFIGURACIÓN DE GOOGLE FORM PARA GUARDAR DATOS

## PASO 1: Crear un Google Form

1. Ve a https://forms.google.com
2. Haz clic en "+ Crear nuevo formulario"
3. Dale un nombre como "Finanzas App"
4. Selecciona FORMULARIO EN BLANCO

## PASO 2: Crear los campos del formulario

Vas a crear 4 preguntas (iguales al Google Sheet):

### Campo 1: FECHA
- Tipo: Respuesta breve
- Título: "Fecha"
- Haz clic en los 3 puntos > Copiar ID de pregunta (ej: 1234567890)
- GUARDA ESTE NÚMERO

### Campo 2: TIPO
- Tipo: Respuesta breve
- Título: "Tipo"
- Copiar ID de pregunta (ej: 1234567891)
- GUARDA ESTE NÚMERO

### Campo 3: MONTO
- Tipo: Respuesta breve
- Título: "Monto"
- Copiar ID de pregunta (ej: 1234567892)
- GUARDA ESTE NÚMERO

### Campo 4: NOTA
- Tipo: Respuesta breve
- Título: "Nota"
- Copiar ID de pregunta (ej: 1234567893)
- GUARDA ESTE NÚMERO

## PASO 3: Obtener tu URL del formulario

1. En el formulario, haz clic en "Enviar" (botón superior derecha)
2. Copia el LINK del formulario
3. Será algo como: https://docs.google.com/forms/d/e/1FAIpQLSc_XXXXXXXXXXXX/viewform

## PASO 4: Actualizar index.html

Abre el archivo index.html y busca:

```javascript
const GOOGLE_FORM_URL = 'https://docs.google.com/forms/d/e/1FAIpQLSc-test-URL-HERE/formResponse';
```

**Reemplaza:**
- `1FAIpQLSc-test-URL-HERE` con el ID de tu formulario (de la URL del paso 3)
- El URL debe terminar en `/formResponse` (no en `/viewform`)

Ejemplo final:
```javascript
const GOOGLE_FORM_URL = 'https://docs.google.com/forms/d/e/1FAIpQLSc_XXXXXXXX/formResponse';
```

## PASO 5: Actualizar los Entry IDs

Busca estas líneas en index.html:

```javascript
formData.append('entry.1234567890', data.date);      // Reemplaza 1234567890 con tu Entry ID de Fecha
formData.append('entry.1234567891', data.type);      // Reemplaza 1234567891 con tu Entry ID de Tipo
formData.append('entry.1234567892', data.amount);    // Reemplaza 1234567892 con tu Entry ID de Monto
formData.append('entry.1234567893', data.note);      // Reemplaza 1234567893 con tu Entry ID de Nota
```

**Y también estas líneas:**

```javascript
img.src = GOOGLE_FORM_URL + '?' + new URLSearchParams({
  'entry.1234567890': data.date,
  'entry.1234567891': data.type,
  'entry.1234567892': data.amount,
  'entry.1234567893': data.note
}).toString();
```

Reemplaza cada `entry.XXXXXXXX` con tus Entry IDs del Paso 2.

## PASO 6: Guardar y probar

1. Guarda los cambios en GitHub
2. La página se actualizará automáticamente
3. Agrega un movimiento en la app
4. Abre tu Google Sheet y verás que aparece el dato (puede tardar 30 segundos)

## VENTAJAS DE ESTE MÉTODO:

✅ NO tiene problemas de CORS
✅ Funciona desde cualquier navegador
✅ Google garantiza que los datos se guardan
✅ Automáticamente se vinculan al Google Sheet
✅ Los datos se guardan PERMANENTEMENTE

## TROUBLESHOOTING:

**¿Los datos no aparecen en el Sheet?**
- Verifica que el Google Form esté conectado al Sheet correctamente
- En el Form, ve a "Respuestas" y haz clic en el ícono de Google Sheets
- Verifica que los Entry IDs sean exactamente iguales a los del formulario

**¿Cómo verificar los Entry IDs correctos?**
- Abre el formulario en modo edición
- Haz clic en cada pregunta
- Haz clic en los 3 puntos (⋮) > "Copiar ID de pregunta"
