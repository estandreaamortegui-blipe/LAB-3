# LAB-3
# Análisis espectral de la voz 

## Asignatura

Procesamiento Digital de Señales

## Programa

Ingeniería Biomédica – Universidad Militar Nueva Granada

## Práctica de laboratorio

**Análisis espectral de la voz**

## Integrantes

Andrea Carolina Amórtegui Carrillo – Código 5600963


---

## Descripción
El laboratorio se centra en el análisis espectral de señales de voz humana mediante herramientas de procesamiento digital de señales. Se emplean grabaciones de voz correspondientes a diferentes hablantes (hombres y mujeres), con el fin de extraer características relevantes tanto en el dominio del tiempo como en el dominio de la frecuencia.

A partir de estas señales, se realiza la visualización de la forma de onda, el cálculo de la Transformada de Fourier (FFT) y la obtención de parámetros característicos como la frecuencia fundamental (F0), la frecuencia media (centroide espectral), el brillo, la energía y la intensidad (RMS).

Adicionalmente, se evalúa la estabilidad de la señal de voz mediante el cálculo de jitter y shimmer, los cuales permiten cuantificar variaciones en la frecuencia y amplitud respectivamente. Finalmente, se comparan los resultados obtenidos entre voces masculinas y femeninas para identificar diferencias espectrales relevantes.

---


## Metodología

El desarrollo del laboratorio se dividió en dos partes principales. En cada etapa se emplearon herramientas de programación en Python para el procesamiento y análisis de señales de voz.

En primer lugar, se realizó el análisis de las señales en el dominio del tiempo y de la frecuencia, utilizando archivos de audio en formato .wav correspondientes a voces masculinas y femeninas. A partir de estas señales, se generaron gráficas temporales y espectrales mediante la Transformada Rápida de Fourier (FFT), lo que permitió identificar características importantes como la distribución de frecuencias.

Posteriormente, se llevó a cabo la extracción de parámetros relevantes de la señal de voz, tales como la frecuencia fundamental (F0) mediante autocorrelación, la frecuencia media (centroide espectral), el brillo, la energía y la intensidad (RMS), los cuales permiten caracterizar el comportamiento acústico de cada señal.

Al finalizar, se realizó el análisis de estabilidad de la voz mediante el cálculo de jitter y shimmer. Para ello, se aplicó un filtro pasa banda según el rango de frecuencias de cada género, se seleccionó una ventana representativa de la señal y se detectaron los picos para estimar las variaciones de frecuencia y amplitud ciclo a ciclo, permitiendo así comparar las diferencias entre voces masculinas y femeninas.

---

## Explicación del código

En esta sección se explica el funcionamiento del código, donde se reconoce la importancia del análisis espectral y la extracción de características en señales de voz, así como la evaluación de su estabilidad mediante jitter y shimmer.

### Importación de librerías

Primero se importan las librerías necesarias para la lectura, procesamiento y análisis de las señales de audio:

* `numpy `: Se utiliza para el manejo de arreglos numéricos y la realización de operaciones matemáticas como promedios, sumas, transformadas y autocorrelación.

* `matplotlib.pyplot `: Se emplea para la generación de gráficas en el dominio del tiempo y de la frecuencia, permitiendo visualizar las señales de voz y sus espectros.

* `scipy.io.wavfile `: Permite la lectura de archivos de audio en formato .wav, extrayendo tanto la señal como la frecuencia de muestreo.

* `scipy.signal ` (butter, filtfilt, find_peaks) :

* `butter `: Se usa para diseñar filtros digitales tipo Butterworth.

* `filtfilt `: Aplica el filtro a la señal sin introducir desfase.

* `find_peaks `: Permite detectar los picos de la señal, fundamentales para el cálculo de jitter y shimmer.

Estas herramientas son fundamentales para el análisis de señales de voz en el contexto del procesamiento digital de señales, permitiendo tanto la visualización como la extracción de características relevantes.

<p align="center">
<img width="1024" height="1536" alt="image" src="https://github.com/user-attachments/assets/945a1096-e777-4a98-b01e-3053878853b7" />
</p>
<p align="center">
  <em>Diagrama de flujo del codigo</em></p


---
### Parte A

Se analizaron seis señales de voz correspondientes a tres hablantes femeninas y tres masculinos, almacenadas en archivos en formato `.wav`. Estas señales fueron procesadas en Python con el fin de estudiar su comportamiento tanto en el dominio del tiempo como en el dominio de la frecuencia.

