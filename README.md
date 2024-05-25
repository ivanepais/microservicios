# microservicios

Arquitectura de software que se utiliza para diseñar aplicaciones complejas y de gran escala como un conjunto de servicios pequeños e independientes que se comunican entre sí. 

Esta arquitectura es una alternativa a la arquitectura monolítica tradicional, en la que toda la funcionalidad de la aplicación está empaquetada en un solo bloque.



|| Características

	Independencia: 

		Cada microservicio es una entidad independiente que realiza una función específica. 

		Puede ser desarrollado, desplegado y escalado de manera autónoma.


	Descentralización:

		En lugar de un único modelo de datos centralizado, cada microservicio puede tener su propia base de datos o esquema.


	Comunicación: 

		Los microservicios se comunican entre sí mediante APIs ligeras, generalmente a través de HTTP/REST, gRPC, o mensajes asíncronos con sistemas de mensajería como RabbitMQ o Apache Kafka.


	Despliegue Independiente: 

		Se pueden desplegar y actualizar microservicios individualmente sin afectar a otros servicios de la aplicación.


	Escalabilidad: 

		Cada microservicio puede ser escalado de manera independiente según las necesidades, permitiendo un uso más eficiente de los recursos.


	Diversidad Tecnológica: 

		Los equipos pueden elegir diferentes tecnologías y lenguajes de programación para cada microservicio, según lo que sea más adecuado para el caso de uso específico.



	Ventajas: 

		Flexibilidad y Agilidad:

			Permite a los equipos desarrollar y desplegar nuevos componentes de manera rápida e independiente.

		Resiliencia: 

			La falla de un microservicio no necesariamente afecta a toda la aplicación, mejorando la resiliencia del sistema.

		Escalabilidad:

			Mejora la capacidad para escalar partes de la aplicación que tienen mayor demanda sin necesidad de escalar toda la aplicación.

		Mantenimiento Simplificado: 

			Es más fácil mantener y actualizar pequeñas piezas de código independientes que una gran base de código monolítica.


	Desafíos: 

		Complejidad Operacional: 

			La gestión de múltiples servicios y su comunicación añade complejidad.

		Consistencia de Datos: 
			
			Mantener la consistencia de datos a través de servicios distribuidos puede ser desafiante.

		Monitoreo y Depuración:

			Requiere herramientas y prácticas avanzadas para monitorear y depurar una arquitectura distribuida.


	Ejemplo:

		En una tienda en línea, una arquitectura monolítica tiene todas las funcionalidades como la gestión de usuarios, el catálogo de productos, el procesamiento de pagos y la gestión de pedidos estarían en un solo bloque de código. 

		En una arquitectura de microservicios, cada una de estas funcionalidades se dividiría en servicios independientes:

	    1. Servicio de Usuarios:

	    	Maneja el registro y autenticación de usuarios.

	    2. Servicio de Catálogo de Productos: 

	    	Gestiona los productos y sus detalles.

	    3. Servicio de Procesamiento de Pagos: 

	    	Se encarga de la lógica de pagos.

	    4. Servicio de Gestión de Pedidos: 

	    	Gestiona la creación y seguimiento de pedidos. 


		Cada uno de estos servicios puede ser desarrollado, desplegado y escalado de manera independiente



|| Principios de Diseño de Microservicios
	
	Descomposición del sistema.
	
	Principio de responsabilidad única (SRP).
	
	Bounded Context en Domain-Driven Design (DDD).



|| Comunicación entre Microservicios	
    APIs RESTful.

    gRPC.

    Mensajería asíncrona (RabbitMQ, Kafka).



|| Desarrollo de microservicios

	Java: Spring Boot.
	
	Node.js: Express.
	
	Python: Flask, FastAPI.
	
	Go: Gin	



|| Construcción de APIs

    Creación de APIs RESTful.

    Manejo de respuestas y errores.

    Autenticación y autorización (JWT, OAuth)



|| Persistencia de Datos

	Bases de datos relacionales (PostgreSQL, MySQL).

	Bases de datos NoSQL (MongoDB, Cassandra).

	Persistencia poliglota.



|| Infraestructura y Despliegue
	
	Contenedores y Orquestación:

    	Docker: Creación y gestión de contenedores.

    	Kubernetes: Orquestación y gestión de contenedores.

    	Docker Compose.


    CI/CD (Integración Continua y Despliegue Continuo):

    	Jenkins, GitLab CI, GitHub Actions.

    	Pipelines de despliegue.
    	
    	Estrategias de despliegue (Blue-Green, Canary).


    Configuración y Gestión de Microservicios:

    	Configuración centralizada (Spring Cloud Config, Consul).

    	Service Discovery (Eureka, Consul).
    	
    	Gateway/API Gateway (Zuul, Kong, Nginx).



|| Monitoreo y Mantenimiento

	Monitoreo y Logging

    Prometheus y Grafana para monitoreo.

    ELK Stack (Elasticsearch, Logstash, Kibana) para logging.
    Tracing distribuido (Jaeger, Zipkin).


    Pruebas y Calidad de Software

   		Pruebas unitarias (JUnit, pytest).

   		Pruebas de integración.

    	Pruebas de contrato (Pact).


    Manejo de Fallos y Resiliencia:

    	Circuit Breaker (Hystrix, Resilience4j).

    	Retries y fallbacks.
    	
    	Tolerancia a fallos y auto-recuperación.



