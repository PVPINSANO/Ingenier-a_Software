
# HU-01 
Como usuario del sistema, quiero iniciar sesión con mi correo institucional y contraseña,
para acceder a mis funciones según mi rol (Docente, Estudiante, director).

## HU-01 Inicio de session:
Escenario 1 Inicio de sesion valido

Given: Dado que el usuario tiene una cuenta registrada en el sistema y esté en la pagina de inicio de sesión.
When: Cuando el Usuario escriba correctamente su correo institucional y contraseña y da click en el boton iniciar sesion.
Then: Entonces podrá acceder a las funciones disponibles segun el rol que identifique el sistema  (docente, Estudiante, director).

Escenario 2 Inicio de sesion inalido:
Given: Dado que el Usuario no tiene una cuenta registrada en el Sistema,
When: Cuando el Usuario digite una correo institucional y una contraseña y le click en iniciar sesion.
Then: Entonces el Sistema no lo dejara ingresar al tener credenciales incorrectos o inexistentes.

Validaciones:
Verificar que el correo y contraseña estén guardados en el Sistema
Verificar que el correo y contraseña estén diligenciadps correctamente.

# HU-02 
Escenario 2: Solicitud de cambio de clave

Dado que: Dado que el usuario está en la pantalla de Login y presiona la opción “Olvidé mi contraseña”.

Cuando: Cuando ingresa su correo institucional registrado y hace clic en “Enviar enlace de recuperación”.

Entonces: Entonces el sistema valida que el correo existe en la base de datos, envía un enlace con un token temporal a su correo institucional y muestra un mensaje en pantalla confirmando el envío.
Validaciones 
•	HU02-01 - Inicio de sesión exitoso - Correo y contraseña correctos - Generación de token y redirección al Dashboard.

•	HU02-02 - Credenciales incorrectas - Correo o contraseña no coinciden - Mensaje de error "Credenciales inválidas".

# HU-03
Escenario 3: Restricción de acceso por rol

Dado que: Dado que un estudiante con sesión activa intenta acceder directamente a la ruta o URL de “Registro de Notas” (función exclusiva de docentes).

Cuando: Cuando el servidor/sistema intercepta la petición y valida los permisos asignados a su rol.

Entonces: Entonces el sistema deniega el acceso, muestra una pantalla o mensaje de error " Sin Autorización" y lo redirige automáticamente a su login de estudiante.

Validaciones 
•	HU03-01 - Restricción por rol - Estudiante con sesión activa ingresa a la URL "registro-notas" - Denegación de acceso, mensaje "Sin Autorización" y redirección al login de estudiante.

•	HU03-02 - Intento de manipulación de rol - Estudiante modifica el token de sesión en el navegador para simular ser docente - El servidor valida el token, bloquea la petición y redirige al login.

Verificar que los roles (Estudiante, docente, director) estén bien estructurados en cuanto a opciones.
## HU-04: Registrar la asistencia diaria a clase:  
Escenario 1: Asistencia
Given: Dado que el docente necesita registrar la asistencia o inasistencia diaria de los estudiantes tendrá las opciones de asistió y no asistió.
When: Cuando el estudiante este presente en la clase, selecciona la opción asistió.
Then: El sistema registrara la asistencia del estudiante junto con la fecha.

Escenario 2 inasistencia
Given:  Dado que el docente necesita registrar la asistencia o inasistencia diaria de los estudiantes tendrá las opciones de asistió y no asistió.
When: Cuando el estudiante no esté presente, se debe seleccionar la opción no asistió.
Then: Entonces el sistema registrará la inasistencia del estudiante junto con la fecha.
Validaciones:
Verificar que cuando se seleccione cualquiera de las dos opciones, esta se registre correctamente.
Verificar que el estudiante tenga una opción (no puede tener asistencia y a la vez no tener asistencia).
Verificar que el estudiante este en

# HU-05: Registro de calificaciones 
Escenario 1: asignar nota.
Given: dado que el docente necesita registra las notas, tendrá disponible unas casillas para colocar la nota
When: Cuando el estudiante tenga una nota, la nota debe ser asignada a un a casilla
Then: Entonces el sistema guardara la nota.

Escenario 2. Nota no asignada
Give: dado que el docente necesita registrar las notas de los estudiantes, tendrá disponible casillas para colocar la nota.
When: Cuando el estudiante no tenga notas, la casilla quedara vacía y quedara con un 0 
Then: Entonces el sistema debe guardar la nota del estudiante (0)
Validaciones:
Verificar que las notas queden guardadas correctamente.
Verificar que las notas solo se le asignen a una actividad y a un solo estudiante.
Verificar que la nota este en el rango permitido según la institución (0-5 o  0-10). 


