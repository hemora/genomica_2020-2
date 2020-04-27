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

  # Descompresión a .fastq
  gunzip -c data/filtered/ERR486827_1.fastq.gz | awk 'NR%4==1{print ">" $0} NR%4==2{print}' > data/filtered/raw_1.fasta

  gunzip -c data/filtered/ERR486827_2.fastq.gz | awk 'NR%4==1{print ">" $0} NR%4==2{print}' > data/filtered/raw_2.fasta

  ~~~

2.
3.
4.


## Parte IV.

## Parte V


