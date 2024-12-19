# Guía de Estándares de Código Java

> Esta guía establece los estándares de codificación para asegurar la consistencia, calidad y facilidad de migración en el desarrollo de aplicaciones Java, garantizando que el código sea comprensible y manejable para todo el equipo de desarrollo, independientemente de la IDE que se utilice.

## Estándar de Codificación Utilizado

> Para garantizar la consistencia y calidad del código, seguimos las **Java Code Conventions** establecidas por Oracle. Estas convenciones abordan las mejores prácticas de formateo, nomenclatura y organización del código. Para los proyectos que utilizan **Apache Camel** y **Spring Boot**, hemos adaptado algunas reglas específicas, que se detallan más adelante.

> La especificación completa de las **Java Code Conventions** puede ser accedida en: [Java Code Conventions - Oracle](https://www.oracle.com/java/technologies/javase/codeconventions-introduction.html).

## Configuración del Archivo Checkstyle

> El archivo `checkstyle.xml` contiene reglas específicas para garantizar que el código siga las convenciones de estilo y las mejores prácticas recomendadas. Entre estas reglas, destacamos las siguientes:
> 
> - **Tamaño máximo de línea**: Limita la longitud de las líneas de código a 120 caracteres, para garantizar la legibilidad.
> - **Indentación y uso de espacios**: Definimos la indentación con 4 espacios y verificamos la organización de los imports y la correcta colocación de espacios en palabras clave.
> - **Reglas específicas para el uso de Apache Camel y Spring Boot**: Hemos incluido verificaciones para garantizar que las clases relacionadas con Camel sigan convenciones de nomenclatura adecuadas y que el uso de logs esté alineado con las mejores prácticas para estas tecnologías.
>
> A continuación, presentamos el contenido del archivo `checkstyle.xml` para que sea posible realizar la configuración en las IDEs y en el build de Gradle.

#### Ejemplo de archivo `checkstyle.xml` (común a todas las IDEs)

```xml
<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE module PUBLIC "-//Puppy Crawl//DTD Checkstyle Configuration 1.3//EN" "http://checkstyle.sourceforge.net/dtds/configuration_1_3.dtd">
<configuration>

    <!-- Definiendo el tamaño máximo de línea para el código -->
    <property name="lineLength" value="120"/>

    <!-- Verificando la indentación del código con 4 espacios -->
    <module name="Indentation">
        <property name="basicOffset" value="4"/>
        <property name="braceAdjustment" value="4"/>
        <property name="lineWrappingIndentation" value="4"/>
    </module>

    <!-- Garantizando que las clases e interfaces sean nombradas correctamente -->
    <module name="NamingConvention">
        <property name="format" value="^[A-Z][a-zA-Z0-9]*$"/>
    </module>

    <!-- Verifica el uso de espacios después de palabras clave y antes de paréntesis -->
    <module name="WhitespaceAround">
        <property name="tokens" value="METHOD_DECLARATION, METHOD_CALL, ASSIGNMENT, LITERAL_IF, LITERAL_FOR, LITERAL_WHILE, LITERAL_DO"/>
        <property name="checkSynthetic" value="true"/>
    </module>

    <!-- Verifica la organización de los imports -->
    <module name="ImportOrder">
        <property name="ordered" value="true"/>
        <property name="separated" value="true"/>
    </module>

    <!-- Garantizar el uso de llaves en bloques de código -->
    <module name="NeedBraces">
        <property name="ignoreSingleLine" value="false"/>
    </module>

    <!-- Forzar el uso del modificador de acceso adecuado -->
    <module name="VisibilityModifier">
        <property name="applyTo" value="all"/>
    </module>

    <!-- Garantizar que métodos y variables sigan las convenciones de nomenclatura -->
    <module name="MethodName">
        <property name="format" value="^[a-z][a-zA-Z0-9]*$"/>
    </module>

    <module name="LocalVariableName">
        <property name="format" value="^[a-z][a-zA-Z0-9]*$"/>
    </module>

    <!-- Garantizar que las clases sigan la convención de nomenclatura -->
    <module name="ClassName">
        <property name="format" value="^[A-Z][a-zA-Z0-9]*$"/>
    </module>

    <!-- Garantizar que la documentación JavaDoc esté presente -->
    <module name="JavadocMethod">
        <property name="minLines" value="3"/>
        <property name="allowMissingParamTags" value="true"/>
    </module>

    <module name="JavadocType">
        <property name="minLines" value="3"/>
    </module>

    <!-- Reglas específicas para uso con Camel -->
    <module name="RegexpSingleline">
        <property name="format" value=".*Camel.*"/>
        <property name="message" value="Las clases relacionadas con Camel deben seguir las convenciones de nomenclatura adecuadas."/>
    </module>

    <!-- Reglas específicas para uso con Spring Boot -->
    <module name="JavadocType">
        <property name="minLines" value="2"/>
    </module>

    <!-- Definiendo la estructura de los paquetes -->
    <module name="PackageName">
        <property name="format" value="^[a-z][a-z0-9]*(\.[a-z][a-z0-9]*)*$"/>
    </module>

    <!-- Verificar que todos los métodos tengan excepciones documentadas -->
    <module name="JavadocMethod">
        <property name="checkExceptions" value="true"/>
    </module>

    <!-- Verificación para evitar código muerto -->
    <module name="UnusedImports"/>

    <!-- Reglas para garantizar que el código esté utilizando buenas prácticas -->
    <module name="FinalLocalVariable"/>
    <module name="FinalParameters"/>

    <!-- Verificar el uso adecuado de logs (aplicable a Spring Boot, AWS, y Camel) -->
    <module name="Regexp">
        <property name="format" value=".*Logger.*"/>
        <property name="message" value="El nombre del Logger debe ser declarado como 'LOG'."/>
        <property name="illegalPattern" value=".*System\.out.*|.*System\.err.*"/>
    </module>

    <!-- Reglas para garantizar una buena formateo general -->
    <module name="LineLength">´
        <property name="max" value="120"/>
    </module>

</configuration>
```
	
### Integración con Gradle
Para integrar Checkstyle en Gradle, sigue estos pasos:

1. **Agregar el plugin de Checkstyle en el archivo `build.gradle`:**

```bash
plugins {
    id 'checkstyle'
}
```

2. **Configurar Checkstyle y el archivo `checkstyle.xml`:**
```bash
checkstyle {
    toolVersion = '10.0' // Versión de Checkstyle
    configFile = file('config/checkstyle/checkstyle.xml') // Ruta al archivo checkstyle.xml
}

```
3. **Añadir la tarea de Checkstyle en el build:**
```bash
task checkstyleMain(type: Checkstyle) {
    source 'src/main/java' // Código fuente
    include '**/*.java' // Archivos Java a verificar
    reports {
        html.enabled = true // Informe en HTML
        xml.enabled = true // Informe en XML
    }
}
```
- Con estos pasos, Checkstyle validará automáticamente tu código durante el proceso de build y generará informes sobre el cumplimiento de las reglas de estilo definidas en checkstyle.xml.

## Configuración en las IDEs 
> Para identificar la configuración necesaria para tu IDE, haz clic en la IDE que usas y sigue el paso a paso. 


- [VisualStudioCode](./vscode.md)
- [Intellij](./intellij.md) 
- [Eclipse](./eclispe.md)