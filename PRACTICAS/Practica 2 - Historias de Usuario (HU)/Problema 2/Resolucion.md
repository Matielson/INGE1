# Historias de Usuario — Problema 2

## Roles

* Usuario
* Conserje

## Historias de Usuario

* Reservar Hospedaje
* Check In
* Check Out

---

# HU 1 — Reservar Hospedaje

## ID: Reservar Hospedaje

### Título

**Como usuario quiero reservar un hospedaje para hospedarme.**

### Reglas de Negocio

* La fecha de ingreso debe estar dentro de los 90 días a partir de la fecha actual.
* Las estadías no pueden durar más de 15 días.

### Criterios de Aceptación

#### Escenario 1: Reserva exitosa

**DADO** que la fecha de ingreso está dentro de los 90 días a partir de la fecha actual y la estadía dura 15 o menos días.

**CUANDO** el usuario ingresa la fecha de ingreso `08/05/26`, la fecha de egreso `18/05/26`, hotel elegido `Hotel del Rey` y `5` personas hospedadas, y aprieta **"Reservar"**.

**ENTONCES** se confirma la reserva y se le envía al usuario por correo el código de reserva y un enlace para continuar el pago.

#### Escenario 2: Reserva fallida por fecha de ingreso

**DADO** que la fecha de ingreso está fuera de los 90 días a partir de la fecha actual.

**CUANDO** el usuario ingresa la fecha de ingreso `12/12/26`, la fecha de egreso `17/12/26`, hotel elegido `Gran Brizo` y `4` personas hospedadas, y aprieta **"Reservar"**.

**ENTONCES** no se efectúa la reserva y se informa:

> "Reserva fallida, fecha de ingreso mayor a 90 días de la fecha actual."

#### Escenario 3: Reserva fallida por estadía superior a 15 días

**DADO** que la fecha de ingreso está dentro de los 90 días a partir de la fecha actual y la estadía dura más de 15 días.

**CUANDO** el usuario ingresa la fecha de ingreso `04/09/26`, la fecha de egreso `20/10/26`, hotel elegido `Hotel del Rey` y `2` personas hospedadas, y aprieta **"Reservar"**.

**ENTONCES** no se efectúa la reserva y se informa:

> "Reserva fallida, estadía superior a 15 días."

---

# HU 2 — Check In

## ID: Check In

### Título

**Como usuario quiero realizar el check in para hospedarme.**

### Reglas de Negocio

* El código ingresado debe pertenecer a una reserva de la fecha actual.
* Solo puede realizarse después de las 10:00 y hasta las 23:59.

### Criterios de Aceptación

#### Escenario 1: Check In exitoso

**DADO** que el código ingresado pertenece a una reserva y el check in se realiza entre las 10:00 y las 23:59.

**CUANDO** el usuario ingresa el código de reserva `666` y presiona **"Realizar Check In"**.

**ENTONCES** el sistema informa la habitación asignada y le manda un mensaje a alguno de los conserjes del hotel para que guíe al usuario hasta la habitación asignada y otro mensaje a los botones para que se hagan cargo de las valijas.

#### Escenario 2: Check In fallido por código incorrecto

**DADO** que el check in se realiza entre las 10:00 y las 23:59 pero el código ingresado no pertenece a una reserva de la fecha actual.

**CUANDO** el usuario ingresa el código de reserva `2222` y presiona **"Realizar Check In"**.

**ENTONCES** el sistema informa que el código ingresado no es válido.

#### Escenario 3: Check In fallido por fuera del rango horario establecido

**DADO** que el check in no se realiza entre las 10:00 y las 23:59.

**CUANDO** el usuario intenta realizar el Check In.

**ENTONCES** el sistema informa:

> "Aún no se encuentran habilitados los ingresos al hotel."

---

# HU 3 — Check Out

## ID: Check Out

### Título

**Como conserje quiero hacer el check out de una habitación para que pueda ser reservada.**

### Reglas de Negocio

* Solo se puede realizar el check out de una habitación sin gastos.

### Criterios de Aceptación

#### Escenario 1: Check Out exitoso

**DADO** que el número de habitación ingresado no tiene gastos sin pagar.

**CUANDO** el conserje ingresa el número de habitación `101` y presiona **"Realizar Check Out"**.

**ENTONCES** el sistema envía un mensaje a las mucamas del hotel avisando que la habitación puede limpiarse.

#### Escenario 2: Check Out fallido

**DADO** que el número de habitación ingresado tiene gastos sin pagar.

**CUANDO** el conserje ingresa el número de habitación `102` y presiona **"Realizar Check Out"**.

**ENTONCES** el sistema informa al conserje que no puede hacerse el check out hasta que no se abonen los gastos realizados.
