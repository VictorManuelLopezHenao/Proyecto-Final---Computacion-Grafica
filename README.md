# Proyecto-Final---Computacion-Grafica

## “Antivirus vs Malware”

**Concepto:** eres un programa antivirus dentro de un sistema infectado. Debes limpiar tres zonas del sistema y destruir al jefe final. Es un shooter 2D de scroll vertical u horizontal, el que prefieran.

**Intro (Req-6):** 3 o 4 pantallas con texto. Por ejemplo: “Un ransomware infectó el servidor de la universidad. Eres el último antivirus activo. Limpia el sistema antes de que cifre todo.”

### Niveles

|Nivel|Fondo|Mecánicas (Req-5)|Enemigos|
|---|---|---|---|
|**1. Red local**|Tonos azules, líneas de circuito|1. Mover y disparar  <br>2. Esquivar enemigos  <br>3. Recoger “parches” (+puntos)|**Bug:** baja en línea recta|
|**2. Servidor**|Tonos verdes, racks y cables|1. Enemigos que te persiguen  <br>2. Power-up de escudo (absorbe un golpe)  <br>3. Disparo doble temporal|**Troyano:** te sigue lento  <br>**Gusano:** zigzag|
|**3. Núcleo del sistema**|Tonos rojos, código|1. Enemigos que disparan  <br>2. Zonas dañinas (corrupción) en el suelo o los lados  <br>3. Power-up de velocidad|**Spyware:** dispara  <br>**Virus:** rápido y frágil|

Los tres niveles reutilizan el mismo código de jugador y de enemigos. Lo que cambia es el prefab, el fondo y la configuración de cada nivel.

### Jefe final: “Ransomware” (Req-10)

Mecánica distinta a los enemigos normales:

- **Fase 1:** dispara en patrón de abanico.
- **Fase 2 (al bajar de 50% de vida):** “cifra” una zona de la pantalla (un rectángulo que bloquea tu movimiento o hace daño) y cambia de lugar cada pocos segundos.
- **Fase 3 (opcional):** invoca minions.
- Lleva barra de vida en el HUD.

### Vidas y puntos (Req-3 y 4)

- **Puntos:** bug = 10, troyano = 25, etc., más los parches recolectados. Se muestran en el HUD y se conservan entre niveles.
- **Vidas:** empiezas con 3. Pierdes una al chocar con un enemigo, recibir una bala o tocar una zona dañina. Al respawnear tienes unos segundos de invulnerabilidad (parpadeo). Con 0 vidas aparece `GameOver`.

### Sprites (Req-1)

Con 12 a 14 sprites sobra:

- Jugador
- Bug, troyano, gusano, spyware, virus (5 enemigos)
- Jefe
- Bala del jugador y bala enemiga
- Power-ups (escudo, disparo doble, velocidad)
- Parche
- 3 fondos

Si no quieren dibujar, hay assets gratuitos en itch.io, OpenGameArt o el Unity Asset Store. Revisen la licencia y citen la fuente en los créditos.

### Pantallas y UI (Req-6, 7 y 9)

- **MainMenu:** título, botones Jugar, Créditos y Salir.
- **Intro:** texto con avance por tecla o botón.
- **HUD:** vidas (íconos), puntos, nivel y barra del jefe.
- **GameOver / Victoria.**
- **Créditos (Req-7):** nombres de los creadores, herramientas y assets usados.
- **Extra con poco costo:** menú de pausa (`Time.timeScale = 0`) y sonidos básicos.

### Lo técnico en Unity (conceptos del curso)

- **Prefabs:** enemigos, balas y power-ups.
- **Física 2D:** `Rigidbody2D`, `Collider2D` y `OnTriggerEnter2D` para impactos.
- **Scripts clave:** `PlayerController`, `Enemy` (con movimiento configurable), `Bullet`, `PowerUp`, `BossController` y `GameManager` (singleton).
- **Animator:** animación simple de enemigos o explosiones.
- **Partículas:** explosiones al destruir enemigos.
- **UI Canvas + TextMeshPro:** HUD y menús.
- **SceneManager:** transiciones entre escenas.

### Por qué es una buena elección

- **Alcance controlado:** un solo tipo de control y una sola mecánica central (disparar).
- **Fácil de defender:** cada requerimiento se puede mostrar en pantalla.
- **Escalable:** si sobra tiempo, agregan sonido, más power-ups o una fase extra del jefe. Si falta, recortan la fase 3 del jefe sin romper nada.

### Riesgos a evitar

- Querer hacer 3 niveles muy distintos. Mejor niveles similares con variaciones.
- Dejar los créditos y el menú para el final. Se hacen en una hora, pero son requisitos obligatorios.
- No usar prefabs. Con ellos, crear los enemigos del nivel 3 toma minutos.
