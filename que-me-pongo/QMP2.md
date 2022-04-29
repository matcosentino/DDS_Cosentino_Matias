~~~
class Prenda 
    Tipo tipo
    Material material
    Color colorPrincipal
    Color colorSecundario
    Trama trama
    
    constructor(Tipo tipo, Material material, Color colorPrimario, Color colorSecundario)
        this.tipo = tipo
        this.material = material
        this.colorPrincipal = colorPrincipal
        this.colorSecunadrio = colorSecundario
        this.trama = trama

    method categoria()
        return tipo.categoria()

class Tipo
  Categoria categoria
    
    constructor(Categoria categoria)
        this.categoria = categoria

    method categoria()
        return this.categoria

Enum Categoria
	PARTE_SUPERIOR, CALZADO, PARTE_INFERIOR, ACCESORIOS

enum Material
	TELA, JEAN, CUERO, ALGODON

class Color
	int rojo, verde, azul

// Defino la trama como un enum proponiendo que sea Prenda quien la conozoca
enum Trama
    LISA, RAYADA, CON_LUNARES, A_CUADROS, ESTAMPADO

// Defino una clase Borrador que me permita la construccion por pasos de la Prenda mediante comportamientos, 
// guardar los estados intermedios y delegar en la misma los problemas creacionales de la prenda.
class Borrador 
    Tipo tipo
    Material material
    Color colorPrincipal
    Color colorSecundario
    trama = Trama.LISA      // Por defecto la trama es lisa
    
    // Como el tipo de prenda es lo primero a especificar, lo coloco en el constructor
    constructor(Tipo tipo)
        this.tipo = requireNonNull(tipo, "el tipo es obligatorio")

    method setMaterial(material)
        this.material = requireNonNull(material, "el material es obligatorio")

    method setColorPrincipal(colorPrincipal)
        this.colorPrincipal = requireNonNull(colorPrincipal, "el color principal es obligatorio")

    method setTrama(trama)
        this.trama = if trama is null then Trama.Lisa else trama
    
    // En este metodo deberia agregar el resto de las validaciones que sean requeridas
    method crearPrenda
        return new Prenda(tipo, materia, colorPrincipal, colorSecundario, trama)

// BONUS - Defino una clase abstracta (Institucion) y delego en las subclases la construccion de las diferentes 
// partes del uniforme
class Uniforme 
    prendaSuperior
    prendaInferior
    calzado

abstract class Institucion
    method fabricarUniforme()
        return new Uniforme(this.fabricarPrendaSuperior(), this.fabricarPrendaInferior(), this.fabricarCalzado)

    abstract method fabricarPrendaSuperior()
    abstract method fabricarPrendaInferior()
    abstract method fabricarCalzado()

class SanJuan inherits Institucion
    method fabricarPrendaSuperior()
        borrador = new Borrador(CHOMBA)
        borrador.setMaterial(PIQUE)
        borrador.setColorPrincipal(new Color(r,g,b))
        return borrador.crearPrenda()
    
    method fabricarPrendaInferior()
        borrador = new Borrador(PANTALON)
        borrador.setMaterial(ACETATO)
        borrador.setColorPrincipal(new Color(r,g,b))
        return borrador.crearPrenda()

    method fabricarCalzado()
        borrador = new Borrador(ZAPATILLAS)
        borrador.setColorPrincipal(new Color(r,g,b))
        return borrador.crearPrenda()
        
class Johnson inherits Institucion
    method fabricarPrendaSuperior()
        borrador = new Borrador(CAMISA)
        borrador.setColorPrincipal(new Color(r,g,b))
        return borrador.crearPrenda()
    
    method fabricarPrendaInferior()
        borrador = new Borrador(PANTALON)
        borrador.setColorPrincipal(new Color(r,g,b))
        return borrador.crearPrenda()

    method fabricarCalzado()
        borrador = new Borrador(ZAPATOS)
        borrador.setColorPrincipal(new Color(r,g,b))
        return borrador.crearPrenda()    
~~~

![uml](https://www.plantuml.com/plantuml/png/jLF1Zfim4BtxAtnafMG_ORKkeLMYB208X_OIUOspwmfiD9XMsjN-Upqu3YIhScelnZFlpNiUUtZiBGSxj0qH3UzxceFKDQVlX1vKPwXr2w5Ft4fGdBR-sn0QcyO05RZcIWlLtIHBAGQd0yeu8U0jfnPNGeMJU36WU7H7FiZP5AtGCWxWHFjK8VNGJaIiobbnI8vbbIV5DYjMJeRjVx1DjWhGDlqQ81R7IPcve0nQeRbcx3dPCyVQ9In5dIefK8NjlsMRB0qLlY6axxSbMr522_QTRHXMPEbnNwMiI4giEyOLsnGPxfFom9voTwfBr_wwK4PfIy7yD7xtIq8j_PQ_3St4_s80U6tW_prEBoqAHoXyDuRXSgAWxjFng0rdyKZCmq2vTefkd3rfT8yihYuXG7Bm0pYVZaghau5MOj_TY9P39vq6X7YhJ-TOyEQDrmQB-NDlWGjBlSfMzrRPGIYZKUZ4dq493a7S6TBtKF9nWVChlqKI7cA15FkJpHihkTuD78_pTxy5amNbdNdLlVctofv6rxNvhTSFumGIN49c-YblgM68Blarg9TNYoKu5ClfoN2SqSjFS3-Ixn-efv7P-qvOO5-ZZJmX69wUX7TO3vtpcL59kCVFoACp7Thc3m00.png)
