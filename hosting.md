# Hostear shark-filter en un servidor (acceso por URL)

Por defecto shark-filter corre solo en tu PC (`http://127.0.0.1:8765`) y no pide contraseña.
Si quieres entrar desde cualquier lugar por una URL, puedes hostearlo en un servidor gratis y
protegerlo con una contraseña. La conexión segura (HTTPS) la entrega un túnel de Cloudflare.

## 1. Conseguir una VM gratis

Crea una máquina virtual en un proveedor con capa gratuita (por ejemplo **Oracle Cloud Free
Tier**). Anota su IP y entra por SSH. Sube el binario `shark-filter_linux_amd64`
(o `_arm64` según la VM) y dale permisos:

    chmod +x shark-filter_linux_amd64

Inicia sesión en Telegram una vez (sigue las instrucciones en pantalla / la UI local):

    ./shark-filter_linux_amd64 login --phone +569XXXXXXXX

## 2. Correrlo como servicio (systemd)

Crea `/etc/systemd/system/shark-filter.service`:

    [Unit]
    Description=shark-filter
    After=network-online.target

    [Service]
    ExecStart=/root/shark-filter_linux_amd64 ui --addr 0.0.0.0:8765 --trust-proxy
    Restart=always
    User=root

    [Install]
    WantedBy=multi-user.target

`--trust-proxy` hace que el límite de intentos use la IP real que entrega el túnel.
Actívalo y arráncalo:

    systemctl daemon-reload
    systemctl enable --now shark-filter

## 3. Exponerlo con un túnel de Cloudflare (HTTPS gratis, sin abrir puertos)

Instala `cloudflared` y levanta un túnel rápido apuntando al puerto local:

    cloudflared tunnel --url http://localhost:8765

Te entregará una URL `https://....trycloudflare.com`. Esa es tu dirección de acceso.
(Para una URL fija puedes crear un túnel con nombre y tu dominio; ver la doc de Cloudflare.)

## 4. Crear tu contraseña (primera vez)

Abre la URL del túnel. La primera vez te llevará a la pantalla **Crear contraseña**.
Como es un servidor público, te pedirá un **token de configuración**: aparece en la consola del
servidor al iniciar. Míralo con:

    journalctl -u shark-filter -n 20

Copia el token, defínelo junto a tu contraseña (mínimo 8 caracteres) y listo. Desde ahí
entras solo con tu contraseña.

> Alternativa: define la variable `SHARK_UI_PASSWORD` en el servicio para fijar la contraseña
> sin pantalla de configuración (útil para automatizar).

## Nota de seguridad

Al hostearlo, tu sesión de Telegram y el token de tu bot viven en la VM, y la contraseña del UI
es el guardia principal: usa una contraseña larga y no compartas la URL. El acceso está limitado
contra ataques de fuerza bruta (intentos por IP + un tope global), pero nada reemplaza una buena
contraseña. Si no necesitas acceso remoto, simplemente corre shark-filter en tu PC sin contraseña.
