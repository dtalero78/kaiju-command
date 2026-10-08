# Kaiju Command — Documento de diseño

Este es el plan acordado, pregunta por pregunta, antes de construir el juego.

## Idea
Eres el **comandante del ejército** y tu misión es defender tu ciudad de monstruos gigantes estilo Godzilla.
Es un juego de **estrategia en tiempo real**: construyes una base, produces tropas y les das órdenes mientras el monstruo ataca.

## Tecnología
- **3D low-poly** con Three.js (desde CDN). Los modelos, los efectos de sonido y la percusión electrónica se generan con código; los instrumentos de la orquesta son grabaciones que se descargan aparte (ver *Sonido y música*).
- **Un solo archivo** `index.html`, que se abre con doble clic.
- Solo para computadora (ratón + teclado). Los textos del juego están en español.

## La batalla
- **Cuenta atrás** para prepararte antes de que llegue el monstruo: 5 min en Fácil, 4 en Normal y 3 en Difícil.
- **Base completa**, como en Command & Conquer: los edificios se construyen desde el menú del Cuartel General, sin obreros, dentro de tu zona de base.
- **Economía con dos recursos:**
  - 💰 **Dinero:** impuestos de cada barrio que sigue en pie (si el monstruo lo destruye, ganas menos).
  - ☢️ **Uranio:** lo traen los recolectores desde las minas a la Refinería. Se usa para el Tanque Máser y el Titán.
- **Ganas** cuando la vida del monstruo llega a 0.
- **Pierdes** si cae el Cuartel General **o** si la barra de "Ciudad en pie" baja del 30 %.
- Los **monumentos** valen mucho más que un edificio normal.
- **Comportamiento del monstruo:** camina hacia un objetivo (un barrio, un monumento o tu base), se voltea contra lo que le hace mucho daño y, si tienes Radar, ves hacia dónde va.

## Unidades
| Unidad | Cuándo la tienes | Para qué sirve |
|---|---|---|
| Soldados | Inicio | Baratos; buenos contra larvas |
| Tanque | Inicio | La base del ejército |
| Recolector | Inicio | Trae uranio |
| Antiaéreo | Desbloqueo | Solo dispara a lo que vuela |
| Helicóptero | Desbloqueo | Rápido; ataca tierra y aire |
| Avión de combate | Con el Helipuerto | Nunca se detiene: pasa sobre el monstruo soltando bombas y misiles, y da la vuelta |
| Vulture | Con el Helipuerto | Traje volador de nanometal (de *Godzilla: City on the Edge of Battle*). Da vueltas alrededor del monstruo disparando de lado, esquiva casi la mitad de sus ataques y a veces lo atraviesa con una embestida. +10 % de daño por cada Vulture cerca (hasta +40 %) |
| Kamikaze | Con el Helipuerto | Avión-bomba sin piloto: vuela directo al monstruo y explota al chocar (1100 de daño). Se pierde al explotar |
| Dron | Con el Helipuerto | Se pilota en **primera persona** (botón «Pilotar» o tecla V): WASD para moverse, ratón o flechas para mirar, Espacio/Shift para subir y bajar, clic para disparar, clic derecho o F para lanzar un misil y Esc para salirse del dron. Si nadie lo pilota, ataca solo |
| Artillería | Desbloqueo | Muy largo alcance; atraviesa el caparazón |
| Lanzallamas | Desbloqueo | Daño en área contra larvas |
| Tanque Máser | Desbloqueo | Rayo de energía (usa uranio) |
| Titán | Último desbloqueo | Robot gigante plateado al estilo de Jet Jaguar. Puñetazos, patada voladora, lluvia de misiles y rayo del pecho; solo uno a la vez |
| MechaGorzak | Con el Titán | Gorzak hecho máquina, al estilo de Mechagodzilla. Misiles desde los dedos, rayo de los ojos y anclas de choque; solo uno a la vez |
| MegaroGorzak | Se llama con el ORCA (no se fabrica; cada llamado cuesta dinero: 6000 en Difícil, 5100 en Normal y 4800 en Fácil) | El Gorzak bueno de 1973, al estilo del MegaroGoji de *Godzilla vs. Megalon*. Sale del mar (o de la tierra, en los mapas sin mar) cerca de la pelea. Puñetazos, coletazos, **aliento atómico** (las placas se encienden de la cola a la cabeza) y la **patada voladora PLUS**: toma impulso, se desliza de espaldas sobre la cola y patea dos veces con los dos pies; la segunda derriba y aturde al monstruo. Mientras se desliza nadie lo puede derribar. Si el Titán está cerca, salta a sujetar al monstruo por detrás (como Jet Jaguar a Megalon) y la patada hace +50 %. Corre cuando la pelea está lejos, se cura solo y los monstruos no pueden levantarlo. Sus ataques tienen botones (automático o manual). Si lo hieren mucho no muere: vuelve al mar a curarse y se le puede volver a llamar 70 s después |
| Kiryū | Último desbloqueo (después del Titán) | El mejor robot, al estilo del Mechagodzilla Kiryu, del tamaño de Gorzak. **Puñetazos** de cerca, rayos máser dobles de la boca, **16 misiles guiados** que salen de la mochila (se abren sus compuertas), cohetes en los antebrazos, el **taladro espiral** (se lanza con los propulsores, perfora corazas y púas, y con el monstruo congelado hace el doble y rompe el hielo) y el **cañón de cero absoluto**: se abren las puertas del pecho, se forma una esfera de frío, el suelo se congela y un rayo con anillos en espiral deja al monstruo encerrado en hielo con cristales; el hielo estalla al final y le hace más daño. Vuela con sus propulsores cuando va lejos. Sus armas especiales tienen botones y se pueden usar en automático o en manual. Los monstruos no pueden levantarlo ni lanzarlo. Solo uno a la vez |
| Camión congelante | Solo en el nivel secreto | Congela a Shin Gorzak |
| Misil y Bomba | Con el Silo de misiles | No son tropas: se guardan en el Silo (hasta 8 de cada uno) y se lanzan contra el monstruo. El misil sube muy alto y cae sobre él aunque se mueva; la bomba la suelta un bombardero que vuela hasta él. Daño moderado |