|| Conceptos Avanzados

	Escalabilidad y Performance:

    Escalado horizontal y vertical.

    Caching (Redis, Memcached).

    Optimización de consultas y recursos.


	Seguridad:

	    Seguridad en APIs.

	    Gestión de secretos (Vault, AWS Secrets Manager).

	    Seguridad de contenedores.



|| Registro de servicios:

	Es un componente que mantiene y gestiona información acerca de los servicios disponibles en un sistema distribuido. 

	Este registro de servicios actúa como un directorio centralizado 
	o un repositorio donde los microservicios pueden registrarse 
	y descubrirse mutuamente.


	1. Registro:

		Cuando un microservicio se inicia o está disponible, se registra en el registro de servicios. 

		Esto implica enviar información relevante sobre el servicio al registro, como su ubicación (dirección IP y puerto), su nombre, y cualquier otra metadata importante.


	2. Descubrimiento:

		Otros microservicios que necesitan interactuar con un servicio en particular pueden consultar el registro de servicios para descubrir la ubicación y la información relevante de ese servicio. 

		El descubrimiento se realiza típicamente mediante consultas al registro utilizando un nombre de servicio o una etiqueta específica.


	3. Dinamicos: 

		El registro de servicios es dinámico y refleja el estado
		actual de los servicios en tiempo real. 

		A medida que los servicios se inician, se detienen o se 
		actualizan, el registro se actualiza automáticamente para reflejar estos cambios.


	4. Tolerancia a Fallos:

		Los registros de servicios a menudo implementan mecanismos de tolerancia a fallos para manejar situaciones en las que
		un servicio deja de estar disponible o se produce un fallo.

		Esto implica la detección y eliminación de servicios no 
		disponibles del registro.


	5. Tecnologías:

		Algunas tecnologías comunes para implementar el registro de servicios en entornos de microservicios incluyen:
		  
		Eureka (por Netflix): 
			
			Un servidor de registro y descubrimiento de servicios.
		  
		Consul (por HashiCorp): 
			
			Un sistema completo de descubrimiento y configuración distribuida.
		 
		etcd (por CoreOS): 

			Un almacén de claves distribuido que se puede utilizar para la configuración y el descubrimiento de servicios.


	6. Beneficios:

		Dinamismo: 
			
			Facilita la administración de servicios en entornos dinámicos donde los servicios pueden cambiar de estado (inicio, parada, actualización) frecuentemente.
	    
		Desacoplamiento:

			Permite que los servicios se descubran mutuamente sintener que conocer detalles específicos de implementación o ubicación.


	Ejemplo de Uso: 

		En un sistema de comercio electrónico basado en microservicios, el servicio de gestión de productos podría registrarse en el registro de servicios cuando se inicia. 

		Cuando el servicio de procesamiento de pedidos necesita interactuar con el servicio de gestión de productos, consulta el registro de servicios para obtener la información necesaria sobre la ubicación del servicio de gestión de productos.


	El registro de servicios es esencial en arquitecturas de
	microservicios para facilitar la comunicación y la colaboración 
	entre los diferentes servicios que componen una aplicación.

	Proporciona una forma dinámica y eficiente para que los servicios descubran y se comuniquen entre sí en entornos distribuidos y escalables.
 


|| Equilibrio de carga: 

	Se refiere a la distribución eficiente de las solicitudes de los clientes entre múltiples instancias de microservicios para garantizar un uso equitativo de los recursos y una alta disponibilidad. 

	Este proceso se lleva a cabo mediante un componente llamado "balanceador de carga" que se encuentra en la capa de red y gestiona la distribución de las solicitudes entrantes.


	1. Balanceador de Carga: 

		El balanceador de carga es un componente que se encuentra entre los clientes y los microservicios. 

		Su función principal es distribuir de manera equitativa las solicitudes de los clientes entre múltiples instancias de un microservicio.


	2. Escalabilidad Horizontal:

		Los microservicios, por su naturaleza, suelen ser escalados horizontalmente, lo que significa que múltiples instancias del mismo servicio se ejecutan en paralelo para manejar una carga mayor. 

		El equilibrio de carga asegura que estas instancias se utilicen de manera eficiente y que ninguna de ellas se sobrecargue mientras otras están subutilizadas.


	3. Algoritmos de Balanceo de Carga: 

		Los balanceadores de carga utilizan diversos algoritmos para distribuir las solicitudes entre las instancias de microservicios.

		Algunos algoritmos comunes incluyen el equilibrio de carga basado en turnos, el equilibrio de carga ponderado, el equilibrio de carga basado en la carga actual de la instancia, entre otros.


	4. Descubrimiento de Servicios:

		Para equilibrar la carga de manera efectiva, el balanceador de carga necesita conocer la ubicación y la disponibilidad de las instancias de los microservicios. 

		Esto se logra a menudo mediante la integración con sistemas de registro de servicios o descubrimiento de servicios.


	5. Tolerancia a Fallos: 

		Los balanceadores de carga suelen implementar mecanismos de tolerancia a fallos para evitar dirigir el tráfico a instancias de microservicios que están inactivas o experimentan problemas. 

		Esto garantiza una mayor disponibilidad y confiabilidad del sistema.


	6. Escalabilidad Dinámica: 

		En entornos donde la carga de trabajo varía con el tiempo, el equilibrio de carga permite escalar dinámicamente el número de instancias de microservicios para adaptarse a la demanda. 

		Esto se conoce como escalabilidad dinámica o escalabilidad automática.


	7. Balanceo de Carga Global y Local: 

		En algunos casos, se utiliza tanto el equilibrio de carga global (entre distintas instancias del mismo servicio) como el equilibrio de carga local (dentro de una instancia de servicio que podría estar distribuida geográficamente).

		Esto asegura una distribución eficiente de las solicitudes en diferentes niveles del sistema.


	Ejemplo de Uso: 

		En una aplicación de comercio electrónico basada en microservicios, el servicio de gestión de inventario puede tener múltiples instancias en ejecución para manejar la carga. 

		Un balanceador de carga distribuirá las solicitudes de los clientes entre estas instancias para garantizar un uso eficiente de los recursos y evitar la congestión.


	El equilibrio de carga es fundamental en arquitecturas de microservicios para garantizar un rendimiento óptimo, una alta disponibilidad y una escalabilidad eficiente. 

	Proporciona una manera efectiva de gestionar el tráfico en entornos dinámicos y distribuidos, donde la carga de trabajo puede variar significativamente.



