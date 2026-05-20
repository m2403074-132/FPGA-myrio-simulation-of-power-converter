# FPGA-myrio-simulation-of-power-converter
name:
Optimized implementation methodology for HIL FPGA simulations for power converters

Autors
Aaron Iván Granjeno Gómez *
Rodolfo Orosco Guerrero *
Elías Rodríguez Segura *
Fany Rodríguez García * 
José Heriberto Rodríguez Estrada *
* Todos los autores pertenecen al instituto tecnológico de Celaya

ID 10594

El código desarrollado en LabVIEW FPGA implementa los modelos matemáticos discretizados de los convertidores DC-DC Boost, Buck y Boost-Buck, obtenidos mediante la aplicación de las leyes de Kirchhoff y discretizados con el método de Euler.
La programación se orientó a Hardware-in-the-Loop (HIL), estructurando las ecuaciones en forma acumulativa de productos entre constantes y señales condicionadas por variables lógicas (estado de interruptores y diodos). Esta optimización redujo el número de operaciones aritméticas y la latencia en ciclos de reloj, permitiendo que los cálculos se ejecutaran en tiempo real sobre la plataforma FPGA NI MyRIO 1900.
El código maneja las variables en formato de punto fijo UQ10.32, garantizando precisión en la representación de voltajes y corrientes. Además, se integró la generación de señales PWM para controlar el ciclo de trabajo de los interruptores, posibilitando la validación de los modelos frente a simulaciones de referencia en PSIM.
En síntesis, el código en LabVIEW FPGA constituye el núcleo de la simulación HIL, al traducir los modelos discretos en operaciones paralelas eficientes que reproducen fielmente el comportamiento dinámico de los convertidores en tiempo real

Codificación de Convertidor boost en FPGA
Para el desarrollo del programa es necesario crear un proyecto como se muestra en la Fig(1) en el programa de labview 2019, en la Fig(2) se muestra la manera conectar el FPGA utilizado, en este caso será la tarjeta Myrio 1900 de National instruments, para la búsqueda de la tarjeta utilizada se da click derecho en el proyecto principal, en “new” y “Targets and devices” y aparecerá una ventana donde al tener la tarjeta conectada aparecerá en la carpeta "myRIO".

<img width="278" height="370" alt="image" src="https://github.com/user-attachments/assets/f3f592ca-bfc2-4a00-9842-6a718ae9d075" />

Fig 1

<img width="330" height="373" alt="image" src="https://github.com/user-attachments/assets/d5e0e4a3-f3cc-474c-b2df-df3a2cdfefd8" />

Fig 2
 
Una vez creado el proyecto, se desarrollaron tres módulos independientes correspondientes a los convertidores Boost, Buck y Boost-Buck, tal como se muestra en la Figura 1. Cada uno de estos programas fue implementado para su simulación en el FPGA, permitiendo el análisis del comportamiento de los convertidores. En dichos módulos únicamente es posible modificar parámetros como el voltaje de entrada/salida y el ciclo de trabajo del control. Para ajustar los valores de la simulación, se pueden redefinir las constantes mediante cálculos basados en los elementos del circuito, o bien sustituirlas por indicadores que faciliten un manejo más intuitivo. Esta metodología se aplica de manera uniforme en todos los programas de simulación de los convertidores.

En este proyecto se emplea el software PSIM en su versión 9.1, el cual fue utilizado para el diseño y simulación de diferentes convertidores de potencia. Entre los programas cargados en la plataforma se encuentran los convertidores Boost, Buck y Boost-Buck, cada uno configurado para analizar su comportamiento bajo distintas condiciones de operación.
El programa se subió a la plataforma con el objetivo de documentar y mostrar cómo se utiliza en conjunto con otras herramientas de análisis. En particular, se configuró la opción que permite realizar el procesamiento de datos en LabVIEW, lo que facilita la comparación y el estudio de los resultados obtenidos en las simulaciones.
Dentro de la interfaz, el usuario puede modificar parámetros clave como los valores de los componentes electrónicos (resistencias, inductores, capacitores, etc.) o el ciclo de trabajo (duty cycle) de los convertidores. Estas modificaciones permiten observar cómo varían las respuestas del sistema y obtener resultados diferentes según las condiciones establecidas, lo que convierte al programa en una herramienta flexible para el análisis y la experimentación.