## Edificios
Cuartel General, Cuartel, Fábrica, Refinería, Torreta, Silo de misiles (fabrica misiles y bombas para lanzarlos contra el monstruo), Radar (minimapa + intención del monstruo), Helipuerto (helicópteros, aviones de combate, Vultures, kamikazes y drones), Hangar del Titán (produce el Titán, MechaGorzak y Kiryū) y **ORCA** (el emisor bioacústico de 2019: imita el llamado de los kaijus para llamar a MegaroGorzak; no necesita medallas, solo dinero).

**Radar de distracción:**
- Es el único edificio que se puede poner lejos de la base: junto a la ciudad o en una calle o un parque de la ciudad.
- Es muy caro (3000 💰 y 150 ☢️) y solo puedes tener uno a la vez.
- Cuando termina de construirse, el monstruo deja todo y va hacia él hasta destruirlo. Sirve para llevarlo a una trampa con tu ejército.

## Llaves y combos
Los robots gigantes y los monstruos pelean cuerpo a cuerpo:
- **MechaGorzak** lanza **anclas de choque**: dos cables eléctricos sujetan al monstruo unos segundos. No se puede mover, si vuela lo bajan al suelo y recibe más daño de todos.
- **El Titán** hace una **patada voladora** que aturde al monstruo y lanza una **lluvia de misiles** desde los hombros.
- **Combos:** si el Titán ataca mientras MechaGorzak sujeta al monstruo, hace el doble de daño. El primer combo de cada batalla se ve en cámara lenta.
- **Los monstruos se defienden** de los robots que se les acercan:
  - Gorzak y Trihydra los agarran y los lanzan por los aires.
  - Pyraxis, Medúgora y la Trihydra del Vacío los levantan y los sueltan.
  - Krakor los atrapa con su pinza.
  - Noctra los envuelve en seda.

