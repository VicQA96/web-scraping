# Analítica descriptiva - Web Scraping🎓
## _Brecha de género en los ingresos del mercado salarial de Chile_




#### Descripción

Este repositorio contiene dos notebooks de Python que utilizan librerias como _'Selenium'_, _'Pandas'_, _'Matplotlib'_ y _'Seaborn'_
para la extracción y visualización de datos que se obtuvieron a travez de web scraping
en el sitio web del [Instituto nacional de Estadísticas de Chile][df5]. 

- ✨Magia

## Contenido

- **Graficos.ipynb** : Este notebook se centra en la visualización de datos utilizando gráficos.
- **ine.ipynb** : Este notebook se encarga de extraer datos de una tabla en línea y guardarlos en un archivo CSV.

## Tecnologías utilizadas

- Python 3.9
- Selenium
- Chromedriver
- Seaborn

```sh
!pip install selenium
!pip install seaborn 
```
Asegurate de tener instaladas las siguientes librerias
- Matplotlib
- Pandas
- Plotly
- Scipy

> Este proyecto puede funcionar sin instalar
> Chromedriver de forma manual si ya está
> incluido en tu PATH o si utilizas herramientas
> que lo gestionan automáticamente



## Uso

#### _Graficos.ipynb_
Este notebook utiliza la biblioteca seaborn para realizar gráficos. 
Asegúrate de tener configurado el entorno adecuado y sigue las instrucciones 
dentro del notebook para crear visualizaciones.

#### _ine.ipynb_
Este notebook realiza la extracción de datos de un sitio web utilizando Selenium. Para ejecutarlo:
1. Asegúrate de tener el controlador de Chrome configurado en tu sistema. 
2. Ejecuta el siguiente comando en una celda del notebook para instalar Selenium:
```sh
!pip install selenium
```
3. Luego, ejecuta el código para extraer los datos:
```sh
from selenium import webdriver
from selenium.webdriver.common.by import By
import pandas as pd

# Configuración del driver de Chrome
options = webdriver.ChromeOptions()
options.add_argument('--headless')
options.add_argument('--no-sandbox')
options.add_argument('--disable-dev-shm-usage')
driver = webdriver.Chrome(options=options)

try:
    driver.get("https://stat.ine.cl/Index.aspx?DataSetCode=ESI_BG_YMEDIO_OCU")
    table = driver.find_element(By.XPATH, "//div[@id='tabletofreeze']/table")
    rows = table.find_elements(By.TAG_NAME, "tr")
    table_data = []
    for row in rows:
        cells = row.find_elements(By.TAG_NAME, "td")
        row_data = [cell.text for cell in cells]
        table_data.append(row_data)

    df = pd.DataFrame(table_data)
    df.to_csv("tabla_extraida.csv", index=False, header=False)
    print("Tabla extraída y guardada en tabla_extraida.csv")
finally:
    driver.quit()
```

## Licencia

Este proyecto está bajo la Licencia MIT. Consulta el archivo LICENSE para más detalles.

# Agradecimientos🌸
Queremos agradecer a los siguientes autores por el arduo trabajo en este proyecto:

- **Ignacia Quezada** - [VicQA96][df6]
- **Thiare Águila** - [ThiareAguila][df7]

**2024-s2 ANALÍTICA INFB6100📘!**




   [df5]: <https://www.ine.gob.cl/>
   [df6]: <https://github.com/VicQA96>
   [df7]: <https://github.com/ThiareAguila>
