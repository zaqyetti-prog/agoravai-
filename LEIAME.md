# Media Car — player de vídeo para multimídia (Android 6.0 ou mais novo)

## O que tem

- **Pastas grandes:** lista de pastas e vídeos com itens enormes. O botão "Tamanho" troca entre Médio, Grande e Enorme.
  Mostra a memória interna e os pendrives que o Android deixar o app ler.
- **Player:** toque na tela para mostrar/esconder os controles. Toque duplo na esquerda volta 10 s, na direita avança 10 s.
  Os vídeos seguintes da mesma pasta tocam em sequência. Botão para ajustar ou esticar a imagem.
- **Equalizador de 15 bandas** (25 Hz a 16 kHz, de -12 a +12 dB), com pré-amp e 8 predefinições.
  É um equalizador por software, então funciona com qualquer número de bandas, independente do aparelho.
  Toque duas vezes numa banda para zerá-la.
- **Retoma sozinho:** ao abrir o app, se o último vídeo estava tocando, ele volta a tocar de onde parou.
  Se o carro acabou de ligar e o pendrive ainda não está pronto, o app espera até ~2 minutos.
  O progresso é gravado a cada 3 segundos, então vale mesmo se o carro desligar de repente.
  Se você pausou antes de sair, ele abre na lista de pastas com o botão **Continuar**.
- Visual escuro com vidro translúcido, inspirado no iOS. A tela fica sempre ligada e em tela cheia, na horizontal.

## Limites que você precisa saber

- **Não foi testado em carro nem em multimídia.** O código foi escrito sem poder compilar nem rodar.
- **Formatos:** MP4, MKV, MOV, WebM, TS, M4V, 3GP e FLV costumam funcionar. **AVI e WMV podem não abrir**,
  e MKV com áudio DTS/AC3 pode ficar sem som, dependendo dos decodificadores do aparelho.
  Quando o vídeo não abre, o app avisa na tela.
- **Pendrive:** o Android da multimídia precisa liberar a leitura dele para o app. Se ele não aparecer na lista,
  toque em "Atualizar lista" depois de espetar o pendrive. Alguns aparelhos mostram o pendrive apenas em
  caminhos que o app não consegue ler.
- A reprodução fica em um serviço de mídia em primeiro plano e continua ao minimizar o app ou abrir outro aplicativo.
- A sessão de mídia publica comandos padrão Android (reproduzir/pausar, anterior e próximo) para botões de mídia e controles compatíveis da multimídia.
- O equalizador aplica os ajustes durante o movimento e agrupa a gravação das preferências para reduzir atrasos.

## Arquivos

- `MainActivity.kt` — tela cheia e permissão de arquivos; não pausa ao sair para outro app
- `PlaybackService.kt` — serviço em primeiro plano e sessão de mídia Android
- `App.kt` — telas e retomada automática do último vídeo
- `BrowserScreen.kt` — lista de pastas grande
- `PlayerScreen.kt` — vídeo e controles
- Reprodução sem equalizador DSP para reduzir consumo e processamento
- `PlayerController.kt` — player (ExoPlayer/Media3) e lista da pasta
- `Files.kt`, `Prefs.kt`, `Ui.kt` — arquivos, memória do app e componentes visuais

Passo a passo para gerar o APK: veja `GITHUB.md`.

## Compatibilidade dos comandos do volante

O MediaCar agora publica uma `MediaSession` do Android ligada ao ExoPlayer. Isso permite que a central encaminhe comandos padrão de mídia (play/pause, anterior e próximo). O volume continua sob controle do sistema de áudio da multimídia. A compatibilidade final depende de como o decodificador CANBUS Raise/Rise e o firmware da central encaminham os comandos; não foi possível validar esse hardware sem testar no Peugeot 308. Se algum botão não responder, será necessário identificar o código de tecla/evento que a central envia.

A reprodução em segundo plano depende de o Android da central permitir o serviço de mídia e não encerrar o aplicativo por economia de energia.


## Versão 1.2 — reprodução contínua

Ao voltar do player para as pastas, a reprodução não é pausada. O áudio continua enquanto você navega e escolhe outro vídeo. O botão **TOCAR EM 2º PLANO** ativa a sessão de mídia e muda para **2º PLANO ATIVO**. Consulte `ATUALIZAR-GITHUB.md` para publicar a atualização.