## Campaña
| Nivel | Ciudad | Monstruo | Qué enseña |
|---|---|---|---|
| 1 | Tokio (Torre de Tokio, pagoda) | **Gorzak**, lagarto atómico inspirado en el Godzilla de 1954 | Lo básico |
| 2 | Río de Janeiro (Cristo Redentor, Maracaná) | **Pyraxis**, ave de fuego que vuela | Defensa aérea |
| 3 | Nueva York (Estatua de la Libertad, Empire State) | **Krakor**, cangrejo acorazado | Rodear al enemigo |
| 4 | París (Torre Eiffel, Arco del Triunfo) | **Noctra**, polilla que suelta larvas | Dos frentes |
| 5 | Colonia en **Xulfura**, planeta desolado y amarillento | **Trihydra**, dragón de tres cabezas al estilo de King Ghidorah | Todo junto |
| 6 | Bogotá de noche (Cerro de Monserrate, Torre Colpatria) | **Medúgora**, medusa del espacio al estilo de Dogora | Atacar cuando baja |
| 7 | Fukuoka (Torre de Fukuoka, Fukuoka Dome) | **SpaceGorzak**, al estilo de SpaceGodzilla | Destruir sus torres de cristal |
| 8 | Xulfura bajo un eclipse | **Trihydra del Vacío**, al estilo de Void Ghidorah | Esperar el momento justo |
| 9 | Ginza en 1947 (Reloj de Ginza, Teatro Nichigeki) | **Gorzak Minus One**, al estilo del Godzilla de *Minus One* | Interrumpir o esquivar |
| 10 | Shanghái (Mirador Perla de Oriente, Edificio de la Aduana) | **Anguirax**, al estilo del Anguirus de *Final Wars* | Esquivar y castigar |
| 11 | Bahía de Suruga en 1971 (Complejo papelero de Fuji, Santuario Sengen) | **Lodora**, al estilo de Hedorah | Elegir bien las armas |
| 12 | Medellín (Edificio Coltejer, Catedral Metropolitana) | **Condorax**, un cóndor de los Andes gigante | Atacar cuando baja |
| 13 | Osaka (Castillo de Osaka, Tsūtenkaku) | **Biolantra**, al estilo de Biollante | Quemarla |
| 🔒 | Tokio de noche | **Shin Gorzak** | Nivel secreto |

En Xulfura, los monumentos son **domos de oxígeno**: si el monstruo rompe uno, el barrio que cubre se pierde.

**Trihydra es una calamidad (nivel 5):**
- Desata tormentas de nubes oscuras con lluvia que recorren la ciudad y tu base soltando rayos que dañan todo y a veces incendian edificios.
- El cielo se oscurece mientras dura la batalla y se despeja cuando cae.
- Lanza sus rayos de gravedad (tres relámpagos dorados) más seguido.

**Medúgora (nivel 6):**
- Flota en el cielo, así que solo la alcanza lo que dispara al aire.
- Cada cierto tiempo baja a absorber un barrio y se cura. Ahí la alcanza todo el ejército.
- Suelta células que van por tu base y lanza pulsos eléctricos contra lo que vuela cerca.

**Trihydra del Vacío (nivel 8), el monstruo más difícil del juego:**
- No tiene cuerpo: tres cuellos dorados salen de agujeros negros en el cielo.
- Allá arriba casi nada le hace daño. Cuando una cabeza baja a morder queda **expuesta** y recibe más daño.
- Lanza relámpagos dorados y abre agujeros negros que arrastran y destrozan lo que atrapan.
- Tiene más vida que Shin Gorzak y a mitad de la batalla se enfurece: muerde más rápido, lanza más relámpagos y abre más agujeros negros.

