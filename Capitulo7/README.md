# Local Storage en HTML5

## ¿Que es?

El **almacenamiento local** permite que las aplicaciones web guarden datos en el navegador del usuario, sin enviarlos al servidor y persistiendo más allá de un refresh de página. Antes de HTML5, esto se hacía con cookies (limitadas a ~4 KB y enviadas al servidor en cada petición) o hacks como Flash, Gears o userData de Internet Explorer.

## Historia del almacenamiento local

* **userData (IE)**: hasta 64 KB por dominio, estructura XML.
* **Flash Local Shared Objects**: hasta 100 KB por dominio, accesible desde JS con AMASS/dojox.storage.
* **Gears (Google)**: plugin que ofrecía base de datos SQLite local.
* **dojox.storage**: unificaba acceso a Flash, Gears, Adobe AIR y prototipos HTML5 Storage.

Todos estos métodos eran específicos de navegador o requerían plugins, con interfaces y limitaciones distintas.

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

