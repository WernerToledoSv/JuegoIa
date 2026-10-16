# Mini RTS — prototipo de estrategia en tiempo real

Juego de estrategia 2D en un solo archivo HTML, desarrollado con Canvas y JavaScript puro.

## Cómo ejecutarlo

1. Descarga o clona este repositorio.
2. Abre `index.html` en un navegador moderno (Firefox, Chrome, Edge, etc.).
3. Elige el bando azul o rojo y pulsa **Comenzar partida**.

No requiere instalación, servidor, librerías ni conexión a Internet.

## Controles

- **Clic izquierdo:** seleccionar una unidad o edificio.
- **Arrastrar con clic izquierdo:** seleccionar varias unidades propias dentro de un recuadro.
- **Clic derecho en el terreno:** mover la unidad o el grupo seleccionado.
- **Clic derecho en un enemigo:** ordenar un ataque cuando el combate esté activo.
- **Mover / Atacar:** activa el modo correspondiente y después selecciona el destino o el objetivo.
- **Esc:** cancelar el modo activo y las órdenes de las unidades seleccionadas.
- **Añadir soldados:** selecciona un cuartel y usa el botón de soldados.
- **Añadir tanques:** selecciona una fábrica y usa el botón de tanques.
- **Construcción:** pulsa **Construir cuartel** o **Construir fábrica** y después elige una zona libre del mapa.
- **Volver a configuración:** termina la partida actual y permite elegir el color para empezar otra.

## Reglas y economía

- Cada bando comienza con **3000 créditos** y recibe **100 créditos por segundo**.
- El jugador elige azul o rojo; la IA usa el color restante.
- Cada bando empieza con una base central, un cuartel y una fábrica de tanques.
- Soldado: **300 créditos**, 65 de vida, 8 de daño y 2,2 segundos de entrenamiento.
- Tanque: **700 créditos**, 170 de vida, 22 de daño y 4,2 segundos de producción.
- Cuartel adicional: **800 créditos**. Fábrica adicional: **1200 créditos**.
- La partida comienza con **30 segundos de preparación**. Durante ese tiempo el jugador puede mover unidades, construir y producir; el combate y el movimiento de ataque de la IA permanecen pausados.
- **Victoria:** destruir todos los edificios enemigos.
- **Derrota:** perder todos los edificios propios.

## Colas de producción

1. Selecciona un cuartel para producir soldados o una fábrica para producir tanques.
2. Indica en el campo de cantidad cuántas unidades quieres añadir (de 1 a 50) y pulsa el botón correspondiente.
3. El costo de cada unidad se descuenta cuando comienza su producción, no cuando se añade a la cola.
4. Si no hay créditos suficientes, la producción se pausa y continúa automáticamente cuando haya fondos.
5. Los contadores **En cola** muestran todas las unidades pendientes del edificio seleccionado: incluyen la unidad que se está produciendo y las unidades que esperan en la cola. La unidad activa sigue contándose aunque la producción esté pausada por falta de créditos.

## IA enemiga

- La IA también produce refuerzos durante la preparación y durante el combate.
- El intervalo entre decisiones de producción y el límite del ejército varían entre partidas, así que la cantidad y composición de los refuerzos no son siempre iguales.
- Las unidades enemigas pueden elegir como objetivo tanto tropas como edificios del jugador.
- Si destruyen su objetivo, buscan otro objetivo válido al azar y continúan atacando.
- El combate termina cuando uno de los bandos pierde todos sus edificios.

## Implementación

- El juego completo está en `index.html`; el mapa, las unidades y los edificios se dibujan con Canvas.
- No utiliza imágenes, sprites, librerías ni recursos externos.
- Las unidades, estructuras y créditos se mantienen en memoria durante la partida.

Este proyecto es un prototipo jugable centrado en probar mecánicas de estrategia en tiempo real; no pretende ser una reproducción exacta de Red Alert.