**Gorzak Minus One (nivel 9), la bomba viviente:**
- Tokio en 1947, apenas reconstruida después de la guerra: casas de madera con techo de teja y edificios bajos de piedra.
- **Aliento atómico:** sus placas dorsales, enormes y dentadas, se levantan una a una de la punta de la cola a la cabeza con un chasquido y se encienden de azul. Mientras tanto aparece en el suelo un **círculo rojo** donde va a caer, y las tropas que están dentro intentan huir.
- Echa la cabeza atrás, las placas se cierran todas de golpe y la luz corre por la espalda hasta la boca (como el núcleo de una bomba que se comprime). Lanza la cabeza hacia adelante y el rayo cae como una **bomba atómica**:
  1. Un destello blanco y una bola de fuego. Todo lo que está en el núcleo desaparece; los robots gigantes aguantan, muy dañados.
  2. Una **onda expansiva** con una cúpula blanca y un muro de polvo y escombros que avanza por las calles, daña lo que alcanza, incendia edificios y lanza por los aires a las tropas.
  3. Un **hongo de humo** mucho más alto que el monstruo, y una falda de polvo que cubre la ciudad y oscurece el cielo. Él ruge delante del hongo.
  4. Cae **lluvia negra** sobre la ciudad. El humo y la lluvia se disipan poco a poco (casi un minuto).
- **Contraataque:** si le haces suficiente daño mientras carga, la energía le estalla en la boca y queda aturdido. Las anclas de MechaGorzak también lo detienen.
- El aliento le quema la cara y la garganta: después de cada bomba queda **QUEMADO** unos segundos, echando vapor mientras se regenera, y recibe +50 % de daño.

**Anguirax (nivel 10), el acorazado de púas:**
- Cuadrúpedo rápido y ágil con un caparazón cubierto de púas, cuerno en el hocico, corona de cuernos y cola con mazo. Sale de debajo de la tierra.
- **Bola de púas:** se enrosca, rueda a toda velocidad por una franja amarilla aplastando edificios y lanzando tropas a los lados, y mientras rueda casi no le entra el daño. Al final rebota, cae con todo su peso y queda **MAREADO** (recibe +50 % de daño).
- **Púas de la espalda:** frenan el daño que le llega por detrás y lastiman a los robots que lo golpean ahí. Muerde a los robots que se le acercan.
- **Excavar:** a veces se mete bajo tierra (no se le puede atacar; solo se ve el polvo) y revienta el suelo de otro barrio.

**Lodora (nivel 11), el monstruo del smog, el más peligroso:**
- Un montón de lodo tóxico que brilla de mojado, con dos ojos rojos verticales. Nació de la contaminación de la bahía.
- **Niebla de ácido sulfúrico:** la rodea, asfixia a las tropas que se acercan y corroe los edificios.
- **Rayos oculares:** rayos rojos que alcanzan también a lo que vuela. **Lodo ácido:** derrite tanques y edificios al instante y deja un charco que sigue corroyendo.
- **Casi inmune:** las balas, misiles, obuses y bombas le hacen el 20 %; el **máser** y el **fuego** la secan (160 %) y los robots, el 60 %.
- **Se divide y se fusiona:** suelta fragmentos (cada cierto tiempo y cuando la golpean fuerte) que atacan con ácido y luego vuelven a fundirse con ella para curarla y hacerla crecer (hasta ×1,5). A los fragmentos sí les hacen daño las armas normales.
- **Platillo:** a ratos se aplana y vuela a otro barrio dejando un rastro de gas venenoso. Al morir se seca y se vuelve polvo.
- **Forma Perfecta:** cuando le queda la mitad de vida crece de golpe, se cura, cubre la ciudad de smog y suelta 4 fragmentos. Desde ahí su gas, sus rayos (dos más por ráfaga) y su lodo pegan un 50 % más fuerte.
- Tiene 78 000 de vida, su niebla es más grande y corrosiva, y sus fragmentos aguantan más y la curan más al fusionarse (hasta 10 a la vez). En las pruebas en Normal gana incluso contra un ejército fuerte con Kiryū unas dos de cada tres veces, como la Trihydra del Vacío.
- Al fondo del mapa se ve el monte Fuji, y las chimeneas de la ciudad no dejan de echar humo.

**Condorax (nivel 12), el cóndor gigante:**
- Un cóndor de los Andes enorme: plumaje negro, collar y manchas blancas en las alas, cabeza calva y pico ganchudo. Siempre vuela muy alto.
- **Picada:** marca un círculo rojo, baja en picada, destroza lo que hay ahí y se lleva una tropa entre las garras. Mientras está abajo, **todo el ejército** lo alcanza.
- **Ráfagas** de alas que arrastran a las tropas y tumban edificios, **plumas afiladas** que caen como dardos y un **graznido** que deja aturdidas a las tropas cercanas unos segundos.

