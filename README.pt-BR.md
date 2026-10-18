[English](README.md) · Português · [Español](README.es.md)

# PrimeVMS

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

O PrimeVMS tem três componentes, que podem ficar em um único computador ou distribuídos
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
| Analíticos de vídeo com IA: contagem de pessoas e reconhecimento facial (AI Engine) | Disponível, gratuito na fase de testes |
| Outros analíticos: detecção de objetos, cruzamento de linha, permanência indevida, filas, fogo e fumaça, EPI, leitura de placas, objetos abandonados, busca inteligente | Em desenvolvimento |
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

## Atualizações

A partir da versão 1.0.4, o PrimeVMS é atualizado pelos próprios apps.

1. Na Workstation, no Console do System Manager ou no Console do Storage, clique em
   **Buscar atualizações** na barra lateral ou na tela de entrada. Os apps também
   verificam sozinhos e avisam quando há uma versão nova.
2. Leia as notas da versão e clique em **Atualizar agora**. É preciso ter permissão de
   administrador.
3. O PrimeVMS atualiza todos os componentes instalados no computador. Ele para os
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
| [1.1.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.1.0) (recomendada) | 18/10/2026 | `PrimeVMS-Setup-1.1.0.exe`, 493 MB | Sim |
| [1.0.6](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.6) | 18/10/2026 | `PrimeVMS-Setup-1.0.6.exe`, 315 MB | Sim |
| [1.0.5](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.5) | 18/10/2026 | `PrimeVMS-Setup-1.0.5.exe`, 315 MB | Sim |
| [1.0.4](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.4) | 18/10/2026 | `PrimeVMS-Setup-1.0.4.exe`, 314 MB | Sim |
| [1.0.3](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.3) | 17/10/2026 | `PrimeVMS-Setup-1.0.3.exe`, 314 MB | Não (instale a 1.1.0) |
| [1.0.2](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.2) | 06/06/2026 | `PrimeVMS-Setup-1.0.2.exe`, 424 MB | Não |
| [1.0.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.0) | 01/06/2026 | `PrimeVMS-Setup-1.0.0.exe`, 265 MB | Não |

As versões anteriores ficam disponíveis para referência. Quem usa a versão 1.0.3 ou
anterior deve instalar a versão mais recente pelo instalador uma vez. Os dados são
mantidos e as versões seguintes são atualizadas pelo app.

### Conferir o download

```powershell
Get-FileHash .\PrimeVMS-Setup-1.1.0.exe -Algorithm SHA256
```

| Arquivo | SHA-256 |
|---|---|
| `PrimeVMS-Setup-1.1.0.exe` | `A10DAC26CA323654E718259BE15B9E6D1442D640C2D9452984F3AF9B934E7B02` |
| `PrimeVMS-Setup-1.0.6.exe` | `B1245763AADB7699C894117A781E11C2044F41A3E84211A3C6E634CA41E087C8` |
| `PrimeVMS-Setup-1.0.5.exe` | `97BAA1164289F40D35D530A1C9AC7A338E73CAA4197B4BF06473DD2FCCFFF746` |
| `PrimeVMS-Setup-1.0.4.exe` | `405B120D9E5BD56915E8CDE0A65D2D55CFD6A9020EB49992CE4177E1E3D71ED4` |
| `PrimeVMS-Setup-1.0.3.exe` | `97B2E821B3182DF8619003B73626AC234D8DA9A407FBD0434E6BDB804F7ED8D0` |
| `PrimeVMS-Setup-1.0.2.exe` | `8810E256670D7D20E791989B38D56D3878F0A753F126A9B990067A2E84FA65E7` |
| `PrimeVMS-Setup-1.0.0.exe` | `827586BE66C64AF0FD3538A8AE00A052ED8CDBF6890F73FD3EABA8DD9448BF0C` |

## Perguntas frequentes

**O PrimeVMS é gratuito?**
Sim. Ao vivo, gravação, playback, exportação, usuários, instalação distribuída e
atualizações são gratuitos, sem licença por câmera. Os analíticos com IA também são
gratuitos na fase de testes atual. Prime Cloud e alta disponibilidade serão módulos pagos.

**Quais câmeras são compatíveis?**
Qualquer câmera IP com ONVIF ou RTSP. O PrimeVMS encontra as câmeras ONVIF na rede e
detecta o caminho do vídeo.

**Ele substitui um NVR?**
O PrimeVMS grava as câmeras IP direto em um PC ou servidor Windows, com retenção por
dias. Também grava a partir de gravadores existentes que disponibilizam RTSP.

**Quantas câmeras posso adicionar?**
A versão gratuita não tem limite por câmera. O limite prático depende do hardware e da
rede. Em locais maiores, use a instalação distribuída com vários servidores de
gravação.

**Quais idiomas estão disponíveis?**
Português (Brasil), inglês e espanhol, nos apps, no instalador e nas notas de versão.

## Desinstalação

Abra **Configurações > Aplicativos > PrimeVMS > Desinstalar** ou use o atalho
"Desinstalar PrimeVMS" no Menu Iniciar. Os serviços e as regras de firewall são
removidos. O banco de dados e as gravações em `C:\ProgramData\Prime VMS` e na pasta de
gravação escolhida não são apagados.

## Licença e suporte

Copyright © 2026 Prime Building Technology. Todos os direitos reservados.

O núcleo VMS (System Manager, Storage e Workstation) é de uso gratuito para a gestão
de vídeo do empreendimento do licenciado. Os módulos de nuvem e alta disponibilidade
exigem licença comercial; os módulos de IA são gratuitos na fase de testes. O operador é responsável por cumprir a
legislação aplicável, inclusive a LGPD, ao captar, gravar e tratar imagens.

O PrimeVMS inclui componentes de terceiros sob suas próprias licenças, como
[FFmpeg](https://ffmpeg.org/) e [go2rtc](https://github.com/AlexxIT/go2rtc).

Suporte: [primebr.com.br](https://primebr.com.br/)
