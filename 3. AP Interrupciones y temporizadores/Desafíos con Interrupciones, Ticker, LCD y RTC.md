# **Desafíos con Interrupciones, Temporizadores (Ticker), LCD y RTC**

Estos desafíos han sido diseñados para que puedas practicar con conceptos avanzados en Arduino, utilizando interrupciones, temporizadores `Ticker`, displays (LCD y 7 segmentos), comunicación serial y RTC (Real Time Clock). Cada desafío tiene un objetivo claro y detalla los componentes y conceptos que deberás aplicar.

---

## **Nivel Medio**

### **1. Contador con Pulsador e Interrupciones**
**Descripción:**  
Configura el sistema para que un pulsador conectado a un pin digital incremente un contador cada vez que sea presionado (detectado con una **interrupción**). El valor del contador debe ser mostrado en un **display de 7 segmentos**. También imprime el valor del contador en el **monitor serial** cada vez que cambia.

**Piezas Clave:**
- **Temporizadores:** No se necesita.
- **Interrupciones:** Detecta el botón presionado.
- **Display de 7 segmentos:** Para mostrar el contador.
- **Comunicación serial:** Para imprimir el contador cuando cambia.

---

### **2. Temporizador de Cuenta Regresiva**
**Descripción:**  
Diseña un temporizador que realice una **cuenta regresiva** de 9 a 0 utilizando un **display de 7 segmentos**. Cuando el temporizador llega a 0, activa un **LED** parpadeante. El parpadeo del LED utiliza un **temporizador Ticker**. Controla el inicio de la cuenta regresiva mediante un botón configurado en **interrupción** y resetea el contador cuando se presiona otro botón.

**Piezas Clave:**
- **Temporizadores:** `Ticker` para el parpadeo del LED.
- **Interrupciones:** Detectar el inicio y reinicio de la cuenta.
- **Display de 7 segmentos:** Para la cuenta regresiva.

---

### **3. Detección de Cambios de Estado con Temporizador**
**Descripción:**  
Configura un sistema donde se evalúe periódicamente el estado de un pin con un **temporizador Ticker** y, si detecta un **cambio de estado** (de bajo a alto o de alto a bajo), muestre el estado actual en una **pantalla LCD alfanumérica** y lo transmita al **monitor serial**.

**Piezas Clave:**
- **Temporizadores:** Detección periódica del estado del pin.
- **Pantalla LCD alfanumérica:** Muestra si el pin está alto o bajo.
- **Comunicación serial:** Envía mensajes indicando el estado del pin.

---

### **4. Cronómetro con Start/Stop**
**Descripción:**  
Diseña un cronómetro que se inicie y detenga utilizando dos **botones** configurados con **interrupciones**. El tiempo transcurrido debe mostrarse en una **pantalla LCD alfanumérica** (hasta 3 dígitos en formato de segundos o segundos:milisegundos) y transmitirse al **monitor serial** en milisegundos cada segundo.

**Piezas Clave:**
- **Temporizadores:** Para actualizar el tiempo transcurrido.
- **Interrupciones:** Start y Stop mediante botones.
- **Pantalla LCD alfanumérica:** Muestra el tiempo transcurrido.
- **Comunicación serial:** Envía el tiempo transcurrido.

---

## **Nivel Alto**

### **1. Temporizador Multi-Función**
**Descripción:**  
Diseña un sistema con tres **modos de temporizador** seleccionables mediante **interrupciones** y muestra el modo actual en una **pantalla LCD alfanumérica**. Los modos son:
- **Modo 1:** Parpadeo rápido de LED cada 100 ms.
- **Modo 2:** Realiza una **cuenta regresiva** de 99 a 0 mostrada en un **display de 7 segmentos**.
- **Modo 3:** Actúa como un **cronómetro**, mostrando el tiempo transcurrido en segundos en la **pantalla LCD alfanumérica** y enviándolo al **monitor serial**.

Cambia entre los modos presionando un botón. Otro botón realiza la acción específica del modo actual (ejemplo: inicia/parpadea/reinicia).

**Piezas Clave:**
- **Temporizadores:** `Ticker` para implementar los temporizadores en cada modo.
- **Interrupciones:** Cambios de modo y ejecución de acción.
- **Pantalla LCD alfanumérica:** Muestra el modo actual y los datos de Modo 1 y 3.
- **Display de 7 segmentos:** Para la cuenta regresiva (Modo 2).
- **Comunicación serial:** Envía datos en el Modo 3 (cronómetro).

---

### **2. Sistema de Registro de Eventos**
**Descripción:**  
Crea un sistema que registre eventos en **interrupciones** (por ejemplo, presionar un botón o un cambio de estado en un pin de entrada) y los almacene en un vector/matriz en memoria. Muestra el total de eventos registrados en una **pantalla LCD alfanumérica** y envía los detalles de cada evento al **monitor serial** periódicamente utilizando un **temporizador Ticker**.

Si el total de eventos registrados supera los 9, muestra un mensaje de "ALERTA" en el monitor serial y alterna el mensaje "FULL" en un **display de 7 segmentos**.

**Piezas Clave:**
- **Temporizadores:** Generación periódica de reportes y alternancia de mensajes.
- **Interrupciones:** Registro de eventos.
- **Pantalla LCD alfanumérica:** Visualización del número de eventos.
- **Display de 7 segmentos:** Mensajes cuando el límite se alcanza.
- **Comunicación serial:** Reporte periódico y alertas de desbordamiento.

---

### **3. Reloj con RTC, Ajustable por Botones**
**Descripción:**  
Diseña un reloj que muestre la hora (segundos, minutos y horas) utilizando un **RTC (Real Time Clock)**. El reloj debe visualizarse en una **pantalla LCD alfanumérica** en el formato `HH:MM:SS`. Un botón configurado como **interrupción** debe permitir ajustar la hora encendiendo un **modo de configuración** en el que:
- Un botón aumenta la hora o los minutos (detectado con interrupciones).
- Otro botón guarda los ajustes y guarda la hora nuevamente al RTC.

Adicionalmente, conecta la configuración al **monitor serial** para permitir usar comandos seriales para ajustar la hora (`SET HH:MM:SS`) y sincronizar los datos.

**Piezas Clave:**
- **RTC:** Para mantener la hora exacta.
- **Pantalla LCD alfanumérica:** Muestra la hora en el formato `HH:MM:SS`.
- **Interrupciones:** Para ajustar la hora y guardar cambios mediante botones.
- **Comunicación serial:** Ajustes avanzados desde el monitor serial.

---

### **Resumen**

Estos desafíos integran diversas funcionalidades:
- **Interrupciones:** Para manejar eventos externos como botones.
- **Temporizadores:** Para realizar tareas periódicas, como parpadeo, actualizaciones o detección de cambios.
- **Displays (LC y 7 segmentos):** Para visualizar diferentes tipos de información.
- **Comunicación serial:** Para reportes y configuraciones interactivas desde la computadora.
- **RTC:** Para gestionar y mantener la hora exacta en sistemas avanzados.

Practica estos desafíos paso a paso y experimenta con combinaciones para dominar las herramientas. Si necesitas asistencia implementando alguno, ¡estoy aquí para ayudarte! 😊