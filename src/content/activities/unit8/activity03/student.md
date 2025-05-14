## Diseña el proceso generativo

Me interesa usar un Flow Field de forma circular en el cual se ubicarán unos agentes. Habrá solo un tipo de agente y este reaccionará de manera distinta a los tres
tipos de frecuencia: baja, media y alta.

Pienso controlar con un ruido Perlin la variación en la dirección de los campos del FlowField. Además, una distribución gaussiana para controlar las variaciones en la velocidad de las partículas

## Define los outputs visuales

Quiero que con las frecuencias altas se generen curvas que aparecen en una sección del FlowField. Esta sección se definirá variará con un ruido Perlin. El largo de las curvas se determinará con la intensidad. Cada vez que se detecte un bajo el canvas variará de color y con las frecuencias medias las curvas cambiarán de grosor, dando el efecto de que se están ensanchando.

as curvas que se generen con las frecuencias altas tendrán un tiempo de vida específico, luego desaparecerán con un "fade out". En su tiempo de vida, recorrerán el flow field.

## Documenta el diseño

```


┌────────────────────┐
│     INPUT AUDIO     │
│ "El Vikingo" (mp3) │
└────────┬───────────┘
         ▼
 ┌────────────────────────────────────────────┐
 │       ANÁLISIS EN TIEMPO REAL (p5.FFT)     │
 └────────────────────────────────────────────┘
         │
         ▼
┌────────────┬────────────┬────────────────────┬──────────────────────────────┐
│ Frecuencias│ Frecuencias│     Frecuencias     │        Amplitud (volumen)     │
│    Graves  │    Medias  │       Altas         │                                │
│  ("bass")  │    ("mid") │     ("treble")      │                                │
└────┬───────┴────┬───────┴──────────────┬──────┴─────────────┬────────────────┘
     │            │                     │                    │
     ▼            ▼                     ▼                    ▼
┌────────────┐ ┌──────────────────┐ ┌────────────────────────────┐ ┌──────────────────────┐
│ Cambio de  │ │ Grosor dinámico  │ │ Sección activa del flowfield│ │ Color de partículas  │
│ color fondo│ │ de las curvas    │ │ (varía con Perlin noise)   │ │ Saturación general   │
│ (canvas)   │ │ (ensanchamiento) │ └────────────┬───────────────┘ └──────────────────────┘
└────┬───────┘ └──────────────────┘              │
     │                                           ▼
     ▼                              ┌────────────────────────────────────────────────┐
┌─────────────────────────┐        │  CURVAS GENERADAS POR AGUDOS ("treble")         │
│ Color del fondo dinámico│        │  - Sección definida por ruido Perlin            │
│ Cambia con cada bajo    │        │  - Largo proporcional a intensidad del treble   │
└─────────────────────────┘        │  - Vida limitada (fade-out progresivo)          │
                                  │  - Siguen el flujo del Flow Field durante vida   │
                                  └──────────────────────────────────────────────────┘

                ┌──────────────────────────────────────────────┐
                │         FLOW FIELD CIRCULAR ORGÁNICO         │
                │   - Vector field deformado con Perlin noise  │
                │   - Utilizado por agentes y curvas activas   │
                └──────────────┬───────────────────────────────┘
                               ▼
               ┌────────────────────────────────────────┐
               │         AGENTES / PARTÍCULAS           │
               │   - Siguen el flujo de forma fluida    │
               │   - Reaccionan con color/tamaño        │
               └────────────────────────────────────────┘

```
