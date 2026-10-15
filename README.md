<p align="center">
  <img src="docs/assets/images/logo.svg" alt="Logo do zapzap" width="88" height="88">
</p>

<h1 align="center">zapzap</h1>

<p align="center"><strong>WhatsApp nativo e rápido.</strong><br>Um app leve de WhatsApp para Windows, macOS e Linux.</p>

<p align="center">
  <a href="Cargo.toml"><img src="https://img.shields.io/badge/Feito_com-Rust-00a884" alt="Feito com Rust"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/Licen%C3%A7a-MIT-00a884" alt="Licença MIT"></a>
</p>

O zapzap é um cliente de WhatsApp escrito em Rust com
[egui](https://www.egui.rs), sem engine de navegador. Ele se vincula ao seu
celular como um dispositivo companheiro através da biblioteca
[whatsapp-rust](https://github.com/oxidezap/whatsapp-rust): abre em menos de
um segundo e usa uma fração da memória do WhatsApp Web.

Este projeto nasceu como um derivado do
[ZapFast](https://github.com/crmne/zapfast) (licença MIT) e segue como um
projeto independente.

A interface está disponível em português (Brasil), inglês, chinês
(simplificado e tradicional), francês, alemão, indonésio, italiano, russo,
espanhol e turco.

<picture>
  <source media="(prefers-color-scheme: light)" srcset="docs/screenshot-light.png">
  <img src="docs/screenshot.png" alt="zapzap mostrando uma conversa com anexo, mensagens de voz, reações, resposta citada e prévia de link">
</picture>

## Suas conversas, no seu computador

| Recurso | O que você pode fazer |
|---|---|
| **Mensagens** | Enviar texto formatado, respostas, edições, reações, encaminhamentos, fotos, arquivos, figurinhas, GIFs, enquetes e mensagens de voz. |
| **Mídia na conversa** | Reproduzir mensagens de voz, vídeos, vídeos redondos, GIFs e figurinhas animadas direto na conversa. |
| **Seu histórico** | Manter as conversas em um arquivo criptografado neste computador e buscar mensagens antigas do celular conforme você rola. |
| **Vários números** | Vincular mais de um número de WhatsApp e alternar entre eles na mesma janela. |
| **Controles de desktop** | Usar atalhos de teclado, selecionar e copiar texto entre mensagens, e ficar conectado na bandeja com notificações. |
| **Temas** | Escolher entre claro, escuro, aparência do sistema ou cores personalizadas. |
| **Privacidade** | Esconder conversas trancadas atrás de um código, ou a janela inteira atrás de um bloqueio de app. Nada vai para um servidor nosso. |

## Compilar a partir do código-fonte

Pré-requisitos:

- [Rust](https://rustup.rs) (a versão exata é fixada em `rust-toolchain.toml` e instalada automaticamente)
- **Windows:** Visual Studio Build Tools com a carga de trabalho de C++, e [CMake](https://cmake.org) (para o codec Opus)
- **Linux:** headers do ALSA (`libasound2-dev` no Debian/Ubuntu, `alsa-lib` no Arch) e CMake
- **macOS:** Xcode Command Line Tools e CMake

```sh
git clone https://github.com/marpe11/zapzap.git
cd zapzap
cargo run --release
```

Para explorar a interface sem uma conta de WhatsApp, use o modo demo:

```sh
cargo run --features demo -- --demo
```

## Vincular seu celular

1. Abra o zapzap. Ele mostra um QR code.
2. No celular, abra o WhatsApp, depois **Configurações**, **Aparelhos
   conectados**, **Conectar aparelho**, e escaneie o código. Ou clique em
   **Vincular com número de telefone** e digite o código de oito caracteres.
3. Suas conversas recentes chegam do celular. As mais antigas aparecem
   conforme você rola para cima.

A vinculação sobrevive a reinicializações, e o celular não precisa ficar
online para você ler o que o zapzap já armazenou.

## Estrutura do projeto

- `src/ui/` — telas e componentes da interface (egui)
- `src/backend/` — comunicação com o WhatsApp em uma runtime tokio própria
- `src/archive/` — histórico local em SQLite criptografado (SQLCipher)
- `assets/i18n/` — traduções da interface
- `docs/` — documentação
- [AGENTS.md](AGENTS.md) — guia de arquitetura para contribuidores e agentes
- [DEMO.md](DEMO.md) — páginas do modo demo, capturas e tours

## Contribuindo

Contribuições são bem-vindas. Abra uma
[issue](https://github.com/marpe11/zapzap/issues) ou um pull request. Antes de
terminar uma mudança, rode as verificações:

```sh
cargo fmt --all --check
cargo clippy --locked --all-targets -- -D warnings
cargo test --locked --all-targets
```

## Aviso

O zapzap é um cliente não oficial e não é afiliado ao WhatsApp ou à Meta.
Usar um cliente não oficial pode violar os termos de serviço do WhatsApp e
levar à suspensão da conta. Use por sua conta e risco. WhatsApp é uma marca
registrada da WhatsApp LLC.

## Agradecimentos

O zapzap é baseado no [ZapFast](https://github.com/crmne/zapfast), de Carmine
Pascal, e usa [whatsapp-rust](https://github.com/oxidezap/whatsapp-rust),
[egui](https://www.egui.rs), [fastframe](https://fastframe.dev), a fonte
[Inter](https://rsms.me/inter/) e Noto Color Emoji (OFL), e os ícones
[Lucide](https://lucide.dev) (ISC), também usados nos desenhos do papel de
parede das conversas. Os sons de notificação são do
[Pidgin](https://pidgin.im), sob a GPL-2.0 (veja `assets/sounds/`).

Licenciado sob a [Licença MIT](LICENSE).