|| Enlace y enrutamiento: 
	
	Forma en que las solicitudes de clientes se dirigen y entregan a instancias específicas de microservicios. 

	Este proceso implica tanto el enrutamiento de las solicitudes a través de la red, como la determinación de qué instancia de un microservicio específico manejará la solicitud.


	Enlace: 

		El enlace se refiere al proceso de establecer una conexión o canal de comunicación entre un cliente y un microservicio específico.

		En un entorno de microservicios, esto implica dirigir la solicitud del cliente a una instancia específica de un servicio.


	Enrutamiento: 

		El enrutamiento se refiere a la determinación de la ruta que seguirá una solicitud desde el cliente hasta la instancia del microservicio que debe manejarla. 

		Esto puede implicar decisiones basadas en diversas consideraciones, como la carga de trabajo actual de las instancias, la proximidad geográfica, las políticas de enrutamiento específicas, etc.


	1. Balanceo de Carga: 

		Como se mencionó anteriormente, los balanceadores de carga desempeñan un papel clave en el enlace y enrutamiento. 

		Se encargan de distribuir las solicitudes entre múltiples instancias de un microservicio, asegurando que la carga se distribuya de manera equitativa.


	2. Descubrimiento de Servicios:

		Para realizar un enrutamiento efectivo, el sistema necesita conocer la ubicación y la disponibilidad de las instancias de microservicios. 

		Los servicios pueden registrarse y descubrirse en un registro centralizado o utilizar sistemas de descubrimiento de servicios para facilitar este proceso.


	3. Protocolos de Comunicación: 

		La elección del protocolo de comunicación también juega un papel en el enlace y enrutamiento. 

		Los microservicios pueden comunicarse a través de protocolos como HTTP, gRPC, o mensajes en colas, y el sistema de enlace debe ser compatible con estos protocolos.


	4. Enrutamiento Dinámico: 

		En entornos dinámicos, el enrutamiento puede ser dinámico, ajustándose en tiempo real según las condiciones del sistema, la carga de trabajo y la disponibilidad de instancias de microservicios


	5. Enlace Directo y Indirecto: 

		El enlace puede ser directo, donde el cliente conoce directamente la ubicación de la instancia del microservicio y se comunica con ella, o indirecto, donde se utiliza un intermediario (como un balanceador de carga) para dirigir la solicitud al servicio correcto.


	6. Segmentación de Tráfico: 

		En algunos casos, se pueden utilizar estrategias de enrutamiento para segmentar el tráfico y dirigir ciertas solicitudes a instancias específicas para gestionar casos de uso especiales o cumplir con requisitos de negocio.


	7. Ejemplo de Uso: 

		En un sistema de comercio electrónico basado en microservicios, cuando un cliente realiza una solicitud para ver los detalles de un producto, el sistema puede utilizar un balanceador de carga para dirigir la solicitud a una instancia específica del servicio de gestión de productos, asegurando un enlace eficiente y un enrutamiento adecuado.



