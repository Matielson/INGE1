Problema 3

Roles:
- Persona
- Usuario

ID: Registrar Persona
TITULO: Como persona quiero registrarme para comprar bebidas.
REGLAS DE NEGOCIO:
- El mail no debe estar registrado
- La edad debe ser mayor a 18 años

Escenario 1: Registro exitoso
DADO que el mail vito@gmail.sos no se encuentra registrado en el sistema y tiene 88 años
CUANDO la persona ingresa nombre: vita, apellido: lopez, mail: vito@gmail.sos, edad: 88 y presiona el boton registrarse
ENTONCES la persona es registrada correctamente y se genera una contraseña que es enviada al mail ingresado en el registro

Escenario 2: Registro fallido por mail registrado
DADO que el mail mati@gmail.sos se encuentra registrado en el sistema y tiene 27 años
CUANDO la persona ingresa nombre: mati, apellido: brugo, mail: mati@gmail.sos, edad: 27 y presiona el boton registrarse
ENTONCES la persona no es registrada y el sistema muestra en pantalla "Mail ya registrado".

Escenario 3: Registro fallido por menor de edad
DADO que el mail tomy@gmail.sos se encuentra registrado en el sistema y tiene 15 años
CUANDO la persona ingresa: tomi, apellido, balboa, mail: tomy@gmail.sos, edad: 15 y presiona el boton registrarse
ENTONCES la persona no es registrada y el sistema muestra en pantalla el texto de la ley que impide la venta de bebidas alcoholicas a menores



ID: Inicio Sesion
TITULO: Como persona quiero iniciar sesion para compraar bebidas.

Escenario 1: Inicio de Sesion exitoso
DADO que el usuario sos@gmail.vos se encuentra registrado en el sistema y la contraseña es valida
CUANDO la persona ingresa el mail sos@gimear.vos y la contraseña sos123 y presiona iniciar sesion
ENTONCES la sesion es iniciada y el sistema muestra una lista de bebidas

Escenario 2: Inicio de Sesion fallido por usuario incorrecto
DADO que el usuario vos@gmail.sos no se encuentra registrado en el sistema y la contreaseña es valida
CUANDO la persona ingresa el mail sosvos@gmail.com y la contraseña sos245 y presiona iniciar sesion
ENTONCES la sesion no es iniciada y el sistema muestra en pantalla "Datos incorrectos".

Escenario 3: Inicio de Sesion fallido por contraseña incorrecta
DADO que el usuario vito@gmail.com se encuentra registrado en el sistema y la contraseña no es valida
CUANDO la persona ingresa el mail vito@gmail.com y la contraseña 2456 y presiona iniciar sesion
ENTONCES la sesion no es iniciada y el sistema muestra en pantalla "Datos incorrectos".



ID: Seleccionar bebida
TITULO: Como usuario quiero seleccionar una bebida para hacer una compra

Escenario 1: Seleccion exitosa
DADO que el usuario selecciona una bebida con disponibilidad
CUANDO el usuario toca el boton seleccionar bebida
ENTONCES se agrega la bebida a la compra y el sistema muestra en pantalla "Bebida agregada exitosamente"

Escenario 2: Seleccion fallida
DADO que el usuario selecciona una bebida sin disponibilidad
CUANDO el usuario toca el boton seleccionar bebida
ENTONCES no se agrega la bebida a la compra y el sistema muestra en pantalla "Bebida sin disponibilidad"



ID: Comprar bebidas
TITULO: Como usuario quiero comprar las bebidas seleccionadas para conocer el monto de los producto elegidos.

REGLAS DE NEGOCIO:
- Si es usuario premium, se le hace un 20% de descuento
- Si el monto de la compra supera $4500, se le hace 10% de descuento

Escenario 1: Compra exitosa sin descuento
DADO que el usuario pedro@gmail.com no es premium y el total es de 3500
CUANDO el usuario pedro@gmail.com apreta "Confirmar compra"
ENTONCES el sistema muestra en pantalla la totalidad de la compra sin descuento.

Escenario 2: Compra exitosa con descuento del 20%
DADO que el usuario marcos@gmail.com es premium y el total es de 3700
CUANDO el usuario marcos@gmail.com apreta "Confirmar compra"
ENTONCES el sistema muestra en pantalla la totalidad de la compra con un descuento del 20%

Escenario 3: Compra exitosa con descuento del 10%
DADO que el usuario mati@gmail.com no es premium y el total es de 7000
CUANDO el usuario mati@gmail.com apreta "Confirmar compra"
ENTONCES el sistema muestra en pantalla la totalidad de la compra con un descuento del 10%

Escenario 4: Compra exitosa con descuento del 10% y del 20%
DADO que el usuario juan@gmail.com es premium y el total es de 8000
CUANDO el usuario juan@gmail.com apreta "Confirmar compra"
ENTONCES el sistema muestra en pantalla la totalidad de la compra con un descuento del 30%

Escenario 5: Compra fallida por no seleccion de bebidas
DADO que el usuario carlos@gmail.com es premium y el total es de 0
CUANDO el usuario carlos@gmail.com apreta "Confirmar compra"
ENTONCES el sistema muestra en pantalla "No hay bebidas seleccionadas"
