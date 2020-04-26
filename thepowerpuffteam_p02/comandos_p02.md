# Comandos de la Práctica 02
## The Powerpuff Team
### Integrante 1: Abasolo Cortés Natalia
### Integrante 2: Pimentel Ruíz Carlos
### Integrante 3: Gómez Mora Héctor Eduardo

## Parte I.
01. `mkdir thepowerpuffteam_p02`
02.
03. `mkdir -p data/{filtered,raw_data} meta scripts figures archive`

## Parte II.

## Parte III.
1.
  ~~~bash
  # Situado en genomica_2020-2
  mv ~/Downloads/ERR486827_1.fastq.gz data/raw_data
  mv ~/Downloads/ERR486827_2.fastq.gz data/raw_data
  #
  ln data/raw_data/ERR486827_1.fastq.gz data/filtered/ERR486827_1.fastq.gz
  # ln data/raw_data/ERR486827_2.fastq.gz data/filtered/ERR486827_2.fastq.gz

  # Descompresión a .fastq
  gunzip -c data/filtered/ERR486827_1.fastq.gz > data/filtered/raw_1.fastq
  # awk -F '[ +#/]' '{ gsub(/^@/,">",$0) ; print $1, $3 }' data/filtered/raw_1.fastq > secuencia
  ~~~

2.
3.
4.


## Parte IV.