|| Procesamiento de datos en tiempo real: 

	Capacidad de procesar y analizar datos de manera inmediata, en el momento en que se generan, en lugar de esperar a que se acumulen para ser procesados en lotes.

	Es esencial en situaciones donde la velocidad de respuesta y la toma de decisiones en tiempo real son críticas

	Cuando se integra con microservicios, el procesamiento de datos en tiempo real puede proporcionar una serie de beneficios para aplicaciones y sistemas distribuidos.


	1. Eventos y Mensajes: 
		
		El procesamiento de datos en tiempo real a menudo se basa en la emisión y recepción de eventos o mensajes. 

		Los microservicios pueden generar eventos cuando ocurren cambios o se produce nueva información, y otros microservicios pueden suscribirse y reaccionar a esos eventos.


	2. Flujo Continuo: 
		
		En lugar de procesar datos en lotes, el procesamiento en tiempo real implica el procesamiento continuo de flujos de datos. 

		Esto permite respuestas más rápidas a eventos y cambios en el sistema.


	3. Arquitecturas de Eventos:

		Arquitecturas basadas en eventos son comunes en el procesamiento de datos en tiempo real con microservicios.

		Los eventos se utilizan para comunicar cambios y desencadenar acciones en diferentes microservicios sin acoplamiento directo.


	4. Arquitecturas de Eventos:

		Arquitecturas basadas en eventos son comunes en el procesamiento de datos en tiempo real con microservicios. 

		Los eventos se utilizan para comunicar cambios y desencadenar acciones en diferentes microservicios sin acoplamiento directo.


	5. Comprensión de Patrones y Reglas: 

		En el procesamiento en tiempo real, los microservicios pueden estar diseñados para comprender patrones y reglas específicas. 

		Esto permite detectar eventos significativos y tomar decisiones basadas en lógica empresarial o análisis de datos


	6. Elasticidad y Escalabilidad:

		El procesamiento de datos en tiempo real puede beneficiarse de la elasticidad y la escalabilidad inherentes a la arquitectura de microservicios. 

		Se pueden escalar individualmente los microservicios que manejan el procesamiento en tiempo real según la carga de trabajo.


	7. Ejemplo: 

		En una aplicación de comercio electrónico basada en microservicios, el procesamiento de datos en tiempo real podría utilizarse para realizar un seguimiento en tiempo real de los cambios en el inventario, actualizaciones de precios, o eventos de interés como la compra de un artículo.


	8. Tecnologías Asociadas: 

		Para implementar el procesamiento de datos en tiempo real en un entorno de microservicios, se pueden utilizar tecnologías como Apache Kafka, Apache Flink, RabbitMQ, o sistemas de procesamiento de eventos en la nube como AWS Kinesis o Azure Event Hubs


	Las aplicaciones pueden obtener información valiosa de manera más rápida y reaccionar de manera más eficiente a los cambios en el entorno. 

	Esto es especialmente útil en casos donde la toma de decisiones inmediata es crucial, como en sistemas de monitoreo, análisis de datos en tiempo real y en aplicaciones de Internet de las cosas (IoT).



|| Orquestación del flujo de datos

	Proceso de coordinar y gestionar el flujo de datos entre diferentes microservicios para lograr una funcionalidad completa de la aplicación.

	Implica el control y la sincronización de las operaciones y la información que se mueven a través de los diversos servicios que componen la arquitectura de microservicios.


	1. Secuencia de Operaciones: 

		La orquestación del flujo de datos implica definir y coordinar la secuencia de operaciones que deben llevarse a cabo entre los diferentes microservicios para completar una tarea o proceso


	2. Interacción entre Microservicios: 

		Los microservicios suelen tener responsabilidades específicas y operar de manera independiente, pero para realizar tareas complejas, a menudo necesitan colaborar. 

		La orquestación asegura que los microservicios se comuniquen y se coordinen adecuadamente


	3. Coreografía vs. Orquestación:

		Existen dos enfoques principales para lograr la coordinación en arquitecturas de microservicios: oreografía y orquestación.

		Coreografía: 

			Cada microservicio participante en un proceso conoce sus responsabilidades y se comunica directamente con otros servicios.

			No hay un componente central que coordine el flujo de datos.


		Orquestación: 

			Un componente central (a menudo llamado orquestador) coordina y dirige las operaciones, enviando instrucciones a los microservicios para lograr el resultado deseado.


	4. Transacciones Distribuidas: 

		La orquestación del flujo de datos puede implicar la coordinación de transacciones distribuidas, donde varias operaciones deben realizarse de manera coherente y, si una operación falla, se deben deshacer las operaciones previas.


	5. Ejecución de Tareas Asincrónicas: 

		En algunos casos, las tareas que forman parte del flujo de datos pueden ejecutarse de manera asincrónica, y la orquestación se encarga de gestionar la secuencia correcta de estas tareas.


	6. Manejo de Excepciones y Errores: 

		La orquestación del flujo de datos debe abordar el manejo de excepciones y errores que puedan ocurrir durante la ejecución de las operaciones.

		Esto implica decisiones sobre cómo manejar fallos, reintentos y reversión de operaciones en caso de problemas.


	7. Ejemplo: 	

		En una aplicación de comercio electrónico basada en microservicios, la orquestación del flujo de datos podría ser necesaria para gestionar el proceso de compra. 

		Esto podría implicar la interacción entre microservicios de gestión de carrito de compras, procesamiento de pagos, gestión de inventario y notificación de envío.


	8. Tecnologías de Orquestación:

		Algunas herramientas y tecnologías populares para la orquestación de microservicios incluyen Kubernetes (para la orquestación de contenedores), Apache Kafka (para la orquestación de eventos), y herramientas específicas de orquestación como Apache Camel o Netflix Conductor.


	Es crucial en entornos de microservicios para garantizar que las operaciones se realicen de manera coherente y eficiente, facilitando la construcción de aplicaciones escalables y modulares. 

	La elección entre coreografía y orquestación dependerá de la complejidad y los requisitos específicos de la aplicación.



