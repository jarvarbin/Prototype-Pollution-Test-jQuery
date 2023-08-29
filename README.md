# POLLUTED PROTOTYPE IN JQUERY
```
                                 _.-*'""'*-._
                              .-"            "-.
                            ,"                  ",
                          .'      _.-.--.-._      ',
                         /     .-'.-"    "-.'-.     \
                        /     /  /"'-.  .-'"\  \     \
                       :     :  :     ;:     ;  ;     ;
                       ;     :  ; *   !! *   :  ;     :
                       ;      ; :   .'  '.   ; :      :
                       :       \ \-'      '-/ /       ;
                        \       '.'-_    _-'.'       /
                         \        '*-"-+"-*'        /
                          '.          /|          .'
                            *,       / |        ,*
                             / '-_            _-'  \
                            /     "*-.____.-*"      \
                           /            |            \
                          :    :        |        ;    ;
                          |.--.;        |        :.--.|
                          (   ()        |        ()   )
                           '--^_        |        _^--'
                              | "'*--.._I_..--*'" |
                              | __..._  | _..._   |
                             .'"      `"'"     ''"'.
                             """""""""""""""""""""""
                                  POLLUTED PROTOTYPE
```
# ¿Qué es la Vulnerabilidad por Contaminación de Prototipo (Polluted Prototype)?

La vulnerabilidad por Contaminación de Prototipo, también conocida como "Prototype Pollution," es una clase de vulnerabilidad que se manifiesta en el entorno de programación de JavaScript. Esta vulnerabilidad surge debido a la naturaleza dinámica de JavaScript, que permite a los desarrolladores modificar prototipos de objetos durante la ejecución del programa.

## 🏷️ Conceptos Fundamentales

- **Prototipo**: En JavaScript, cada objeto tiene una propiedad especial llamada prototipo. Los prototipos permiten que los objetos hereden métodos y propiedades de otros objetos. Este mecanismo de herencia es la esencia del modelo de objetos basado en prototipos de JavaScript.

- **Contaminación**: El término se refiere al acto de añadir o modificar propiedades en el prototipo de un objeto.

## 🛠️ ¿Cómo Ocurre?

Cuando funciones como `merge`, `extend`, `clone`, o cualquier operación que involucre la copia profunda de objetos no validan adecuadamente las propiedades que se añaden o modifican, un atacante puede insertar propiedades maliciosas en el prototipo de un objeto. 

## 🌐 Impacto en la Aplicación

1. **Alteración del Comportamiento**: Al modificar una propiedad en el prototipo de un objeto, esta modificación se propaga a todos los objetos que hereden de ese prototipo, lo cual podría cambiar el comportamiento de toda la aplicación.

2. **Inserción de Código Malicioso**: Los atacantes pueden aprovecharse para inyectar código malicioso que podría ser ejecutado en el contexto de la aplicación.

3. **Denegación de Servicio (DoS)**: Un ataque exitoso podría desencadenar excepciones no manejadas, lo cual podría resultar en un fallo general de la aplicación.

4. **Ejecución Remota de Código**: En casos extremos, la vulnerabilidad podría ser explotada para ejecutar código arbitrario, comprometiendo la seguridad de la aplicación.

## 🛡️ Mitigación

- Validar todas las entradas que puedan modificar objetos o sus prototipos.
- Utilizar librerías que estén diseñadas para evitar este tipo de vulnerabilidad.
- Mantener actualizadas todas las dependencias del proyecto para beneficiarse de las últimas correcciones de seguridad.

## 🚨 Advertencia

La explotación de la vulnerabilidad por Contaminación de Prototipo puede tener serias implicaciones en la integridad y seguridad de una aplicación web. Por lo tanto, es crucial entender completamente este riesgo y tomar medidas preventivas adecuadas.

Con la comprensión adecuada y las contramedidas en su lugar, es posible mitigar los riesgos asociados con la contaminación del prototipo y fortalecer la seguridad de las aplicaciones basadas en JavaScript.

**¿Cómo comprobarlo?**

- Abrir la consola del navegador sobre la web que queremos comprobar
- Ejecutar el siguiente comando:

   > var pollutedtest = '{ "propiedadejemplo" : "a", "__proto__" : { "isVulnerable" : true } }'; var testObject = jQuery.extend(true, {}, JSON.parse(pollutedtest )); if (typeof {}.isVulnerable !== 'undefined' && {}.isVulnerable === true) { alert("Vulnerable 🚨 :(\na polluted prototype") } else { alert("Nice! :)\nprotegido ante Prototype Pollution") }
    
- Tras ejecutarlo se abrirá una ventana emergente indicando si es vulnerable
   
**Vulnerable:**

![image](https://user-images.githubusercontent.com/93614373/175272782-6c8d35cb-a6fd-4713-a97a-6efdd708f43f.png)

**No vulnerable:**

![image](https://user-images.githubusercontent.com/93614373/175272988-f98c1e97-f344-41fd-ae2a-4c0c23722489.png)


# What is Prototype Pollution Vulnerability?

The Prototype Pollution vulnerability, also known as "Prototype Pollution," is a class of vulnerability that manifests itself in the JavaScript programming environment. This vulnerability arises due to the dynamic nature of JavaScript, allowing developers to modify object prototypes during program execution.

## 🏷️ Fundamental Concepts

- **Prototype**: In JavaScript, each object has a special property called a prototype. Prototypes enable objects to inherit methods and properties from other objects. This inheritance mechanism is the essence of JavaScript's prototype-based object model.

- **Pollution**: The term refers to the act of adding or modifying properties in an object's prototype.

## 🛠️ How Does It Occur?

When functions like `merge`, `extend`, `clone`, or any operation involving deep object copying do not adequately validate the properties that are added or modified, an attacker can insert malicious properties into an object's prototype.

## 🌐 Impact on the Application

1. **Behaviour Alteration**: By modifying a property in an object's prototype, this change propagates to all objects inheriting from that prototype, potentially altering the behaviour of the entire application.

2. **Malicious Code Injection**: Attackers may exploit this to inject malicious code that could be executed in the application context.

3. **Denial of Service (DoS)**: A successful attack could trigger unhandled exceptions, possibly leading to an application-wide failure.

4. **Remote Code Execution**: In extreme cases, the vulnerability could be exploited to execute arbitrary code, compromising the application's security.

## 🛡️ Mitigation

- Validate all inputs that might modify objects or their prototypes.
- Use libraries that are designed to prevent this type of vulnerability.
- Keep all project dependencies up to date to benefit from the latest security patches.

## 🚨 Warning

Exploiting the Prototype Pollution vulnerability can have serious implications for the integrity and security of a web application. Therefore, it is crucial to fully understand this risk and take appropriate preventive measures.

With adequate understanding and countermeasures in place, it's possible to mitigate the risks associated with prototype pollution and strengthen the security of JavaScript-based applications.

**How to Check?**

- Open the browser console on the website you want to check.
- Run the following command:

  ```javascript
  var pollutedtest = '{ "exampleproperty" : "a", "__proto__" : { "isVulnerable" : true } }'; var testObject = jQuery.extend(true, {}, JSON.parse(pollutedtest )); if (typeof {}.isVulnerable !== 'undefined' && {}.isVulnerable === true) { alert("Vulnerable 🚨 :(\nA polluted prototype") } else { alert("Nice! :)\nProtected against Prototype Pollution") }
