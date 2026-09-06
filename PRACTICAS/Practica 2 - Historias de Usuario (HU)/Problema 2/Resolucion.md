**Roles:**

- Usuario
- Conserje

**Historias de Usuario:**

- Reservar Hospedaje
- Check In
- Check Out

#### **ID: Reservar Hospedaje**

**TITULO:** Como usuario quiero reservar un hospedaje para hospedarme

**REGLAS DE NEGOCIO:**
- La fecha de ingreso debe estar dentro de los 90 dias a partir de la fecha actual.
- Las estadias no pueden durar mas de 15 dias.
##### CRITERIOS DE ACEPTACION:

###### **Escenario 1:** Reserva exitosa
**DADO** que la fecha de ingreso esta dentro de los 90 dias a partir de la fecha actual y la estadia dura 15 o menos dias
**CUANDO** el usuario ingresa la fecha de ingreso: 08/05/26, la fecha de egreso: 18/05/26, hotel elegido: Hotel del Rey y 5 personas hospedadas, y apreta "Reservar"
**ENTONCES** se confirma la reserva y le envia al usuario por correo el codigo de reserva y un enlace para continuar el pago

###### **Escenario 2:** Reserva fallida debido a que la fecha de ingreso esta fuera de los 90 dias a partir de la fecha actual.
**DADO** que la fecha de ingreso esta fuera de los 90 dias a partir de la fecha actual
**CUANDO** el usuario ingresa la fecha de ingreso 12/12/26, fecha de egreso 17/12/26, hotel elegido: Gran Brizo y 4 personas hospedadas, y apreta "Reservar"
**ENTONCES** no se efectua la reserva y se informa "Reserva fallida, fecha de ingreso mayor a 90 dias de la fecha actual"

###### **Escenario 3**: Reserva fallida debido a que la estadia es superior a 15 dias.
**DADO** que la fecha de ingreso esta dentro de los 90 dias a partir de la fecha actual y la estadia dura mas de 15 dias
**CUANDO** el usuario ingresa la fecha de ingreso 04/09/26, fecha de egreso 20/10/26, hotel elegido: Hotel del Rey y 2 personas hospedadas, y apreta "Reservar"
**ENTONCES** no se efectua la reserva y se informa "Reserva fallida, estadia superior a 15 dias."


#### **ID: Check In**

**TITULO:** Como usuario quiero realizar el check in para hospedarme

**REGLAS DE NEGOCIO:**
- El codigo ingresado pertenezca a una reserva de la fecha actual
- Solo puede realizarse despues de las 10am y hasta las 23:59pm

**CRITERIOS DE ACEPTACION:**
###### **Escenario 1:** Check In Exitoso
**DADO** que el codigo ingresado pertenece a una reserva y el check in se realiza entre las 10am y las 23:59pm
**CUANDO** el usuario ingresa el codigo de reserva 666 y presiona "Realizar Check In"
**ENTONCES** el sistema informa la habitacion asignada y le manda mensaje a alguno de los conserjes del hotel para que guíen al usuario hasta la habitación asignada y otro mensaje a los botones para que se hagan cargo de las valijas

###### **Escenario 2:** Check In Fallido por codigo incorrecto
**DADO** que el check in se realiza entre las 10am y las 23:59pm pero el codigo ingresado no pertenece a una reserva de la fecha actual
**CUANDO** el usuario ingresa el codigo de reserva 2222 y presiona "Realizar Check In"
**ENTONCES** el sistema informa que el codigo ingresado no es valido

###### **Escenario 3:** Check In Fallido por fuera de rango de horario establecido
**DADO** que el check in no se realiza entre las 10am y las 23:59pm
**CUANDO** el usuario 
**ENTONCES** el sistema informa "Aun no se encuentran habilitados los ingresos al hotel"

#### **ID: Check Out**

**TITULO:** Como conserje quiero hacer el check out de una habitacion para que pueda ser reservada

**REGLAS DE NEGOCIO:**
- Solo se puede realizar el check out de una habitacion sin gastos.

**CRITERIOS DE ACEPTACION:**
###### **Escenario 1:** Check Out Exitoso
**DADO** que el numero de habitacion ingresado no tiene gastos sin pagar
**CUANDO** el conserje ingresa el numero de habitacion 101 y presiona "Realizar Check Out"
**ENTONCES** el sistema envia un mensaje a las mucamas del hotel avisando que la habitación puede limpiarse

###### **Escenario 2:** Check In Fallido
**DADO** que el numero de habitacion ingresado tiene gastos sin pagar
**CUANDO** el conserje ingresa el numero de habitacion 102 y presiona "Realizar Check Out"
**ENTONCES** el sistema informa al conserje que no puede hacerse el check out hasta que no se abonen los gastos realizados