|| Pipelining

	Se refiere a la práctica de conectar varios microservicios en una cadena o tubería (pipeline) para realizar una secuencia de operaciones coordinadas.

	Cada microservicio en la cadena realiza una tarea específica y pasa los resultados al siguiente servicio en la secuencia.

	Permite construir flujos de trabajo más complejos y completos mediante la composición de servicios más pequeños y especializados.


	1. Secuencia de Operaciones:

		En un pipeline, los microservicios se organizan en una secuencia lógica donde cada servicio realiza una operación específica. 

		La salida de un servicio se convierte en la entrada del siguiente.


	2. Desacoplamiento: 

		El pipelining permite el desacoplamiento entre los microservicios individuales, ya que cada uno se centra en una tarea específica. 

		Esto facilita la escalabilidad, el mantenimiento y la evolución independiente de los servicios


	3. Composición de Servicios: 

		La composición de servicios a través del pipelining permite construir flujos de trabajo más grandes y complejos utilizando servicios más pequeños y especializados. 

		Cada microservicio puede ser desarrollado, desplegado y escalado de forma independiente.


	4. Ejecución Asíncrona o Sincrónica: 

		Dependiendo de los requisitos, un pipeline de microservicios puede ejecutarse de manera síncrona, donde cada servicio se llama secuencialmente, o de manera asíncrona, donde los servicios pueden operar en paralelo.


	5. Manejo de Errores: 

		El pipelining debe abordar el manejo de errores y excepciones a medida que se propagan a lo largo del pipeline. 

		Esto puede implicar la implementación de mecanismos de reintentos, manejo de transacciones distribuidas y estrategias de recuperación.


	6. Interacción con Sistemas de Mensajería: 

		El pipelining a menudo se integra con sistemas de mensajería para facilitar la comunicación entre los microservicios. 

		Los mensajes pueden llevar datos entre servicios y activar operaciones en el siguiente eslabón del pipeline


	7. Ejemplo: 

		En una aplicación de análisis de datos basada en microservicios, se podría implementar un pipeline donde un servicio de ingestión recopila datos, luego un servicio de procesamiento realiza operaciones de filtrado, seguido por un servicio de análisis estadístico y, finalmente, un servicio de almacenamiento almacena los resultados.


	8. Tecnologías Asociadas:

		Tecnologías como Apache Kafka, RabbitMQ o servicios de orquestación de eventos pueden ser utilizadas para implementar pipelines de microservicios, facilitando la comunicación entre servicios y la gestión de eventos es una estrategia efectiva para construir aplicaciones modulares y flexibles, permitiendo la composición de funcionalidades complejas a partir de componentes más simples y especializados.

		Esto promueve la reutilización, la escalabilidad y la agilidad en el desarrollo de software.



|| Tareas por lotes 

	Ejecución de un conjunto de operaciones o trabajos de manera eficiente y coordinada utilizando microservicios. 

	Estas tareas por lotes pueden abordar diversas necesidades, como procesamiento de datos en lotes, actualizaciones masivas, o cualquier operación que deba aplicarse a un conjunto significativo de datos.


	1. Procesamiento en Lotes: 

		Las tareas por lotes suelen implicar procesamiento en lotes, donde se toma un conjunto de datos y se aplica una operación o conjunto de operaciones a todos esos datos de manera eficiente. 

		Esto es diferente del procesamiento en tiempo real, que se ocupa de eventos individualmente a medida que ocurren


	2. Coordinación de Microservicios: 

		Las tareas por lotes pueden requerir la coordinación de múltiples microservicios para completar la operación. 

		Cada microservicio puede tener una función específica en el proceso global de la tarea por lotes.


	3.  Secuencia de Operaciones:

		Similar al pipelining, las tareas por lotes pueden implicar una secuencia de operaciones donde cada microservicio realiza una parte específica del trabajo.


	4. Escalabilidad y Paralelismo:

		La implementación eficiente de tareas por lotes en microservicios debe considerar la escalabilidad y el paralelismo. 

		Puede haber múltiples instancias de microservicios trabajando en diferentes lotes de datos simultáneamente.


	5. Manejo de Errores y Transacciones Distribuidas:

		Debido a que las tareas por lotes pueden implicar operaciones en gran escala, es crucial abordar el manejo de errores y las transacciones distribuidas para garantizar la consistencia y la integridad de los datos.


	6. Ejemplo: 

		Una aplicación de comercio electrónico basada en microservicios, las tareas por lotes podrían aplicarse para realizar actualizaciones masivas, como la actualización de precios de productos en función de un nuevo conjunto de reglas comerciales.


	7. Integración con Sistemas de Colas de Mensajes: 

		Las tareas por lotes pueden beneficiarse de la integración con sistemas de colas de mensajes para manejar la comunicación entre microservicios y para la gestión eficiente de las operaciones en lotes.


	8. Programación Distribuida: 

		La implementación de tareas por lotes implica a menudo programación distribuida, donde se deben coordinar y gestionar las operaciones a través de los límites de los microservicios.


	9. Tecnologías Asociadas:
		
		Tecnologías como Apache Kafka, Apache Flink, Apache Spark o sistemas de mensajería en la nube pueden ser utilizadas para implementar eficientemente tareas por lotes en un entorno de microservicios.


	Las tareas por lotes son útiles cuando se necesitan aplicar operaciones a grandes conjuntos de datos de manera eficiente y escalable. 

	Proporcionan una manera modular y desacoplada de abordar operaciones en lote, permitiendo que cada microservicio cumpla con su función específica en el proceso global.



