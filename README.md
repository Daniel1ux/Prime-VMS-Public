<div align="center">

# PRIME**VMS**

**Gestão de vídeo (CFTV) profissional — gravação, ao vivo, playback e exportação.**
Feito no Brasil pela [Prime Building Technology](https://primebr.com.br/).

[![Versão mais recente](https://img.shields.io/github/v/release/Daniel1ux/Prime-VMS-Public?label=vers%C3%A3o%20mais%20recente&color=c5e82e&labelColor=0a1626)](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest)
![Windows 10/11 64-bit](https://img.shields.io/badge/Windows-10%20%2F%2011%20(64--bit)-0b2545)

### [⬇ Baixar o PrimeVMS (versão mais recente)](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest)

</div>

Este repositório é o **canal oficial de distribuição** do PrimeVMS: aqui ficam os
**instaladores** de cada versão e os **pacotes de atualização** que o próprio
PrimeVMS baixa quando você clica em **Buscar atualizações**.

---

## O que vem no instalador

Um único instalador (`PrimeVMS-Setup-X.Y.Z.exe`) com os três componentes. Você
escolhe o que instalar em cada computador:

| Componente | O que faz |
|---|---|
| **System Manager** | Servidor central: câmeras, usuários e permissões, configuração do empreendimento. Roda como serviço do Windows. |
| **Storage** | Servidor de gravação: grava as câmeras, guarda e serve as gravações. Roda como serviço do Windows. |
| **Workstation** | Estação do operador: mosaico ao vivo, playback com timeline, exportação de imagens. |

Os serviços iniciam sozinhos com o Windows e se reerguem automaticamente se caírem.
Não é preciso instalar .NET nem outro programa.

## Requisitos

- **Windows 10 ou 11, 64 bits**.
- Permissão de **administrador** para instalar e atualizar.
- **Câmeras IP com RTSP/ONVIF** na mesma rede.
- Para o Storage: um disco com espaço para a retenção desejada (as gravações ficam
  fora da pasta do programa).
- Para a Workstation: placa de vídeo com aceleração (decodificação por GPU) é
  recomendada para mosaicos grandes.

## Instalação

1. Baixe o `PrimeVMS-Setup-X.Y.Z.exe` da [versão mais recente](https://github.com/Daniel1ux/Prime-VMS-Public/releases/latest).
2. Execute e aceite o pedido de administrador.
   > O instalador ainda não tem assinatura digital de código. Se o Windows mostrar
   > *"O Windows protegeu o computador"*, clique em **Mais informações → Executar assim mesmo**.
3. Escolha o **modelo de implantação**:
   - **Um único computador (tudo neste PC)** — instala System Manager, Storage e
     Workstation já conectados entre si. Indicado para projetos pequenos
     (até cerca de 16 câmeras), sem redundância de gravação.
   - **Instalação distribuída** — marque o papel de cada computador: System Manager
     num servidor dedicado, Storage em um ou mais servidores de gravação e
     Workstation nos computadores de operação.
4. Ao final, abra a **Workstation** (ou o **Console do System Manager**).

**Primeiro acesso:** usuário `admin`, senha `admin`. **Troque a senha logo após entrar.**

### Portas de rede

O instalador libera no Firewall do Windows as portas usadas entre os computadores:

| Porta (TCP) | Serviço |
|---|---|
| **58100** | System Manager |
| **58200** | Storage |

Em instalação distribuída, garanta que a rede permita essas portas entre os
servidores e as Workstations.

## Atualizações

A partir da versão **1.0.4**, o PrimeVMS se atualiza **de dentro dos apps** — não é
preciso baixar o instalador de novo:

1. Na Workstation, no Console do System Manager ou no Console do Storage, clique em
   **⟳ Buscar atualizações** (barra lateral ou tela de login). Ao abrir, o app também
   verifica sozinho e avisa quando há **versão nova**.
2. Veja as novidades e clique em **Atualizar agora** (pede permissão de administrador).
3. O PrimeVMS atualiza **tudo o que está instalado naquele computador de uma vez**:
   para os serviços, fecha os apps, instala, sobe os serviços, confere se estão
   respondendo na versão nova e reabre o app. Leva cerca de 1 minuto.

O que garante uma atualização segura:

- **Baixa só o que mudou** — normalmente cerca de 1 MB, e não o instalador inteiro.
- **Assinatura digital** — cada versão é assinada pela Prime Building Technology;
  arquivos alterados ou corrompidos são recusados antes de qualquer mudança.
- **Volta sozinho se algo der errado** — se um serviço não subir após a
  atualização (ou faltar energia no meio dela), a versão anterior é restaurada
  automaticamente.
- **Seus dados ficam intactos** — configurações, câmeras, usuários e gravações são
  mantidos; o banco de dados é atualizado automaticamente.

> Durante a atualização a gravação fica pausada por alguns instantes. Em sites com
> gravação crítica, atualize em horário de menor movimento.

**Atualização sem internet:** copie os arquivos de atualização de uma versão
(`update-manifest.json`, `update-manifest.json.sig` e os `pack-*.zip`) para uma
pasta e execute, como administrador:

```
"C:\Program Files\Prime VMS\Updater\PrimeVMS Updater.exe" --apply --source folder:D:\atualizacao-primevms
```

## Versões

| Versão | Data | Instalador | Atualização pelo app |
|---|---|---|---|
| **[1.0.4](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.4)** ⭐ recomendada | 18/10/2026 | `PrimeVMS-Setup-1.0.4.exe` (314 MB) | ✅ Sim |
| [1.0.3](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.3) | 17/10/2026 | `PrimeVMS-Setup-1.0.3.exe` (314 MB) | ⚠️ Canal antigo — instale a 1.0.4 |
| [1.0.2](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.2) | 06/06/2026 | `PrimeVMS-Setup-1.0.2.exe` (424 MB) | ❌ Não |
| [1.0.0](https://github.com/Daniel1ux/Prime-VMS-Public/releases/tag/v1.0.0) | 01/06/2026 | `PrimeVMS-Setup-1.0.0.exe` (265 MB) | ❌ Não |

As versões antigas ficam disponíveis só como histórico. **Quem tem 1.0.3 ou
anterior** instala a versão mais recente pelo setup uma vez — os dados são
preservados — e, dali em diante, atualiza pelo app.

As novidades de cada versão estão na página de cada [release](https://github.com/Daniel1ux/Prime-VMS-Public/releases).

### Conferir o download (opcional)

Para confirmar que o instalador não foi alterado, compare o SHA-256 no PowerShell:

```powershell
Get-FileHash .\PrimeVMS-Setup-1.0.4.exe -Algorithm SHA256
```

| Arquivo | SHA-256 |
|---|---|
| `PrimeVMS-Setup-1.0.4.exe` | `405B120D9E5BD56915E8CDE0A65D2D55CFD6A9020EB49992CE4177E1E3D71ED4` |
| `PrimeVMS-Setup-1.0.3.exe` | `97B2E821B3182DF8619003B73626AC234D8DA9A407FBD0434E6BDB804F7ED8D0` |
| `PrimeVMS-Setup-1.0.2.exe` | `8810E256670D7D20E791989B38D56D3878F0A753F126A9B990067A2E84FA65E7` |
| `PrimeVMS-Setup-1.0.0.exe` | `827586BE66C64AF0FD3538A8AE00A052ED8CDBF6890F73FD3EABA8DD9448BF0C` |

## Desinstalação

**Configurações do Windows → Aplicativos → PrimeVMS → Desinstalar** (ou o atalho
"Desinstalar PrimeVMS" no Menu Iniciar). Os serviços e as regras de firewall são
removidos. Os dados (banco e gravações) ficam em `C:\ProgramData\Prime VMS` e na
pasta de gravação escolhida, e **não são apagados** automaticamente.

## Licença e suporte

Copyright © 2026 **Prime Building Technology**. Todos os direitos reservados.
O núcleo VMS (System Manager, Storage e Workstation) é de uso livre para a gestão de
vídeo do empreendimento do licenciado; módulos de Inteligência Artificial, acesso
pela nuvem e alta disponibilidade dependem de licença comercial. O operador é
responsável por observar a legislação aplicável (inclusive a LGPD) ao captar,
gravar e tratar imagens.

O PrimeVMS inclui componentes de terceiros sob suas próprias licenças, como
[FFmpeg](https://ffmpeg.org/) e [go2rtc](https://github.com/AlexxIT/go2rtc).

**Suporte e contato:** [primebr.com.br](https://primebr.com.br/)
