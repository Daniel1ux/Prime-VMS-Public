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

O NexaVMS tem quatro componentes, que podem ficar em um único computador ou distribuídos
pela rede:

| Componente | Função |
|---|---|
| System Manager | Servidor central. Gerencia câmeras, usuários, permissões e dados do empreendimento. Roda como serviço do Windows. |
| Storage | Servidor de gravação. Grava as câmeras em disco, aplica a retenção e entrega vídeo ao vivo e gravado. Roda como serviço do Windows. |
| Workstation | Aplicativo do operador. Mosaicos ao vivo, playback com linha do tempo e exportação. |
| Servidor de IA | Analisa o vídeo das câmeras para os módulos de IA e envia os eventos ao System Manager. Fica no mesmo computador ou em computadores próprios, um ou vários. Roda como serviço do Windows. |

Todos vêm em um único instalador. Os apps estão disponíveis em português, inglês e
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
- Para o servidor de IA, pelo menos 8 GB de memória e 10 GB livres. Uma placa de vídeo
  compatível atende muito mais câmeras; sem ela, a análise roda no processador.

## Instalação

1. Baixe o `PrimeVMS-Setup-X.Y.Z.exe` da
   [versão mais recente](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest).
2. Execute o instalador, escolha o idioma e aceite o pedido de administrador.
   O instalador ainda não tem assinatura de código. Se o Windows SmartScreen aparecer,
   clique em **Mais informações** e depois em **Executar assim mesmo**.
3. Escolha como este computador vai participar:
   - **Tudo neste computador.** Instala System Manager, Storage e Workstation já
     conectados entre si. Indicado para até cerca de 16 câmeras, sem redundância de
     gravação. O servidor de IA pode ser incluído na mesma instalação.
   - **Só o servidor de IA.** Para um computador que só analisa vídeo para um Nexa VMS
     que já existe. Não instala System Manager, Storage nem Workstation. O instalador
     confere o hardware, pede o nome do servidor, o endereço que o System Manager vai
     usar e a senha, e pode já conectá-lo ao System Manager ou deixar para depois.
   - **Escolher as partes.** Marque os papéis deste computador: System Manager num
     servidor dedicado, Storage em um ou mais servidores de gravação, Workstation nos
     computadores de operação e servidor de IA.
4. Abra a Workstation ou o Console do System Manager. No servidor de IA, o app
   Servidor de IA NexaVMS abre ao final.

Entre com o usuário `admin` e a senha `admin` e troque a senha em seguida. No servidor
de IA, o usuário é `admin` e a senha é a escolhida no instalador.

Os modelos de IA (cerca de 600 MB) são baixados em segundo plano depois da instalação.
O andamento aparece no app do servidor de IA, em Modelos.

O idioma escolhido no instalador passa a ser o padrão dos apps. Cada usuário pode
trocar pelo seletor de idioma na tela de entrada ou na barra lateral.

### Portas de rede

| Porta (TCP) | Serviço |
|---|---|
| 58100 | System Manager |
| 58200 | Storage |
| 58300 | Servidor de IA |

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
| [2.20.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.20.0) (recomendada) | 01/11/2026 | `PrimeVMS-Setup-2.20.0.exe`, 639 MB | Sim |
| [2.19.1](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.19.1) | 01/11/2026 | `PrimeVMS-Setup-2.19.1.exe`, 639 MB | Sim |
| [2.19.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v2.19.0) | 01/11/2026 | `PrimeVMS-Setup-2.19.0.exe`, 639 MB | Sim |

Ficam publicadas só as três últimas versões. Qualquer instalação anterior atualiza direto
para a mais recente pelo app. Quem usa a versão 1.4.0 ou anterior deve instalar a mais
recente pelo instalador uma vez; os dados são mantidos.

A partir da 2.5.0, a instalação precisa ser ativada com uma conta Nexa VMS, criada em
[nexavms.io](https://nexavms.io), pelo Console do System Manager. Sem ativação, o NexaVMS não grava
nem mostra vídeo. A primeira ativação traz 30 dias de avaliação do Professional.

### Conferir o download

```powershell
Get-FileHash .\PrimeVMS-Setup-2.20.0.exe -Algorithm SHA256
```

| Arquivo | SHA-256 |
|---|---|
| `PrimeVMS-Setup-2.20.0.exe` | `D72E11FF4229954A7FDE064C2B2B614268E2DC9A406AB92D6E6D0CD34E7BD76D` |
| `PrimeVMS-Setup-2.19.1.exe` | `6D4C08D71D0E2BC244E370C349F1F56A59D0D70264B329A69FE56602054A2DAA` |
| `PrimeVMS-Setup-2.19.0.exe` | `72BA6A8FC37B29F23CEB53FF05DC4DFE3085084AAEDDD1AE3A4CA7A8D9FDF327` |

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
