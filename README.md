# FYYUR 
Proyecto: Fyyur: Sitio de Reserva de Artistas (Artist Booking Site)
Este documento detalla los requisitos y criterios de evaluación para el proyecto Fyyur, un sitio web donde los artistas y los locales pueden gestionar sus perfiles y las reservas de espectáculos. El proyecto se centra en demostrar una sólida comprensión de los modelos de datos relacionales, las bases de datos SQL y el uso del ORM SQLAlchemy en una aplicación web.

1. Modelos de Datos (Data Models)
Esta sección se enfoca en cómo estructurarás la información de tu aplicación en la base de datos.

Criterios y Requisitos de Entrega:

Implementación de Modelos de Datos Relacionales y Normalizados:

Debes diseñar tus modelos de datos (por ejemplo, Artistas, Locales, Espectáculos) de forma que sigan los principios de las bases de datos relacionales y estén normalizados. Esto significa evitar la redundancia de datos y organizar tus tablas de manera eficiente.

Cada campo en tus modelos debe tener el tipo de dato correcto asociado (ej. VARCHAR para nombres, INTEGER para IDs, BOOLEAN para disponibilidad, TIMESTAMP para fechas/horas).

Relaciones entre Objetos (Shows, Artists, Venues):

El objeto Shows (Espectáculos) es fundamental y debe establecer una relación correcta entre Artists (Artistas) y Venues (Locales).

Debes demostrar la capacidad de seleccionar y aplicar el tipo de relación adecuado:

Uno a uno (One-to-one): Cuando una instancia de una entidad se relaciona con exactamente una instancia de otra.

Uno a muchos (One-to-many): Cuando una instancia de una entidad puede relacionarse con múltiples instancias de otra, pero cada instancia de la segunda solo se relaciona con una de la primera (ej. Un local tiene muchos espectáculos).

Muchos a muchos (Many-to-many): Cuando múltiples instancias de una entidad pueden relacionarse con múltiples instancias de otra (ej. Un artista puede tocar en muchos locales, y un local puede albergar a muchos artistas; esto se resuelve con una tabla intermedia como Shows).

Conexión de Modelos de Datos a una Base de Datos:

Tu código debe establecer una conexión funcional con una base de datos PostgreSQL local.

Dominio de la Normalización de Bases de Datos:

El modelo Shows debe tener las claves foráneas (Foreign Keys) configuradas correctamente para vincularse con Artists y Venues. Esto es esencial para las relaciones muchos a muchos.

Los modelos Artists y Venues deben estar, como mínimo, en Tercera Forma Normal (3NF). Esto asegura que no haya dependencias transitivas y que los datos estén bien estructurados.

Dominio de SQLAlchemy:

Todo el código de definición de modelos debe utilizar la sintaxis de SQLAlchemy ORM (Object Relational Mapper).

Las consultas SQL para interactuar con la base de datos (seleccionar, insertar, actualizar, eliminar) deben estar envueltas en comandos de SQLAlchemy ORM siempre que sea posible.

El uso de SQL "crudo" (raw SQL) debe minimizarse y solo utilizarse en casos donde las abstracciones de SQLAlchemy no sean suficientes.

2. SQL
Esta sección evalúa tu habilidad para interactuar con la base de datos utilizando SQL y SQLAlchemy.

Criterios y Requisitos de Entrega:

Uso de Sintaxis SQL para Seleccionar Registros:

El código debe ser capaz de traducir exitosamente el código SQLAlchemy ORM para seleccionar registros a su equivalente en comandos PostgreSQL. Esto demuestra tu comprensión subyacente de SQL.

Debes demostrar el uso correcto de las sentencias SELECT y WHERE para ejecutar búsquedas de manera efectiva.

Uso de Sintaxis SQL y SQLAlchemy para Unir Tablas Relacionales (JOIN):

Las sentencias JOIN deben utilizarse correctamente para ejecutar consultas que involucren múltiples tablas.

Debes unir tablas para:

