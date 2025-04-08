# Ferrestore

Nombre del Proyecto: Ferretestore.
Descripción General: Este proyecto es un AI Agent Conversacional con Procesamiento de Datos y Cálculos Automatizados en n8n, implementa un agente inteligente diseñado para funcionar como asistente virtual de una tienda de ferretería hipotética. El AI Agent interactúa con los usuarios mediante un chat, respondiendo consultas y realizando cálculos según las solicitudes del usuario. Para ello, accede a una base de datos en formato CSV que contiene información sobre los productos disponibles y sus respectivos precios. El agente se conecta a múltiples nodos dentro del entorno de n8n, lo que le permite ejecutar tareas específicas como el procesamiento de lenguaje natural, la realización de cálculos matemáticos, el almacenamiento de interacciones y la consulta dinámica de datos, ofreciendo así una experiencia conversacional automatizada y eficiente.

![image](https://github.com/user-attachments/assets/3db8eb7f-6d91-4a87-9db9-bd424518649d)
Componentes del Workflow
Componentes del Workflow
1. Trigger – Chat de Entrada


Tipo de nodo: Chat Trigger


Descripción: Este nodo funciona como el punto de entrada para la interacción del usuario. Permite que los mensajes sean enviados al agente desde una interfaz conversacional.


Configuración clave:


Método: POST


Respuesta inmediata: Estado 200 OK

![Imagen de WhatsApp 2025-04-07 a las 22 33 35_5167b72c](https://github.com/user-attachments/assets/063f3081-b571-4249-a6b0-d2220c9368af)


2. Modelo de Inteligencia Artificial (IA)

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

 Flujo General
 
[Usuario] 

   ↓ 
   
[Chat Trigger] 

   ↓ 
   
[Modelo de IA]

   ↓
   
┌──────────────┬─────────────┬─────────────┐

↓              ↓             ↓

[CSV Reader]  [Calculadora] [Almacenamiento]

   ↓              ↓             ↓

   
   →→→→→→→→→→→ [Respuesta al Usuario] ←←←←←←←←←←
   

   

Casos de Uso
Consulta de datos específicos:

Usuario: "¿Cuál es el valor del producto _1?"
Respuesta: "El valor de producto 1 es 25."

Realización de cálculos:
Usuario: "¿Cuál es la suma de los valores de todos los productos?"
Respuesta: "La suma total es 65."

Registro de interacciones:
Todas las interacciones quedan guardadas para seguimiento o análisis posterior.

Requisitos del Sistema
Plataforma: n8n (self-hosted o cloud)

Nodos requeridos:

Webhook / Chat

AI Agent (OpenAI, Hugging Face, etc.)

CSV Parser

Function o Math

Nodo de almacenamiento


 Pruebas Realizadas
Validación de respuestas del modelo de IA
Lectura correcta del CSV
Ejecución de cálculos con inputs dinámicos
Almacenamiento exitoso de logs
Flujo completo sin errores


 Observaciones
Se recomienda validar que el CSV esté actualizado antes de cada sesión de usuario.
El modelo de IA puede personalizarse para responder con un estilo específico o seguir ciertas reglas.
El sistema puede escalarse para integrar APIs externas, otros tipos de datos o flujos más complejos.





