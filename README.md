# 🧠 WindowsTranslator

**WindowsTranslator** é uma ideia de aplicação desktop Windows que será desenvolvida em **C# com WPF (.NET 6)** e **inteligência artificial** para traduzir automaticamente, em tempo real, o texto de uma área especifica exibida na tela.  
A aplicação captura uma região específica da tela, detecta os textos usando OCR inteligente, traduz com IA e substitui o texto original por sua versão traduzida diretamente na imagem — tudo de forma automática e contínua.

---

## ✨ Funcionalidades Desejadas

- 📸 **Captura contínua de tela** em uma região definida pelo usuário.
- 🔍 **Reconhecimento de texto com IA (OCR)** suportando:
  - Japonês 🇯🇵
  - Chinês 🇨🇳
  - Inglês 🇺🇸
- 🌐 **Tradução automática** usando modelos de IA (GPT-4, Google Translate ou DeepL).
- 🖌️ **Substituição visual do texto** no local original com fonte semelhante.
- 🚟️ **Janela overlay transparente**, que exibe a imagem traduzida por cima da interface original.
- ⚙️ **Totalmente automatizado**: sem cliques, sem interações manuais durante a leitura.

---

## 🏗️ Arquitetura Proposta

```
[ Timer Loop ]
      ↓
[ Captura de Tela da Região ]
      ↓
[ OCR com IA (Azure) ]
      ↓
[ Tradução com IA (OpenAI/Google/DeepL) ]
      ↓
[ Redesenho da Imagem com Texto Traduzido ]
      ↓
[ Exibição via Overlay Transparente (WPF) ]
```

---

## 💻 Tecnologias que serão Utilizadas

| Componente              | Tecnologia                                |
| ----------------------- | ----------------------------------------- |
| UI/Overlay              | WPF (.NET 6)                              |
| Captura de Tela         | System.Drawing / Windows.Graphics.Capture |
| OCR (Reconhecimento)    | Azure Computer Vision OCR                 |
| Tradução                | OpenAI GPT-4 Turbo / Google Translate     |
| Manipulação de Imagem   | System.Drawing / SkiaSharp                |
| Overlay Transparente    | WPF Window (Topmost + AllowsTransparency) |
| Timer / Background Loop | DispatcherTimer                           |

---

## 🔑 Pré-requisitos

- Conta na [Azure](https://portal.azure.com/) com chave da **Computer Vision API**.
- Conta na [OpenAI](https://platform.openai.com/) ou chave da **Google Translate API**.
- Visual Studio 2022 com .NET 6 ou superior instalado.
- Sistema operacional: **Windows 10 ou 11**.

---

## ⚙️ Como Funcionará

1. **Seleção da Região**: Ao iniciar o app, o usuário define com o mouse qual área da tela será monitorada.
2. **Execução Contínua**: Um timer dispara a cada poucos segundos:
   - Captura a imagem da região.
   - Executa OCR com IA.
   - Traduz automaticamente o texto detectado.
   - Redesenha a imagem com o texto traduzido no mesmo lugar.
3. **Exibição**: A imagem final é exibida em uma janela overlay transparente sobre a área original, simulando uma tradução "invisível".

---

## 📂 Estrutura Esperada do Projeto

```
MangaTranslatorAI/
├── MangaTranslatorAI.sln
├── /Assets/
│   └── icone, fontes, configurações
├── /Services/
│   ├── OcrService.cs
│   ├── TranslationService.cs
│   └── ImageProcessor.cs
├── /UI/
│   ├── MainWindow.xaml
│   └── OverlayWindow.xaml
├── /Utils/
│   ├── RegionSelector.cs
│   └── TimerManager.cs
├── appsettings.json
├── README.md
```

---

## 🤛 Contribuição

Sinta-se livre para sugerir melhorias ou reportar bugs. Esse projeto pode crescer com a ajuda da comunidade — especialmente com sugestões de desempenho, otimização de tradução e UX.

