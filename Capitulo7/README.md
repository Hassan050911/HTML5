# Local Storage en HTML5

## ¿Que es?

El **almacenamiento local** permite que las aplicaciones web guarden datos en el navegador del usuario, sin enviarlos al servidor y persistiendo más allá de un refresh de página. Antes de HTML5, esto se hacía con cookies (limitadas a ~4 KB y enviadas al servidor en cada petición) o hacks como Flash, Gears o userData de Internet Explorer.

## Historia del almacenamiento local

* **userData (IE)**: hasta 64 KB por dominio, estructura XML.

* **Flash Local Shared Objects**: hasta 100 KB por dominio, 
accesible desde JS con AMASS/dojox.storage.

* **Gears (Google)**: plugin que ofrecía base de datos SQLite local.

* **dojox.storage**: unificaba acceso a Flash, Gears, Adobe AIR y prototipos HTML5 Storage.

Todos estos métodos eran específicos de navegador o requerían plugins, con interfaces y limitaciones distintas.


# Usando HTML5 Storage

## Claves y valores

- HTML5 Storage funciona con **pares clave/valor**.

- La **clave siempre es un string**.

- El valor se guarda como string, aunque JS permite guardar Boolean, int o float.

- Para recuperar datos numéricos: usar `parseInt()` o `parseFloat()`.

## imitaciones actuales

- 5 MB de espacio por dominio (aprox., depende del navegador).

- Error: QUOTA_EXCEEDED_ERR si excedes el límite.

- No se puede pedir más espacio al usuario desde el código.

- Todo se guarda como string → números y floats ocupan más espacio.

# HTML5 Storage in Action

## Problema 

En el juego Halma hecho en `<Canvas>`, si cierras la ventana del navegador se pierde el progreso.

## Solución con HTML5 Storage

* Se usa localStorage para guardar el estado del juego en el navegador.

* Así, al cerrar y volver a abrir, el juego recuerda:

* Si hay partida en progreso (gGameInProgress, Boolean).

* La posición de cada pieza (row y column).

* Qué pieza está seleccionada (gSelectedPieceIndex).

* Si esa pieza ya se movió (gSelectedPieceHasMoved).

* El número total de movimientos (gMoveCount).

## Codigo Guardar Progreso 
 ```js 
 function saveGameState() {
  if (!supportsLocalStorage()) return false;

  localStorage["halma.game.in.progress"] = gGameInProgress;
  
  for (var i = 0; i < kNumPieces; i++) {
    localStorage["halma.piece." + i + ".row"] = gPieces[i].row;
    localStorage["halma.piece." + i + ".column"] = gPieces[i].column;
  }

  localStorage["halma.selectedpiece"] = gSelectedPieceIndex;
  localStorage["halma.selectedpiecehasmoved"] = gSelectedPieceHasMoved;
  localStorage["halma.movecount"] = gMoveCount;

  return true;
}
```
## Codigo Recuper Profreso 

```js
function resumeGame() {
  if (!supportsLocalStorage()) return false;

  gGameInProgress = (localStorage["halma.game.in.progress"] == "true");
  if (!gGameInProgress) return false;

  gPieces = new Array(kNumPieces);
  for (var i = 0; i < kNumPieces; i++) {
    var row = parseInt(localStorage["halma.piece." + i + ".row"]);
    var column = parseInt(localStorage["halma.piece." + i + ".column"]);
    gPieces[i] = new Cell(row, column);
  }

  gSelectedPieceIndex = parseInt(localStorage["halma.selectedpiece"]);
  gSelectedPieceHasMoved = (localStorage["halma.selectedpiecehasmoved"] == "true");
  gMoveCount = parseInt(localStorage["halma.movecount"]);

  drawBoard();
  return true;
}
```
# Soporte en navegadores

| Navegador | Versión mínima |
|------------|---------------|
| IE         | 8             |
| Firefox    | 3.5           |
| Safari     | 4             |
| Chrome     | 4             |
| Opera      | 10.5          |
| iPhone     | 2             |
| Android    | 2             |