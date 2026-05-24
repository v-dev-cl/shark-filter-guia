# 🦈 shark-filter — Guía de uso

**shark-filter** es una herramienta que filtra las ofertas de OfertasShark en tu propio
computador. Inicia sesión con tu cuenta de Telegram, elige qué canales seguir, define tus
filtros y recibe **solo las ofertas que te interesan** — por tu propio bot y/o en tus Mensajes
Guardados.

> Todo corre **localmente** en tu equipo. Tus credenciales nunca salen de tu computador.

---

## 1. Descarga

Descarga el archivo para tu sistema operativo desde la última versión:

- **Windows:** `shark-filter_windows_amd64.exe`
- **macOS:** `shark-filter_darwin_arm64` (Apple Silicon) o `shark-filter_darwin_amd64` (Intel)
- **Linux:** `shark-filter_linux_amd64` o `shark-filter_linux_arm64`

> 📥 Enlace de descarga: **`<COMPLETAR_CON_EL_ENLACE_DE_DESCARGA>`**

---

## 2. Abrir la aplicación

### Windows
1. Haz **doble clic** en `shark-filter.exe`. Se abre tu navegador con la configuración.
2. La primera vez, Windows puede mostrar *"Windows protegió tu PC"* (la app no está firmada):
   haz clic en **Más información → Ejecutar de todas formas**.
3. Se abre una pequeña ventana negra (consola) mientras la app funciona. **Para detenerla, cierra
   esa ventana.**

### macOS
1. La primera vez, haz **clic derecho → Abrir** (para saltar el aviso de Gatekeeper).
2. Si no se abre el navegador solo, entra a **http://127.0.0.1:8765**.

### Linux
Ejecuta el binario desde la terminal:
```bash
chmod +x shark-filter_linux_amd64
./shark-filter_linux_amd64
```

En todos los casos se abre la interfaz en **http://127.0.0.1:8765**.

---

## 3. Iniciar sesión

> Si ya iniciaste sesión antes, la app **reanuda tu sesión automáticamente** y no te pide nada.

1. En **01 · Acceso**, escribe tu número de teléfono (formato internacional, ej.
   `+569XXXXXXXX`) y presiona **Enviar código**.
2. Telegram te envía el código **dentro de la app de Telegram** (un mensaje del servicio
   "Telegram"), **no por SMS**. Cópialo, pégalo y presiona **Confirmar código**.
3. Si tu cuenta tiene **verificación en dos pasos (2FA)**, ingresa tu contraseña de la nube y
   presiona **Confirmar contraseña**.

Cuando el estado arriba a la derecha diga **Conectado**, verás tu cuenta y la lista de canales.

---

## 4. Elegir canales

En **02 · Canales** aparecen los canales de OfertasShark a los que perteneces.

- Marca los canales que quieres seguir y elige su **moneda** (CLP, ARS, MXN, COP, USD).
- Usa el **buscador** para encontrar un canal rápido (búsqueda tolerante: "nke" encuentra "Nike").
- El contador **"N activos"** y la opción **"Solo activos"** te muestran qué tienes seleccionado.
- Presiona **Guardar canales**.

---

## 5. Crear filtros

En **03 · Filtros** defines qué ofertas quieres recibir. Cada filtro puede combinar:

- **Palabras** (separadas por coma): nombre, marca o tienda — ej. `nike, lego`.
- **Precio máximo**.
- **Descuento mínimo (%)**.
- **Criterio IA** (opcional, ver punto 7).

Presiona **Agregar / actualizar filtro**. Recibirás una oferta si cumple **cualquiera** de tus
filtros.

- **Editar:** toca el nombre del filtro para cargarlo en el formulario; guarda con el mismo
  nombre para actualizarlo.
- **Pausar / activar:** usa el **interruptor** de cada filtro. Un filtro pausado deja de avisarte
  **sin borrarlo**.
- **Eliminar:** usa la **✕**.

---

## 6. Cómo quieres recibir las ofertas

En **04 · Entrega** elige uno o ambos métodos:

- **Notificación por bot (push):** recibe un aviso real en Telegram.
  1. Abre **@BotFather** en Telegram, crea un bot y copia su **token**.
  2. Pega el token y presiona **Iniciar** en tu bot una vez.
- **Mensajes Guardados:** se reenvía una copia a tus *Mensajes Guardados* (sirve de archivo).

Presiona **Guardar entrega**.

---

## 7. Filtro con IA (opcional)

En **05 · Filtro IA** puedes pedir que una IA evalúe cada oferta con un criterio en lenguaje
natural (ej. *"solo notebooks gamer con RTX 40-series"*). Funciona con:

- **Un modelo local** (privado, gratis): ej. Ollama → URL base `http://localhost:11434/v1`,
  modelo `llama3.1`, sin clave.
- **OpenAI / compatible:** URL base `https://api.openai.com/v1`, tu modelo y tu API key.

La IA solo se ejecuta sobre las ofertas que ya pasaron tus filtros normales, así que es rápida y
económica.

---

## 8. Dejarlo funcionando

- Mantén la app **abierta** para recibir ofertas.
- Cada vez que guardas algo, aparece una **notificación** (verde = ok, roja = error).
- Para detenerla: cierra la ventana (Windows) o presiona `Ctrl-C` en la terminal (macOS/Linux).

---

## Privacidad y seguridad

- Todo se ejecuta en tu equipo; tus mensajes y credenciales **no se envían a ningún servidor**.
- Tu sesión de Telegram y los tokens se guardan **cifrados** en tu computador.
- Solo procesa mensajes de OfertasShark.

## ¿Problemas?

Si algo falla, el estado arriba a la derecha y la ventana de consola muestran el error. Anótalo y
escríbenos a **`<COMPLETAR_CON_CONTACTO_DE_SOPORTE>`**.