# HU-06: Visualizar alertas por inasistencia

Escenario 1: Generación y visualización de alerta roja
Dado que: que un estudiante tenga registrado un porcentaje de 
inasistencias superior al 15%.
Cuando: el sistema actualiza o verifica el porcentaje de inasistencias del 
estudiante.
Entonces: el sistema debe generar una alerta roja y mostrarla al director 
de programa para que pueda intervenir preventivamente.
Escenario 2: Porcentaje de inasistencias permitido
Dado que: que un estudiante tenga registrado un porcentaje de 
inasistencias igual o inferior al 15%.
Cuando: el sistema verifica el porcentaje de inasistencias del estudiante.
Entonces: el sistema no debe generar una alerta roja para el estudiante.
Validaciones
1. Verificar que el sistema genere y muestre una alerta roja cuando un 
estudiante supere el 15% de inasistencias. 
2. Verificar que el sistema no genere una alerta roja cuando el 
porcentaje de inasistencias sea igual o inferior al 15%.

## # HU-07 : Recibir alertas por bajo promedio

Escenario 1: Generación de alerta amarilla
Dado que: que un estudiante tenga registrado un promedio ponderado 
inferior a 3.0.
Cuando: el sistema verifique y actualice el promedio ponderado del 
estudiante.
Entonces: el sistema debe generar una alerta amarilla para el director, 
indicando que el estudiante requiere asesoría. 

Escenario 2: Estudiante sin alerta
Dado que: que un estudiante tenga registrado un promedio ponderado 
igual o superior a 3.0.
Cuando: el sistema verifique y actualice el promedio ponderado del 
estudiante.
Entonces: el sistema no debe generar una alerta amarilla para ese 
estudiante.
Validaciones
1. Verificar que el sistema genere una alerta amarilla cuando el 
promedio ponderado del estudiante sea inferior a 3.0. 
2. Verificar que el sistema no genere una alerta amarilla cuando el 
promedio ponderado sea igual o superior a 3.0.

# HU-08 : Solicitar tutoría de académica.
Escenario 1: Solicitud exitosa
Given (Dado que): que el estudiante en riesgo ha ingresado al portal móvil y tiene habilitada la 
opción de tutorías académicas.
When (Cuando): selecciona la opción de solicitar tutoría, elige la asignatura y confirma la 
solicitud.
Then (Entonces): el sistema debe registrar la solicitud y mostrar un mensaje confirmando que la 
tutoría fue solicitada correctamente.
Escenario 2: Datos imcompletos
Given (Dado): que el estudiante en riesgo se encuentra en el formulario de solicitud de tutoría.
When (Cuando): intenta enviar la solicitud sin seleccionar una asignatura.
Then (Entonces): el sistema debe impedir el envío y mostrar un mensaje indicando que debe 
seleccionar una asignatura.
Validaciones
1. Verificar que un estudiante en riesgo pueda seleccionar una asignatura y enviar 
correctamente la solicitud de tutoría.
2. Verificar que el sistema no permita enviar la solicitud cuando el estudiante no haya 
seleccionado una asignatura y que muestre el mensaje correspondiente.
# HU-09: Agendar y confirmar citas de acompañamiento
Escenario 1: Agendar una cita.
Given (Dado): que el tutor/psicólogo ha ingresado al portal y tiene estudiantes asignados.
When (Cuando): selecciona un estudiante, elige una fecha y hora disponible y confirma la cita.
Then (Entonces): el sistema debe registrar la cita y mostrar un mensaje indicando que fue 
agendada correctamente.
Escenario 2: Confirmar una cita.
Given (Dado): que existe una cita previamente agendada con un estudiante asignado.
When (Cuando): el tutor/psicólogo selecciona la cita y pulsa la opción "Confirmar".
Then (Entonces): el sistema debe actualizar el estado de la cita a "Confirmada" y mostrar la 
confirmación correspondiente.
Validaciones:
1. Verificar que el tutor/psicólogo pueda seleccionar un estudiante asignado, elegir una 
fecha y hora disponible y agendar correctamente la cita.
2. Verificar que una cita previamente agendada pueda cambiar su estado a confirmada 
cuando el tutor/psicólogo seleccione la opción correspondiente.
