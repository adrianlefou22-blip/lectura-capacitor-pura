# Lectura Pura — Capacitor Android App

Tu biblioteca personal con voz. Lee PDF, TXT y EPUB sin publicidad.

---

## ⚡ Cómo generar el APK desde GitHub (sin instalar nada)

### 1. Subir este proyecto a GitHub
1. Creá un repositorio nuevo en [github.com](https://github.com) (puede ser privado)
2. Subí todos estos archivos al repositorio (arrastrá la carpeta o usá `git push`)

### 2. El APK se genera automáticamente
- Cada vez que hacés un `push` a la rama `main`, GitHub Actions compila el APK solo
- Entrá a tu repositorio → pestaña **Actions** → workflow **Build APK**
- Esperá ~5 minutos a que termine (ícono verde ✅)
- Bajá el APK desde **Artifacts → lectura-pura-debug.apk**

### 3. También podés ejecutarlo manualmente
- Entrá a **Actions → Build APK → Run workflow**

---

## 🛠 Para compilar localmente (opcional)

### Requisitos
- Node.js 18+
- JDK 17
- Android Studio (o solo Android SDK)

### Pasos
```bash
# 1. Instalar dependencias
npm install

# 2. Sincronizar Capacitor
npx cap sync android

# 3. Compilar APK debug
cd android
./gradlew assembleDebug

# El APK queda en:
# android/app/build/outputs/apk/debug/app-debug.apk
```

---

## 📁 Estructura del proyecto

```
lectura-pura-capacitor/
├── www/                      ← Tu app HTML (index.html, sw.js, etc.)
├── capacitor.config.json     ← Configuración de Capacitor
├── package.json
├── android/
│   ├── app/
│   │   └── src/main/
│   │       ├── AndroidManifest.xml
│   │       ├── java/com/lecturapura/app/MainActivity.java
│   │       └── res/
│   │           ├── mipmap-*/   ← Íconos en todos los tamaños
│   │           ├── values/     ← strings, colors, styles
│   │           └── xml/        ← file_paths, network_security
│   └── build.gradle
└── .github/workflows/
    └── build-apk.yml          ← GitHub Actions (compila el APK)
```

---

## 🎨 Ícono

El ícono está diseñado con fondo plano (sin esquinas redondeadas propias) para que Android aplique correctamente su máscara Adaptive Icon en todos los launchers. Los archivos están en:

- `android/app/src/main/res/mipmap-*/ic_launcher.png`
- `android/app/src/main/res/mipmap-*/ic_launcher_round.png`
- `android/app/src/main/res/mipmap-*/ic_launcher_foreground.png`
- `android/app/src/main/res/mipmap-anydpi-v26/ic_launcher.xml` (Adaptive Icon)

---

## 📦 App Info

| Campo | Valor |
|-------|-------|
| App ID | `com.lecturapura.app` |
| Version | 1.0.0 |
| Min SDK | 22 (Android 5.1+) |
| Target SDK | 34 (Android 14) |
| Orientación | Portrait |
