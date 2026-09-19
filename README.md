# Tienda de apps de Umbrel de Mucho

Apps de [Mucho](https://mucho.finance) para umbrelOS.

## Cómo añadir esta tienda a tu Umbrel

1. Abre tu Umbrel → **App Store** → menú «⋯» (arriba a la derecha) →
   **Community App Stores**.
2. Pega esta dirección y pulsa **Add**:

   ```
   https://github.com/Blockchain-Networks-IO/mucho-umbrel-apps
   ```

3. Abre la tienda **Mucho** que aparece e instala la app que quieras.

## Apps

### Conector Mucho

Conecta tu nodo Bitcoin (la app **Mempool** de tu Umbrel) con
[Mucho Wallet](https://wallet.mucho.finance) para que el saldo, la actividad,
las comisiones y el envío de bitcoin salgan de **tu** nodo, desde cualquier
navegador y estés donde estés.

- Es tu nodo el que abre una conexión saliente hacia Mucho: sin abrir puertos,
  sin dominio, sin certificados.
- Cada consulta y cada respuesta viajan **cifradas de extremo a extremo** entre
  tu navegador y este conector. El servidor de Mucho solo ve sobres cerrados,
  nunca tus direcciones.
- Solo atiende lecturas de la API de Mempool y la difusión de transacciones ya
  firmadas. Nunca firma nada ni tiene acceso a tus llaves.

**Cómo se usa:** en Mucho Wallet ve a «Mi wallet» › Conexiones › Conector Mucho
y pulsa «Vincular mi nodo». Copia el código que aparece y pégalo en la app del
conector. En unos segundos el monedero dirá «en línea».

Requiere la app **Mempool** instalada en el mismo Umbrel.

**¿Tu nodo no es de Umbrel?** El conector es un contenedor Docker normal:

```
docker run -d --name mucho-conector --restart unless-stopped \
  -p 3040:3040 -v mucho-conector-data:/data \
  -e NODE_API_BASE=http://<ip-del-nodo>:3006/api \
  ghcr.io/blockchain-networks-io/mucho-conector:latest
```

Abre `http://<esa máquina>:3040` y pega ahí el mismo código.

---

Código fuente del conector y del monedero:
[mucho-wallet](https://github.com/Blockchain-Networks-IO/mucho-wallet)
(carpeta `connector/`; esta tienda se mantiene desde `umbrel-store/`).
Incidencias: [issues](https://github.com/Blockchain-Networks-IO/mucho-umbrel-apps/issues).