Mostrar "Actuaciones Pasadas" en la página de un Local: Seleccionar Artistas que han actuado previamente en un Local específico.

Mostrar "Locales Donde Actuó" en la página de un Artista: Seleccionar Locales donde un Artista ha actuado.

El código debe incluir los equivalentes correctos en SQLAlchemy ORM para todas las sentencias SQL correspondientes.

Uso de SQL para Crear Registros con Restricciones de Unicidad:

El código debe conectar los formularios de "Nuevo Artista" y "Nuevo Local" a la base de datos, utilizando SQLAlchemy para insertar nuevos registros tras el envío del formulario.

Debes comprender el comando equivalente de SQLAlchemy para INSERT INTO en SQL.

El código debe utilizar correctamente las restricciones SQL a nivel de base de datos para asegurar que los campos que deben ser únicos (ej. nombre de local, nombre de artista si aplica) y los campos obligatorios (NOT NULL) tengan estas restricciones, lanzando un error si se violan.

3. Calidad y Despliegue de la Aplicación (Application Quality & Deployment)
Esta sección se enfoca en la estructura, la ejecución y la funcionalidad de tu aplicación web.

Criterios y Requisitos de Entrega:

Construcción de una Base de Código Bien Organizada:

El código debe estar desacoplado en partes relevantes a través de diferentes archivos (ej. modelos en un archivo, rutas en otro, configuración, etc.).

El código debe incluir un buen uso de comentarios donde la lógica no sea inmediatamente clara. Si no hay comentarios, el código debe ser auto-documentado (es decir, fácil de entender por sí mismo).

El código de consulta a la base de datos debe estar encapsulado en los lugares apropiados dentro de los Modelos y los puntos finales de la API.

Creación de una Aplicación Web que Compile y se Ejecute sin Errores:

No debe haber errores de compilación o ejecución al lanzar la aplicación web.

Funcionalidades del Usuario Final:

Un usuario debe poder ejecutar una búsqueda exitosa que consulte la base de datos.

Un usuario debe poder ver la página de un Local con información del local y de los artistas que han actuado allí, obtenida de la base de datos.

Un usuario debe poder ver la página de un Artista con información del artista y de los locales donde ha actuado, obtenida de la base de datos.

Un usuario debe poder crear un nuevo listado de local a través de la página "Nuevo Local".

Un usuario no debe poder enviar un formulario inválido (ej. con un State de enumeración inválido o con campos obligatorios faltantes como nombre o ciudad; el género no es un campo obligatorio).

Un usuario debe poder crear nuevos listados de artista a través de la página "Nuevo Artista".

Un usuario no debe poder enviar un formulario inválido (ej. sin campos obligatorios).

Un usuario debe poder hacer clic en el local de un espectáculo próximo en la página de un Artista y, al llegar a la página de ese Local, ver el mismo espectáculo en la sección de espectáculos próximos del Local. Esto valida la coherencia de las relaciones.

Sugerencias para Hacer Destacar tu Proyecto (Challenges):
Estas son funcionalidades adicionales que puedes implementar para ir más allá de los requisitos básicos y mostrar un nivel avanzado de habilidad:

CHALLENGE: Implementar Disponibilidad de Tiempo:

Permite que un artista solo esté disponible para ser reservado en ciertas fechas/horas.

Deshabilita la capacidad de reservar un artista para un espectáculo fuera de su disponibilidad definida.

Mostrar Artistas Recientemente Listados y Locales Recientemente Listados en la Página de Inicio:

Muestra los resultados de Artistas y Locales ordenados por fecha de creación (los más nuevos primero).

Limita la visualización a los 10 elementos más recientemente listados.

Mostrar Álbumes y Canciones de un Artista en la Página del Artista:

Amplía el perfil del artista para incluir una sección donde se muestren sus álbumes y canciones. Esto implicaría expandir tu modelo de datos para incluir esta información.

Este desglose te ayudará a entender cada aspecto del proyecto y a planificar tu desarrollo de manera más efectiva. ¡Mucha suerte!