Inicialmente, cada señal fue cargada y preprocesada, convirtiéndola a formato mono en caso de ser estéreo y ajustando su tipo de dato para facilitar su manipulación numérica. Posteriormente, se construyó un eje temporal que permitió representar la señal de voz en función del tiempo.

Para cada archivo se generó la gráfica de la señal en el dominio del tiempo, lo cual permitió observar la variación de la amplitud y la estructura general de la voz.

A partir de estos cálculos, se generaron los espectros de magnitud considerando únicamente las frecuencias positivas, lo cual facilita su interpretación.

<table>
  <tr>
    <td align="center">
      <img width="817" height="632" alt="image" src="https://github.com/user-attachments/assets/cfbeb95c-23a3-4888-84da-b2cd3ea7a6ab" />
      <br />
      <em>GRAFICA MUJER 1</em>
    </td>
    <td align="center">
      <img width="821" height="611" alt="image" src="https://github.com/user-attachments/assets/6289393c-5b5e-4279-960d-5394f410096b" />
      <br />
      <em>ESPECTRO DE FRECUENCIA MUJER 1</em>
    </td>
  </tr>
</table>
<table>
  <tr>
    <td align="center">
      <img width="811" height="622" alt="image" src="https://github.com/user-attachments/assets/d71c16a3-e25c-4f04-acba-3e130ab2711f" />
      <br />
      <em>GRAFICA MUJER 2</em>
    </td>
    <td align="center">
      <img width="827" height="624" alt="image" src="https://github.com/user-attachments/assets/364a4616-4eb7-4e6e-bbd8-5d8b9302284b" />
      <br />
      <em>ESPECTRO DE FRECUENCIA MUJER 2</em>
    </td>
  </tr>
</table>
<table>
  <tr>
    <td align="center">
      <img width="827" height="626" alt="image" src="https://github.com/user-attachments/assets/536ff779-8532-44a8-8303-03cd3e111243" />
      <br />
      <em>GRAFICA MUJER 3</em>
    </td>
    <td align="center">
      <img width="813" height="620" alt="image" src="https://github.com/user-attachments/assets/b941e7d3-9c03-491a-9012-39174bfe26bf" />
      <br />
      <em>ESPECTRO DE FECUENCIA MUJER 3</em>
    </td>
  </tr>
</table>
<table>
  <tr>
    <td align="center">
      <img width="820" height="623" alt="image" src="https://github.com/user-attachments/assets/380e0386-aacb-4190-beac-9bff125790e6" />
      <br />
      <em>GRAFICA HOMBRE 1</em>
    </td>
    <td align="center">
<img width="825" height="612" alt="image" src="https://github.com/user-attachments/assets/8ffdf001-3b38-48a3-8c3e-870d56953cf0" />
      <br />
      <em>ESPECTRO DE FRECUENCIA HOMBRE 1</em>
    </td>
  </tr>
</table>
<table>
  <tr>
    <td align="center">
     <img width="822" height="625" alt="image" src="https://github.com/user-attachments/assets/50525d6b-f095-4065-975f-afabe57a8ad4" />
      <br />
      <em>GRAFICA HOMBRE 2</em>
    </td>
    <td align="center">
      <img width="820" height="621" alt="image" src="https://github.com/user-attachments/assets/5bd10e04-d59e-43cc-8713-88e43b0fd3d6" />
      <br />
      <em>ESPECTRO DE FRECUENCIA HOMBRE 2</em>
    </td>
  </tr>
</table>
<table>
  <tr>
    <td align="center">
      <img width="828" height="625" alt="image" src="https://github.com/user-attachments/assets/30e82290-c050-4964-85f5-7bf9e68f8856" />
      <br />
      <em>GRAFICA HOMBRE 3</em>
    </td>
    <td align="center">
     <img width="828" height="629" alt="image" src="https://github.com/user-attachments/assets/14e5c41c-f838-4500-809a-be9c34ea665b" />
      <br />
      <em>ESPECTRO DE FRECUENCIA HOMBRE 3</em>
    </td>
  </tr>
</table>

Posteriormente, se aplicó la Transformada Rápida de Fourier (FFT) a cada señal, con el fin de obtener su representación en el dominio de la frecuencia. Este proceso permitió identificar la distribución de energía en las diferentes componentes frecuenciales de la señal.

```python
fft_audio = np.fft.fft(audio)
frecuencias = np.fft.fftfreq(N, 1/fs)
magnitud = np.abs(fft_audio) / N
```

