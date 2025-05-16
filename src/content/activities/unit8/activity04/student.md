## Explica brevemente cómo configuraste la detección de audio

En TouchDesigner hay varias herramientas para rastrear audio, y a partir de ellas se puede construiir un detector de beats o frecuencias muy completo. Sin embargo, 
Touch ya tiene una herramienta llamada audioAnalysis que nos da la posibilidad de rastrear las frecuencias bajas, medias y altas.

![image](https://github.com/user-attachments/assets/29aca055-4c83-4e8c-9e5b-ca5ed3737aec)

Yo decidí tomar solamente las frecuencias bajas y altas, pues era las que más detectaba con precisión. Sin embargo, hubiese podido también usar el "kick" o el "snare"

## Interacción

Para la interacción descargué el modelo de Mediapipe de Torim, que permite detectar las partes del cuerpo, las manos y la cara. Yo usé específicamente la detección 
de manos. Con el movimiento de una de las manos se puede mover todo el sistema de partículas. A donde vaya la mano, las partículas irán. Si no se detecta una mano,
no irán a ningún lado.

## Video

(Enlace)[https://youtu.be/RjoubEqzEdU]