**Biolantra (nivel 13), la rosa mutante:**
- Sale de la bahía de Osaka como una **rosa gigante** con pétalos rojos y raíces, y se queda plantada en la orilla: la rosa no camina.
- **Lianas:** seis zarcillos con boca que azotan lo que esté a su alcance (también lo que vuela) y a veces atrapan tropas.
- **Savia ácida:** escupe bolas de savia dorada que dejan charcos corrosivos. Si un robot se le acerca, lo agarra y lo lanza; a los robots grandes como Kiryū los derriba.
- **Semillas:** lanza semillas que brotan en **retoños** carnívoros por toda la ciudad (y de vez en cuando junto a tu base). Hay que arrancarlos.
- **Se regenera** sin parar, salvo cuando arde: el **fuego** le hace +60 % de daño y la deja **QUEMÁNDOSE**, sin curarse.
- **Forma final:** al llegar al 55 % de vida se transforma con una escena propia en un monstruo de cabeza de cocodrilo con ocho lianas que sí camina hacia la ciudad, muerde y lanza un **chorro de savia** en cono. Al morir se deshace en esporas doradas que suben al cielo.
- 110 000 de vida. En Normal, con un ejército fuerte pero sin Kiryū, se pierde; con Kiryū se gana salvando la mitad de la ciudad.

**Shin Gorzak (nivel secreto):** se desbloquea con 15 medallas (de las 39 de la campaña). Evoluciona en 3 formas: cría marina → erguido → despertar. Cada transformación tiene su propia escena.

En la forma final, su ataque es un **aliento en tres fases**:
1. Humo negro que sale de la boca y cubre la ciudad.
2. El humo se convierte en fuego.
3. Termina en un láser morado muy potente, acompañado de láseres dorsales que derriban lo que vuela.

La primera vez que lo usa hay una escena cinematográfica.

No puede morir: cuando queda agotado, hay que llevarle **camiones de agente congelante** antes de que se recupere.

## Progresión
- 3 medallas por nivel: 🥉 ganar · 🥈 salvar al menos el 70 % de la ciudad · 🥇 no perder ningún monumento.
- Se pueden repetir niveles; las medallas ya ganadas no se vuelven a contar.
- Las medallas se gastan en un **árbol de mejoras permanentes**, que sirve para desbloquear unidades y mejorar vida, daño, velocidad, impuestos, minería, rapidez de construcción y cuenta atrás.
- El progreso se guarda automáticamente en el navegador.

## Controles
- Cámara: `WASD` / flechas / bordes de la pantalla, rueda para el zoom y `Q`/`E` para girar.
- Clic: seleccionar · arrastrar: selección múltiple · clic derecho: mover o atacar.
- `Ctrl` (o `Shift`) + número: guardar un grupo · número: seleccionar ese grupo.
- **`Espacio`: pausa táctica.** El juego se congela, pero puedes seguir dando órdenes.

## Modos
| Dificultad | Vida y daño del monstruo | Cuenta atrás | Dinero inicial |
|---|---|---|---|
| Fácil | 50 % | 5 min | 5.000 |
| Normal | 70 % | 4 min | 4.000 |
| Difícil | 100 % | 3 min | 3.000 |

Y **Sandbox**: todo desbloqueado, recursos infinitos, cualquier ciudad y monstruo, y un panel para ajustar valores en vivo. Las medallas no cuentan en Sandbox.

## Sonido y música
- Los efectos de sonido se generan por código y hay un botón para silenciarlos.
- **Instrumentos mixtos:**
  - **Grabados:** un núcleo orquestal compartido (cuerdas, metales, coro y timbales) más los instrumentos característicos de cada ciudad. Vienen de la colección FluidR3 (CC BY 3.0, con créditos en el menú).
  - **Por código:** la batería de marcha, el bajo y los efectos electrónicos.
- Los instrumentos grabados se descargan **en segundo plano** desde el menú. Mientras tanto, o sin internet, suena una versión sintetizada.
- La música **baja de volumen** cuando el monstruo ruge o dispara.
- **Cada nivel tiene su propia melodía** y el **himno de Kaiju Command** vuelve en los momentos clave.