Adicionalmente, se calcularon parámetros característicos de cada señal de voz. La frecuencia fundamental (F0) fue estimada mediante autocorrelación, lo cual permite identificar la periodicidad principal de la señal.

```python
corr = np.correlate(signal, signal, mode='full')
corr = corr[len(corr)//2:]
```
La frecuencia media o centroide espectral se calculó como el promedio ponderado de las frecuencias presentes en la señal, indicando el “centro de masa” del espectro.

```python
frecuencia_media = np.sum(frecuencias * magnitud) / np.sum(magnitud)
```
El brillo corresponde al centroide espectral, por lo que valores más altos indican mayor contenido en frecuencias altas.

La energía de la señal se obtuvo como la suma del cuadrado de sus amplitudes, representando la potencia total de la señal.

```python
energia = np.sum(audio**2)
```
La intensidad se calculó mediante el valor RMS (Root Mean Square), el cual representa el nivel promedio de la amplitud de la señal.

```python
rms = np.sqrt(np.mean(audio**2))
```


### Representación gráfica de las señales

Las gráficas obtenidas permiten visualizar claramente las diferencias entre las señales de voz. En el dominio del tiempo se observan variaciones en la amplitud y forma de onda, mientras que en el dominio de la frecuencia se identifican las componentes principales de cada señal.

A partir de estas representaciones, es posible evidenciar que las voces femeninas presentan mayor contenido en frecuencias altas, mientras que las voces masculinas concentran su energía en frecuencias más bajas.


### Resultado parte A

El análisis espectral permitió caracterizar cada señal de voz mediante parámetros relevantes como la frecuencia fundamental, el centroide espectral, la energía y la intensidad.

Se observó que las voces masculinas presentan valores de frecuencia fundamental menores en comparación con las voces femeninas, lo cual está relacionado con las diferencias fisiológicas en las cuerdas vocales. Asimismo, el contenido frecuencial de las voces femeninas tiende a ser más alto, lo que se refleja en un mayor brillo y centroide espectral.

Estos resultados evidencian la utilidad del análisis en frecuencia para la diferenciación de señales de voz y su aplicación en áreas como el reconocimiento de voz y el análisis biomédico.

---

### Parte B

En esta sección se realizó el análisis de la estabilidad de las señales de voz mediante el cálculo de jitter y shimmer, los cuales permiten evaluar variaciones en la frecuencia y amplitud respectivamente.

Inicialmente, cada señal fue filtrada utilizando un filtro pasa banda con el fin de eliminar ruido y conservar únicamente el rango de frecuencias relevante para la voz humana. Para las voces masculinas se empleó un rango entre 80 Hz y 400 Hz, mientras que para las voces femeninas se utilizó un rango entre 150 Hz y 500 Hz.

```python
senal_filtrada = filtro_pasabanda(senal, fs, f_low, f_high)
```
<table>
  <tr>
    <td align="center">
     <img width="1297" height="517" alt="image" src="https://github.com/user-attachments/assets/b4b1f1ed-c5ca-4fe3-b5fa-63a984b92bdf" />
      <br />
      <em>SEÑAL ORIGNIAL VS FILTRADA (MUJER 1)</em>
    </td>
    <td align="center">
      <img width="813" height="620" alt="image" src="https://github.com/user-attachments/assets/e2f87bb9-7272-44e0-b839-d2ede64d4fb1" />
      <br />
      <em>ESPECTRO DE FRECUENCIA DE LA SEÑAL FILTRADA</em>
    </td>
  </tr>
</table>
<table>
  <tr>
    <td align="center">
     <img width="1292" height="519" alt="image" src="https://github.com/user-attachments/assets/2d507950-9b4b-4373-affc-4c23a7ff4fe2" />
      <br />
      <em>SEÑAL ORIGNIAL VS FILTRADA (HOMBRE 1)</em>
    </td>
    <td align="center">
      <img width="818" height="609" alt="image" src="https://github.com/user-attachments/assets/ca5a35e1-6893-4557-bd45-bb4d3156835e" />
      <br />
      <em>ESPECTRO DE FRECUENCIA DE LA SEÑAL FILTRADA</em>
    </td>
  </tr>
</table>

En los puntos dos, tres y cuatro, se realizó la medición de jitter y shimmer con el objetivo de evaluar la estabilidad de las señales de voz, teniendo en cuenta las variaciones en la frecuencia y en la amplitud a lo largo del tiempo.

