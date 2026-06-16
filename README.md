[Index.html](https://github.com/user-attachments/files/29013232/Index.html)
![targets](https://github.com/user-attachments/assets/f6d9c53f-6992-4117-ad15-f368eba5136f)

<img width="1600" height="2000" alt="cuadro" src="https://github.com/user-attachments/assets/467bdca7-0a36-4bcb-8899-14ae1b0d34a5" />
[audio..mp3](https://github.com/user-attachments/files/29013174/audio.mp3)

{\rtf1\ansi\ansicpg1252\cocoartf2870
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\froman\fcharset0 Times-Roman;\f1\fmodern\fcharset0 Courier;}
{\colortbl;\red255\green255\blue255;\red0\green0\blue0;}
{\*\expandedcolortbl;;\cssrgb\c0\c0\c0;}
\margl1440\margr1440\vieww17560\viewh12760\viewkind0
\deftab720
\pard\pardeftab720\partightenfactor0

\f0\fs24 \cf0 \expnd0\expndtw0\kerning0
\outl0\strokewidth0 \strokec2 HTML\
\
\pard\pardeftab720\partightenfactor0

\f1\fs26 \cf0 <!DOCTYPE html>\
<html lang="es">\
<head>\
    <meta charset="UTF-8">\
    <meta name="viewport" content="width=device-width, initial-scale=1.0">\
    <title>Experiencia RA - Octubre S\'e1nchez</title>\
    \
    <script src="https://aframe.io/releases/1.5.0/aframe.min.js"></script>\
    <script src="https://cdn.jsdelivr.net/npm/mind-ar@1.2.5/dist/mindar-image-aframe.prod.js"></script>\
</head>\
<body>\
\
    <a-scene mindar-image="imageTargetSrc: ./targets.mind; autoStart: true; uiLoading: yes; uiScanning: yes; uiError: yes;" \
             color-space="sRGB" \
             renderer="colorManagement: true, physicallyCorrectLights" \
             vr-mode-ui="enabled: false" \
             device-orientation-permission-ui="enabled: false">\
        \
        <a-assets>\
            <audio id="sonidoCuadro" src="./audio.mp3" preload="auto"></audio>\
        </a-assets>\
\
        <a-camera position="0 0 0" look-controls="enabled: false"></a-camera>\
\
        <a-entity mindar-image-target="targetIndex: 0" id="cuadro-target">\
            \
            <a-entity sound="src: #sonidoCuadro; autoplay: false; loop: true; volume: 1; positional: true; refDistance: 1; rolloffFactor: 5"></a-entity>\
            \
        </a-entity>\
    </a-scene>\
\
    <script>\
        const targetEl = document.querySelector('#cuadro-target');\
        const entitySound = document.querySelector('[sound]');\
\
        // Cuando la c\'e1mara detecta el cuadro\
        targetEl.addEventListener("targetFound", event => \{\
            console.log("Cuadro detectado: Iniciando audio");\
            entitySound.components.sound.playSound();\
        \});\
\
        // Cuando el usuario deja de apuntar al cuadro\
        targetEl.addEventListener("targetLost", event => \{\
            console.log("Cuadro perdido: Pausando audio");\
            entitySound.components.sound.pauseSound();\
        \});\
    </script>\
</body>\
</html>\
}
