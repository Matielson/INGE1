# Problema 3

## Roles

* Persona
* Usuario

---

# HU 1 — Registrar Persona

## ID: Registrar Persona

### Título

**Como persona quiero registrarme para comprar bebidas.**

### Reglas de Negocio

* El mail no debe estar registrado.
* La edad debe ser mayor a 18 años.

### Criterios de Aceptación

#### Escenario 1: Registro exitoso

**DADO** que el mail `vito@gmail.sos` no se encuentra registrado en el sistema y tiene 88 años.

**CUANDO** la persona ingresa nombre `vita`, apellido `lopez`, mail `vito@gmail.sos`, edad `88` y presiona el botón **"Registrarse"**.

**ENTONCES** la persona es registrada correctamente y se genera una contraseña que es enviada al mail ingresado en el registro.

#### Escenario 2: Registro fallido por mail registrado

**DADO** que el mail `mati@gmail.sos` se encuentra registrado en el sistema y tiene 27 años.

**CUANDO** la persona ingresa nombre `mati`, apellido `brugo`, mail `mati@gmail.sos`, edad `27` y presiona el botón **"Registrarse"**.

**ENTONCES** la persona no es registrada y el sistema muestra en pantalla:

> "Mail ya registrado."

#### Escenario 3: Registro fallido por menor de edad

**DADO** que el mail `tomy@gmail.sos` se encuentra registrado en el sistema y tiene 15 años.

**CUANDO** la persona ingresa nombre `tomi`, apellido `balboa`, mail `tomy@gmail.sos`, edad `15` y presiona el botón **"Registrarse"**.

**ENTONCES** la persona no es registrada y el sistema muestra en pantalla el texto de la ley que impide la venta de bebidas alcohólicas a menores.

---

# HU 2 — Inicio Sesión

## ID: Inicio Sesión

### Título

**Como persona quiero iniciar sesión para comprar bebidas.**

### Criterios de Aceptación

#### Escenario 1: Inicio de Sesión exitoso

**DADO** que el usuario `sos@gmail.vos` se encuentra registrado en el sistema y la contraseña es válida.

**CUANDO** la persona ingresa el mail `sos@gimear.vos` y la contraseña `sos123` y presiona **"Iniciar sesión"**.

**ENTONCES** la sesión es iniciada y el sistema muestra una lista de bebidas.

#### Escenario 2: Inicio de Sesión fallido por usuario incorrecto

**DADO** que el usuario `vos@gmail.sos` no se encuentra registrado en el sistema y la contraseña es válida.

**CUANDO** la persona ingresa el mail `sosvos@gmail.com` y la contraseña `sos245` y presiona **"Iniciar sesión"**.

**ENTONCES** la sesión no es iniciada y el sistema muestra en pantalla:

> "Datos incorrectos."

#### Escenario 3: Inicio de Sesión fallido por contraseña incorrecta

**DADO** que el usuario `vito@gmail.com` se encuentra registrado en el sistema y la contraseña no es válida.

**CUANDO** la persona ingresa el mail `vito@gmail.com` y la contraseña `2456` y presiona **"Iniciar sesión"**.

**ENTONCES** la sesión no es iniciada y el sistema muestra en pantalla:

> "Datos incorrectos."

---

# HU 3 — Seleccionar Bebida

## ID: Seleccionar Bebida

### Título

**Como usuario quiero seleccionar una bebida para hacer una compra.**

### Criterios de Aceptación

#### Escenario 1: Selección exitosa

**DADO** que el usuario selecciona una bebida con disponibilidad.

**CUANDO** el usuario toca el botón **"Seleccionar bebida"**.

**ENTONCES** se agrega la bebida a la compra y el sistema muestra en pantalla:

> "Bebida agregada exitosamente."

#### Escenario 2: Selección fallida

**DADO** que el usuario selecciona una bebida sin disponibilidad.

**CUANDO** el usuario toca el botón **"Seleccionar bebida"**.

**ENTONCES** no se agrega la bebida a la compra y el sistema muestra en pantalla:

> "Bebida sin disponibilidad."

---

# HU 4 — Comprar Bebidas

## ID: Comprar Bebidas

### Título

**Como usuario quiero comprar las bebidas seleccionadas para conocer el monto de los productos elegidos.**

### Reglas de Negocio

* Si es usuario premium, se le hace un 20% de descuento.
* Si el monto de la compra supera $4500, se le hace un 10% de descuento.

### Criterios de Aceptación

#### Escenario 1: Compra exitosa sin descuento

**DADO** que el usuario `pedro@gmail.com` no es premium y el total es de `$3500`.

**CUANDO** el usuario `pedro@gmail.com` aprieta **"Confirmar compra"**.

**ENTONCES** el sistema muestra en pantalla la totalidad de la compra sin descuento.

#### Escenario 2: Compra exitosa con descuento del 20%

**DADO** que el usuario `marcos@gmail.com` es premium y el total es de `$3700`.

**CUANDO** el usuario `marcos@gmail.com` aprieta **"Confirmar compra"**.

**ENTONCES** el sistema muestra en pantalla la totalidad de la compra con un descuento del 20%.

#### Escenario 3: Compra exitosa con descuento del 10%

**DADO** que el usuario `mati@gmail.com` no es premium y el total es de `$7000`.

**CUANDO** el usuario `mati@gmail.com` aprieta **"Confirmar compra"**.

**ENTONCES** el sistema muestra en pantalla la totalidad de la compra con un descuento del 10%.

#### Escenario 4: Compra exitosa con descuento del 10% y del 20%

**DADO** que el usuario `juan@gmail.com` es premium y el total es de `$8000`.

**CUANDO** el usuario `juan@gmail.com` aprieta **"Confirmar compra"**.

**ENTONCES** el sistema muestra en pantalla la totalidad de la compra con un descuento del 30%.

#### Escenario 5: Compra fallida por no selección de bebidas

**DADO** que el usuario `carlos@gmail.com` es premium y el total es de `$0`.

**CUANDO** el usuario `carlos@gmail.com` aprieta **"Confirmar compra"**.

**ENTONCES** el sistema muestra en pantalla:

> "No hay bebidas seleccionadas."
