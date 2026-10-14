# Actividades de Búsqueda de Similitud Secuencial

## Desafío VII: Análisis de parámetros (E-value, Score e Identidad)

Al procesar la secuencia problema contra la base de datos y analizar los resultados obtenidos, se observan las siguientes relaciones estadísticas y matemáticas entre los parámetros del alineamiento:

- **E-value vs. % de Identidad:** Se evidencia una relación inversamente proporcional. A medida que aumenta el porcentaje de identidad entre la secuencia problema y las secuencias de la base de datos, el E-value disminuye. El E-value indica la cantidad de alineamientos con un score determinado que se esperarían encontrar por azar; por ende, un valor tendiente a cero refleja una mayor significancia estadística.
- **Score vs. % de Identidad:** Existe una relación directa, aunque no perfectamente lineal. En términos generales, a mayor identidad corresponde un mayor score. Sin embargo, un alineamiento corto con un alto porcentaje de identidad puede presentar un score total inferior al de un alineamiento extenso con menor identidad, debido a que el score tiene un carácter acumulativo a lo largo de toda la longitud alineada.
- **Score vs. E-value:** Presentan una relación inversamente proporcional y de carácter exponencial. Los scores más altos corresponden a valores de E-value que caen rápidamente hacia cero.

En conclusión, el E-value no es una probabilidad directa, sino un valor esperado que depende del tamaño de la base de datos, la longitud de la secuencia y el score del alineamiento. Si bien una alta significancia estadística sugiere fuertemente una relación de homología, esta inferencia biológica requiere considerar el contexto completo del análisis.

## Desafío VIII: Efecto de la longitud de la secuencia en la búsqueda

Al repetir las búsquedas utilizando fragmentos reducidos de la secuencia original (la mitad y un cuarto de su longitud), se evidencian cambios drásticos en los parámetros de los alineamientos devueltos:

- El score total y la cobertura del alineamiento (query cover) disminuyen drásticamente, dado que existen menos residuos disponibles para alinear y acumular puntaje en la matriz de sustitución.
- Los valores de E-value aumentan de forma considerable. Al acortar la longitud de la secuencia, se incrementa la probabilidad estadística de encontrar un alineamiento similar por puro azar dentro de una base de datos de gran tamaño, lo que reduce la significancia del resultado.
- Debido a la pérdida de poder discriminatorio, comienzan a aparecer resultados espurios (falsos positivos) y se pierde la sensibilidad analítica necesaria para detectar homólogos verdaderos pero evolutivamente distantes.

Se concluye que la confiabilidad estadística de un alineamiento depende de manera intrínseca de la longitud de la secuencia problema. Las secuencias muy cortas carecen del contexto necesario para separar homologías reales del simple ruido estadístico, independientemente de que presenten porcentajes de identidad elevados.

## Desafío IX: Identificación funcional y taxonómica

Al ejecutar la búsqueda de similitud secuencial contra la base de datos de proteínas no redundantes (nr), se definen los siguientes puntos:

- **Identidad funcional:** El mejor resultado obtenido corresponde a la enzima LpxA (acil-[ACP]--UDP-N-acetilglucosamina O-aciltransferasa). La secuencia analizada presenta repeticiones periódicas de hexapéptidos, patrón estructural característico del plegamiento de tipo beta-hélice levógira propio de esta superfamilia de proteínas.
- **Función biológica:** Esta enzima es responsable de catalizar la primera etapa de la biosíntesis del lípido A. Este componente lipídico actúa como el anclaje hidrofóbico central de los lipopolisacáridos (endotoxinas) localizados en la membrana externa bacteriana.
- **Grupo taxonómico:** La enzima es propia de las bacterias Gram-negativas, correspondientes al filo Pseudomonadota (Proteobacterias). Si bien el resultado principal suele clasificarse como "Multispecies" debido a su extrema conservación evolutiva, el organismo modelo de referencia inmediato es *Escherichia coli*.
- **Significancia estadística:** Se recuperan miles de secuencias homólogas con significancia estadística adecuada. Los primeros resultados del alineamiento arrojan un 100% de cobertura e identidad con un E-value de 0.0, confirmando que se trata de una enzima biológicamente esencial y altamente conservada en estos microorganismos.

## Desafío X: Búsqueda orientada a estructuras tridimensionales (PDB)

Al modificar la configuración de la búsqueda para utilizar Protein Data Bank (PDB) como base de datos objetivo en lugar de nr, los resultados varían de manera sustancial:

- La cantidad de resultados (hits) recuperados es significativamente menor. Esto responde a la naturaleza de la base de datos: PDB es un repositorio sumamente restrictivo que contiene de forma exclusiva aquellas secuencias proteicas cuyas estructuras tridimensionales han sido resueltas empíricamente (mediante cristalografía de rayos X, resonancia magnética nuclear o criomicroscopía electrónica).
- Los resultados recuperan estructuras físicas resueltas correspondientes a la enzima LpxA, las cuales son identificadas en el sistema mediante códigos alfanuméricos únicos de cuatro caracteres (como por ejemplo, 2JF2).
- Ejecutar una búsqueda contra PDB es el procedimiento inicial y fundamental para el **modelado por homología**. Resulta indispensable cuando el objetivo trasciende la mera identificación de la proteína y se requiere utilizar la estructura tridimensional de un homólogo validado como molde espacial. Esto permite predecir computacionalmente el plegamiento, analizar la estabilidad estructural o localizar el sitio activo de la secuencia problema.
