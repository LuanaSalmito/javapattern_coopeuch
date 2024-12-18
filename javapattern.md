# Guía de Estándares de Código Java


> Esta guía establece los estándares de codificación para asegurar la consistencia, calidad y facilidad de migración en el desarrollo de aplicaciones Java, garantizando que el código sea comprensible y manejable para todo el equipo de desarrollo, independientemente de la IDE que se utilice.

 
### Estándar de Codificación Utilizado

> Para garantizar la consistencia y calidad del código, seguimos las **Java Code Conventions** establecidas por Oracle. Estas convenciones abordan las mejores prácticas de formateo, nomenclatura y organización del código.

> La especificación completa está disponible en: [Java Code Conventions - Oracle](https://www.oracle.com/java/technologies/javase/codeconventions-introduction.html).

#### Uso do Checkstyle

> Checkstyle es una herramienta que ayuda a garantizar la consistencia y calidad del código, validando si sigue las reglas de estilo predefinidas. Se puede integrar tanto en el proceso de build de Gradle como en las principales IDEs (Eclipse, IntelliJ IDEA y VSCode).

#### Configuración de Checkstyle

> Checkstyle depende de un archivo de configuración, normalmente llamado checkstyle.xml, que define las reglas de formateo y estilo del código. Este archivo puede ser utilizado de manera consistente en todas las herramientas para garantizar que todos los desarrolladores sigan las mismas convenciones de estilo.
	
#### Integración con Gradle

> Para integrar Checkstyle en Gradle, agrega el plugin Checkstyle al archivo build.gradle y apunta al archivo checkstyle.xml que contiene las reglas.

#### Ejemplo de archivo checkstyle.xml (común a todas las IDEs)

``` bash
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE module PUBLIC "-//CHECKSTYLE//DTD Checkstyle Configuration 1.3//EN" "http://checkstyle.sourceforge.net/dtds/configuration_1_3.dtd">

<configuration>

    <!-- Definiendo reglas generales de Checkstyle -->
    <module name="Checker">

        <!-- Longitud de línea: Limita a 100 caracteres para facilitar la lectura, pero sin exceder 80 cuando sea posible -->
        <module name="LineLength">
            <property name="max" value="100"/>
        </module>

        <!-- Indentación: Usando 4 espacios, como recomienda Oracle -->
        <module name="Indentation">
            <property name="tabWidth" value="4"/>
            <property name="indentation" value="4"/>
        </module>

        <!-- Reglas para los espacios en blanco alrededor de los operadores -->
        <module name="WhitespaceAround">
            <property name="checkSpaceBefore" value="true"/>
            <property name="checkSpaceAfter" value="true"/>
        </module>

        <!-- Verificar el uso adecuado de Javadoc en métodos y clases -->
        <module name="JavadocStyle">
            <property name="allowMissingJavadoc" value="false"/>
            <property name="minLines" value="1"/>
        </module>

        <!-- Verificar la convención de nombres de paquetes (minúsculas y estructura jerárquica) -->
        <module name="PackageName">
            <property name="format" value="^[a-z]+([.][a-z][a-z0-9_]*)*$"/>
        </module>

        <!-- Organizar las importaciones con reglas específicas -->
        <module name="ImportOrder">
            <property name="groups" value="javax, java, org, com"/>
            <property name="separated" value="true"/>
            <property name="ordered" value="true"/>
        </module>

        <!-- Definir convenciones para el nombre de métodos (camelCase) -->
        <module name="MethodName">
            <property name="format" value="^[a-z][a-zA-Z0-9]*$"/>
        </module>

        <!-- Definir convenciones para el nombre de clases (PascalCase) -->
        <module name="TypeName">
            <property name="format" value="^[A-Z][a-zA-Z0-9]*$"/>
        </module>

        <!-- Los nombres de las variables deben usar la convención camelCase -->
        <module name="VariableName">
            <property name="format" value="^[a-z][a-zA-Z0-9]*$"/>
        </module>

        <!-- Verificar el orden de los modificadores de acceso y la visibilidad de las clases -->
        <module name="ModifiersOrder"/>

        <!-- Limitar la complejidad de los métodos y funciones para evitar métodos demasiado complejos -->
        <module name="CyclomaticComplexity">
            <property name="threshold" value="10"/>
        </module>

        <!-- Regla para garantizar que los archivos no sean excesivamente grandes -->
        <module name="FileLength">
            <property name="max" value="1000"/>
        </module>

        <!-- Validar que el código no utilice caracteres tabulados (tab) para la indentación -->
        <module name="FileTabCharacter">
            <property name="useSpace" value="true"/>
        </module>

        <!-- Garantizar que haya una clase por archivo (Java) -->
        <module name="SingleClassFile"/>

        <!-- Asegurar que las clases tengan al menos una línea en blanco después de las importaciones -->
        <module name="SeparatorLine">
            <property name="lineCount" value="1"/>
        </module>

    </module>

</configuration>



## Configuración en las IDEs 
> Para identificar la configuración necesaria para tu IDE, haz clic en la IDE que usas y sigue el paso a paso. 


- [VisualStudioCode](./vscode.md)
- [Intellij](./intellij.md) 
- [Eclipse](./eclispe.md)


