# Cómo Usar Checkstyle en IntelliJ IDEA

**1. Instalar el Plugin Checkstyle
Abra o IntelliJ IDEA.**

- Ve a Archivo > Configuración.

- En el menú de configuraciones, selecciona Plugins.

- En la pestaña Marketplace, busca Checkstyle.

- Haz clic en Instalar para agregar el plugin.

- Después de la instalación, reinicia IntelliJ IDEA.

**2. Configurar Checkstyle con el Archivo Existente**

- Ve a Archivo > Configuración > Herramientas > Checkstyle.
- Haz clic en el ícono + para agregar una nueva configuración de Checkstyle.

- Selecciona el archivo de configuración checkstyle.xml que ya tienes. Este archivo contiene las reglas de estilo que deseas aplicar.

- Define el Ámbito para especificar qué archivos o paquetes de tu proyecto serán analizados. Puede ser todo el proyecto o partes específicas.

**3. Ejecutar la Verificación de Checkstyle**

- Para ejecutar Checkstyle manualmente, ve al menú Herramientas > Checkstyle > Verificar Código con Checkstyle.

- Checkstyle analizará el código y mostrará los errores y advertencias basados en las reglas definidas en el archivo checkstyle.xml.


**4. Corregir los Errores**

- Los errores y advertencias se mostrarán en el panel de Checkstyle. Haz clic en los errores para ser redirigido al código y corregirlos según las recomendaciones de Checkstyle.

**5. Configuração de Verificação Automática (Opcional)**

- En el menú de configuraciones de Checkstyle, puedes configurar para realizar la verificación automáticamente cada vez que guardes o compiles el código.

