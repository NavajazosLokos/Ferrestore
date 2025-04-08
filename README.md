# Ferrestore

Nombre del Proyecto: Ferretestore.
Descripción General: Este proyecto es un AI Agent Conversacional con Procesamiento de Datos y Cálculos Automatizados en n8n, implementa un agente inteligente diseñado para funcionar como asistente virtual de una tienda de ferretería hipotética. El AI Agent interactúa con los usuarios mediante un chat, respondiendo consultas y realizando cálculos según las solicitudes del usuario. Para ello, accede a una base de datos en formato CSV que contiene información sobre los productos disponibles y sus respectivos precios. El agente se conecta a múltiples nodos dentro del entorno de n8n, lo que le permite ejecutar tareas específicas como el procesamiento de lenguaje natural, la realización de cálculos matemáticos, el almacenamiento de interacciones y la consulta dinámica de datos, ofreciendo así una experiencia conversacional automatizada y eficiente.

Componentes del Workflow
Componentes del Workflow
Trigger – Chat de Entrada


Tipo de nodo: Chat Trigger


Descripción: Este nodo funciona como el punto de entrada para la interacción del usuario. Permite que los mensajes sean enviados al agente desde una interfaz conversacional.


Configuración clave:


Método: POST


Respuesta inmediata: Estado 200 OK


Modelo de Inteligencia Artificial (IA)


Tipo de nodo: Gorq Chat Model


Descripción: Este nodo procesa el mensaje del usuario utilizando un modelo de lenguaje avanzado, con el fin de generar respuestas relevantes y coherentes en función del contexto.


Parámetros:


Entrada: Texto proporcionado por el usuario


Contexto adicional: Historial de la conversación


Modelo: deepseek-r1-distill-qwen-32b



 Nodo CSV – Fuente de Datos
Tipo de nodo: Read Binary File → Convert to JSON (o Read CSV)
Descripción: Lee un archivo CSV que contiene una base de datos utilizada por el agente para responder o tomar decisiones.
Ejemplo de contenido del CSV:

![image](https://github.com/user-attachments/assets/de79156c-c5e7-439b-84c9-516b631021bd)


4.  Nodo Calculadora
Tipo de nodo: Function - Code
Descripción: Realiza operaciones matemáticas con los datos extraídos del CSV o del mensaje del usuario.
Ejemplo: Sumar valores, calcular promedios, etc.

5.  Nodo de Almacenamiento
Tipo de nodo: Connected Chat Trigger Node - Archivo JSON
Descripción: Guarda los resultados de las interacciones o cálculos del agente, permitiendo registrar consultas, respuestas y datos procesados.
Campos comunes:
Timestamp
Pregunta del usuario
Respuesta generada
Datos utilizados
Resultado del cálculo



![image](https://github.com/user-attachments/assets/3db8eb7f-6d91-4a87-9db9-bd424518649d)
