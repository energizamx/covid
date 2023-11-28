# covid
Proceso de Tasas de Defunción con Datos Oficiales México
Estos 2 archivos son las fuentes de datos y Fueron descargados según instrucciones en este canal https://t.me/sinmitos/3077
diccionario_datos_covid19(1).zip
Casos_Diarios_Municipio_Defunciones_20230625.csv
El Script covid.pl va leyendo estos datos y acomoda los casos por municipio, que vienen fecha-casos, fecha-casos durante los 1191 días=3.263 años de acumular casos, para reacomodarlos en forma de registros tipo:  entidad-municipio-casos
Adicionalmente, en ese mismo registro viene la población municipal, la cual se extrae para crear la tabla de poblacion municipal tipo : clave_municipal-municipio-población-entidad
La tabla de entidades tipo: clave_entidad-entidad-abreviatura
Con todo lo anterior generar una tabla nueva en la base de datos llamada Totales, con cada municipio y su total de casos en todos los 1191 días.  
Una tabla adicional llamada pobxent (población por entidad) para poder medir el avance porcentual de acumulación de casos en esa entidad
Los archivos municipios.sql, entidades.sql, casos.sql, población.sql siempre se están regenerando, pero no tienen cambios, son simples copias de los datos originales, así es que esos ya están cargados en la base de datos.
Con ellos y con el archivo queries.sql se producen la tabla pobxent y totales, las cuales previamente se limpian con truncate al inicio de queries.sql
Con esas tablas (municipios, entidades, casos, población) ya en la base de datos, se produce el primer reporte tablas.txt en la linea 121 dels script covid.pl, junto con los reportes internos en la base totales y pobxedo.  tablas.txt son 2 tablas en texto para ser leídas por el mismo script covid.pl  pobxedo y todos los municipios con sus casos, su población y su tasa de mortandad.
Esta misma tabla será leída por covid.pl para completarle columnas según se indica en covid.pl, lineas 149 y 151, que se escriben en el archivo tasas_defun.csv, según declarado en la linea 124 de covid.pl
Con tasas_defun.csv en hoja de cálculo se decora el reporte con títulos, colores, etc., que va en el archivo resultado.ods de donde se exporta el PDF, tasas_covid_municipio.pdf
Finalmente se exportó toda la base a covid.sql.gz para empaquetarse todo el folder tal como se ve.
El archivo casos.sql sólo se hizo una vez y se detectaron muchos registros con fecha y cero en esa fecha, se notará el tamaño monstruoso de tal archivo 108 MB y se mantiene este archivo por razones educativas.  No es de hecho malo mantenerlo, es ilustrativo de "no borrar ni los ceros", el registro indica que efectivamente esa fecha en ese municipio no se omitió registro, sino que fue cero.
Por esa razón se creó casos_no_cero.sql que ya elimina todos esos registros en cero (cero defunciones) y el espacio de trabajo pasa de 108 MB a 5.3 MB
El mensaje final para los que manejan tantos datos, es acostumbrarse a enviar la base de datos, no hojas de Excel.  Cuando la cantidd de datos es tan grande y estos deben procesarse, trabajar con tablas en bases de datos, es lo más fácil y práctico.  Todo este trabajo que tomó lo que se ve, escasas 2 medias tardes, realmente toma segundos para generar información útil como TASAS de defunción
De esas 2 medias tardes, la segunda, fue donde se crearon las 3 columnas de tasas estatales y tasa nacional, para poder detectar la tasa MEDIA de defunción de México. 
¿Por qué?  Si no hay media, no sabemos qué municipio está por arriba o por abajo de la media
Por qué tasa estatal (media estatal), porque hay estados con tasa media por encima y por abajo de la media nacional
Y lo mismo para municipios.  Los hay con tasas por debajo de su media estatal o nacional y por encima.
¿Todo lo anterior nos lleva a la razón central de ese reporte: QUIEN Y PARA QUE SACA PROVECHO de estos números?
Cualquiera con interes en entender qué pasó y por qué pasó.  
Aprender de este evento para entender qué causó que ciertos estados y/o municipios, no tuvieran tanta mortandad como otros lugares.  Acaso nos parece importante ¿entender esto?  Acaso nutrición, cultura, ¿genética?  ¿Acaso otros lugares del mundo han estado trabajando en esto?  
¿Sabíamos que tratar esto en línea fue tema de censura y cierre de canales de Youtube tildados de desinformadores?
Como si la ciencia suciediera por decreto o concenso (teorías del cambio climático incuestionable y los invernaderos con lo doble del CO2 atmosférico a 900 PPM resultan producir mucho mejor que a 45o PPM) y nadie tuviera razón para investigar más por razón natural de la ciencia: nunca dejar de investigar.
