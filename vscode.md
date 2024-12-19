# Cómo Usar Checkstyle en VSCode

**1. Instalar la Extensión de Checkstyle**

* Abre Visual Studio Code.

* Ve a la barra lateral izquierda y haz clic en el ícono de Extensiones (o presiona Ctrl+Shift+X en Windows/Linux).

* En la barra de búsqueda, escribe Checkstyle for Java.

* Encuentra la extensión Checkstyle for Java desarrollada por Shawn y haz clic en Install.

* Después de la instalación, la extensión estará lista para ser configurada y utilizada en VSCode.


**2. Configurar o Checkstyle com o Arquivo Existente**

* Abre la paleta de comandos (Ctrl+Shift+P en Windows/Linux).

* Escribe Checkstyle: Configure y selecciona la opción Checkstyle: Configure.

* Selecciona Use an existing checkstyle.xml.

* Navega hasta el archivo checkstyle.xml que ya tienes y selecciónalo.

* Este puede ser un archivo local o puedes usar un archivo de configuración almacenado en un repositorio en línea.

* Si el archivo checkstyle.xml está en un repositorio en línea, puedes usarlo directamente insertando la URL del archivo de configuración.


**3. Ejecutar la Verificación de Checkstyle**

- Después de configurar el archivo checkstyle.xml, abre la paleta de comandos (Ctrl+Shift+P en Windows/Linux).

- Escribe Checkstyle: Check y selecciona la opción Checkstyle: Check para ejecutar la verificación.


- La extensión analizará el código Java en tu proyecto según las reglas definidas en el archivo de configuración checkstyle.xml.

**4. Corregir los Errores**

- Los resultados del análisis de Checkstyle aparecerán en el panel de Problemas de VSCode, y los errores se listarán con detalles.

- Haz clic en los errores listados para navegar directamente hasta el código donde se encontró el problema y corrígelo según las reglas de estilo.



**5.  Configuración de Verificación Automática (Opcional)**

- La extensión de Checkstyle también permite configurar la verificación automática al guardar los archivos.

- Para habilitar esta configuración: Ve a las configuraciones de VSCode (Archivo > Preferencias > Configuración en Windows/Linux).

- Busca "Checkstyle" y activa la opción Check on Save.

- Esto hará que VSCode ejecute Checkstyle automáticamente cada vez que guardes el archivo.