# Mini RTS — prototipo de estrategia en tiempo real

## Archivos

```text
mini-rts-prototipo/
├── index.html   # Juego completo: HTML, CSS y JavaScript sin dependencias
└── README.md    # Estas instrucciones
```

## Cómo ejecutarlo

1. Descarga o descomprime la carpeta.
2. Abre `index.html` directamente en Chrome, Firefox, Edge u otro navegador moderno.
3. Selecciona Azul o Rojo y pulsa **Comenzar partida**. No se necesita servidor, instalación ni conexión a Internet.

## Controles

- **Preparación de 30 segundos:** después de comenzar, aparece una cuenta regresiva. Durante esta fase puedes seleccionar, mover, construir y producir; los ataques y la actividad del enemigo quedan pausados. Al llegar a cero empieza el combate.
- **Clic izquierdo:** seleccionar una unidad o edificio.
- **Arrastrar con clic izquierdo:** dibuja un recuadro y selecciona todas las unidades propias dentro del área.
- **Clic derecho sobre terreno:** mover la unidad o grupo seleccionado (el grupo se distribuye en una formación sencilla).
- **Clic derecho sobre enemigo:** ordenar a la unidad o grupo seleccionado que ataque el objetivo cuando el combate esté activo.
- **Mover / Atacar:** activa el modo correspondiente y después haz clic en el mapa.
- **Esc:** cancela la orden o el modo activo para las unidades seleccionadas.
- Selecciona un **cuartel** y pulsa **Producir soldado**, o selecciona una **fábrica** y pulsa **Producir tanque**.
- Para construir estructuras adicionales, pulsa **Construir cuartel** o **Construir fábrica** y luego haz clic en una zona libre del mapa.
- **Volver a configuración:** permite elegir de nuevo el color y comenzar otra partida.

## Decisiones de diseño

- **Implementación:** un único `index.html`, con Canvas y JavaScript puro. Todas las entidades y créditos viven en memoria; no se cargan imágenes, sprites, librerías ni recursos externos.
- **Colores:** el jugador elige Azul o Rojo antes de iniciar. El enemigo recibe automáticamente el color restante.
- **Economía:** ambos bandos comienzan con **3000 créditos** y reciben **100 créditos por segundo**. El ingreso da margen para adquirir unidades con cierta frecuencia sin hacer gratuitas las compras.
- **Unidades:** soldado **300 créditos** (65 de vida, 8 de daño, entrenamiento de 2,2 s); tanque **700 créditos** (170 de vida, 22 de daño, producción de 4,2 s).
- **Edificios:** cada bando empieza con base central, cuartel y fábrica de tanques como parte del escenario inicial. Construir un cuartel adicional cuesta **800 créditos** y una fábrica adicional **1200 créditos**. La base central inicial es el objetivo principal y no se puede reconstruir.
- **Preparación y selección:** cuenta regresiva de 30 segundos antes del combate. El jugador puede reposicionar unidades, construir y producir durante ese tiempo; los ataques y la IA enemiga permanecen pausados. Arrastrar el ratón permite seleccionar varias unidades propias dentro de un recuadro; las órdenes de movimiento se distribuyen en una formación sencilla.
- **Acciones y combate:** el panel muestra la acción actual y el registro conserva las últimas acciones. Las unidades se mueven, persiguen objetivos y aplican daño; el enemigo produce unidades y las envía hacia los edificios del jugador una vez iniciado el combate. Si destruye un edificio, las tropas enemigas buscan y atacan automáticamente el edificio propio más cercano que siga en pie. La partida termina cuando un bando pierde todos sus edificios.

Es un prototipo jugable enfocado en la prueba de mecánicas, no una reproducción exacta de Red Alert.


## Novedades de producción y victoria

- Puedes indicar cuántas unidades añadir a la cola (de 1 a 50) desde el panel Producción.
- Cada botón muestra el número de unidades en cola para el edificio seleccionado.
- Los créditos se descuentan al iniciar cada unidad, no al añadirla a la cola.
- Si no hay créditos suficientes, la producción se pausa automáticamente y se reanuda cuando los ingresos permitan pagar la siguiente unidad.
- Para ganar debes destruir todos los edificios enemigos. Pierdes cuando el enemigo destruye todos tus edificios.

## Comportamiento de las tropas enemigas

- Las unidades enemigas atacan edificios del jugador.
- Cuando destruyen el edificio que tenían como objetivo, seleccionan automáticamente el edificio propio más cercano que siga en pie y continúan el ataque.
- Si no quedan edificios del jugador, las tropas enemigas se quedan sin objetivos y se activa la condición de derrota.
