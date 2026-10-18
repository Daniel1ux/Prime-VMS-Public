<div align="center">

[English](README.md) · **Português** · [Español](README.es.md)

# PRIME**VMS** — Software VMS grátis para câmeras IP

**Sistema de gerenciamento de vídeo (VMS) gratuito para CFTV: ao vivo, gravação 24/7, playback e exportação.**
Núcleo grátis **sem licença por câmera** · módulos avançados com **planos acessíveis**.

[![Versão mais recente](https://img.shields.io/github/v/release/Daniel1ux/Prime-VMS-Public?label=vers%C3%A3o%20mais%20recente&color=c5e82e&labelColor=0a1626)](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest)
![Windows 10/11 64-bit](https://img.shields.io/badge/Windows-10%20%2F%2011%20(64--bit)-0b2545)
![ONVIF / RTSP](https://img.shields.io/badge/c%C3%A2meras-ONVIF%20%2F%20RTSP-00e5ff?labelColor=0a1626)
![Idiomas](https://img.shields.io/badge/idiomas-PT%20%C2%B7%20EN%20%C2%B7%20ES-c5e82e?labelColor=0a1626)

### [⬇ Baixar o PrimeVMS grátis](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest) · [🌐 Site](https://daniel1ux.github.io/Prime-VMS-Public/pt/)

</div>

O **PrimeVMS** é um **sistema de gerenciamento de vídeo (VMS)** profissional para
Windows — **software de CFTV / NVR gratuito** para gravar, assistir ao vivo e
reproduzir **câmeras IP** de qualquer marca compatível com **ONVIF ou RTSP**. O núcleo
do VMS é de **uso gratuito**, sem licença por câmera. Você só paga pelo que agrega
valor: **analíticos de vídeo com IA**, **acesso pela nuvem** e **alta
disponibilidade** — em planos acessíveis.

Feito no Brasil pela [Prime Building Technology](https://primebr.com.br/), disponível
em **português, inglês e espanhol**.

---

## Por que o PrimeVMS

| | PrimeVMS | VMS tradicional |
|---|---|---|
| Licença do núcleo | **Grátis** — sem custo por câmera | Paga por câmera / canal |
| Câmeras | **Qualquer câmera ONVIF / RTSP** | Muitas vezes preso a um fabricante |
| Implantação | **Um instalador**: um PC → servidores distribuídos | Produtos / edições diferentes |
| Atualizações | **Um clique dentro do app**, com volta automática | Baixar e reinstalar |
| Recursos avançados | **Módulos com planos acessíveis** — pague só pelo que usar | Pacotes caros |
| Idiomas | **Português · English · Español** | Varia |

## Recursos — núcleo grátis

- 📹 **Funciona com as suas câmeras** — **descoberta ONVIF** automática e detecção
  do caminho RTSP (basta informar usuário e senha da câmera), com padrões RTSP
  embutidos para Hikvision/Annke, Dahua/Intelbras, Axis e Reolink, além de ONVIF/RTSP
  genérico.
- 🔴 **Gravação 24/7** em disco (MP4 segmentado, sem recodificar), com catálogo de
  gravações e **retenção por dias**.
- 🖥️ **Ao vivo** em mosaicos de até 4×4, tela cheia, **multi-monitor** e vídeo wall,
  com **decodificação acelerada por GPU**.
- ⏱️ **Playback** com linha do tempo de 24 h e zoom, **marcadores**, reprodução de
  várias câmeras sincronizadas e data/hora no vídeo.
- 📤 **Exportação** de imagens e vídeos com **marca d'água anti-fraude** (logotipo +
  data/hora).
- 👥 **Usuários e perfis** (administrador, supervisor, operador) aplicados no servidor.
- 🏢 **Cresce com você** — tudo num PC só, ou instalação **distribuída** com servidor
  central, vários servidores de gravação e várias estações de operação.
- 🔄 **Atualização automática** — busque atualizações dentro do app; só o que mudou é
  baixado, com assinatura digital e volta automática se algo falhar.
- 🌐 **Três idiomas** — português, inglês e espanhol (troque no app).

## Módulos pagos — planos acessíveis

| Módulo | Situação |
|---|---|
| 🤖 **Analíticos de vídeo com IA** — contagem de pessoas | ✅ Disponível |
| 🤖 Mais analíticos — detecção de objetos, cruzamento de linha/intrusão, permanência indevida, filas, fogo e fumaça, EPI, reconhecimento facial, leitura de placas (LPR), objetos abandonados, busca inteligente | 🛠️ Em desenvolvimento |
| ☁️ **Prime Cloud** — acesso remoto e celular **sem abrir portas** (sem configurar NAT) | 🔜 Em breve |
| 🛡️ **Alta disponibilidade** — servidor central redundante (principal/reserva) | 🔜 Em breve |

Planos pensados para caber em projetos pequenos e médios.
**[Fale com a Prime](https://primebr.com.br/)** para um orçamento.

## O que vem no instalador

Um único instalador (`PrimeVMS-Setup-X.Y.Z.exe`) com os três componentes — você
escolhe o que instalar em cada computador:

| Componente | O que faz |
|---|---|
| **System Manager** | Servidor central: câmeras, usuários e permissões, configuração do empreendimento. Roda como serviço do Windows. |
| **Storage** | Servidor de gravação: grava as câmeras, guarda e serve as gravações. Roda como serviço do Windows. |
| **Workstation** | Estação do operador: mosaico ao vivo, playback com linha do tempo, exportação. |

Os serviços iniciam sozinhos com o Windows e se reerguem automaticamente se caírem.
Não é preciso instalar .NET nem outro programa.

## Requisitos

- **Windows 10 ou 11, 64 bits**.
- Permissão de **administrador** para instalar e atualizar.
- **Câmeras IP com ONVIF/RTSP** na mesma rede.
- Para o Storage: um disco com espaço para a retenção desejada (as gravações ficam fora
  da pasta do programa).
- Para a Workstation: placa de vídeo com decodificação por hardware é recomendada para
  mosaicos grandes.

## Instalação

1. Baixe o `PrimeVMS-Setup-X.Y.Z.exe` da [versão mais recente](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest).
2. Execute, escolha o idioma (English, Português ou Español) e aceite o pedido de
   administrador.
   > O instalador ainda não tem assinatura digital de código. Se o Windows mostrar
   > *"O Windows protegeu o computador"*, clique em **Mais informações → Executar assim mesmo**.
3. Escolha o **modelo de implantação**:
   - **Um único computador (tudo neste PC)** — System Manager, Storage e Workstation já
     conectados. Para projetos pequenos (até cerca de 16 câmeras), sem redundância de
     gravação.
   - **Instalação distribuída** — marque o papel de cada computador: System Manager num
     servidor dedicado, Storage em um ou mais servidores de gravação e Workstation nos
     computadores de operação.
4. Abra a **Workstation** (ou o **Console do System Manager**).

**Primeiro acesso:** usuário `admin`, senha `admin`. **Troque a senha logo após
entrar.** O idioma escolhido no instalador vira o idioma dos apps; cada usuário pode
trocar quando quiser no seletor 🌐 **PT · EN · ES**.

### Portas de rede

| Porta (TCP) | Serviço |
|---|---|
| **58100** | System Manager |
| **58200** | Storage |

O instalador libera essas portas no Firewall do Windows. Em instalação distribuída,
garanta que a rede permita essas portas entre os servidores e as Workstations.

## Atualizações

Desde a versão **1.0.4**, o PrimeVMS se atualiza **de dentro dos apps**:

1. Na Workstation, no Console do System Manager ou no Console do Storage, clique em
   **⟳ Buscar atualizações** (barra lateral ou tela de login). Os apps também verificam
   sozinhos e avisam quando há **versão nova**.
2. Veja as novidades e clique em **Atualizar agora** (pede permissão de administrador).
3. O PrimeVMS atualiza **tudo o que está instalado naquele computador de uma vez**:
   para os serviços, fecha os apps, instala, sobe os serviços, confere se estão
   respondendo na versão nova e reabre o app. Leva cerca de 1 minuto.

- **Baixa só o que mudou** — normalmente cerca de 1 MB, e não o instalador inteiro.
- **Assinatura digital** — arquivos alterados ou corrompidos são recusados antes de
  qualquer mudança.
- **Volta sozinho se algo der errado** — se um serviço não subir (ou faltar energia no
  meio), a versão anterior é restaurada.
- **Seus dados ficam intactos** — configurações, câmeras, usuários e gravações são
  mantidos; o banco de dados é atualizado automaticamente.

> Durante a atualização a gravação fica pausada por alguns segundos. Em sites com
> gravação crítica, atualize em horário de menor movimento.

**Atualização sem internet:** copie os arquivos de atualização de uma versão
(`update-manifest.json`, `update-manifest.json.sig` e os `pack-*.zip`) para uma pasta e
execute, como administrador:

```
"C:\Program Files\Prime VMS\Updater\PrimeVMS Updater.exe" --apply --source folder:D:\atualizacao-primevms
```

## Versões

| Versão | Data | Instalador | Atualização pelo app |
|---|---|---|---|
| **[1.0.5](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.5)** ⭐ recomendada | 18/10/2026 | `PrimeVMS-Setup-1.0.5.exe` (315 MB) | ✅ Sim |
| [1.0.4](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.4) | 18/10/2026 | `PrimeVMS-Setup-1.0.4.exe` (314 MB) | ✅ Sim |
| [1.0.3](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.3) | 17/10/2026 | `PrimeVMS-Setup-1.0.3.exe` (314 MB) | ⚠️ Canal antigo — instale a 1.0.5 |
| [1.0.2](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.2) | 06/06/2026 | `PrimeVMS-Setup-1.0.2.exe` (424 MB) | ❌ Não |
| [1.0.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.0) | 01/06/2026 | `PrimeVMS-Setup-1.0.0.exe` (265 MB) | ❌ Não |

As versões antigas ficam só como histórico. **Quem tem 1.0.3 ou anterior** instala a
versão mais recente pelo setup uma vez — os dados são preservados — e, dali em diante,
atualiza pelo app. As novidades de cada versão estão na página de cada
[release](https://github.com/Daniel1ux/Prime-VMS-Public/releases).

### Conferir o download (opcional)

```powershell
Get-FileHash .\PrimeVMS-Setup-1.0.5.exe -Algorithm SHA256
```

| Arquivo | SHA-256 |
|---|---|
| `PrimeVMS-Setup-1.0.5.exe` | `97BAA1164289F40D35D530A1C9AC7A338E73CAA4197B4BF06473DD2FCCFFF746` |
| `PrimeVMS-Setup-1.0.4.exe` | `405B120D9E5BD56915E8CDE0A65D2D55CFD6A9020EB49992CE4177E1E3D71ED4` |
| `PrimeVMS-Setup-1.0.3.exe` | `97B2E821B3182DF8619003B73626AC234D8DA9A407FBD0434E6BDB804F7ED8D0` |
| `PrimeVMS-Setup-1.0.2.exe` | `8810E256670D7D20E791989B38D56D3878F0A753F126A9B990067A2E84FA65E7` |
| `PrimeVMS-Setup-1.0.0.exe` | `827586BE66C64AF0FD3538A8AE00A052ED8CDBF6890F73FD3EABA8DD9448BF0C` |

## Perguntas frequentes

**O PrimeVMS é grátis mesmo?**
Sim. O núcleo do VMS — ao vivo, gravação, playback, exportação, usuários, servidores
distribuídos e atualizações — é gratuito, sem licença por câmera. Só os módulos
avançados (analíticos com IA, Prime Cloud, alta disponibilidade) são pagos, em planos
acessíveis.

**Quais câmeras funcionam?**
Qualquer câmera IP com **ONVIF** ou **RTSP**, de qualquer fabricante. O PrimeVMS
encontra as câmeras ONVIF na rede e descobre sozinho o caminho do vídeo.

**Ele substitui um NVR/DVR?**
O PrimeVMS grava as câmeras IP direto num PC ou servidor Windows (NVR por software),
com retenção por dias, e também funciona junto com gravadores que já disponibilizam
RTSP.

**Quantas câmeras posso usar?**
Não há limite de licença por câmera no núcleo grátis. O limite prático é o hardware e a
rede; para projetos maiores, use a instalação distribuída com vários servidores de
gravação.

**Quais idiomas estão disponíveis?**
Português (Brasil), inglês e espanhol — nos apps, no instalador e nas notas de versão.

## Desinstalação

**Configurações do Windows → Aplicativos → PrimeVMS → Desinstalar** (ou o atalho
"Desinstalar PrimeVMS" no Menu Iniciar). Os serviços e as regras de firewall são
removidos. Os dados (banco e gravações) ficam em `C:\ProgramData\Prime VMS` e na pasta
de gravação escolhida, e **não são apagados** automaticamente.

## Licença e suporte

Copyright © 2026 **Prime Building Technology**. Todos os direitos reservados.
O núcleo VMS (System Manager, Storage e Workstation) é de uso livre para a gestão de
vídeo do empreendimento do licenciado; módulos de Inteligência Artificial, acesso pela
nuvem e alta disponibilidade dependem de licença comercial. O operador é responsável
por observar a legislação aplicável (inclusive a LGPD) ao captar, gravar e tratar
imagens.

O PrimeVMS inclui componentes de terceiros sob suas próprias licenças, como
[FFmpeg](https://ffmpeg.org/) e [go2rtc](https://github.com/AlexxIT/go2rtc).

**Suporte e contato:** [primebr.com.br](https://primebr.com.br/)