|| Puerta de enlace para enrutamiento

	Componente que actúa como intermediario para manejar la entrada y salida del tráfico entre clientes externos y los diversos microservicios que componen una aplicación.

	Esta puerta de enlace facilita la gestión del tráfico, el enrutamiento y la seguridad, ofreciendo una interfaz unificada para los clientes externos y simplificando la comunicación entre los microservicios


	1. Unificación de Interfaz: 

		La puerta de enlace proporciona una interfaz unificada para los clientes externos. 

		En lugar de interactuar directamente con cada microservicio individualmente, los clientes se comunican con la puerta de enlace, que luego enruta las solicitudes al microservicio correspondiente.


	2. Enrutamiento Dinámico: 

		La puerta de enlace puede realizar enrutamiento dinámico de las solicitudes a los microservicios, basándose en reglas configurables, información de contexto o incluso en la carga actual de los microservicios.


	3. Gestión de Tráfico: 

		La puerta de enlace puede gestionar aspectos como la carga del tráfico, el equilibrio de carga y la escalabilidad de los microservicios. 

		Puede distribuir de manera eficiente las solicitudes entrantes entre las instancias de los microservicios para garantizar un rendimiento óptimo.


	4. Seguridad y Autenticación:

		Puede proporcionar funciones de seguridad, como autenticación y autorización, centralizando el manejo de la seguridad en un solo punto. 

		Esto facilita la implementación de políticas de seguridad coherentes en toda la aplicación.


	5. Aggregation de Datos: 

		La puerta de enlace puede realizar agregación de datos al reunir la información de múltiples microservicios para construir respuestas completas y significativas para los clientes. 

		Esto evita que los clientes tengan que realizar múltiples solicitudes para obtener la información deseada.


	6. Proxy Inverso: 

		La puerta de enlace a menudo actúa como un proxy inverso, ocultando la complejidad de la infraestructura de microservicios al exponer una interfaz simple y consistente a los clientes.


	7. Resiliencia y Tolerancia a Fallos: 

		Puede implementar mecanismos de resiliencia y tolerancia a fallos, como la detección de instancias de microservicios inactivas o la capacidad de cambiar dinámicamente a instancias de respaldo en caso de problemas


	8. Ejemplo de Uso: 

		En una aplicación de comercio electrónico basada en microservicios, la puerta de enlace podría manejar solicitudes de clientes para buscar productos, procesar pagos y realizar seguimiento de pedidos. 

		En lugar de interactuar directamente con cada microservicio, los clientes se comunican con la puerta de enlace, que enruta las solicitudes a los microservicios correspondientes


	9. Tecnologías Asociadas: 

		Algunas tecnologías comunes para implementar puertas de enlace para enrutamiento en microservicios incluyen NGINX, Spring Cloud Gateway, Envoy Proxy y API Gateways en plataformas de nube como AWS API Gateway o Azure API Management.


	La puerta de enlace para enrutamiento en microservicios proporciona una capa de abstracción que simplifica la interacción entre clientes externos y microservicios individuales. 

	Ofrece beneficios en términos de seguridad, escalabilidad, gestión de tráfico y facilita la evolución de la arquitectura de microservicios.



|| Tolerancia a Fallos

	Capacidad de un sistema basado en la arquitectura de microservicios para gestionar y recuperarse de fallos de manera efectiva, garantizando la continuidad del servicio incluso cuando algunos de sus componentes fallan. 

	Dado que los microservicios son unidades de software independientes y autónomas que trabajan juntas para ofrecer funcionalidades más amplias, es crucial implementar estrategias que mitiguen el impacto de fallos en uno o más microservicios.


	1. Detección de Fallos: 
		
		Implementar mecanismos de supervisión y detección de fallos para identificar rápidamente problemas en los microservicios. Uso de sondas de salud, verificación de integridad y monitoreo constante


	2. Detección de Fallos: 

		Implementar mecanismos de supervisión y detección de fallos para identificar rápidamente problemas en los microservicios.

		Uso de sondas de salud, verificación de integridad y monitoreo constante.


	3. Resiliencia en la Comunicación:

		Implementar patrones de comunicación resistentes, como circuit breakers y fallbacks, para gestionar la comunicación entre microservicios en situaciones de fallo.

		Utilizar colas de mensajes o patrones de mensajería asincrónica para desacoplar microservicios y permitir la recuperación asincrónica.


	4. Recuperación Automática:
		
		Configurar mecanismos de recuperación automática para reintentar operaciones que han fallado debido a fallos temporales.

		Automatizar el reinicio de instancias de microservicios en caso de fallo.


	5. Gestión de Transacciones Distribuidas: 
		
		Implementar estrategias para gestionar transacciones distribuidas y garantizar la coherencia de los datos en caso de fallo.

		Uso de compensaciones o reversión de transacciones para mantener la integridad del sistema.


	6. Redundancia:
		
		Utilizar redundancia para tener instancias adicionales de microservicios críticos. 

		Replicar datos y servicios para garantizar la disponibilidad continua en caso de fallo.


	7. Diseño Antifragilidad: 

		Adoptar un enfoque antifragilidad, donde el sistema no solo es resistente a fallos, sino que también mejora y aprende de ellos. 

		Utilizar prácticas como la introducción controlada de fallos (chaos engineering) para evaluar y fortalecer la resiliencia del sistema.


	8. Gestión de Versiones y Despliegue Continuo: 

		Implementar estrategias de espliegue continuo que faciliten la rápida implementación de correcciones y actualizaciones en respuesta a fallos.

		Utilizar prácticas de gestión de versiones para minimizar el riesgo de fallos relacionados con actualizaciones.


	9. Planificación para Fallos:

		Considerar escenarios de fallos durante el diseño y la planificación del sistema. 

		Realizar pruebas de resistencia y escenarios de fallos para evaluar la capacidad del sistema para manejar situaciones adversas.


	La tolerancia a fallos en microservicios es esencial para garantizar la disponibilidad y la fiabilidad del sistema, especialmente en entornos distribuidos y dinámicos. 

	La adopción de prácticas y herramientas que fomenten la resiliencia y la recuperación eficaz ayuda a minimizar el impacto de los fallos y proporciona una experiencia más robusta para los usuarios finales



