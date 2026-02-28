# Tablero dinámico de vigilancia epidemiológica de enfermedades transmitidas por vector: Dengue

Primeros pasos:
Descargar e instalar *R* 'https://cran.r-project.org/'   
Descargar e instalar Rtools correspondientes con la versión de *R* instalada (actualmente 4.5) 'https://cran.r-project.org/bin/windows/Rtools/rtools45/rtools.html'   
Descargar e instalar Rstudio 'https://posit.co/download/rstudio-desktop/'   

Dentro del archivo Rmd vienen las librerias a instalar, cada una se instala de la siguiente forma dentro del programa Rstudio:
*install.library("nombre del paquete")*

Este tablero se encuentra en modo de pruebas, para utilizarlo se recomienda hacer las siguientes modificaciones en las líneas de código de la 126 a la 129:

## Dice
`126 hist <- read_rds('data/historicos/dengue_2020_2024.rds') %>% `  
`127  bind_rows(`  
`128    read_delim('data/historicos/DENGUE2_311225.txt', delim = '|', locale = locale(encoding = 'latin1'), quote = '', comment = '') %>% mutate(CERTIFICADO_DEFUNCION = as.numeric(CERTIFICADO_DEFUNCION))`   
`129  ) %>% `   

## Debe decir
`126 hist <- bind_rows(`  
`127 read_delim('data/historicos/DENGUE_2021.txt', delim = '|', locale = locale(encoding = 'latin1'), comment = '', quote = '') %>% mutate(CERTIFICADO_DEFUNCION = as.numeric(CERTIFICADO_DEFUNCION)),`   
`128 read_delim('data/historicos/DENGUE_2022.txt', delim = '|', locale = locale(encoding = 'latin1'), comment = '', quote = '') %>% mutate(CERTIFICADO_DEFUNCION = as.numeric(CERTIFICADO_DEFUNCION)),`   
`129 read_delim('data/historicos/DENGUE_2023.txt', delim = '|', locale = locale(encoding = 'latin1'), comment = '', quote = '') %>% mutate(CERTIFICADO_DEFUNCION = as.numeric(CERTIFICADO_DEFUNCION)),`   
`130 read_delim('data/historicos/DENGUE_2024.txt', delim = '|', locale = locale(encoding = 'latin1'), comment = '', quote = '') %>% mutate(CERTIFICADO_DEFUNCION = as.numeric(CERTIFICADO_DEFUNCION)),`   
`131 read_delim('data/historicos/DENGUE_2025.txt', delim = '|', locale = locale(encoding = 'latin1'), comment = '', quote = '') %>% mutate(CERTIFICADO_DEFUNCION = as.numeric(CERTIFICADO_DEFUNCION))`   
`132 ) %>% `   

La configuración de la estructura de los datos es la siguiente:   
Carpeta raíz -> dengue__.Rmd   
Carpeta raíz -> poblacion_1990_2040.rds es un archivo armado con datos de CONAPO y DGIS, incluye población dividida y división de Jurisdicciones   
Carpeta raíz/data -> Archivo actual de dengue de vigilancia epidemiológica (archivo de txt de plataforma)   
Carpeta raíz/data/historicos -> archivos de cierre de vigilancia epidemiológica en txt   

# Fechas de corte probables:    
* 2020, el archivo se subió el 26 de febrero de 2021
* 2021, el archivo se subió el 15 de marzo de 2022
* 2022, el archivo se subió el 19 de abril de 2023
* 2023, el archivo se subió el 26 de marzo de 2024
* 2024, el archivo se subió el 31 de marzo de 2025
* 2025, el archivo más reciente se subió el 20 de febrero de 2026

Recursos para aprender bases de *R*   
'https://swcarpentry.github.io/r-novice-inflammation/'   
'https://swcarpentry.github.io/r-novice-gapminder'   
