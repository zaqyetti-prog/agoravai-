# Atualizar o MediaCar no GitHub — versão 1.2

Esta versão corrige a navegação para que abrir pastas ou voltar do player para o navegador não pause a reprodução.

## Pelo Git (recomendado)

1. Abra o repositório do MediaCar no GitHub e copie a URL em **Code > HTTPS**.
2. No computador, abra o PowerShell e execute (substitua a URL):

```powershell
git clone COLE_A_URL_DO_SEU_REPOSITORIO
cd MediaCar
```

3. Extraia este ZIP. Copie todo o conteúdo da pasta `MediaCar-main` para dentro da pasta clonada, aceitando substituir os arquivos. **Não apague a pasta `.git`.**
4. Execute:

```powershell
git add .
git commit -m "MediaCar 1.2: manter reprodução ao navegar e em segundo plano"
git push
```

5. No GitHub, abra **Actions**, aguarde **Gerar APK** terminar com sucesso e baixe o artefato **MediaCar-apk**.

## Alterações desta versão

- Removida a pausa automática ao voltar do player para a lista de pastas.
- A navegação entre pastas não altera o estado do player; o áudio do vídeo atual continua tocando enquanto você escolhe outro arquivo.
- Botão compacto **TOCAR EM 2º PLANO** no canto esquerdo do cabeçalho, tanto no navegador quanto na tela do player. Ao tocar, ele garante que o serviço de mídia esteja iniciado e, se houver vídeo carregado pausado, retoma a reprodução. O botão passa a mostrar **2º PLANO ATIVO**.
- O serviço Media3 mantém a sessão de mídia ativa e não encerra o serviço quando a tarefa do app é removida dos recentes enquanto ainda estiver tocando.
- Adicionada a permissão declarativa para serviço de reprodução de mídia em versões recentes do Android.
- Versão atualizada para 1.2 (versionCode 3).

## Observações importantes

- A reprodução em segundo plano depende de o Android/firmware da multimídia permitir o serviço de mídia em primeiro plano e não impor restrição de bateria ao MediaCar. Se a central tiver uma opção de economia/limpeza automática, permita execução em segundo plano para o MediaCar.
- Ao navegar para as pastas, o vídeo continua reproduzindo sem imagem, apenas com o áudio audível. Escolher outro vídeo substitui a reprodução atual, como esperado.
- Os comandos do volante que já estavam funcionando foram preservados; esta versão não altera a integração CANBUS.
- Não foi possível compilar neste ambiente por falta do Android SDK/Gradle. A compilação deve ser validada no GitHub Actions antes de instalar.
- O APK precisa manter a mesma assinatura da versão instalada para atualizar sem desinstalar. Não desinstale a versão anterior se o Android indicar conflito de assinatura, pois isso pode apagar dados locais.
