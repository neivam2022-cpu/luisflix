# LuisFlix — Projeto pronto para empacotar em APK

Este repositório contém um app React + wrapper Capacitor preparado para você **construir um APK** e instalar na sua TV Android (TCL).  
**Observação importante:** não posso gerar o APK aqui para você — você precisa rodar os comandos localmente (ou usar um serviço de CI) porque a construção requer o Android SDK / Android Studio no seu computador.

## O QUE TEM AQUI
- `src/App.jsx` — o app principal (LuisFlix).
- `src/main.jsx`, `index.html`, `styles.css`
- `package.json` com scripts úteis.
- Instruções abaixo para gerar o APK.

## PASSO A PASSO PARA GERAR O APK (resumido)

1. Instale Node.js (versão 18+ recomendada) e npm.
2. Instale Android Studio e configure o Android SDK + variáveis de ambiente (`ANDROID_HOME` / `ANDROID_SDK_ROOT`, e `PATH` com `platform-tools`).
3. No terminal, dentro da pasta do projeto:
   ```bash
   npm install
   npm run build
   npx cap init luisflix com.luisflix.app
   npx cap add android
   npx cap copy android
   ```
4. Abra o projeto `android` no Android Studio:
   ```bash
   npx cap open android
   ```
   No Android Studio: aguarde a sincronização, selecione um dispositivo (ou emule) e clique em **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
5. O APK será gerado no diretório do projeto Android; instale na sua TV usando `adb install` ou via transfer.

## Acesso ao Jellyfin
- No app, abra "⚙️" e insira o endereço do seu Jellyfin (ex.: `http://192.168.1.42:8096`) e a API Key (Dashboard > API Keys no Jellyfin).
- Para acesso remoto: exponha o Jellyfin com um domínio/porta pública via roteador, reverse-proxy ou ngrok. Mantenha o API Key privado.

## Segurança
- Não compartilhe sua API Key.
- Ao expor o servidor para a internet, use HTTPS (reverse-proxy) e autenticação.

## Dúvidas
Se quiser, eu posso:
- Escrever um arquivo `capacitor.config.json` específico.
- Gerar um `AndroidManifest.xml` de exemplo com permissões.
- Preparar um script de CI (GitHub Actions) que constrói o APK (você terá que fornecer chaves/signing).