| Tema | Estilo |
|---|---|
| Menú: *El Himno* | Marcha épica orquestal |
| Tokio: *La Marcha del Lagarto* | Escala japonesa, con taiko, koto y shakuhachi |
| Río: *Samba de Fuego* | Batucada ardiente, con guitarra de nailon y flauta |
| Nueva York: *Acero en la Bahía* | Big band *noir*, con metales, saxofón y contrabajo |
| París: *Vals de la Polilla* | Vals en 3/4, con acordeón, arpa y celesta |
| Xulfura: *Himno de Xulfura* | Ciencia ficción épica, con tres voces que se responden |
| Bogotá: *Joropo Cósmico* | Joropo en 3/4 con arpa llanera, cuatro y maracas, y una voz que flota como la medusa |
| Eclipse: *Réquiem del Vacío* | Órgano y coro, con la célula de las tres cabezas deformada |
| Medellín: *Sombra sobre el Valle* | Bambuco en 6/8 con guitarra, flauta y arpa; el motivo del Cóndor sube planeando |
| Shanghái: *Rodando por el Bund* | Re pentatónico, rápido, con koto, flauta y taiko; el motivo de Anguirax sube rodando |
| Osaka: *La Rosa de Osaka* | Vals lento y triste en la menor, con arpa, cuerdas y coro; el motivo de Biolantra se abre como una flor |
| Suruga: *La ciudad que se ahoga* | Lento y melancólico, como una canción de art-pop: voz que flota, arpa, gotas de celesta y un bajo que se hunde |
| Ginza: *Ceniza sobre Ginza* | Marcha fúnebre en mi frigio, con cuerdas graves, taiko y koto; su motivo es el de Gorzak torcido hacia un tritono |
| Shin Gorzak: *Despertar* | Lamento lento con voz solista, coro y cuerdas |

- **Fases en batalla:**
  1. Cuenta atrás tensa.
  2. Himno al llegar el monstruo.
  3. Tema completo, de casi 2 minutos.
  4. Versión crítica con el himno desesperado.
- **Motivo propio de cada monstruo,** que suena cuando carga su ataque fuerte. El de Shin Gorzak es la primera frase de su lamento, en la voz solista.
- **El ataque final de Shin Gorzak:** la primera vez que usa su aliento suena el lamento completo, y después vuelve la música de batalla.
- **Frases cortas** para el despliegue del Titán y de MechaGorzak (el motivo de Gorzak convertido en marcha mecánica), la llegada de MegaroGorzak (una fanfarria alegre de héroe de los años setenta, con metales, flauta y redoblante), la caída de un monumento y las evoluciones de Shin.
- **Banda sonora:** una pantalla del menú para escuchar todos los temas. Los de Shin Gorzak se pueden escuchar aunque el nivel secreto siga bloqueado.
- **Entregas:**
  1. Himno y Tokio.
  2. Río, Nueva York, París, Xulfura y Shin Gorzak, con sus motivos y las frases de evolución de Shin.

  Las dos están hechas. La orquesta completa son 16 instrumentos grabados (unos 38 MB) y se descargan primero los de la ciudad que vas a jugar.
- **Comparar:** la Banda sonora tiene una sección para escuchar el tema y el motivo anteriores de Shin Gorzak junto a los nuevos.

