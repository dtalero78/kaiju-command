# Kaiju Command

Juego de **estrategia en tiempo real** en 3D: eres el comandante del ejército y tienes que defender tu ciudad de monstruos gigantes estilo Godzilla.

Todo el juego está en un solo archivo: [index.html](index.html). El motor 3D (Three.js) y los instrumentos de la orquesta se descargan de internet. Los modelos, los efectos de sonido y la percusión electrónica se generan con código, y las composiciones son originales.

## Cómo jugar

Abre `index.html` en Safari, Chrome o Firefox. Necesitas conexión a internet: el motor 3D y los instrumentos de la orquesta (unos 38 MB) se descargan la primera vez y el navegador los guarda. Sin internet, la música suena sintetizada.

1. **Cuenta atrás:** antes de que llegue el monstruo, construye tu base con el panel **CONSTRUIR** (abajo a la derecha).
2. **Economía:**
   - 💰 **Dinero:** sale de los impuestos de la ciudad.
   - ☢️ **Uranio:** lo traen los Recolectores desde las minas verdes a la Refinería.
3. **Batalla:** selecciona tus tropas y atácalo con clic derecho. Usa la **pausa táctica** (`Espacio`) para planear.
   Con el **Silo de misiles** fabricas misiles y bombas: selecciónalo y pulsa 🚀 o 💣 para lanzarlos contra el monstruo.
   Con el **ORCA** llamas a **MegaroGorzak**, el Gorzak bueno de 1973, para que pelee a tu lado: cada llamado cuesta dinero.
4. **Ganas** si derrotas al monstruo. **Pierdes** si cae tu Cuartel General o si la ciudad baja del 30 %.

### Controles

| Tecla | Acción |
|---|---|
| `WASD` / flechas / bordes de la pantalla | Mover la cámara |
| Rueda del ratón | Zoom |
| `Q` / `E` | Girar la cámara |
| Clic / arrastrar | Seleccionar (doble clic: todas las unidades de ese tipo) |
| Clic derecho | Mover, atacar, recolectar o fijar el punto de reunión |
| `Ctrl` o `Shift` + `1-9` | Guardar un grupo (`1-9` para seleccionarlo) |
| `Espacio` | Pausa táctica |
| `H` / `F` | Ir a tu base / buscar al monstruo |
| `N` | Silenciar |
| `M` | Panel del Sandbox |
| `Esc` | Cancelar / menú |

## Campaña

| Nivel | Ciudad | Monstruo |
|---|---|---|
| 1 | Tokio | Gorzak, lagarto atómico |
| 2 | Río de Janeiro | Pyraxis, ave de fuego |
| 3 | Nueva York | Krakor, cangrejo acorazado |
| 4 | París | Noctra, polilla madre |
| 5 | Colonia Xulfura | Trihydra, dragón de tres cabezas |
| 6 | Bogotá | Medúgora, medusa del espacio |
| 7 | Fukuoka | SpaceGorzak, el Gorzak de las estrellas |
| 8 | Xulfura (eclipse) | Trihydra del Vacío |
| 9 | Ginza (1947) | Gorzak Minus One, la bomba viviente |
| 10 | Shanghái | Anguirax, el acorazado de púas |
| 11 | Bahía de Suruga (1971) | Lodora, el monstruo del smog |
| 12 | Medellín | Condorax, el cóndor gigante |
| 13 | Osaka | Biolantra, la rosa mutante |
| 🔒 | Tokio de noche | ??? (consigue 15 medallas) |

Cada nivel da 3 medallas: ganar, salvar el 70 % de la ciudad y no perder ningún monumento. Las medallas se gastan en **Mejoras** permanentes. El progreso se guarda en el navegador.

## Modos

- **Fácil, Normal y Difícil.**
- **Sandbox:** todo desbloqueado, recursos infinitos, cualquier ciudad y cualquier monstruo. Las medallas no cuentan.

Si el juego va lento, baja la **Calidad gráfica** en *Opciones*. En el menú también están la **Banda sonora** (para escuchar los temas) y los **Créditos**.

El plan completo del juego está en [DISEÑO.md](DISEÑO.md).