|| Escalabilidad

	Capacidad de un sistema basado en arquitectura de microservicios para manejar el crecimiento de la carga de trabajo y la demanda sin comprometer el rendimiento, la disponibilidad o la calidad del servicio. 

	La escalabilidad es un principio fundamental en el diseño de sistemas distribuidos, y en el contexto de microservicios, implica la capacidad de escalar los componentes de manera independiente para satisfacer los requisitos específicos de cada servicio.


	1. Escalabilidad Horizontal: 

		La escalabilidad horizontal implica agregar más instancias de un servicio para manejar una mayor carga.

		Cada microservicio puede ser escalado de manera independiente, permitiendo ajustar la capacidad según la demanda específica de ese servicio.


	2. Descomposición por Funciones:

		La descomposición de una aplicación en microservicios independientes permite escalar solo aquellos servicios que experimentan una alta carga, en lugar de escalar toda la aplicación de manera uniforme. 

		Cada microservicio puede ser escalado de acuerdo con su función y demanda.


	3. Uso de Contenedores y Orquestación: 

		La encapsulación de microservicios en contenedores, como Docker, facilita la replicación y distribución de instancias.

		Herramientas de orquestación como Kubernetes permiten gestionar eficientemente la implementación, escalado y administración de contenedores


	4. Escalabilidad Vertical: 

		La escalabilidad vertical implica mejorar el rendimiento de un servicio mediante el aumento de recursos (CPU, memoria) en una instancia existente.

		Algunos servicios pueden requerir escalabilidad vertical para manejar tareas intensivas en recursos.


	5. Autoscaling: 

		La implementación de autoscaling permite que los microservicios ajusten dinámicamente su escala según las condiciones de carga. 

		Las métricas de rendimiento, como el uso de CPU o la latencia, pueden desencadenar la adición o eliminación automática de instancias


	6. Gestión de Cargas Pico: 

		La escalabilidad en microservicios es esencial para gestionar cargas pico, como períodos de tráfico intenso o eventos inesperados.

		Permite manejar aumentos repentinos en la demanda sin afectar la calidad del servicio.


	7. Escalabilidad Global: 

		La arquitectura de microservicios facilita la escalabilidad global al permitir la distribución geográfica de instancias y servicios.

		CDNs (Content Delivery Networks) y servicios de equilibrio de carga global pueden utilizarse para optimizar la entrega de servicios en ubicaciones geográficamente distribuidas.


	8. Gestión de Estado y Datos Distribuidos: 

		La gestión efectiva de la escalabilidad en microservicios implica considerar la distribución de datos y el manejo del estado en un entorno distribuido.

		El uso de bases de datos distribuidas y técnicas de particionamiento de datos es fundamental


	La escalabilidad en microservicios es esencial para adaptarse a las cambiantes demandas del negocio y del usuario. 

	Sin embargo, también introduce desafíos, como la gestión de la coherencia de datos, la comunicación entre servicios y la complejidad en la administración de sistemas distribuidos. 

	Es importante equilibrar la escalabilidad con la eficiencia y comprender las necesidades específicas de cada microservicio en el contexto general del sistema.



