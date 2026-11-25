# Gerar o APK pelo GitHub (sem Android Studio)

Use o repositório do MediaCar já criado, se existir. Esta é uma atualização do projeto, não precisa criar outro repositório.

1. No GitHub, clique em **+ > New repository**. Nome: `MEDIA-CAR`. Deixe **Private**. Clique em **Create repository**.
2. Descompacte o ZIP atualizado `MediaCar-atualizado.zip` no computador. Vai aparecer a pasta `MediaCar-main`.
3. No repositório, clique em **uploading an existing file** (ou **Add file > Upload files**).
4. Abra a pasta `MediaCar-main`, aperte **Ctrl+A** para selecionar TUDO que está dentro dela e arraste para a página do GitHub.
   - Devem subir: a pasta `app`, a pasta `.github` e os arquivos `build.gradle.kts`, `settings.gradle.kts`, `gradle.properties`, `.gitignore`, `GITHUB.md` e `LEIAME.md`.
   - A pasta `.github` é oculta no Windows. Se ela não aparecer: Explorador de Arquivos > Exibir > Mostrar > Itens ocultos.
5. Role até o fim e clique em **Commit changes**.
6. Abra a aba **Actions**. O trabalho **Gerar APK** começa sozinho e leva de 3 a 10 minutos.
   Se não começar, clique em **Gerar APK** na lista da esquerda e depois em **Run workflow**.
7. Quando ficar com o visto verde, clique no trabalho, role até **Artifacts** e baixe **MediaCar-apk**.
8. Extraia o .zip baixado. Dentro está o `app-debug.apk`. Copie esse arquivo (sem renomear) para o pendrive.

## Se a pasta .github não subiu

Sem ela o GitHub não compila nada. Crie o arquivo direto no site:

1. No repositório: **Add file > Create new file**.
2. No campo do nome, digite exatamente: `.github/workflows/build.yml`
   (ao digitar a barra `/`, o site cria as pastas sozinho).
3. Cole o conteúdo do arquivo `.github/workflows/build.yml` que está dentro do zip.
4. Clique em **Commit changes**.

## Atenção: existem DOIS arquivos build.gradle.kts

- Um fica solto na raiz do repositório (curto, 4 linhas, com `version "8.5.2"`).
- Outro fica dentro da pasta `app` (longo, com `android { ... }`).

Não troque o conteúdo de um pelo do outro.

## Se der X vermelho

Clique no trabalho, abra o passo que ficou com o X (normalmente "Compilar o APK") e copie o texto do erro
(ou tire uma foto da tela) para mandar para quem está te ajudando.
