# Cambios: Cuadrangular en IceFire
- Pestaña **Equipos**: ahora hay botón "4 Equipos". Al repartir (equilibrado por posición y OVR, incluida defensa) aparece **Iniciar cuadrangular**.
- **Cuadrangular en vivo**: ronda 1 = A-B y C-D; después, cancha 1 = ganadores vs ganadores y cancha 2 = perdedores vs perdedores. Se repite hasta que el admin pulsa **Terminar**, que publica la tabla en el muro.
- Suma victorias/derrotas a los perfiles (igual que el triangular). **Deshacer último** las resta.
- Nueva colección `quads` en Firestore. **IMPORTANTE:** pega `firestore.rules` en Firebase (Firestore → Reglas → Publicar); sin eso el cuadrangular no podrá guardar.

## Corrección de rondas (cuadrangular)
Cada vuelta tiene 3 rondas: 1) A-B y C-D · 2) ganadores vs ganadores y perdedores vs perdedores · 3) los cruces que faltan (así todos juegan contra todos). Luego vuelve a empezar la ronda 1 hasta que el admin pulse Terminar (fin de la hora alquilada).
- Cuentas del cuadrangular: siempre S/ 3 por cabeza en cada partido (cada perdedor paga 3, cada ganador cobra 3); si los equipos son desiguales se muestra la diferencia. Saldo por jugador y quién le paga a quién.

## Cuadrangular con tus nombres y cartas
- En la pestaña **Equipos** (solo admin, cuando no hay cuadrangular en curso) aparece **✍️ Cuadrangular con mis nombres**: escribes o pegas los nombres (sirve la lista de WhatsApp con números y emojis), pones el nombre de cada equipo y listo.
- Los nombres que coinciden con un jugador registrado traen su carta (posición y OVR). A los demás les pones posición y nivel ★1-5.
- Reparte en 4 equipos parejos (mismo número de jugadores, posiciones repartidas y nivel total parecido) y empieza el cuadrangular.
- Cada equipo muestra sus **cartas** (nombre · posición · ⭐). El admin puede cambiar el nombre de un equipo con ✏️.

## Invitados con nivel y traer convocados de la pichanga
- Al anotar un **invitado** en una pichanga (admin) ahora eliges también su **nivel ★1-5**, además de la posición. En la lista de convocados el admin puede cambiar su nivel con el selector ★ (los demás lo ven como ★n).
- El nivel del invitado se usa en el **reparto equilibrado** de la pestaña Equipos (se guarda como habilidades iguales; si ya lo calibraste en detalle, se respeta hasta que cambies el nivel).
- En **Cuadrangular con mis nombres** hay un selector **📥 Traer convocados de una pichanga** que carga a los registrados y a los invitados con su posición y nivel.

## Invitados frecuentes
- Cada invitado que anotes (con posición y nivel) o cuyo nivel/posición cambies queda guardado en la colección `guests`. También se guardan los que pones en **Cuadrangular con mis nombres**.
- Al escribir su nombre en "Anotar invitado" aparece la lista de guardados y se rellenan solos su posición y nivel. En el cuadrangular con nombres también se rellenan solos.
- Nueva regla `guests` en `firestore.rules`: **vuelve a publicarla en Firebase** (Firestore → Reglas → Publicar).

## Pestaña Cartas
- Nueva pestaña **Cartas** (junto a Plantel): todos los jugadores como cartas (número tipo FIFA, posición y 5 barras de habilidades). Incluye a los registrados y a los invitados guardados, con buscador.
- El admin puede **➕ Nueva carta** (nombre, posición y las 5 habilidades de 1 a 5), **✏️ editar** y **✕ borrar** las cartas de invitados. Los registrados se editan desde su perfil.
- Esas cartas se guardan en `guests` (misma regla ya incluida en `firestore.rules`) y se usan solas al anotar invitados en una pichanga y al armar el cuadrangular con nombres.

## Foto en las cartas
- Al crear o editar una carta de invitado puedes **📷 poner una foto** (se reduce sola a un tamaño pequeño). Las cartas muestran la foto en grande; los registrados usan la foto de su perfil, y si no tienen, su avatar.

## Todo por S/ 3: triangular, individual y tardanza
- **Triangular:** ahora tiene sección **💰 Cuentas**: S/ 3 por cabeza en cada partido (cada perdedor paga 3, cada ganador cobra 3), saldo por jugador y quién le paga a quién.
- **Individual** (pestaña Equipos, solo admin): jugadores con sets ganados/perdidos y botón de **⏰ tardanza**. Cada set vale S/ 3 (ganado suma, perdido resta) y la tardanza resta S/ 3. Hay grupos (G1 a G6) con botones "+ Set ganado/perdido (todos)", liquidación por WhatsApp y Reiniciar. Se guarda en la colección `indiv`.
- Nueva regla `indiv` en `firestore.rules`: **publícala otra vez en Firebase**.

## Cartas: marcar quién irá a la pichanga
- En la pestaña **Cartas** (admin) hay un selector de pichanga próxima y cada carta tiene el botón **➕ Irá** / **✅ Irá (quitar)**. Sirve para registrados e invitados (los invitados necesitan posición en su carta). Muestra cuántos irán.
