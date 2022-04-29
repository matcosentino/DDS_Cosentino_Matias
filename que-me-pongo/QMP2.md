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

enum Categoria
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
        borrador = new Borrador(tipo.PANTALON)
        borrador.setMaterial(ACETATO)
        borrador.setColorPrincipal(new Color(r,g,b))
        return borrador.crearPrenda()

    method fabricarCalzado()
        borrador = new Borrador(tipo.ZAPATILLAS)
        borrador.setColorPrincipal(new Color(r,g,b))
        return borrador.crearPrenda()
        
class Johnson inherits Institucion
    method fabricarPrendaSuperior()
        borrador = new Borrador(tipo.CAMISA)
        borrador.setColorPrincipal(new Color(r,g,b))
        return borrador.crearPrenda()
    
    method fabricarPrendaInferior()
        borrador = new Borrador(tipo.PANTALON)
        borrador.setColorPrincipal(new Color(r,g,b))
        return borrador.crearPrenda()

    method fabricarCalzado()
        borrador = new Borrador(tipo.ZAPATOS)
        borrador.setColorPrincipal(new Color(r,g,b))
        return borrador.crearPrenda()    
~~~

![uml](https://www.plantuml.com/plantuml/png/hLDVRvim47_tf_0ZbP9-XAeUOHCH1GJXONk9NCTfFO6DZDcaLltky-4T2QdIgT9UZ7tt--Fp7VU3uzQDNKj4ouU1bbRg0wUlXEvKRwZp2w4Ft4chEEt2joKqDgsnLC1QAYrKVn6ifHYzZbN62rdUSUfW9LHuYIVZHQ8RyaQ2QR3obZ4cPzXxXjHZTm82gsJLBjdNJPbKQL6jl0pBVh1DiS9Kcd_558lZf2xyeKOjBAwTQauovb7RXEMWqoHL0QJiMx4fScI4WW2UfJLRKK8hzfrj632AV9yrEQkI6dZxk66Rge1zKk_OG-blDLSTdWjab7RKcfycx7v9Uv1Xor_6zeJ_Ogpb1sC_rHpxgUuCqe5o1Cetqn5V9qBv48uNuj722o5Bf-Z2EO0czyZ1wWF2Icx319wFHwFLqTXEGk7zbAt7NdeDY-TK7_-U1MzV_2C1cJyENbWu6bHIFJZbHg6C1g4ZVxHAS8lYtf2-8kLjJfSBlmz1U8ahe3ZSxBomckljoF4wL_okcdoal3NFUZ3_Lpd0wFfWVklrtJI211QCdFxAIoWEqHnVM_Nqx802G_6lC1fECph_1RSJ-FQE1XWvx--SG_GosyeZ9B7r1Fkm7dllSmOb-8xlC_VUTEpQFm00.png)
