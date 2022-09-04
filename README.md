# Proyecto-1_SISTEMAS-OPERATIVOS-I
PROYECTO 1
# Mí Repositorio 
#  Proyecto I Sistemas Operativos I

Proyecto simulador de procesos

## Introducción

El programa consiste en simular un gestor de procesos, para el cual se realizo  una aplicación con una interfaz gráfica similar a un administrador de tareas, la aplicación pretende mostrar la simulación donde se ejecutan varios procesos en maquina a través de un diseño grafico personalizado pero estos procesos requieren un tiempo de ejecución ya que deben esperar hasta que el proceso anterior sea ejecutado.

## Características
El programa es un gestor de procesos mismo que es utilizado para enfocar el trabajo, donde se persigue el mejoramiento continuo de las actividades de una organización mediante la identificación, selección, descripción, documentación y mejora continua de los procesos. para la representación del mismo se implementó una aplicación con interfaz gráfica la cuales utilizan elementos gráficos como iconos, menús e imágenes para facilitar el manejo del usuario.

## Contenido del Proyecto (Funciones)

Enumeración de las funciones del programa:

1. Función 1: Simulador de Procesos.
2. Función 2: asignación de usuario y nombre.
3. Función 3: Tiempo de ejecución. 
4. Función 4: lista de los procesos agregados.
5. Función 5: controla la CPU%.
6. Función 6: visualiza numero de procesos. 
7. Función 7: Uso de memoria.
8. Función 8: Visualización de procesos a ejecutar y ejecutados.
9. Función 9: Limitantes de RAM.   

### Función 1
El programa gráficamente es similar a un administrador de tareas cuya función es agregar y ejecutar procesos que se le ingresen.

---
### Función 2
El programa contiene un apartado para asignar un usuario y nombre del proceso para ser identificado y luego ser mostrado en un formulario.

---
### Función 3
Los procesos asignados al programa se proceden a ejecutar para luego ser mostrados en un formulario donde se muestra en un apartado el tiempo de ejecución en segundos de cada proceso.

---
### Función 4
Cuando se agregan procesos al programa estos pasan a ser enlistados para iniciar su ejecución y son mostrados en  un formulario con todos sus datos.

---
### Función 5 
El programa contiene un apartado donde se asignara un porcentaje del CPU  a un proceso para luego ser ejecutado ya que no se puede utilizar el 100% de la misma.

---
### Función 6 
Cuando se agrega un proceso a la lista esta enumera los procesos y muestra la cantidad de procesos agregados esperando su ejecución. 

---
### Función 7
La cantidad máxima de procesos en la tabla dependerá del uso de memoria por proceso que se esta ejecutando, si se intenta agregar uno cuando la memoria esta excedida este pasara a la cola de espera y luego de que el resto de procesos se terminen de ejecutar se ejecutaran los que están en espera para terminar los procesos. 

---
### Función 8
El programa contiene dos formularios,  en el primero se muestra cada proceso enlistado a ejecutar y en el segundo cada procesos enlistado ejecutado. 

---
### Función 9
En la pantalla del programa se solicitaran los datos generales del proceso para luego ser agregados en la tabla, pero se debe de tener en cuenta que la capacidad de la memoria RAM es de 8192. Cabe mencionar que si se ingresa un numero mayor a la capacidad que es 1024, esta se eliminara y lanzara un mensaje que se excede, dando lugar a escribir un numero aceptado dentro de los parámetros admitidos. 

---
## Funciones Código (textos)
```java 
int Contador;//Contador de procesos ingresados
    int NProceso;//muestra los numeros de procesos ejecutandose 
    int RAFAGA=0;//muestra Rafaga de ejecucion
    int Quantum=0;//muestra Quamtum en ejecucion
    int ResiduoRafaga=0;//muestra el residuo 
    int TiempoProceso=0;//Muestra el tiempo de procesado 
    int ValorBarra;//muestra procesos de barra
    int CantidadProcesos;//numeros de procesos finalizados
``` 
---
```java 
 //Esta funcion permite que la limitante de la ram no sea excedida.
private void jBAgregarActionPerformed(java.awt.event.ActionEvent evt) {                                          
       if((Integer.parseInt(RAM2.getText()))<=1024){
            Ingresar();
            RAM();
        }else{
            JOptionPane.showMessageDialog(null, "LAS LIMITANTE DE LA RAM ES EXCEDIDA TIENE QUE SER MENOR DE 1024");
            RAM2.setText(null);
            RAM2.grabFocus();
        }
```
---
```java 
//Este apartado tiene la funcion prinsipal es de agregar procesos a la tabla para luego proceder a ser ejecutados.
public void Ingresar(){ 
    DefaultTableModel modelo=(DefaultTableModel) jTIngreso.getModel();
    Contador ++;
    Object[] miTabla = new Object[5];
    miTabla[0]= Contador;
    miTabla[1]= jTFCapturaRafaga.getText();
    miTabla[2]= jTFCapturaQuantum.getText();
    miTabla[3]= jTFCapturaRafaga.getText();
    miTabla[4]= "LISTO";
    modelo.addRow(miTabla);
    jTIngreso.setModel(modelo);
    jTFCapturaRafaga.setText(null);
    jTFCapturaRafaga.grabFocus();
}
//Este apartado tiene la funcion de eliminar los registros de la tabla procesos. 
public void Borrar(int c){ 
    jTIngreso.setValueAt(0,c,0);
    jTIngreso.setValueAt("0",c,1);
    jTIngreso.setValueAt("0",c,2);
    jTIngreso.setValueAt("0",c,3);
    jTIngreso.setValueAt("-----",c,4);
}
//este apartado calcula el progreso y porcentaje de la barra de ejecucion de los procesos.
   public void Barra(int rafaga, int residuo){ 
        int Rafaga=rafaga;
        int valor=100/rafaga;
        int porcentaje=100-(valor*residuo);
        ValorBarra=porcentaje;
        jLPorcentajeProceso.setText(String.valueOf(ValorBarra+"%"));
}

    public void Pintar(){
        jPBEstado.setValue(ValorBarra);
        jPBEstado.repaint();
    }
//Este apartado da inicio a la ejecucion de la secuencia de los procesos.
    public void Iniciar(){ 
        jLabel2.setVisible(true);
        jLabel1.setVisible(true);
        jTFCapturaRafaga.setVisible(true);
        jTFCapturaQuantum.setVisible(true);
        jBAgregar.setVisible(true);
        jBIniciar.setVisible(true);
} 
```
---
## Resolución

Gracias a la propuesta e implementación de una metodología para un sistema de gestión de procesos se concluye lo siguiente:
La implementación de un sistema de gestor de procesos requiere de un diseño e implementación adecuada para cada organización, debido a que la información y el conocimiento que se crea y se gestiona dentro del sistema, debe estructurarse de acuerdo a los requerimientos de información de la organización.
El manejo eficiente de los recursos para llegar a resultados cada vez mejores, es uno de los requisitos de las organizaciones hoy en día, esto incluye que dentro de toda la cadena de proceso la eficacia y eficiencia sean pilares que dirijan la organización, y se puede evidenciar si se está logrando a través de la medición con indicadores de gestión.

--- 
