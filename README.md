# POLLUTED PROTOTYPE IN JQUERY
![Esta es una imagen](https://1.bp.blogspot.com/-OyKrIuQlH0s/VyAKTW2fvfI/AAAAAAAAWGQ/PthNgy1c3sYgGfFq7UJoSrKoSqTAALnJwCLcB/s1600/Jar%2BJar%2BBinks%2BSith.jpg)

**¿Qué es Polluted Prototype?**

Primeramente, la vulnerabilidad por contaminación de prototipo, se refiere a la capacidad 
de inyectar propiedades en prototipos de construcciones de lenguaje JavaScript existentes, 
como objetos. Prototype es un atributo relacionado con Object, el cual se utiliza como un 
mecanismo que permite a los objetos JavaScript heredar características de uno a otro, y el uso 
de funciones inseguras como merge, clone, extend y asignación de rutas en objetos JSON
maliciosos, para su manipulación. 
Por lo tanto, si un atacante sobrescribe el prototipo de un objeto JavaScript 
predeterminado, al modificar el prototipo de un objeto en un solo lugar, entonces el 
comportamiento de todos los objetos podría verse afectado en toda la aplicación, permitiéndole
realizar ataques como la inserción de propiedades en el código JavaScript de la aplicación,
ataques de denegación de servicio, la activación de excepciones de JavaScript, la ejecución 
remota de código, y inyección código malicioso

**¿Cómo comprobarlo?**

- Abrir la consola del navegador sobre la web que queremos comprobar
- Ejecutar el siguiente comando:

   > var pollutedtest = '{ "propiedadejemplo" : "a", "__proto__" : { "isVulnerable" : true } }'; var testObject = jQuery.extend(true, {}, JSON.parse(pollutedtest )); if (typeof {}.isVulnerable !== 'undefined' && {}.isVulnerable === true) { alert("Vulnerable 🚨 :(\na polluted prototype") } else { alert("Nice! :)\nprotegido ante Prototype Pollution") }
    
   Tras ejecutarlo se abrirá una ventana emergente indicando si es vulnerable
   
**Vulnerable:  **

![image](https://user-images.githubusercontent.com/93614373/175272782-6c8d35cb-a6fd-4713-a97a-6efdd708f43f.png)

**No vulnerable:**

![image](https://user-images.githubusercontent.com/93614373/175272988-f98c1e97-f344-41fd-ae2a-4c0c23722489.png)
