~~~
interface ServicioMeteorologico
  List<Map<String, Object>> getClima();
  Integer getTemperatura();

public class ServicioAccuWeather implements ServicioMeteorologico
    List<Map<String, Object>> ultimaTemp;
    LocalDate proximaExpiracion
    AccuWeatherAPI api
    Integer tiempoExpiracion
    String ciudad

    ServicioAccuWeather(AccuWeatherAPI api, Integer tiempoExpiracion, String ciudad)
        this.api = api;
        this.tiempoExpiracion = tiempoExpiracion;
        this.ciudad = ciudad;

    List<Map<String, Object>> getClima()
    if (this.ultimaTemp == null || this.expiro()) {
            this.ultimaTemp = api.getWeather(this.ciudad)
            this.proximaExpiracion = LocalDate.now().plus(this.tiempoExpiracion)
        }
    return this.ultimaTemp;

    boolean expiro()
        return LocalDate.now().isAfter(this.proximaExpiracion);
       
    Integer getTemperatura() {
        return this.getClima().get(0).get("Temperature").get("Value");


class Prenda
    Integer temperaturaMaxima
    
    public boolean aptaParaTemperatura(Integer temperaturaActual) {
        return this.temperaturaMaxima < temperaturaActual;

class Atuendo
  Prenda prendaSuperior
  Prenda prendaInferior
  Prenda calzado

  constructor(Prenda prendaSuperior, Prenda prendaInferior, Prenda calzado)
    this.prendaSuperior = prendaSuperior;
    this.prendaInferior = prendaInferior;
    this.calzado = calzado;


class Asesor
    ServicioMeteorologico servicioMeteorologico
    List<Prenda> prendas;
    
    constructor(ServicioMeteorologico servicioMeteorologico, List<Prenda> prendas)
        this.servicioMeteorologico = servicioMeteorologico
        this.prendas = prendas

    Atuendo sugerirAtuendo()
        return new Atuendo(sugerirPrenda(Categoria.PARTE_SUPERIOR), sugerirPrenda(Categoria.PARTE_INFERIOR),sugerirPrenda(Categoria.CALZADO))

    Prenda sugerirPrenda(Categoria categoria)
        return prendas.stream()
                .filter(prenda -> prenda.categoria().equals(categoria))
                .filter(prenda -> prenda.aptaParaTemperatura(servicioMeteorologico.getTemperatura()))
                .findFirst().get()
~~~

![uml](http://www.plantuml.com/plantuml/png/jLHTRziW57tdL_3eIcr_mLIL9TwKAXzMd6ZQNgfRGb8csrZNq4sj-jztmU0wLHHr3tt1SEyvvrx3WTlE0bfNLqnMq7MyGDNiWBymlj6juPO6nXTW5MhWTV-j69-OoY2NVYnq8tNxBbWgwKW7jI4XX1guzIFZiyQgWq9kLTqg1EiG5l1N-vG4IXdIpouOXzP20GYRDrmsuWXf7LGNx9N5laEtrFKaYGnonygUeHfNZu34AiHwaz-Nso9VprRhIv8HyrzYkhfCgTdoMqg9oIGlLxGearRQdofiMpuNXBhBnTBhRFErLn7pxwlfQfaOSKy8Ff-Luf8plXO_nLHuncfvFzyknJelFUz-iXNJzShFyt8Z5WLrDVnrt76IqOtbQ7wRVlQaSAVwAJoxwWt_rI32pk3ddM-dh1VElF15MARDoP9w7mvY1KRnJ8wN2N9SAJkk7EL3zInKfu141TXxE1kvGrX7eM2GDYHBrogImBIUDVkubb0zqnPvBZnqf2ijxqLcJMUrTLARnWljuG6r1DmsUc-mLjwrBudoEgIBetfdGTJ4ET2axspyNoKqTmvIEwVhdIboHldEF3QT-GnbqQckT-1ST_PBpxs9vz3HcRe3oM1_PCHCaNIimsKEchgn2lSW5IyLFccfpK9PPP2iSj0odFY1d5JfcWmHvkCNPTHMeWiftGy5zb7XnyaZaYXcaHS3cTHk1xk0Zg_hrSxyQQvkmXLaVaYHjrVfFJJTeY6E-l1eAH4koVdeK2vSqU4Dk0xWwnlUmzZOtqCkeO-phgLKF26MJ7ZbMYeomh5eeXEPo4sjfHR-BnoTT5sflHtr4yEdmMc7Jjk5dN11_DkFurFXOrCmTajzkBhg_W40.png)
