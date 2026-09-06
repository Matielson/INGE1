# Problema 4

## Roles

* Usuario
* Administrador

---

# HU 1 — Solicitar Kit

## ID: Solicitar Kit

### Título

**Como usuario quiero solicitar un kit para grabar presentaciones, entrevistas o material audiovisual para trabajos académicos.**

### Reglas de Negocio

* El préstamo no puede durar más de 3 horas.
* Un usuario no puede solicitar un préstamo si tiene algún préstamo anterior activo.

### Criterios de Aceptación

#### Escenario 1: Préstamo exitoso

**DADO** que la duración del préstamo es de 2,5 hs y el usuario solicitante no tiene ningún préstamo anterior activo.

**CUANDO** el usuario ingresa tipo de kit `básico`, día `08-08-26`, hora de retiro `16 hs`, duración del préstamo `2,5 hs` y presiona **"Solicitar"**.

**ENTONCES** el sistema almacena la reserva e informa:

> "Préstamo exitoso."

#### Escenario 2: Préstamo fallido por duración mayor a la estipulada

**DADO** que la duración del préstamo es de 4 hs y el usuario solicitante no tiene ningún préstamo anterior activo.

**CUANDO** el usuario ingresa tipo de kit `avanzado`, día `05-08-26`, hora de retiro `12 hs`, duración del préstamo `4 hs` y presiona **"Solicitar"**.

**ENTONCES** el sistema no almacena la reserva e informa:

> "Préstamo fallido por duración mayor a 3 hs."

#### Escenario 3: Préstamo fallido por préstamo activo

**DADO** que la duración del préstamo es de 2 hs y el usuario solicitante tiene un préstamo anterior activo.

**CUANDO** el usuario ingresa tipo de kit `avanzado`, día `01-06-26`, hora de retiro `11 hs`, duración del préstamo `2 hs` y presiona **"Solicitar"**.

**ENTONCES** el sistema no almacena la reserva e informa:

> "Préstamo fallido por préstamo activo."

---

# HU 2 — Agregar Elemento

## ID: Agregar Elemento

### Título

**Como Administrador quiero agregar un elemento para que forme parte de un kit.**

### Reglas de Negocio

* El número de serie debe ser único.
* El precio de compra no puede superar el millón de pesos.

### Criterios de Aceptación

#### Escenario 1: Agregado exitoso de elemento nacional

**DADO** que el administrador ingresa un número de serie único, el precio de compra es menor a 1 millón de pesos y el elemento es nacional.

**CUANDO** el administrador ingresa el número de serie `555`, tipo de elemento `cámara`, precio de compra `$600.000`, origen de fabricación `Mendoza, Argentina` y fecha de alta `08-03-26` y aprieta **"Agregar"**.

**ENTONCES** el sistema agrega exitosamente el elemento e informa en pantalla:

> "Se agregó el elemento exitosamente."

#### Escenario 2: Agregado exitoso de elemento internacional

**DADO** que el administrador ingresa un número de serie único, el precio de compra es menor a 1 millón de pesos y el elemento no es nacional.

**CUANDO** el administrador ingresa el número de serie `343`, tipo de elemento `trípode`, precio de compra `$200.000`, origen de fabricación `China` y fecha de alta `08-04-26` y aprieta **"Agregar"**.

**ENTONCES** el sistema agrega exitosamente el elemento, le suma el impuesto adicional del 10% e informa en pantalla:

> "Se agregó el elemento exitosamente."

#### Escenario 3: Agregado fallido por número de serie repetido

**DADO** que el administrador ingresa un número de serie repetido y el precio de compra es menor a 1 millón de pesos.

**CUANDO** el administrador ingresa el número de serie `222`, tipo de elemento `micrófono`, precio de compra `$50.000`, origen de fabricación `BsAs, Argentina` y fecha de alta `08-05-26` y aprieta **"Agregar"**.

**ENTONCES** el sistema no agrega el elemento e informa en pantalla:

> "Número de serie repetido, no se pudo agregar el elemento."

#### Escenario 4: Agregado fallido por precio de compra superior al millón de pesos

**DADO** que el administrador ingresa un número de serie único y el precio de compra es mayor a 1 millón de pesos.

**CUANDO** el administrador ingresa el número de serie `333`, tipo de elemento `cámara`, precio de compra `$1.100.000`, origen de fabricación `BsAs, Argentina` y fecha de alta `08-06-26` y aprieta **"Agregar"**.

**ENTONCES** el sistema no agrega el elemento e informa en pantalla:

> "Precio de compra mayor a $1.000.000, no se pudo agregar el elemento."
