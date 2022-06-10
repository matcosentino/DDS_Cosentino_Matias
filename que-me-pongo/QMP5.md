~~~
class Usuario
 List<Guardarropa> guardarropas;

 method agregarGuadarropa(Guardarropa unGuardarropa)
  guardarropas.add(unGuardarropa)

 method quitarGuardarropa(Guardarropa unGuardarropa)
  guardarropas.remove(unGuardarropa)

	
class Guardarropa
 List<Prenda> prendas
 List<PropuestaModificacion> propuestas
    
 method agregarPrenda(Prenda unaPrenda)
  prendas.add(unaPrenda)

 method quitarPrenda(Prenda unaPrenda)
  prendas.remove(unaPrenda)
	
 method propuestasDeModificacionPendientes()
  propuestas.filter( propuesta => propuesta.estado == Estado.PENDIENTE )
 

abstract class PropuestaModificacion
 EstadoPropuesta estado = EstadoPropuesta.PENDIENTE

 method aceptarEn(Guardarropa unGuardarropa)
  realizarAceptacionEn(unGuardarropa)
  estado = EstadoPropuesta.ACEPTADA

 method rehazar()
  estado = EstadoPropuesta.RECHAZADA

 abstract method realizarEn(Guardarropa unGuardarropa)
 abstract method deshacerEn(Guardarropa unGuardarropa)

	
class PropuestaAgregar extends PropuestaModificacion
 Prenda prenda

 method realizarEn(Guardarropa unGuardarropa)
  unGuardarropa.agregarPrenda(prenda)

 method deshacerEn(Guardarropa unGuardarropa)
  unGuardarropa.quitarPrenda(prenda)


class PropuestaQuitar extends PropuestaModificacion
 Prenda prenda

 method realizarEn(Guardarropa unGuardarropa)
  unGuardarropa.quitarPrenda(prenda)

 method deshacerEn(Guardarropa unGuardarropa)
  unGuardarropa.agregarPrenda(prenda)


enum EstadoPropuesta
 PENDIENTE, APROBADA, RECHAZADA
~~~

![uml](https://www.plantuml.com/plantuml/png/jLNDZkCs3BxhANHqW9bvWY9ODN6t6UJ7ZHCKtSk0goY92iToQMbRp7RVlPHbUJI64MmFUt4aVXy_KXJ5V6Wje7MtYiaAsfONgEeJyA-C7tHZkAKFunkm2ZNmM_Yj65-OoY2N_bleMkfcP2oLTAI3sf0GmWsuzL_6LxLL5uNSgbkZ4An3sC0_saCI23AadyqOXyP20GY7DrwM-0Xf7LGpzes5l4EsbFKYYWno8sNoKBMx9KJoAiJ-aB-KnoBVhtRx1v8HwqzYkNk8q6hxIuJ4Of6NEzgKKIlMf-hAbgy5iPvpiVKwntplLSJwuswvsqQFlYP4NwzAyS0Ptui_n59uZztsPNtSYdrUUh-NnL4izpk_pik3s1IKrN3glk8aeslBqVnfmkgBmfCAItXrrHl_PuC89uC_xdvRPRrmveLdtJOM9ulgmTo95TYBPpBP9fGqKZQA74XTzAoBJWQ92Z3qS9PqXx2EJ5s3D1rOkaQH1CRzgZxtUmdLAvN8-yBdbdIbvK5aLRTMMoUrgRtG6JwZbe37MfyDtfJlsg_HvTi05-_YtILH4lT8Yv1PUguIwcS7bCvWUJRNkZMfvTWwNwsksNHhV_f8MweVcWRc_FAsQHc72weB835wMvRWbDHVJjiEnaby29amXh3XYFE-tcsq4iUfriB6dFHPI_3L9L8q4wzr5uKQ-olCPj4IhtbutBDuW8Y4K37liJK9ibHf-89mhMghsb1gJKiyWrIyLFX54sMZh398tNZHiYliHTb5fMz03dwT3gsaBD5TIEb-Ls2l2h_VEN4InQhtwmsPrEu4fzb4qquMs7ldP3kP0UQgspCEKZKMCAz7TuzANk4Lnis92YhzEi5FE2VLNabsn8bdIvCKuVvyVk6s-dQPeFxcj9rYnWaxFfydvjlbAjyUycwAvyKXJDnzllXLVAArz-t57a_cx_fntWr9vZ-3PVZV65FZd1lig2zNIq0tnkvRXt3T41scz5D7VfhtHsJf11gmo7wFkeQW_ismE2OUNVFuxvmdH1RdnGJKUyVaOXB_pnodJpGdeu4bQ_xayIJb51j9fb0iv_JJP1ClBfJc-_an-kW1li-YKcTAOlgniKbhz1dtAHk_XNWpzxNZSxXB_a3bSxVgFm00.png)
