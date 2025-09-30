# Local Storage en HTML5

## ¿Que es?

El **almacenamiento local** permite que las aplicaciones web guarden datos en el navegador del usuario, sin enviarlos al servidor y persistiendo más allá de un refresh de página. Antes de HTML5, esto se hacía con cookies (limitadas a ~4 KB y enviadas al servidor en cada petición) o hacks como Flash, Gears o userData de Internet Explorer.

## Historia del almacenamiento local

* **userData (IE)**: hasta 64 KB por dominio, estructura XML.
* **Flash Local Shared Objects**: hasta 100 KB por dominio, accesible desde JS con AMASS/dojox.storage.
* **Gears (Google)**: plugin que ofrecía base de datos SQLite local.
* **dojox.storage**: unificaba acceso a Flash, Gears, Adobe AIR y prototipos HTML5 Storage.

Todos estos métodos eran específicos de navegador o requerían plugins, con interfaces y limitaciones distintas.


