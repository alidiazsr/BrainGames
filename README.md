# BrainGames - Configuración de Firebase

## 🚀 Configuración Rápida para Funcionar entre PCs

### 1. Crear proyecto en Firebase
1. Ve a [Firebase Console](https://console.firebase.google.com/)
2. Haz clic en "Crear un proyecto"
3. Nombra tu proyecto (ej: "braingames-quiz")
4. Desactiva Google Analytics (no es necesario)
5. Haz clic en "Crear proyecto"

### 2. Configurar Realtime Database
1. En la consola de Firebase, ve a "Realtime Database"
2. Haz clic en "Crear base de datos"
3. Selecciona una ubicación (ej: us-central1)
4. **IMPORTANTE**: Inicia en "Modo de prueba" (permite lecturas/escrituras durante 30 días)
5. Haz clic en "Listo"

### 3. Configurar reglas de seguridad
En la pestaña "Reglas", reemplaza el contenido con:

```json
{
  "rules": {
    "rooms": {
      ".read": true,
      ".write": true
    }
  }
}
```

### 4. Obtener configuración del proyecto
1. Ve a "Configuración del proyecto" (ícono de engranaje)
2. En la pestaña "General", baja hasta "Tus apps"
3. Haz clic en el ícono web `</>`
4. Registra la app con un nombre (ej: "BrainGames Web")
5. **COPIA** la configuración que aparece

### 5. Actualizar archivos con tu configuración

#### En `teacher.html` (línea ~422):
```javascript
const firebaseConfig = {
  apiKey: "tu-api-key-aqui",
  authDomain: "tu-proyecto.firebaseapp.com",
  databaseURL: "https://tu-proyecto-default-rtdb.firebaseio.com/",
  projectId: "tu-proyecto",
  storageBucket: "tu-proyecto.appspot.com",
  messagingSenderId: "123456789",
  appId: "tu-app-id-aqui"
};
```

#### En `student.html` (línea ~442):
```javascript
const firebaseConfig = {
  apiKey: "tu-api-key-aqui",
  authDomain: "tu-proyecto.firebaseapp.com", 
  databaseURL: "https://tu-proyecto-default-rtdb.firebaseio.com/",
  projectId: "tu-proyecto",
  storageBucket: "tu-proyecto.appspot.com",
  messagingSenderId: "123456789",
  appId: "tu-app-id-aqui"
};
```

## ✅ Probar la Comunicación Real

### Desde diferentes PCs:
1. **PC del Profesor**: Abre `teacher.html`, carga cuestionario, abre sala
2. **PC de Estudiantes**: Abre `student.html`, únete con el código de sala
3. **El profesor verá** a los estudiantes conectándose en tiempo real
4. **Inicia el cuestionario** y todos verán las preguntas sincronizadas

### Funcionalidades Sincronizadas ⚡:
- ✅ **Conexión de estudiantes** en tiempo real
- ✅ **Inicio del juego** coordinado
- ✅ **Preguntas simultáneas** con temporizador
- ✅ **Respuestas de estudiantes** enviadas al profesor
- ✅ **Rankings** actualizados en vivo
- ✅ **Avance de preguntas** controlado por el profesor

## 🛠️ Sin Firebase (Modo Local)

Si no configuras Firebase, el sistema funciona en modo local:
- ⚠️ Solo en la misma PC/red local
- ⚠️ Estudiantes no aparecen al profesor
- ⚠️ No hay sincronización real

## 📁 Estructura del proyecto

```
BrainGames/
├── index.html          # Página principal ✅
├── teacher.html        # Panel del profesor ✅
├── student.html        # Panel del estudiante ✅
├── example-quiz.json   # Cuestionario de ejemplo ✅
└── README.md          # Esta documentación ✅
```

## 🎯 Uso básico

1. **Configura Firebase** (una sola vez)
2. **Profesor**: Abre `teacher.html`, contraseña `profesor123`
3. **Carga cuestionario** JSON o usa el demo
4. **Abre sala** y comparte el código de 6 dígitos
5. **Estudiantes**: Abren `student.html` desde sus PCs
6. **Se unen** con nombre y código de sala
7. **Profesor ve** estudiantes conectándose
8. **Inicia el cuestionario** cuando todos estén listos
9. **Juegan en tiempo real** con preguntas sincronizadas

## 🌐 Desplegar Online (Opcional)

### GitHub Pages:
1. Sube todos los archivos a un repositorio de GitHub
2. Ve a Settings → Pages
3. Selecciona "Deploy from a branch" → main
4. Tu quiz estará en: `https://tu-usuario.github.io/tu-repositorio`

### Firebase Hosting:
```bash
npm install -g firebase-tools
firebase login
firebase init hosting
firebase deploy
```

## 🔧 Personalización

- **Contraseña profesor**: Cambia `profesor123` en `index.html`
- **Colores y diseño**: Modifica las variables CSS
- **Tiempo de preguntas**: Ajusta `timeLimit` en archivos JSON
- **Puntuación**: Modifica la fórmula en `selectAnswer`