Para el desarrollo de esta parte, inicialmente se aplicó un filtro pasa banda a cada señal con el fin de aislar el rango de frecuencias correspondiente a la voz humana. Posteriormente, se seleccionó una ventana de la señal con comportamiento periódico, lo que permitió realizar un análisis más preciso.

#### Medición del Jitter (variación en la frecuencia fundamental)

El jitter mide la variación en el periodo de la señal de voz entre ciclos consecutivos. Para su cálculo, se detectaron los picos de la señal, los cuales representan los ciclos de vibración. A partir de estos picos, se calcularon los periodos \( T_i \) y sus diferencias sucesivas.

El jitter absoluto se obtuvo como el promedio de las diferencias entre periodos consecutivos, mientras que el jitter relativo se calculó como el porcentaje de esta variación respecto al periodo promedio.

Los resultados obtenidos muestran valores elevados de jitter en varias señales, especialmente en las voces masculinas. Por ejemplo, la señal *hombre1.wav* presenta un jitter de 13.9308%, mientras que *mujer3.wav* alcanza un valor de 12.4154%. Estos valores se encuentran por encima del rango típico (menor al 1%), lo que indica una alta variabilidad en la frecuencia de la señal.

#### Medición del Shimmer (variación en la amplitud)

El shimmer mide la variación en la amplitud de la señal entre ciclos consecutivos. Para su cálculo, se tomaron las amplitudes en los picos detectados y se analizaron las diferencias entre valores consecutivos.

El shimmer absoluto corresponde al promedio de estas diferencias, mientras que el shimmer relativo se expresa como un porcentaje respecto a la amplitud promedio.

En los resultados obtenidos, se observan valores de shimmer superiores a los rangos típicos (3%–5%). Por ejemplo, la señal *hombre1.wav* presenta un shimmer de 17.6272%, y *hombre2.wav* alcanza 15.1376%. Incluso en señales femeninas como *mujer3.wav*, el valor es de 10.0855%, lo cual indica una variabilidad significativa en la amplitud de la señal.

#### Análisis de los resultados

Los valores obtenidos de jitter y shimmer evidencian una alta variabilidad en varias de las señales analizadas. Esto puede explicarse por diferentes factores:

- Presencia de ruido en las grabaciones.
- Segmentos de voz que no son completamente periódicos.
- Variaciones naturales en la producción vocal de los hablantes.
- Limitaciones en la detección automática de picos.
- Condiciones no controladas durante la adquisición de las señales.

Además, es importante considerar que el cálculo de estos parámetros depende fuertemente de la correcta identificación de los ciclos de la señal. Si la señal no presenta una periodicidad clara, los valores de jitter y shimmer pueden aumentar considerablemente.

#### Resultados obtenidos

Los valores finales de jitter y shimmer se resumen en la siguiente tabla:

| Archivo     | Genero | Jitter (%) | Shimmer (%) |
|------------|--------|------------|-------------|
| mujer1.wav | Mujer  | 3.1462     | 4.9545      |
| mujer2.wav | Mujer  | 2.2534     | 5.5305      |
| mujer3.wav | Mujer  | 12.4154    | 10.0855     |
| hombre1.wav| Hombre | 13.9308    | 17.6272     |
| hombre2.wav| Hombre | 11.5165    | 15.1376     |
| hombre3.wav| Hombre | 11.6516    | 12.5142     |

A partir de estos resultados, se observa que las señales masculinas presentan, en general, mayores valores de jitter y shimmer en comparación con las señales femeninas, lo cual indica una mayor variabilidad en la frecuencia y amplitud de estas señales bajo las condiciones de análisis realizadas.

---

### Parte C – Comparación y conclusiones

#### 1. ¿Qué diferencias se observan en la frecuencia fundamental?

A partir de los resultados obtenidos, se observa una diferencia clara entre las voces masculinas y femeninas en términos de frecuencia fundamental (F0).

Las voces femeninas presentan valores de F0 más altos:
- mujer1: 229.67 Hz  
- mujer2: 178.44 Hz  
- mujer3: 181.13 Hz  

Mientras que las voces masculinas presentan valores más bajos:
- hombre1: 113.74 Hz  
- hombre2: 109.43 Hz  
- hombre3: 154.84 Hz  

Esto confirma el comportamiento esperado, ya que las voces masculinas tienen frecuencias fundamentales menores debido a que las cuerdas vocales son más largas y gruesas, generando vibraciones más lentas. En contraste, las voces femeninas presentan frecuencias más altas debido a cuerdas vocales más cortas y delgadas.

