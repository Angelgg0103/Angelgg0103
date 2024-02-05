# Cargar los datos de la ENCODAT
datos <- read.csv("https://www.gob.mx/cms/uploads/attachment/file/477564/Informe_sobre_la_situacio_n_de_las_drogas_en_Me_xico_.csv")

# Filtrar los datos por tipo de droga (cualquier droga ilícita)
datos <- datos[datos$tipo == "Cualquier droga ilícita", ]

# Crear la gráfica de consumo de drogas por sexo y año
library(ggplot2)
ggplot(datos, aes(x = año, y = prevalencia, color = sexo)) +
  geom_line(size = 1.5) +
  geom_point(size = 3) +
  scale_x_continuous(breaks = seq(2005, 2024, by = 2)) +
  scale_y_continuous(labels = scales::percent) +
  labs(title = "Consumo de drogas ilícitas en México de 2005 a 2024",
       subtitle = "Prevalencia de consumo en población general de 12 a 65 años",
       x = "Año",
       y = "Prevalencia de consumo",
       color = "Sexo") +
  theme_minimal()
  