## Modelos
Todo es **low-poly** y se arma con piezas geométricas:
- **Monstruos:** cuerpos facetados con placas dorsales, garras, dientes y brillo en la garganta antes de atacar.
- **Unidades:** tanques con orugas y antena, soldados con casco y mochila, helicóptero con alas cortas y cohetes.
- **Monstruos nuevos y renovados:**
  - Gorzak se inspira en el Godzilla de 1954: gris carbón, piel rugosa, placas en forma de hoja de arce, orejas y aliento blanco azulado.
  - Trihydra tiene coronas de cuernos, cuellos largos con escamas, alas enormes con venas y lanza tres relámpagos dorados.
  - Medúgora es una medusa translúcida con núcleo brillante.
  - La Trihydra del Vacío son tres cuellos que salen de agujeros negros.
  - Kiryū es MechaGorzak tipo 3: plateado claro, con mochila de misiles y propulsores, el cañón de cero absoluto en el pecho y una cuchilla máser en el brazo, y mide lo mismo que Gorzak Minus One. Condorax es un cóndor negro con collar blanco y alas enormes de plumas abiertas en la punta.
  - Anguirax tiene un caparazón café con decenas de púas, y al rodar se convierte en una bola de púas. Lodora es lodo gris verdoso y brillante con grumos, brazos que cuelgan y ojos rojos verticales con la pupila en raya.
  - Biolantra es primero una rosa roja enorme sobre un tallo con hojas y raíces, y luego un cuerpo verde oscuro con cabeza de cocodrilo, dientes, garganta dorada y lianas con boca.
  - Gorzak Minus One es casi negro, de piel muy rugosa, con la cola larga y placas blancas enormes y dentadas que se levantan antes de disparar.
- **Avión de combate:** alas en delta, doble cola, postquemadores, y misiles y bombas bajo las alas.
- **MegaroGorzak:** hecho mirando fotos del traje de 1973. Casi negro y muy rugoso, con bultos grises; cuerpo en forma de pera y cuello corto; cabeza redonda con **cejas enormes**, **ojos grandes color café** y hocico redondo con la boca roja y dientes blancos; brazos hacia adelante con garras color crema; uñas grandes color crema en los pies; placas plateadas pequeñas y acolchadas en tres filas que siguen en una fila por la cola, que se arrastra por el suelo. Mide como Gorzak.
- **ORCA:** un maletín negro reforzado con la tapa abierta (pantalla central con dos flechas azules y dos alas con pantallas doradas), la pantalla de la onda azul que late, una perilla con anillo de luz, dos tubos emisores y dos torres de altavoces, como las del estadio de la película.
- **Vulture:** casco blanco alargado con el piloto acostado, dos brazos-cañón, alas cortas en flecha con puntas naranjas, dos toberas azules y venas doradas de nanometal. **Kamikaze:** fuselaje de misil con ojiva roja y alas rectas. **Dron:** cuadricóptero negro con cuatro hélices, cámara y luces de navegación.
- **Robots del Hangar:** el Titán es plateado con franjas rojas, amarillas y azules, cabeza puntiaguda y una cara que sonríe, como Jet Jaguar. MechaGorzak es de acero, con ojos amarillos, placas dorsales, cola y misiles de punta roja en los dedos.
- **Base:** Cuartel General con torre de mando, fábrica con grúa, refinería con tanques que brillan, radar sobre una torre de celosía y hangar con los ojos del Titán en la oscuridad.
- **Monumentos:** Arco del Triunfo con su bóveda, Maracaná con gradas y cancha, Torre Eiffel y Torre de Tokio con patas de celosía, Cristo sobre el Corcovado y Estatua de la Libertad sobre su fuerte en forma de estrella.
- **Ciudades:** cada estilo tiene sus detalles, como tiendas con toldos, balcones, azoteas con aparatos y rascacielos escalonados o de vidrio. París tiene mansardas con buhardillas, Nueva York tanques de agua y escaleras de incendios, y Río cajas de agua azules.

## Cinemáticas (se pueden saltar)
Entrada de cada monstruo · primer rayo especial · primera bomba de Gorzak Minus One, con la onda vista desde la calle (y un plano corto de cada bomba siguiente) · primera vez que Anguirax rueda · primera picada del Cóndor · transformación de Biolantra · primer disparo del cañón de cero absoluto de Kiryū · despliegue del Titán y de MechaGorzak · el ORCA emitiendo el llamado y MegaroGorzak saliendo del mar · su primera patada voladora PLUS en cámara lenta (o el «combo de héroes» si el Titán sujeta al monstruo) · primeras anclas de choque · primer combo en cámara lenta · victoria y derrota · cada evolución de Shin Gorzak · su primer aliento de humo, fuego y láser · su congelación.

## Dónde vive el juego
- Repo propio: `kaiju-command`, con GitHub Pages.
- En `JET-bullet-hell` solo hay un `kaiju.html` que lleva al juego.