---

#### 2. ¿Qué otras diferencias notan en términos de brillo, media o intensidad?

En cuanto a la frecuencia media y el brillo (centroide espectral), se observa que en general las voces femeninas tienden a presentar valores elevados, como en el caso de:
- mujer2: 4337.16 Hz  
- mujer3: 3353.4 Hz  

Sin embargo, también se observa que una señal masculina (hombre3) presenta un valor alto (4712.82 Hz), lo cual indica que este parámetro no depende únicamente del género, sino también del contenido espectral específico de la señal y la forma de pronunciación.

En términos de energía e intensidad (RMS), no se observa una relación directa con el género. Por ejemplo:
- mujer2 presenta una intensidad alta (5071.45)
- hombre2 presenta una intensidad baja (1367.55)

Esto indica que estos parámetros dependen más de la fuerza de la voz, la distancia al micrófono y las condiciones de grabación, más que del género del hablante.

---

#### 3. Conclusiones sobre el comportamiento de la voz en hombres y mujeres

El análisis realizado permite concluir que la frecuencia fundamental es el parámetro más confiable para diferenciar entre voces masculinas y femeninas, ya que presenta una separación clara entre ambos grupos.

Por otro lado, parámetros como el brillo y la frecuencia media pueden mostrar tendencias generales, pero no son determinantes por sí solos, ya que pueden variar dependiendo del contenido espectral de la señal.

En cuanto a la energía y la intensidad, estos parámetros no permiten diferenciar el género de forma directa, ya que dependen principalmente de la forma en que se emite la voz y de las condiciones de grabación.

Adicionalmente, el análisis de jitter y shimmer mostró valores elevados en varias señales, especialmente en las masculinas:
- hombre1: jitter 13.93%, shimmer 17.62%
- hombre2: jitter 11.51%, shimmer 15.13%

Estos valores indican una alta variabilidad en la señal, lo cual puede deberse a ruido, falta de periodicidad o condiciones no controladas durante la grabación.

---

#### 4. Importancia clínica del jitter y shimmer en el análisis de la voz

El jitter y el shimmer son parámetros fundamentales en el análisis clínico de la voz, ya que permiten evaluar la estabilidad de la vibración de las cuerdas vocales.

El jitter mide las variaciones en la frecuencia entre ciclos consecutivos, mientras que el shimmer mide las variaciones en la amplitud. En condiciones normales, estos valores suelen ser bajos (jitter < 1% y shimmer < 3–5%).

En los resultados obtenidos, muchos valores superan estos rangos, lo cual puede deberse a:
- Ruido en las señales
- Segmentos no periódicos
- Errores en la detección de picos
- Condiciones de grabación no controladas

En el ámbito clínico, valores elevados de jitter y shimmer pueden estar asociados a patologías vocales como disfonías o alteraciones en las cuerdas vocales. Sin embargo, en este caso no se puede concluir la presencia de una patología, ya que los valores también pueden estar influenciados por factores externos.

Por lo tanto, estos parámetros son herramientas útiles para el análisis de la voz, pero deben ser interpretados en conjunto con otros estudios y en condiciones controladas.

---

## Discusión y analisis de resultados

Las señales de voz en el laboratorio, la idea era meternos de lleno en cómo se comportan distintas características acústicas, tanto en el tiempo como en la frecuencia, y de paso mirar unos parámetros que miden la estabilidad de la voz, como el jitter y el shimmer.

Lo primero que saltó a la vista fue lo de siempre: la frecuencia fundamental (esa que asociamos con el tono de la voz) es claramente distinta entre hombres y mujeres. En las voces femeninas andaba entre 178 Hz y 229 Hz, mientras que en las masculinas estaba más abajo, entre 109 Hz y 154 Hz. Nada nuevo bajo el sol, la teoría lo explica: cuerdas vocales más largas y gruesas vibran más lento (hombres), y las más cortas y delgadas vibran más rápido (mujeres).

Después nos pusimos a ver otros aspectos, como el centroide espectral o el brillo, que básicamente te dicen dónde se concentra la energía en el espectro. Aquí las mujeres, en general, apuntan más hacia frecuencias altas. Pero ojo, no es una regla fija. Por ejemplo, en el archivo hombre3.wav los valores de frecuencia media salieron bastante altos. Eso te hace pensar que el asunto no es solo cuestión de género, también influye cómo pronuncia cada quien, la entonación, la intensidad y hasta lo que está diciendo en ese momento.