|| Programación Distribuida 

	Enfoque de diseñar, desarrollar y desplegar sistemas de software distribuidos basados en la arquitectura de microservicios. 

	En este contexto, la programación distribuida implica la creación de servicios independientes y autónomos que se ejecutan de manera distribuida en una red, y estos servicios colaboran entre sí para proporcionar la funcionalidad completa de una aplicación.


	1. Microservicios Independientes: 

		Cada microservicio es una unidad de desarrollo, implementación y escalado independiente.

		Se centra en la creación de servicios pequeños y especializados que realizan funciones específicas


	2. Comunicación entre Microservicios: 

		Los microservicios se comunican entre sí a través de mecanismos como API REST, mensajería asíncrona o servicios de descubrimiento.

		La comunicación es esencial para que los microservicios colaboren y proporcionen funcionalidades más complejas.


	3. Descentralización de la Lógica de Negocio: 

		Cada microservicio puede contener su propia lógica de negocio y base de datos, lo que permite la descentralización de la funcionalidad. 

		Los microservicios pueden ser desarrollados en diferentes tecnologías según sus requisitos específicos


	4. Gestión de Datos Descentralizada: 

		Cada microservicio puede tener su propia base de datos o almacenamiento de datos asociado.

		La descentralización de los datos evita acoplamientos fuertes entre microservicios y permite la elección de tecnologías de almacenamiento adecuadas para cada servicio.


	5. Resiliencia y Tolerancia a Fallos: 

		Se debe diseñar para manejar fallos en servicios individuales sin afectar la funcionalidad global del sistema. 

		Estrategias como la redundancia, la recuperación automática y la gestión de transacciones son importantes.


	6. Escalabilidad Independiente:

		Cada microservicio puede ser escalado de forma independiente según la carga de trabajo específica que enfrenta.

		La escalabilidad independiente mejora la eficiencia y el rendimiento del sistema.


	7. Diseño Guiado por Dominio:

		El diseño de microservicios se centra en organizar los servicios alrededor de los límites del dominio del negocio.

		Cada microservicio puede ser propiedad y mantenido por un equipo específico, lo que facilita la responsabilidad y la evolución del sistema.


	8. Despliegue Continuo:

		Los microservicios pueden ser desplegados y actualizados de forma independiente, permitiendo la entrega continua y la rápida adaptación a cambios.


	9. Monitoreo y Gestión:

		Es necesario implementar herramientas y prácticas sólidas para el monitoreo y la gestión de microservicios distribuidos.

		Las métricas, registros y herramientas de diagnóstico son esenciales para la identificación y resolución de problemas.


	La programación distribuida en el contexto de microservicios 
	busca aprovechar los beneficios de la descentralización, 
	la independencia y la escalabilidad para construir sistemas 
	más flexibles, resistentes y adaptables. 

	Sin embargo, también introduce desafíos en términos de 
	coordinación, consistencia y comunicación entre los 
	servicios. 

	La elección de adoptar esta arquitectura debe basarse en
	los requisitos específicos del proyecto y la capacidad de
	gestionar la complejidad asociada



|| BBDD Distribuida

	Son sistemas de almacenamiento de datos que se diseñan para ser utilizados en entornos distribuidos y escalables, donde los microservicios interactúan de manera independiente y pueden tener sus propias instancias de base de datos. 

	A diferencia de las bases de datos monolíticas, donde un único sistema de gestión de bases de datos (DBMS) maneja todos los datos, las bases de datos distribuidas permiten que los datos se distribuyan entre múltiples nodos.


	1. Descentralización de Datos:

		En un entorno de microservicios, cada microservicio puede tener su propia base de datos o esquema de base de datos dedicado.

		Los datos relacionados con la funcionalidad específica de un microservicio se almacenan y gestionan localmente.


	2. Independencia de Datos:
		
		Cada microservicio puede utilizar la tecnología de base de datos que mejor se adapte a sus necesidades.

		La elección de la tecnología de base de datos puede basarse en los requisitos de rendimiento, modelo de datos, consistencia y otros factores específicos del microservicio.


	3. Consistencia y Coordinación:

		La consistencia de datos entre microservicios puede gestionarse mediante técnicas como la consistencia eventual o transacciones distribuidas.

		La coordinación entre microservicios puede requerir prácticas como el uso de eventos y colas de mensajes para mantener la coherencia.


	4. Escalabilidad Horizontal:

		Las bases de datos distribuidas permiten la escalabilidad horizontal, donde se pueden agregar más nodos para manejar mayores cargas de trabajo.

		Cada microservicio puede escalar su base de datos de manera independiente según sus necesidades.


	5. Particionamiento de Datos:

		El particionamiento de datos distribuye los datos entre múltiples nodos según ciertos criterios (por ejemplo, clave primaria).

		Esto permite una mejor distribución de la carga y una escalabilidad eficiente.


	6. Redundancia y Alta Disponibilidad:

		La redundancia de datos se puede lograr mediante la replicación de datos entre nodos para garantizar la disponibilidad continua en caso de fallos.

		Las bases de datos distribuidas suelen implementar estrategias de respaldo y recuperación para proteger contra la pérdida de datos.


	7. Microservicios sin Estado y con Estado:

		Los microservicios sin estado pueden almacenar datos de manera efímera y no dependen de almacenamiento persistente a largo plazo.

		Los microservicios con estado pueden requerir bases de datos distribuidas para gestionar datos persistentes.


	8. Desacoplamiento de Datos:

		El desacoplamiento de datos permite que cada microservicio evolucione de manera independiente sin afectar a otros microservicios.

		Cambios en el esquema de datos de un microservicio no deberían afectar directamente a otros.


	9. Patrones de Acceso a Datos:

		La elección de patrones de acceso a datos, como el patrón CQRS (Command Query Responsibility Segregation) y el patrón Event Sourcing, puede afectar la forma en que los microservicios interactúan con las bases de datos distribuidas.


	10. Seguridad y Gestión de Acceso:

		La seguridad y la gestión de acceso deben ser consideradas cuidadosamente para garantizar que solo los microservicios autorizados puedan acceder a los datos pertinentes.


	Es importante señalar que, si bien las bases de datos 
	distribuidas ofrecen ventajas en términos de escalabilidad
	y autonomía de los microservicios, también introducen desafíos
	adicionales, como la consistencia de datos, la coordinación y la complejidad en la gestión de transacciones.

	La elección de una base de datos distribuida debe basarse en los requisitos específicos de cada microservicio y del sistema en su conjunto.
