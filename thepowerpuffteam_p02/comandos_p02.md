# Comandos de la Práctica 02
## The Powerpuff Team
### Integrante 1: Abasolo Cortés Natalia
### Integrante 2: Pimentel Ruíz Carlos
### Integrante 3: Gómez Mora Héctor Eduardo

## Parte I.
01. `mkdir thepowerpuffteam_p02`
02.	\
03.	\
04. `mkdir -p data/{filtered,raw_data} meta scripts figures archive`

## Parte II.

|          Plataforma/compañía          	| Longitud de Reads (pb) 	| # reads por run 	|  Tiempo  	| Costo x 10^6 bases 	| % Error 	|                          Química                         	|
|:-------------------------------------:	|:----------------------:	|:---------------:	|:--------:	|:------------------:	|:-------:	|:--------------------------------------------------------:	|
| Primera Generación                    	|                        	|                 	|          	|                    	|         	|                                                          	|
|        Sanger/Life Technologies       	|           800          	|        1        	|    2h    	|        2400        	|   0.3   	|                    Terminador Dideoxi                    	|
| Segunda Generación                    	|                        	|                 	|          	|                    	|         	|                                                          	|
|           454 GS FLX+/Roche           	|           700          	|      1×10^6     	|  24/48 h 	|         10         	|    1    	|                     Pirosecuenciación                    	|
|             HiSeq/Illumina            	|         2 x 150        	|      5x10^9     	| 27/240 h 	|         0.1        	|   0.8   	|                 Terminadores reversibles                 	|
|           Retrovolocity/BGI           	|           50           	|      1x10^9     	|    14d   	|        0.01        	|   0.01  	|                   Nanoesferas/ Ligadura                  	|
|     Ion Proton /Life Technologies     	|           200          	|      6x10^7     	|   2-5 h  	|          1         	|   1.7   	|                   detección de Protones                  	|
| Tercera Generación                    	|                        	|                 	|          	|                    	|         	|                                                          	|
|           Heliscope/Helicos           	|           35           	|      7x10^9     	|    8d    	|        0.01        	|   0.2   	| Secuenciación de molécula sencilla (SMS) en tiempo real. 	|
| Nanopore/Oxford Nanopore Technologies 	|          >5000         	|      6x10^4     	|  48/72h  	|         <1         	|    34   	|                    SMS en Tiempo Real                    	|

Fuente: Kulski, J., 2016. Next-Generation Sequencing — An Overview of the History, Tools, and “Omic” Applications. Next Generation Sequencing - Advances, Applications and Challenges,.

## Parte III.
1.
  ~~~bash
  # Situado en thepowerpuffteam_p02
  mv ~/Downloads/ERR486827_1.fastq.gz data/raw_data
  mv ~/Downloads/ERR486827_2.fastq.gz data/raw_data
  #
  ln data/raw_data/ERR486827_1.fastq.gz data/filtered/ERR486827_1.fastq.gz
  ln data/raw_data/ERR486827_2.fastq.gz data/filtered/ERR486827_2.fastq.gz

  # Conversión a .fasta
  gunzip -c data/filtered/ERR486827_1.fastq.gz | awk 'NR%4==1{print ">" $0} NR%4==2{print}' > data/filtered/raw_1.fasta

  gunzip -c data/filtered/ERR486827_2.fastq.gz | awk 'NR%4==1{print ">" $0} NR%4==2{print}' > data/filtered/raw_2.fasta
  ~~~

2.
  Ambos archivos tienen la misma cantidad de secuencias:
  ~~~bash
  # Cuenta de la cantidad de secuencias en el primer archivo
  wc -l data/filtered/raw_1.fasta # número de líneas incluyendo headers
  expr 797648 / 2 # 398824 secuencias del primer archivo .fasta

  #Cuenta de la cantidad de secuencias en el segundo archivo
  wc -l data/filtered/raw_2.fasta # número de líneas incluyendo headers
  expr 797648 / 2 # 398824 secuencias del segundo archivo .fasta
  ~~~

  Obtención de la longitud por cada lectura:
  ~~~bash
  awk 'NR%2==0{printf length ","}' data/filtered/raw_1.fasta > data/filtered/lengths_1.csv
  #
  awk 'NR%2==0{printf length ","}' data/filtered/raw_2.fasta > data/filtered/lengths_2.csv
  ~~~

  Cálculo de los promedios:
  ~~~bash
  awk -F [,] '{total=398824; for(i=1;i<=NF;i++) sum+=$i; print sum/total; sum=0}' data/filtered/lengths_1.csv

  awk -F [,] '{total=398824; for(i=1;i<=NF;i++) sum+=$i; print sum/total; sum=0}' data/filtered/lengths_2.csv
  ~~~

3. Del siguiente alineamiento
  ~~~
  AGCATGTTAGATTA--GATAGCTGTGCTA
  ------TTAGATAAAGGATA-CTG-----
  ~~~
  su CIGAR string es `6M1I1M2I4M1X3M`.

4.

  ~~~bash
  ln -s genomica_2020/hmora_p01/data/filtered/sequence.gff3 data/filtered/sequence.gff3

  # Número de reportes por categorías
  awk '{print $3}' data/filtered/sequence.gff3 | sort | uniq -c
  ~~~  

  De lo cuál se obtiene:

  | #  | categorías      |
  |----|-----------------|
  | 2  |                 |
  | 1  | 1               |
  | 13 | CDS             |
  | 1  | five_prime_UTR  |
  | 11 | gene            |
  | 1  | region          |
  | 5  | stem_loop       |
  | 1  | three_prime_UTR |

## Parte IV.

## Parte V


Las secuencias crudas de Orcinus orca se obtuvieron de https://www.ebi.ac.uk/ena/browser/view/PRJNA167475
Posteriormente las posicionamos en el escritorio donde procedimos a colocar todas las secuencias `fastq.gz` en un mismo directorio llamado `Orcinus_orca_genome`

1.
~~~bash
mv ~/Desktop/ena_files/S*/*.fastq.gz ~/Desktop/ena_files/Orcinus_orca_genome/

mv ~/Desktop/ena_files/Orcinus_orca_genome/ ~/Desktop/genomica_2020-2/thepowerpuffteam_p02/data/raw_data/
~~~

2. Se utilizó Ilumina HiSeq 2000. Esta realiza una secuenciación por síntesis basada en terminadores reversibles, presenta una cobertura de ~30x en una sola corrida.
