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

![uml](https://www.plantuml.com/plantuml/png/hPF1RkCW48RlF0L7Lqhw25LPnxjAbCQM7HzsBn75f6M5mS9uLshLT-y0nQM9v5Cl16R--NucZEz7IusTUecOfEE8AyDLH_4hmaSnQ6nXGVY1Mcu4nNtubGZdMcg3cLihePWOBe8DPnDmZD00ChIdsBeLOGQ89msGx0QzeM0QhC0oZybPTbt1rTGdGgYgI7qiJarR5VMsh5U08Vi_P5EkOcfx-1bJ9C-BfeH34rcnEUbxBlO4LBk271odBMf78VjVvQOyn8hGa9FljmrPOOHhyfjiYAie3wTzUo1rqRYwKzwIJLswVT4SoKC5jvgx3d-NmmXbiT5_TTZzuwRZOKjV9lcf_w6DeLqekNuS-HslCtBho9aZt_XZf6UH7iAvPviFUCRIOo99dB8Bvo3oxfbtXm0pd9emWUbuj4gSjUcvQtpmsMOQE31CF6_L-UFCg7oXdNR5z744CBCuKBPgjC9EJ6ZbG6VwQ0IZ9iB14B_6ahSvNNtnMnJ19PP4URXPsbX3rMwYwNMk_HPC5iWx_Qn6_Rta8CFhJlzNwpi_WiWjCVBvLLvAun3DyRKHJyyMCdv8biAfeP_H-IkuzUBREnnaA7tVEHVLNxEIdrqoFZsAxx2U1l19f2Z-ZzUPUp2TUlaE.png)
