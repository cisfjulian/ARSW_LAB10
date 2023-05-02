### Escuela Colombiana de Ingeniería
### Arquitecturas de Software - ARSW

## Escalamiento en Azure con Maquinas Virtuales, Sacale Sets y Service Plans

### Dependencias
* Cree una cuenta gratuita dentro de Azure. Para hacerlo puede guiarse de esta [documentación](https://azure.microsoft.com/es-es/free/students/). Al hacerlo usted contará con $100 USD para gastar durante 12 meses.
Antes de iniciar con el laboratorio, revise la siguiente documentación sobre las [Azure Functions](https://www.c-sharpcorner.com/article/an-overview-of-azure-functions/)

### Parte 0 - Entendiendo el escenario de calidad

Adjunto a este laboratorio usted podrá encontrar una aplicación totalmente desarrollada que tiene como objetivo calcular el enésimo valor de la secuencia de Fibonnaci.

**Escalabilidad**
Cuando un conjunto de usuarios consulta un enésimo número (superior a 1000000) de la secuencia de Fibonacci de forma concurrente y el sistema se encuentra bajo condiciones normales de operación, todas las peticiones deben ser respondidas y el consumo de CPU del sistema no puede superar el 70%.

### Escalabilidad Serverless (Functions)

1. Cree una Function App tal cual como se muestra en las  imagenes.

![](images/part3/part3-function-config.png)

![](images/part3/part3-function-configii.png)

2. Instale la extensión de **Azure Functions** para Visual Studio Code.

![](images/part3/part3-install-extension.png)

3. Despliegue la Function de Fibonacci a Azure usando Visual Studio Code. La primera vez que lo haga se le va a pedir autenticarse, siga las instrucciones.

![](images/part3/part3-deploy-function-1.png)

![](images/part3/part3-deploy-function-2.png)

4. Dirijase al portal de Azure y pruebe la function.

![](images/part3/part3-test-function.png)

5. Modifique la coleción de POSTMAN con NEWMAN de tal forma que pueda enviar 10 peticiones concurrentes. Verifique los resultados y presente un informe.

6. Cree una nueva Function que resuleva el problema de Fibonacci pero esta vez utilice un enfoque recursivo con memoization. Pruebe la función varias veces, después no haga nada por al menos 5 minutos. Pruebe la función de nuevo con los valores anteriores. ¿Cuál es el comportamiento?.

**Solución**

![](https://i.gyazo.com/c724ec92e721aedf086bf5c19d8be5fe.png)
![](https://i.gyazo.com/d07c9305d2d9fc47a3dc230d7141171f.png)
![](https://i.gyazo.com/038b966bdb12ca35a0afe96be1412fb8.png)
![](https://i.gyazo.com/ca3ee5804f9e35cae076899503287d9e.png)

**Respuestas Preguntas**

* ¿Qué es un Azure Function?

es un servicio de computación sin servidor de Microsoft Azure que permite a los desarrolladores ejecutar código en la nube sin tener que preocuparse por la infraestructura subyacente. Permite a los desarrolladores crear y ejecutar pequeñas piezas de código que se ejecutan de forma independiente y responden a eventos o desencadenadores específicos.

* ¿Qué es serverless?

Es un modelo de computación en la nube en el que el proveedor de la nube gestiona automáticamente los recursos de infraestructura subyacentes necesarios para ejecutar y escalar las aplicaciones. Donde los desarrolladores pueden centrarse en escribir y desplegar el código de su aplicación en forma de funciones pequeñas y autosuficientes.

* ¿Qué es el runtime y que implica seleccionarlo al momento de crear el Function App?

Se refiere al entorno de ejecución en tiempo de ejecución de un programa o aplicación. Este entorno proporciona los recursos necesarios para que el programa se ejecute, incluyendo la memoria, el procesador y los controladores de dispositivos, así como las bibliotecas y herramientas necesarias para la ejecución del código. Al momento de seleccionarlo determinamos cual va a ser este entorno en el cual ejecutaremos la app.

* ¿Por qué es necesario crear un Storage Account de la mano de un Function App?

Ya que es un lugar donde la funcion puede almacenar sus archivos, y permite un acceso escalable y seguro de archivos y datos. Permitiendo mejorar la capacidad de la funcion para procesar datos y realizar las tareas necesarias.

* ¿Cuáles son los tipos de planes para un Function App?, ¿En qué se diferencias?, mencione ventajas y desventajas de cada uno de ellos.

- Consumption Plan: que es basado en que se paga por lo usado. Azure escala automaticamente en funcion de la carga de trabajo. Hecho para cargas ligeras.

- App Service Plan: Se ejecuta en una maquina virtual dedicada, el pago es por la capacidad reservada de esta maquina. La funcion se ejecuta en la maquina virtual y se esacala manualmente dependiendo de la carga. 

- Premium Plan: Es parecido al app service, trabaja con una maquina virtual dedicada pero con una mayor capacidad de procesamiento y memoria. Hecho para tener el mayor control dela infraestructura.

* ¿Por qué la memoization falla o no funciona de forma correcta?

La razón por la que el mecanismo de recursividad falla o no funciona correctamente al implementarlo, es porque los valores buscados se almacenan para optimizar su futura búsqueda. Sin embargo, debido al gran tamaño de los números que se ingresan en las diferentes consultas, la memoria se consume rápidamente, lo que impide que la función funcione adecuadamente.

* ¿Cómo funciona el sistema de facturación de las Function App?

Primero basado en el plan de servicio si es por consumo o App Service Plan. A partir de esto el tiempo de ejecucion, el numero de solicitud realizadas, el consumo de recursos como el procesamiento o almacenamiento y si hay servicios como el Storage o el Event Grid. Estos son los factores que utiliza el sistema de facturacion para la function App. Y finalmente segun la region tambien varian los precios.

* Informe

En los pantallazos adjuntos se ve el desarrollo del laboratorio
