#📚 Sistema de Registro y Control de Personal (E.B.N. Cristóbal Rojas)

##✨ Descripción del Proyecto
Este proyecto presenta un sistema integral que automatiza el registro y control de entrada y salida del personal de la Escuela Básica Nacional (E.B.N.) Cristóbal Rojas. Desarrollado con MIT App Inventor para la interfaz móvil, el sistema permite escanear códigos QR personalizados para registrar la asistencia del personal directamente en una base de datos en la nube. Es una combinación de varios componentes que facilitan una gestión de asistencia digital, eficiente y en tiempo real.

##🚀 Funcionalidades Clave
Registro de Asistencia por QR: El personal escanea su fotocheck (código QR único) con la aplicación móvil.

Consulta y Registro en Tiempo Real: La aplicación consulta los datos del personal (nombre, apellido, cargo, código, foto) y registra la fecha y hora exacta de entrada/salida desde el dispositivo móvil.

Base de Datos en la Nube (Google Sheets): Almacenamiento centralizado y seguro de todos los registros de asistencia y datos del personal.

Generación de QR Personalizados: Códigos QR únicos generados a través de macros de Excel y alojados en OneDrive para fácil acceso.

Integración con Formularios de Google: Utilizado para enviar y registrar la asistencia directamente en la hoja de cálculo.

##🛠️ Tecnologías Utilizadas
MIT App Inventor: Desarrollo de la aplicación móvil para Android (frontend y lógica de interacción).

Google Sheets: Base de datos en la nube para almacenar la información del personal y los registros de asistencia.

Google Apps Script: Backend personalizado para consultar y enviar datos a Google Sheets de forma programática.

Google Forms: Empleado para la recepción de los datos de asistencia enviados desde la aplicación móvil hacia Google Sheets.

Microsoft Excel (con Macros): Herramienta utilizada para la generación masiva y personalizada de códigos QR para cada miembro del personal.

Microsoft OneDrive: Almacenamiento en la nube de las imágenes de los códigos QR, accesibles por la aplicación.

##🔗 Arquitectura del Sistema y Flujo de Trabajo
El sistema opera bajo la siguiente secuencia lógica:

Preparación de Datos:

Una Hoja de Cálculo de Google sirve como base de datos principal con campos como: Código, Nombres, Apellidos, Cargo, Asistencia, Foto

Los códigos QR se generan mediante macros de Excel, cada uno asociado a un Código de personal, y se guardan en OneDrive.

Consulta de Datos (Google Apps Script):

Un Google Apps Script actúa como intermediario, permitiendo que la aplicación móvil consulte los datos del personal en Google Sheets (nombre, apellido, cargo, foto) basándose en el Código escaneado. La información se devuelve en formato JSON.

Registro de Asistencia (Google Forms):

Para registrar la asistencia, se utiliza un formulario de Google con campos específicos (Código del personal y Asistencia - que incluye hora y fecha de escaneo). La aplicación envía los datos directamente a este formulario.

Aplicación Móvil (App Inventor):

El usuario (personal de la E.B.N.) escanea su fotocheck QR.

El código QR leído se usa para consultar la información del personal (a través del Apps Script) y mostrarla en la app.

Simultáneamente, la app envía el Código del personal y la Hora/Fecha actual (del dispositivo) a Google Forms, registrando así la asistencia en Google Sheets.

##⚠️ Nota Importante: Privacidad de Datos y Configuración
Por motivos de privacidad y seguridad, este repositorio NO CONTIENE datos reales ni enlaces directos a las hojas de cálculo, formularios o scripts de Google utilizados en el entorno de producción. Las URLs y IDs dentro del archivo .aia y en la lógica del sistema han sido reemplazadas por placeholders (marcadores de posición).

Para que el proyecto sea funcional y puedas probarlo o adaptarlo, debera configurar sus propios servicios de Google, siguiendo la estructura descrita:

Pasos para Configurar tu Propio Entorno de Pruebas
Crea una Hoja de Cálculo de Google (Base de Datos Dummy):

