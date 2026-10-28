[English](README.md) · Português · [Español](README.es.md)

# NexaVMS

Software de gerenciamento de vídeo (VMS) gratuito para câmeras IP e CFTV no Windows.
Assista ao vivo, grave 24 horas por dia, reproduza e exporte vídeo de qualquer câmera
ONVIF ou RTSP.

O núcleo do produto é gratuito, sem licença por câmera. Os módulos avançados estão
disponíveis em planos acessíveis.

[Download](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest) ·
[Site](https://daniel1ux.github.io/Prime-VMS-Public/pt/) ·
[Notas de versão](https://github.com/Daniel1ux/Prime-VMS-Public/releases)

[![Versão mais recente](https://img.shields.io/github/v/release/Daniel1ux/Prime-VMS-Public?label=vers%C3%A3o&color=c5e82e&labelColor=0a1626)](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest)
![Windows 10 e 11](https://img.shields.io/badge/Windows-10%20%7C%2011-0b2545)

## Visão geral

O NexaVMS tem três componentes, que podem ficar em um único computador ou distribuídos
pela rede:

| Componente | Função |
|---|---|
| System Manager | Servidor central. Gerencia câmeras, usuários, permissões e dados do empreendimento. Roda como serviço do Windows. |
| Storage | Servidor de gravação. Grava as câmeras em disco, aplica a retenção e entrega vídeo ao vivo e gravado. Roda como serviço do Windows. |
| Workstation | Aplicativo do operador. Mosaicos ao vivo, playback com linha do tempo e exportação. |

Os três vêm em um único instalador. Os apps estão disponíveis em português, inglês e
espanhol.

## Recursos

Incluídos na versão gratuita:

- Descoberta automática de câmeras ONVIF e do caminho do vídeo RTSP. Basta o usuário e
  a senha da câmera. Padrões de caminho embutidos para Hikvision, Annke, Dahua,
  Intelbras, Axis e Reolink.
- Busca de câmeras na rede e cadastro em lote: adicione várias câmeras de uma vez, com a
  leitura dos recursos ONVIF de cada uma.
- Gravação contínua em disco em MP4 segmentado, sem recodificação, com retenção por
  dias.
- Ao vivo em mosaicos de até 4×4, tela cheia, vários monitores e vídeo wall, com
  decodificação acelerada por hardware.
- Playback com linha do tempo de 24 horas, zoom, marcadores e reprodução sincronizada
  de várias câmeras.
- Exportação de imagens e vídeos com marca d'água (logotipo, data e hora).
- Usuários com perfis de administrador, supervisor e operador, aplicados pelo servidor.
- Instalação em um único computador ou distribuída, com vários servidores de gravação.
- Atualização pelo próprio app.

## Módulos pagos

| Módulo | Disponibilidade |
|---|---|
| Analíticos de vídeo com IA: contagem de pessoas, reconhecimento facial, leitura de placas Mercosul, busca inteligente e proteção de perímetro, cada um com modo de teste por vídeos reais (AI Engine) | Disponível, gratuito na fase de testes |
| Outros analíticos: permanência indevida, filas, fogo e fumaça, EPI, objetos abandonados | Em desenvolvimento |
| Prime Cloud: acesso remoto e pelo celular sem abrir portas | Em breve |
| Alta disponibilidade: servidor central redundante | Em breve |

Os planos foram pensados para projetos pequenos e médios.
[Fale com a Prime Building Technology](https://primebr.com.br/) para um orçamento.

## Requisitos

- Windows 10 ou Windows 11, 64 bits.
- Permissão de administrador para instalar e atualizar.
- Câmeras IP com ONVIF ou RTSP na mesma rede.
- Para o Storage, um disco com espaço para a retenção desejada. As gravações ficam fora
  da pasta do programa.
- Para a Workstation, recomenda-se placa de vídeo com decodificação por hardware em
  mosaicos grandes.

## Instalação

1. Baixe o `PrimeVMS-Setup-X.Y.Z.exe` da
   [versão mais recente](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest).
2. Execute o instalador, escolha o idioma e aceite o pedido de administrador.
   O instalador ainda não tem assinatura de código. Se o Windows SmartScreen aparecer,
   clique em **Mais informações** e depois em **Executar assim mesmo**.
3. Escolha o modelo de implantação:
   - **Um único computador.** Instala System Manager, Storage e Workstation já
     conectados entre si. Indicado para até cerca de 16 câmeras, sem redundância de
     gravação.
   - **Distribuída.** Marque os papéis deste computador: System Manager num servidor
     dedicado, Storage em um ou mais servidores de gravação e Workstation nos
     computadores de operação.
4. Abra a Workstation ou o Console do System Manager.

Entre com o usuário `admin` e a senha `admin` e troque a senha em seguida.

O idioma escolhido no instalador passa a ser o padrão dos apps. Cada usuário pode
trocar pelo seletor de idioma na tela de entrada ou na barra lateral.

### Portas de rede

| Porta (TCP) | Serviço |
|---|---|
| 58100 | System Manager |
| 58200 | Storage |

O instalador adiciona essas regras ao Firewall do Windows. Em uma instalação
distribuída, garanta que a rede permita essas portas entre os servidores e as
Workstations.

## Nexa Player

A exportação protegida (`.pvx`) é cifrada com senha e tem verificação de integridade, por isso não
abre em players de vídeo comuns. Para assistir, use o Nexa Player, gratuito, para Windows. Ele abre
pacotes `.pvx`, pastas exportadas e arquivos MP4, e mostra se cada vídeo está íntegro e assinado.

- [Baixar o Nexa Player (zip, sem instalar)](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest/download/NexaPlayer-win-x64.zip)
- [Baixar o instalador do Nexa Player](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest/download/NexaPlayer-Setup.exe)

1. Baixe o `NexaPlayer-win-x64.zip`, clique nele com o botão direito e escolha **Extrair tudo**.
2. Abra o `PrimePlayer.exe` na pasta extraída. Se aparecer o aviso do SmartScreen, clique em
   **Mais informações** e depois em **Executar assim mesmo**.
3. Clique em **Abrir arquivo**, escolha o arquivo `.pvx` e digite a senha. A lista mostra se cada
   vídeo está íntegro e assinado.

A senha não fica no pacote. Peça a quem fez a exportação. Os links sempre levam à versão mais
recente.

## Atualizações

A partir da versão 1.0.4, o NexaVMS é atualizado pelos próprios apps.

1. Na Workstation, no Console do System Manager ou no Console do Storage, clique em
   **Buscar atualizações** na barra lateral ou na tela de entrada. Os apps também
   verificam sozinhos e avisam quando há uma versão nova.
2. Leia as notas da versão e clique em **Atualizar agora**. É preciso ter permissão de
   administrador.
3. O NexaVMS atualiza todos os componentes instalados no computador. Ele para os
   serviços, fecha os apps, instala a versão nova, inicia os serviços, confere se eles
   respondem e reabre o app. O processo leva cerca de um minuto.

Como a atualização funciona:

- Só os arquivos alterados são baixados, normalmente cerca de 1 MB.
- Cada versão tem assinatura digital. Arquivos alterados ou corrompidos são recusados
  antes de qualquer mudança.
- Se um serviço não iniciar, ou se faltar energia durante a atualização, a versão
  anterior é restaurada automaticamente.
- Configurações, câmeras, usuários e gravações são mantidos. O banco de dados é
  atualizado automaticamente.

A gravação fica pausada por alguns segundos durante a atualização. Em locais com
gravação crítica, atualize em horário de menor movimento.

### Atualização sem internet

Copie os arquivos de atualização de uma versão (`update-manifest.json`,
`update-manifest.json.sig` e os arquivos `pack-*.zip`) para uma pasta e execute como
administrador:

```
"C:\Program Files\Prime VMS\Updater\PrimeVMS Updater.exe" --apply --source folder:D:\atualizacao-primevms
```

## Versões

| Versão | Data | Instalador | Atualização pelo app |
|---|---|---|---|
| [2.12.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.12.0) (recomendada) | 28/10/2026 | `PrimeVMS-Setup-2.12.0.exe`, 637 MB | Sim |
| [2.11.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.11.0) | 28/10/2026 | `PrimeVMS-Setup-2.11.0.exe`, 637 MB | Sim |
| [2.10.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.10.0) | 28/10/2026 | `PrimeVMS-Setup-2.10.0.exe`, 637 MB | Sim |
| [2.9.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.9.1) | 27/10/2026 | `PrimeVMS-Setup-2.9.1.exe`, 637 MB | Sim |
| [2.9.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.9.0) | 27/10/2026 | `PrimeVMS-Setup-2.9.0.exe`, 637 MB | Sim |
| [2.8.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.8.0) | 27/10/2026 | `PrimeVMS-Setup-2.8.0.exe`, 637 MB | Sim |
| [2.7.18](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.18) | 26/10/2026 | `PrimeVMS-Setup-2.7.18.exe`, 637 MB | Sim |
| [2.7.17](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.17) | 26/10/2026 | `PrimeVMS-Setup-2.7.17.exe`, 637 MB | Sim |
| [2.7.16](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.16) | 26/10/2026 | `PrimeVMS-Setup-2.7.16.exe`, 637 MB | Sim |
| [2.7.15](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.15) | 26/10/2026 | `PrimeVMS-Setup-2.7.15.exe`, 637 MB | Sim |
| [2.7.14](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.14) | 26/10/2026 | `PrimeVMS-Setup-2.7.14.exe`, 637 MB | Sim |
| [2.7.13](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.13) | 26/10/2026 | `PrimeVMS-Setup-2.7.13.exe`, 637 MB | Sim |
| [2.7.12](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.12) | 26/10/2026 | `PrimeVMS-Setup-2.7.12.exe`, 637 MB | Sim |
| [2.7.11](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.11) | 26/10/2026 | `PrimeVMS-Setup-2.7.11.exe`, 637 MB | Sim |
| [2.7.10](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.10) | 26/10/2026 | `PrimeVMS-Setup-2.7.10.exe`, 637 MB | Sim |
| [2.7.9](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.9) | 26/10/2026 | `PrimeVMS-Setup-2.7.9.exe`, 637 MB | Sim |
| [2.7.8](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.8) | 26/10/2026 | `PrimeVMS-Setup-2.7.8.exe`, 637 MB | Sim |
| [2.7.7](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.7) | 26/10/2026 | `PrimeVMS-Setup-2.7.7.exe`, 637 MB | Sim |
| [2.7.6](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.6) | 26/10/2026 | `PrimeVMS-Setup-2.7.6.exe`, 637 MB | Sim |
| [2.7.5](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.5) | 26/10/2026 | `PrimeVMS-Setup-2.7.5.exe`, 637 MB | Sim |
| [2.7.4](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.4) | 26/10/2026 | `PrimeVMS-Setup-2.7.4.exe`, 637 MB | Sim |
| [2.7.3](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.3) | 26/10/2026 | `PrimeVMS-Setup-2.7.3.exe`, 637 MB | Sim |
| [2.7.2](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.2) | 26/10/2026 | `PrimeVMS-Setup-2.7.2.exe`, 636 MB | Sim |
| [2.7.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.1) | 25/10/2026 | `PrimeVMS-Setup-2.7.1.exe`, 636 MB | Sim |
| [2.7.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.7.0) | 25/10/2026 | `PrimeVMS-Setup-2.7.0.exe`, 636 MB | Sim |
| [2.6.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.6.0) | 25/10/2026 | `PrimeVMS-Setup-2.6.0.exe`, 636 MB | Sim |
| [2.5.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.5.0) | 23/10/2026 | `PrimeVMS-Setup-2.5.0.exe`, 634 MB | Sim |
| [2.4.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.4.0) | 22/10/2026 | `PrimeVMS-Setup-2.4.0.exe`, 633 MB | Sim |
| [2.2.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.2.0) | 21/10/2026 | `PrimeVMS-Setup-2.2.0.exe`, 626 MB | Sim |
| [2.1.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.1.0) | 21/10/2026 | `PrimeVMS-Setup-2.1.0.exe`, 626 MB | Sim |
| [2.0.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.0.1) | 20/10/2026 | `PrimeVMS-Setup-2.0.1.exe`, 625 MB | Sim |
| [2.0.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.0.0) | 20/10/2026 | `PrimeVMS-Setup-2.0.0.exe`, 625 MB | Sim |
| [1.9.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.9.0) | 20/10/2026 | `PrimeVMS-Setup-1.9.0.exe`, 622 MB | Sim |
| [1.8.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.8.1) | 20/10/2026 | `PrimeVMS-Setup-1.8.1.exe`, 543 MB | Sim |
| [1.8.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.8.0) | 20/10/2026 | `PrimeVMS-Setup-1.8.0.exe`, 543 MB | Sim |
| [1.7.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.7.0) | 20/10/2026 | `PrimeVMS-Setup-1.7.0.exe`, 542 MB | Sim |
| [1.5.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.5.0) | 19/10/2026 | `PrimeVMS-Setup-1.5.0.exe`, 498 MB | Sim |
| [1.4.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.4.0) | 18/10/2026 | `PrimeVMS-Setup-1.4.0.exe`, 497 MB | Não (instale a 2.12.0) |
| [1.3.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.3.1) | 18/10/2026 | `PrimeVMS-Setup-1.3.1.exe`, 494 MB | Não (instale a 2.12.0) |
| [1.3.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.3.0) | 18/10/2026 | `PrimeVMS-Setup-1.3.0.exe`, 494 MB | Não (instale a 2.12.0) |
| [1.2.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.2.1) | 18/10/2026 | `PrimeVMS-Setup-1.2.1.exe`, 493 MB | Não (instale a 2.12.0) |
| [1.2.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.2.0) | 18/10/2026 | `PrimeVMS-Setup-1.2.0.exe`, 493 MB | Não (instale a 2.12.0) |
| [1.1.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.1.0) | 18/10/2026 | `PrimeVMS-Setup-1.1.0.exe`, 493 MB | Não (instale a 2.12.0) |
| [1.0.6](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.6) | 18/10/2026 | `PrimeVMS-Setup-1.0.6.exe`, 315 MB | Não (instale a 2.12.0) |
| [1.0.5](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.5) | 18/10/2026 | `PrimeVMS-Setup-1.0.5.exe`, 315 MB | Não (instale a 2.12.0) |
| [1.0.4](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.4) | 18/10/2026 | `PrimeVMS-Setup-1.0.4.exe`, 314 MB | Não (instale a 2.12.0) |
| [1.0.3](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.3) | 17/10/2026 | `PrimeVMS-Setup-1.0.3.exe`, 314 MB | Não (instale a 2.12.0) |
| [1.0.2](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.2) | 06/06/2026 | `PrimeVMS-Setup-1.0.2.exe`, 424 MB | Não |
| [1.0.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.0) | 01/06/2026 | `PrimeVMS-Setup-1.0.0.exe`, 265 MB | Não |

As versões anteriores ficam disponíveis para referência. Quem usa a versão 1.4.0 ou
anterior deve instalar a versão mais recente pelo instalador uma vez. Os dados são
mantidos e as versões seguintes são atualizadas pelo app.

A partir da 2.5.0, a instalação precisa ser ativada com uma conta Nexa VMS, criada em
[nexavms.io](https://nexavms.io), pelo Console do System Manager. Sem ativação, o NexaVMS não grava
nem mostra vídeo. A primeira ativação traz 30 dias de avaliação do Professional.

### Conferir o download

```powershell
Get-FileHash .\PrimeVMS-Setup-2.12.0.exe -Algorithm SHA256
```

| Arquivo | SHA-256 |
|---|---|
| `PrimeVMS-Setup-2.12.0.exe` | `A55FEC076B79DA5FAAF32123BAD7506918746BE9333D534D6FA6E43B98447293` |
| `PrimeVMS-Setup-2.11.0.exe` | `601EB0D23E60A71C0E2B256B0CD668C10742901445EC3CC9E414033E50DCF1DF` |
| `PrimeVMS-Setup-2.9.1.exe` | `47EF3D35A556C95A0542D4B93FC70CC56CAE5BDEDD120378048BE76CD406E79D` |
| `PrimeVMS-Setup-2.9.0.exe` | `FAD438DA95913185F893567CC8085321FE369BD54298A77345AF100339BF0B2F` |
| `PrimeVMS-Setup-2.8.0.exe` | `53B71D15C45345FF9BE9A4155B59E57B3D8E00E0507698F8D0B0F5482F1E51AF` |
| `PrimeVMS-Setup-2.7.18.exe` | `747646A19ACC3A3BAE6BB7D15E341274D4A1D7D29D81AE14421FFBAFF6F127A2` |
| `PrimeVMS-Setup-2.7.17.exe` | `A0D26E80CD4C592A0DA16260CB61C4F249C655382C3300080D78947FF0EA9237` |
| `PrimeVMS-Setup-2.7.16.exe` | `FA5EE73C47F2981838B8C5080517A32886A6585AD679C771CFF85036103E07E4` |
| `PrimeVMS-Setup-2.7.15.exe` | `9682AC8C48FF8D8F209AD57BB607DA8F66AFC072B519EACF49AAB8882F7CFE45` |
| `PrimeVMS-Setup-2.7.14.exe` | `4D8FA295BBE1166703EED5673B77A7B0CDADF36EEDB433201BFAEF469AC47D30` |
| `PrimeVMS-Setup-2.7.13.exe` | `98A19BBEF3DA31AADBEBBE38C5AEB8EE2A6575052714291FABA064363ABCF4BE` |
| `PrimeVMS-Setup-2.7.12.exe` | `AAA5CAF2FC603BAC558E4A3FC24359182EFCEDACFD58EDA40DD44FA3F481F805` |
| `PrimeVMS-Setup-2.7.11.exe` | `43E5457EF3B98673A0F85257CAD71ADDB87979C48BF64E4BB5963748F5525EFB` |
| `PrimeVMS-Setup-2.7.10.exe` | `F141C55616FEA93A95D5F5C89C7E0862B8473DD1EFC8BA1C20931860CC9BB3C9` |
| `PrimeVMS-Setup-2.7.9.exe` | `E9EDE1067C294A008D80FEF245F3CF94015E82E3CAC658F2DD803665884C2BD0` |
| `PrimeVMS-Setup-2.7.8.exe` | `5F7038E5CFA8B59166A27A08780B3D25D3EB06ED8A1747751E71470F5A2E0ADE` |
| `PrimeVMS-Setup-2.7.7.exe` | `D3513D5E7EEF083122D19F63189CDC409A6D44F5C80CB71949789680918C6D92` |
| `PrimeVMS-Setup-2.7.6.exe` | `5F715CE1AAD46EA82EE4971BC5159C5160BC0B0BA4C93991B6DE448BA509BFE0` |
| `PrimeVMS-Setup-2.7.5.exe` | `07B71E570610544BD37DDDEEEE6A91E587969F9DFD1B5ECD9E6CD1963643F2E6` |
| `PrimeVMS-Setup-2.7.4.exe` | `9AB65DBC6E8B75B4C2BCBBF3FA914162A8A1F8C370C6C3EB739C83C1DDF92A02` |
| `PrimeVMS-Setup-2.7.3.exe` | `6794E1F5124F9A1EC80D1EBD16B8F04084888FB69A747E4C2FF6D3A4ED24EEFD` |
| `PrimeVMS-Setup-2.7.2.exe` | `6EF47D5A72822544DD0173EFECEC4EF48B65CF1F4778328A4B5C58E3114DEADD` |
| `PrimeVMS-Setup-2.7.1.exe` | `60387D0AE76CBC3FFDD5D85592402B60176BE4308C5940B91D4E793C1341E2A1` |
| `PrimeVMS-Setup-2.7.0.exe` | `E4E22CC3E2B567C485F1B3A68BA735A247064A06AD76B87C53662205135E37FB` |
| `PrimeVMS-Setup-2.6.0.exe` | `08F72A36753CC5ED2CCBB7CFCF9F2C46F9531E5D4EB710637DB68014F95CEAD1` |
| `PrimeVMS-Setup-2.5.0.exe` | `CAE6D8F2876AAE838D09F29AF7A458B5E7DB2DEA1D15911CE10152A0F6BAFAAD` |
| `PrimeVMS-Setup-2.4.0.exe` | `E2B507AFBDBD440AC0D02A2097F340CF3F907F47AEF63BD42E532DD3A1A465D1` |
| `PrimeVMS-Setup-2.2.0.exe` | `8CF877C5ADBF2343BA6F6367C52883D7343DF1B851C5FD9A56692E7156762D70` |
| `PrimeVMS-Setup-2.1.0.exe` | `105DDD7A8E21FF7225C73A4496866636220BE2C1B3C1BE1C14323ED70C3BB9A1` |
| `PrimeVMS-Setup-2.0.1.exe` | `D9D9BA966B4CC612DB9AB528F2990078868A69952F979048F30F112CC6D19A26` |
| `PrimeVMS-Setup-2.0.0.exe` | `FFACF9BF70416534605FC6CC01DFED300A1BE9AB987BEF64CAF312E783D6C8D8` |
| `PrimeVMS-Setup-1.9.0.exe` | `A1FAEF166392A63B3A873C572CBB858F95722910DADA3C8F1DD52729BD70D43C` |
| `PrimeVMS-Setup-1.8.1.exe` | `05C9E031DC9B8885542728C1BC21659E7D5BCF5964A55D3730BE51B5C3417F46` |
| `PrimeVMS-Setup-1.8.0.exe` | `7198021CE27F554F47385322EB8CE8948BD6BDE0BC88CF6B60B6980F7BDF28E7` |
| `PrimeVMS-Setup-1.7.0.exe` | `E404DAA88A8CBD05562472DEAC84A8F681196FFB809D1BD2F341B3015A28D825` |
| `PrimeVMS-Setup-1.5.0.exe` | `A1190CD79D0F85C933A00C90AF8C03A1F6E60545C028F96B376D1EFD4DE6EEAA` |
| `PrimeVMS-Setup-1.4.0.exe` | `32E47D8F89BA60DF91C06A99D1FADC20965AC7E698FCCDF6DFE072884594209F` |
| `PrimeVMS-Setup-1.3.1.exe` | `DD44CDFEDA869F5A4C0212D7C11464C37627C290ED1AF95EE723246F7F504FD7` |
| `PrimeVMS-Setup-1.3.0.exe` | `51D039F8B7059B46AFB4C38FAF5B7D126B99AF9FCDF7E5FF65C185C4EABDD054` |
| `PrimeVMS-Setup-1.2.1.exe` | `B1816D7EA9E87AE6A2C9E68DC7E7E01E2DA8CB86836BF1865AFCD51E69D0CCFD` |
| `PrimeVMS-Setup-1.2.0.exe` | `431926639B594119DAFA7CE3C0BA416A16D4D01367AD8AC41868C82FEE70FC33` |
| `PrimeVMS-Setup-1.1.0.exe` | `A10DAC26CA323654E718259BE15B9E6D1442D640C2D9452984F3AF9B934E7B02` |
| `PrimeVMS-Setup-1.0.6.exe` | `B1245763AADB7699C894117A781E11C2044F41A3E84211A3C6E634CA41E087C8` |
| `PrimeVMS-Setup-1.0.5.exe` | `97BAA1164289F40D35D530A1C9AC7A338E73CAA4197B4BF06473DD2FCCFFF746` |
| `PrimeVMS-Setup-1.0.4.exe` | `405B120D9E5BD56915E8CDE0A65D2D55CFD6A9020EB49992CE4177E1E3D71ED4` |
| `PrimeVMS-Setup-1.0.3.exe` | `97B2E821B3182DF8619003B73626AC234D8DA9A407FBD0434E6BDB804F7ED8D0` |
| `PrimeVMS-Setup-1.0.2.exe` | `8810E256670D7D20E791989B38D56D3878F0A753F126A9B990067A2E84FA65E7` |
| `PrimeVMS-Setup-1.0.0.exe` | `827586BE66C64AF0FD3538A8AE00A052ED8CDBF6890F73FD3EABA8DD9448BF0C` |

## Perguntas frequentes

**O NexaVMS é gratuito?**
Sim. Ao vivo, gravação, playback, exportação, usuários, instalação distribuída e
atualizações são gratuitos, sem licença por câmera. Os analíticos com IA também são
gratuitos na fase de testes atual. Prime Cloud e alta disponibilidade serão módulos pagos.

**Quais câmeras são compatíveis?**
Qualquer câmera IP com ONVIF ou RTSP. O NexaVMS encontra as câmeras ONVIF na rede e
detecta o caminho do vídeo.

**Ele substitui um NVR?**
O NexaVMS grava as câmeras IP direto em um PC ou servidor Windows, com retenção por
dias. Também grava a partir de gravadores existentes que disponibilizam RTSP.

**Quantas câmeras posso adicionar?**
A versão gratuita não tem limite por câmera. O limite prático depende do hardware e da
rede. Em locais maiores, use a instalação distribuída com vários servidores de
gravação.

**Quais idiomas estão disponíveis?**
Português (Brasil), inglês e espanhol, nos apps, no instalador e nas notas de versão.

## Desinstalação

Abra **Configurações > Aplicativos > NexaVMS > Desinstalar** (PrimeVMS nas instalações anteriores à 2.4.0) ou use o atalho
"Desinstalar NexaVMS" no Menu Iniciar. Os serviços e as regras de firewall são
removidos. O banco de dados e as gravações em `C:\ProgramData\Prime VMS` e na pasta de
gravação escolhida não são apagados.

## Licença e suporte

Copyright © 2026 Prime Building Technology. Todos os direitos reservados.

O núcleo VMS (System Manager, Storage e Workstation) é de uso gratuito para a gestão
de vídeo do empreendimento do licenciado. Os módulos de nuvem e alta disponibilidade
exigem licença comercial; os módulos de IA são gratuitos na fase de testes. O operador é responsável por cumprir a
legislação aplicável, inclusive a LGPD, ao captar, gravar e tratar imagens.

O NexaVMS inclui componentes de terceiros sob suas próprias licenças, como
[FFmpeg](https://ffmpeg.org/) e [go2rtc](https://github.com/AlexxIT/go2rtc).

Suporte: [primebr.com.br](https://primebr.com.br/)
