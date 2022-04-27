~~~
class Prenda 
    Tipo tipo
    Material material
    Color colorPrincipal
    Color colorSecundario
    
    constructor(Tipo tipo, Material material, Color colorPrimario, Color colorSecundario)
        this.tipo = requireNonNull(tipo, "el tipo es obligatorio")
        this.material = requireNonNull(material, "el material es obligatorio")
        this.colorPrincipal = requireNonNull(colorPrincipal, "el color principal es obligatorio")
        this.colorSecunadrio = colorSecundario


class Tipo
	Categoria categoria

Enum Categoria
	PARTE_SUPERIOR, CALZADO, PARTE_INFERIOR, ACCESORIOS

ZAPATO = new Tipo(Categoria.CALZADO)
PANTALON = new Tipo(Categoria.PARTE_INFERIOR)
REMERA = new Tipo(Categoria.PARTE_SUPERIOR)

enum Material
	TELA, JEAN, CUERO, ALGODON

class Color
	int rojo, verde, azul
~~~


![uml](https://www.plantuml.com/plantuml/png/NP3HJiCW58RlUOhp0di5CzAXcQcbQRSRRmoXE34KbbFGnCLtzo2b9jwS_3by_UZFVeaAOveTqquj2_He_AJWnk1ahm4Y3GPFAXgqoi6y1WPDS051vzcZzTfU_sr7enEPq0RspOgyA6-4aUOII0IwfWqgZanP7m73UoZfm-1aIbHVoMNU-3J_kV8dFHzEucKyzs8uoe4kukqpFyXwSEpkrmFUD6AKbCTDL4lcwgBb31u5xqXn5WC9UFiW3xBBzFf4EsTUu-xkjnJB0tPJ-FIqsNvfGz5UteWjtUgsulLYjgTrcjqF.png)
