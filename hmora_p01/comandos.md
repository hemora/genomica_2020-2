# Comandos de la Práctica 01
# Héctor E. Gómez Mora

# Parte I.

- `echo $0`
- `mkdir data filtered raw_data meta scripts figures archive`
- `mv raw_data data` y `mv filtered data`

**Respuesta 4:** El esquema trata de lidiar con el problema de la repoducibilidad
de los análisis mediante la estandarización de los nombres de directorios y ficheros.
De ello, siempre que exista...

- un directorio `data`, se sabrá que contiene las fuentes de datos utilizados
para realizar el análisis.
- un directorio `meta`, se sabrá que contiene metadatos que facilitan la manipulación
y caracterización de los datos.
- un directorio `scripts`, se sabrá que contiene el código que implementa las
funciones necesarias para replicar el análisis.
- un directorio `figures`, se sabrá que contiene scripts para generar y/o renderizar
modelos, imágenes y esquemas ilustrativos.
- un directorio `archive`, estará dedicado a guardar scripts con funcionalidades
potencialmente utilizables y del cuál se desea tener registro.
- un fichero `README` de extención `.txt` o `.md`, explicará brevemente
el objetivo del proyecto y cómo utilizar los componentes mencionados para generar
los resultados.

# Parte II.

- `chmod 700 scripts/delay.sh`
- `ls -l scripts/delay.sh`
- `sleep 30` added into delay.sh
- `./scripts/delay.sh &`
- `kill -9 10038` pid can change

# Parte III.

COVID-19 pertenece a la familia *Coronaviridae*, dentro de la cuál es clasificado como un
betacoronavirus. Se compone de una cadena sencilla positiva de RNA asociada con una glicoproteína de membrana
y una nucleocápside, además de proteínas espículas glicosiladas que le otorgan su forma
característica y le permiten alcanzar dimensiones de  500-200 nm.

Dichas espículas, también denominadas como proteínas **S**, son las encargadas de facilitar la
entrada del virus hacia las células del tracto gastro-intestinal y de los tejidos
repiratorio y nervioso. Cabe destacar que todos los activadores de esta proteína
se encuentran fácilmente en la célula afectada.

Una vez activada, esta proteína se encarga de "perforar" e introducir el material genético
mediante un proceso de estiramiento y separación de los receptores de la membrana celular, interceptados
previamente por el dominio **S1**, a través del dominio **S2**.

- `cd ~/Downloads`
- `mv sequence.fasta sequence.gff3 sequence_1.faa sequence_2.faa sequence_3.faa sra_data.fasta.gz sra_data.fastq.gz ~/Desktop/genomica_2020-2/hmora_p01/data/raw_data`

# Parte IV.
1. `ln -s data/raw_data/sequence.fasta data/filtered/sequence.fasta`
2. `ln -s data/raw_data/sequence.gff3 data/filtered/sequence.gff3`
3. `ln -s data/raw_data/sequence_1.faa data/filtered/sequence_1.faa`
4. `ln -s data/raw_data/sequence_2.faa data/filtered/sequence_2.faa`
5. `ln -s data/raw_data/sequence_3.faa data/filtered/sequence_3.faa`
6. `ln -s data/raw_data/sra_data.fasta.gz data/filtered/sra_data.fasta.gz`
7. `ln -s data/raw_data/sra_data.fastq.gz data/filtered/sra_data.fastq.gz`

- mkdir data/filtered/proteins
- mv sequence_1.faa sequence_2.faa sequence_3.faa