Con el RMS, que viene siendo la intensidad promedio de la señal, no encontramos ningún patrón claro ligado al género. Había mujeres con RMS alto y hombres con RMS bajo, y viceversa. La explicación más sensata es que la intensidad depende más de cosas como si la persona habló cerca o lejos del micrófono, cómo estaba configurada la grabación, o el ruido del entorno, que de si es hombre o mujer.

Ahora, el tema del jitter y el shimmer sí que dio para pensar. El jitter mide las variaciones en el periodo (la frecuencia) de un ciclo a otro, y el shimmer hace lo mismo pero con la amplitud. En una voz estable, estos valores suelen ser bajos. Pero cuando vimos los resultados, algunos eran altísimos. En voces masculinas, por ejemplo, encontramos jitter por encima del 10% y shimmer llegando al 17%. Para que te hagas una idea, lo que se considera normal suele ser jitter menor al 1% y shimmer entre 3% y 5% más o menos.

Uno podría pensar que esos números tan altos son señal de algún problema vocal, pero no hay que apresurarse. Resulta que estos parámetros son muy sensibles. Si la señal tiene ruido, si hay partes donde la voz no es tan periódica, o si el algoritmo que usamos para detectar los picos falla un poco, los valores se disparan. Y como nuestras grabaciones no fueron en un entorno súper controlado, pues es probable que eso haya pasado. De hecho, para poder estimarlos bien tuvimos que filtrar y elegir ventanas donde la voz se viera más estable.

En el mundo clínico, el jitter y el shimmer sí se usan para evaluar la voz, sobre todo en casos de disfonías o problemas en las cuerdas vocales. Pero si hablamos de patologías más complejas, como las afasias (que afectan el lenguaje, no la parte motora de la voz), pues estos parámetros no dicen mucho. En la disartria, que sí afecta el control muscular del habla, pueden tener más sentido, pero igual hay que combinarlos con otras pruebas.

Al final, lo que queda claro es que estas herramientas son útiles, pero no son la verdad absoluta. Sirven para dar pistas, pero un diagnóstico clínico requiere más cosas: otros análisis acústicos, la opinión de especialistas, evaluaciones más completas.

En resumen, el laboratorio nos sirvió para ver en la práctica cómo el procesamiento de señales (con Fourier, autocorrelación, filtros, etc.) permite describir la voz con números y gráficas. También aprendimos que los resultados dependen un montón de cómo se tomen las muestras y cómo se procesen. Y sí, aunque hay diferencias generales entre voces de hombres y mujeres, al final cada señal es única y está llena de matices.

---

## Conclusiones

- Se logró implementar correctamente el procesamiento digital de señales de voz mediante herramientas como la Transformada de Fourier y la autocorrelación, permitiendo analizar las señales tanto en el dominio del tiempo como en el dominio de la frecuencia.

- La frecuencia fundamental (F0) demostró ser el parámetro más confiable para diferenciar entre voces masculinas y femeninas, evidenciando valores más altos en las voces femeninas y más bajos en las masculinas, en concordancia con las características fisiológicas de las cuerdas vocales.

- El análisis del centroide espectral (frecuencia media) y el brillo mostró que las voces femeninas tienden a presentar mayor contenido en frecuencias altas; sin embargo, estos parámetros no son completamente determinantes, ya que dependen del contenido espectral específico de cada señal.

- La energía y la intensidad (RMS) no presentaron una relación directa con el género, lo que indica que estos parámetros están más influenciados por factores como la forma de emisión de la voz, la intensidad del hablante y las condiciones de grabación.

- Los parámetros de jitter y shimmer permitieron evaluar la estabilidad de la señal de voz; sin embargo, los valores obtenidos fueron en muchos casos superiores a los rangos típicos, evidenciando la sensibilidad de estos indicadores frente al ruido, la falta de periodicidad y posibles errores en la detección de picos.

- Se evidenció la importancia del preprocesamiento de la señal, especialmente el filtrado y la selección de ventanas periódicas, ya que estos procesos influyen significativamente en la precisión de los resultados obtenidos.

- Se permitió comprender la relevancia del procesamiento digital de señales en aplicaciones como el análisis biomédico y el reconocimiento de voz, destacando la necesidad de trabajar con señales de buena calidad y condiciones controladas para obtener resultados más precisos

