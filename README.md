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