Ve a Google Sheets (sheets.new).

Crea una hoja nueva con las mismas cabeceras de columna exactas que se utilizan en el proyecto original: Código, Nombres, Apellidos, Cargo, Asistencia, Foto

Rellénala con datos de prueba ficticios (¡nunca datos reales o sensibles!).

Copia el ID de esta hoja de cálculo (es la parte larga en la URL, entre /d/ y /edit).

Crea un Google Apps Script (Backend Dummy):

Ve a Google Apps Script (script.new).

Copia el código del Apps Script original (https://drive.google.com/file/u/0/d/11JT6SNGWm56ROCwzvyPhK9C6tAtAl-tt/view?usp=sharing&pli=1) y pégalo en tu nuevo script.

CRÍTICO: Modifica la variable SSID o la dirección de la hoja dentro de este script para que apunte al ID de tu nueva Hoja de Cálculo Dummy creada en el paso anterior.

Despliega el script como una Aplicación Web (Deploy as web app), con la versión 1 y con acceso para "Cualquiera" (Anyone).

Copia la URL de despliegue obtenida (https://script.google.com/macros/s/TU_NUEVO_ID_DE_DESPLIEGUE/exec).

Verifica la URL añadiéndole ?accion=consultar&num=CODIGO_DE_PRUEBA en tu navegador.

Crea un Google Form (Formulario Dummy de Asistencia):

Ve a Google Forms (forms.new).

Crea un nuevo formulario con dos campos principales que correspondan a la lógica de envío de asistencia:

Un campo de texto para el Código del Personal.

Un campo de texto para la Asistencia (donde se enviará la fecha y hora).

Haz clic en los tres puntos (...) en la esquina superior derecha del formulario y selecciona Obtener vínculo de prellenado (Get pre-filled link).

Rellena un valor de ejemplo en cada campo y haz clic en Obtener vínculo (Get Link).

De la URL generada, extrae los IDs de campo (las partes como entry.1399015751= y entry.723180202=).

Copia la URL base del formulario para la respuesta (https://docs.google.com/forms/d/TU_NUEVO_ID_DE_FORMULARIO/formResponse).

Actualiza el Archivo .aia en App Inventor:

Importa el archivo registro_qr.aia de este repositorio en tu entorno de MIT App Inventor.

En la sección de "Bloques", localiza los componentes que se conectan a Google Sheets/Forms/Apps Script.

Reemplaza las URLs o IDs de placeholder (ej., YOUR_APPS_SCRIPT_DEPLOYMENT_ID_HERE, YOUR_GOOGLE_FORM_ID_HERE, YOUR_FORM_FIELD_ID_1, etc.) con los IDs y URLs que obtuviste de tus propios servicios de Google creados en los pasos 1, 2 y 3.

Genera tus Propios Códigos QR y Aloja Imágenes (Opcional pero recomendado para pruebas):

Para probar la funcionalidad completa de la aplicación, deberás generar tus propios códigos QR que apunten a los Códigos de personal en tu Hoja de Cálculo Dummy.

También, aloja imágenes de prueba del personal en OneDrive y asegúrate de que las URLs de estas imágenes estén correctamente registradas en la columna Foto de tu Hoja de Cálculo Dummy.

Cómo Abrir y Explorar el Proyecto App Inventor (.aia)
Visita MIT App Inventor: Navega a ai2.appinventor.mit.edu.

Inicia Sesión: Inicia sesión con tu cuenta de Google.

Importar Proyecto: Ve a Projects (Proyectos) en el menú superior y selecciona Import project (.aia) from my computer (Importar proyecto (.aia) desde mi computadora).

Selecciona el Archivo: Sube el archivo .aia descargado de este repositorio.

Explora los Bloques: Una vez importado, podrás visualizar el diseño de la interfaz de usuario en la sección "Designer" y la lógica de programación detallada en la sección "Blocks".

##📄 Licencia
Este proyecto está bajo la Licencia MIT. Consulta el archivo LICENSE para más detalles.

