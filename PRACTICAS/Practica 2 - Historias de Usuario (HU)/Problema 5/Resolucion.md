# Problema 5

## Roles

* Empleado
* Administrativo

---

# HU 1 — Registro Usuario

## ID: Registro Usuario

### Título

**Como empleado quiero registrarme en el sistema para solicitar una licencia.**

### Criterios de Aceptación

#### Escenario 1: Registro exitoso

**DADO** un nombre de usuario único y una contraseña.

**CUANDO** el empleado ingresa el nombre de usuario `"Pepe123"` y la contraseña `"Sos12345"`.

**ENTONCES** el sistema registra el usuario e informa:

> "Registro exitoso."

#### Escenario 2: Registro fallido por usuario ya registrado

**DADO** un nombre de usuario ya registrado y una contraseña.

**CUANDO** el empleado ingresa el nombre de usuario `"Pepe123"` y la contraseña `"Sos12345"`.

**ENTONCES** el sistema no registra el usuario e informa:

> "Registro fallido, usuario ya registrado."

---

# HU 2 — Inicio Sesión

## ID: Inicio Sesión

### Título

**Como empleado quiero iniciar sesión en el sistema para solicitar una licencia.**

### Criterios de Aceptación

#### Escenario 1: Inicio exitoso

**DADO** un nombre de usuario y contraseña registrados en el sistema.

**CUANDO** el empleado ingresa el nombre de usuario `"Pepe123"` y la contraseña `"Sos12345"`.

**ENTONCES** el sistema inicia sesión e informa:

> "Inicio de sesión exitoso."

#### Escenario 2: Inicio fallido por usuario incorrecto

**DADO** un nombre de usuario no registrado en el sistema y una contraseña.

**CUANDO** el empleado ingresa el nombre de usuario `"Pepe123"` y la contraseña `"Sos12345"`.

**ENTONCES** el sistema no inicia sesión e informa:

> "Datos incorrectos."

#### Escenario 3: Inicio fallido por contraseña incorrecta

**DADO** un nombre de usuario registrado en el sistema y una contraseña incorrecta.

**CUANDO** el empleado ingresa el nombre de usuario `"Pepe123"` y la contraseña `"Sos12345"`.

**ENTONCES** el sistema no inicia sesión e informa:

> "Datos incorrectos."

---

# HU 3 — Cierre Sesión

## ID: Cierre Sesión

### Título

**Como empleado quiero cerrar sesión para finalizar mi sesión en el sistema.**

### Criterios de Aceptación

#### Escenario 1: Cierre de sesión exitoso

**DADO** un empleado que se encuentra autenticado en el sistema.

**CUANDO** presiona el botón **"Cerrar Sesión"**.

**ENTONCES** el sistema cierra la sesión.

---

# HU 4 — Solicitar Licencia

## ID: Solicitar Licencia

### Título

**Como empleado quiero solicitar una licencia para justificar el ausente.**

### Reglas de Negocio

* El empleado debe tener más de 1 mes de antigüedad.

### Criterios de Aceptación

#### Escenario 1: Solicitud exitosa

**DADO** que el empleado tiene más de 1 mes de antigüedad.

**CUANDO** ingresa el tipo de licencia `presencial`, la fecha de inicio de reposo `08-08-26`, la matrícula de su médico personal `234523`, el diagnóstico `NOSE`, para `titular` y presiona **"Solicitar"**.

**ENTONCES** el sistema registra la solicitud e informa:

> "Solicitud exitosa."

#### Escenario 2: Solicitud fallida por antigüedad insuficiente

**DADO** que el empleado tiene menos de 1 mes de antigüedad.

**CUANDO** ingresa el tipo de licencia `presencial`, la fecha de inicio de reposo `02-08-26`, la matrícula de su médico personal `234523`, el diagnóstico `NOSE`, para `titular` y presiona **"Solicitar"**.

**ENTONCES** el sistema no registra la solicitud e informa:

> "Solicitud fallida por antigüedad insuficiente."

---

# HU 5 — Consultar Licencias

## ID: Consultar Licencias

### Título

**Como administrativo quiero consultar las licencias solicitadas para ver el informe de los ausentes.**

### Reglas de Negocio

* Solo se puede imprimir un informe por mes para cada empleado.

### Criterios de Aceptación

#### Escenario 1: Consulta exitosa

**DADO** un CUIL perteneciente a un empleado y sin consulta en el último mes.

**CUANDO** el administrativo ingresa el CUIL del empleado `20-55555555-5` y un rango de fechas `08-08-26` hasta `08-09-26` y presiona **"Consultar informe"**.

**ENTONCES** el sistema muestra en pantalla el informe correspondiente.

#### Escenario 2: Consulta fallida por CUIL inválido

**DADO** un CUIL no perteneciente a un empleado y sin consulta en el último mes.

**CUANDO** el administrativo ingresa el CUIL del empleado `20-55555555-5` y un rango de fechas `08-08-26` hasta `08-09-26` y presiona **"Consultar informe"**.

**ENTONCES** el sistema informa:

> "CUIL no registrado como empleado."

#### Escenario 3: Consulta fallida por informe ya solicitado en este mes

**DADO** un CUIL perteneciente a un empleado y con su informe consultado en este mes.

**CUANDO** el administrativo ingresa el CUIL del empleado `20-55555555-5` y un rango de fechas `08-08-26` hasta `08-09-26` y presiona **"Consultar informe"**.

**ENTONCES** el sistema informa:

> "Informe ya solicitado este mes."
