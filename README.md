# DESCRIPCIÓN
El programa lee de una carpeta en Google Drive los archivos de sentencias judiciales de la la Sala Especializada en materia de Propiedad Intelectual del Tribunal Federal de Justicia Administrativa y divide su contenido en las siguientes columnas: 

● Autoridad demandada
● Magistrada
● Secretario
● Preámbulo
● Resultando
● Considerando
● Resolutivos

# OBJETIVO
El objetivo de este proyecto es impiar las sentencias judiciales de la Sala Especializada en materia de Propiedad Intelectual del Tribunal Federal de Justicia Administrativa en un dataset que pueda ser utilizado para entrenar un modelo de Procesamiento de Lenguaje Natural (PLN)

# ESTRUCTURA DE UNA SENTENCIA JUDICIAL
La estructura de una sentencia del TFJA es la siguiente (Soberanes Lasses & Soberanes Sánchez, 2018):
● Preámbulo: contiene los datos de identificación del asunto, incluyendo nombre de las partes, lugar y fecha, tipo de proceso.
● Resultandos: expresa los antecedentes procesales del caso.
● Considerandos: contiene los argumentos de las partes, las conclusiones y opiniones del tribunal, así como el criterio jurídico utilizado.
● Puntos resolutivos: Se consolida el sentido de la resolución.
● Firma del juez.
● Autorización del secretario.

# FUENTES DE DATOS
Los documentos se obtuvieron de la consulta de sentencias públicas en el SICSEJLDOC del Tribunal Federal de Justicia Administrativa, disponible en el
siguiente enlace:
http://sentencias.tfjfa.gob.mx:8080/SICSEJLDOC/faces/content/public/consultasentencia.xhtml

# ELIMINACIÓN DE DATOS NO RELEVANTES
El programa elimina los siguientes datos para evitar que el modelo se entrene con información irrelevante.
● Encabezados repetitivos posteriores a la primera página.
● Eliminación de números de página.
● Eliminación de asteriscos por información testada.
● Eliminación de espacios blancos y saltos de línea innecesarios.

# EXPRESIONES REGULARES
Las expresiones regulares utilizadas para obtener las secciones fueron:
❖ Preámbulo: Esta parte se tomó desde el inicio del documento hasta el párrafo en el que aparece el lugar y fecha de la sentencia.
❖ Resultandos: Se obtiene a partir de la palabra R E S U L T A N D O y sus variantes, hasta la palabra C O N S I D E R A N D O y sus variantes. Se obtienen de uno a más párrafos bajo la columna homónima.
❖ Considerandos: Se obtiene a partir de la palabra C O N S I D E R A N D O y sus variantes, hasta la palabra R E S U E L V E y sus variantes. Se obtienen de uno a más párrafos bajo la columna homónima.
❖ Puntos resolutivos: Se obtiene a partir de la palabra R E S U E L V E y sus variantes, hasta la palabra NOTIFÍQUESE y sus variantes. Se obtienen de uno a más párrafos bajo la columna “Puntos Resolutivos”.
