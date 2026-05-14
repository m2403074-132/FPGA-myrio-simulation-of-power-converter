# FPGA-myrio-simulation-of-power-converter
name:
Optimized implementation methodology for HIL FPGA simulations for power converters

Autors
Aaron Iván Granjeno Gómez
Rodolfo Orosco Guerrero
Elías Rodríguez Segura
Fany Rodríguez García
José Heriberto Rodríguez Estrada 

ID 10594

El código desarrollado en LabVIEW FPGA implementa los modelos matemáticos discretizados de los convertidores DC-DC Boost, Buck y Boost-Buck, obtenidos mediante la aplicación de las leyes de Kirchhoff y discretizados con el método de Euler.
La programación se orientó a Hardware-in-the-Loop (HIL), estructurando las ecuaciones en forma acumulativa de productos entre constantes y señales condicionadas por variables lógicas (estado de interruptores y diodos). Esta optimización redujo el número de operaciones aritméticas y la latencia en ciclos de reloj, permitiendo que los cálculos se ejecutaran en tiempo real sobre la plataforma FPGA NI MyRIO 1900.
El código maneja las variables en formato de punto fijo UQ10.32, garantizando precisión en la representación de voltajes y corrientes. Además, se integró la generación de señales PWM para controlar el ciclo de trabajo de los interruptores, posibilitando la validación de los modelos frente a simulaciones de referencia en PSIM.
En síntesis, el código en LabVIEW FPGA constituye el núcleo de la simulación HIL, al traducir los modelos discretos en operaciones paralelas eficientes que reproducen fielmente el comportamiento dinámico de los convertidores en tiempo real



