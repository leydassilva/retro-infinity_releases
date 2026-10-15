# Retro-Infinity Multi-System — versões

Downloads do **Retro-Infinity Multi-System**, um frontend de emuladores (libretro) para Windows e Linux com interface de TV, feito para controle ou teclado.

Os pacotes ficam na página [Releases](https://github.com/leydassilva/retro-infinity_releases/releases).

| Pacote | Para |
|---|---|
| `Retro-Infinity-vX-WindowsXP-32bits.zip` | Windows XP SP3 em diante (32 ou 64 bits) |
| `Retro-Infinity-vX-Windows7-64bits.zip` | Windows 7 64 bits em diante; inclui PlayStation 2, GameCube, Wii e Xbox |
| `Retro-Infinity-vX-Linux-x86_64.zip` | Linux 64 bits: Ubuntu 22.04/24.04 e Linux Mint 21/22 ([instruções](#linux-ubuntu-e-linux-mint)) |
| `Retro-Infinity-OS-vX-x86_64.iso` | **Retro-Infinity OS**: sistema completo que liga direto no Retro-Infinity, como um console ([instruções](#retro-infinity-os-iso-linux)) |
| `Retro-Infinity-vX-scraper.zip` | ferramenta opcional para baixar imagens, vídeos e descrições num PC moderno |
| `Retro-Infinity-vX-kit-iso-windows7.zip` | kit para montar um instalador do Windows 7 enxuto, com o Retro-Infinity, a partir da sua ISO ([instruções](#iso-do-windows-7-com-o-retro-infinity)) |
| `Retro-Infinity-vX-kit-iso-windowsxp.zip` | o mesmo para o Windows XP SP3 (32 bits): um CD de instalação enxuto com o Retro-Infinity ([instruções](#cd-do-windows-xp-com-o-retro-infinity)) |

## Como instalar

1. Descompacte a pasta `Retro-Infinity` onde quiser (ex.: `C:\Retro-Infinity`).
2. Abra `multijogos.exe`. Na primeira vez, com internet, o programa baixa sozinho os emuladores das plataformas que tiverem jogos.
3. Coloque os jogos em `roms\<plataforma>`, ou envie pelo celular: **Menu → Conteúdo e downloads → Receber jogos pela rede**, e aponte a câmera para o QR code.
4. Algumas plataformas precisam da BIOS do console: veja `sistema\LEIA-ME - BIOS.txt`.

O manual completo está no `LEIA-ME.md`, dentro do pacote.

## Linux (Ubuntu e Linux Mint)

1. Baixe o `Retro-Infinity-vX-Linux-x86_64.zip` e descompacte onde quiser (ex.: na sua pasta pessoal).
2. No terminal, dentro da pasta `Retro-Infinity`, rode uma vez:
   ```bash
   ./criar-atalho.sh
   ```
   O script confere as bibliotecas que o programa usa: SDL2, cairo, FreeType e a fonte DejaVu, que já vêm no Ubuntu e no Mint. Se faltar alguma, ele pergunta antes de instalar; se a resposta for não, só encerra. Depois cria o atalho **Retro-Infinity Multi-System** no menu de aplicativos e na área de trabalho.
3. Abra pelo atalho ou com `./multijogos`. Os jogos vão em `roms/<plataforma>`, como no Windows. O mesmo `multijogos.ini` serve nos dois sistemas.

Ainda não vêm na versão Linux: emuladores 3D (Nintendo 64, PlayStation 2, GameCube e Wii, que precisam de OpenGL), música de fundo, prévias em vídeo e o editor de informações. Eles chegam nas próximas versões, pelo atualizador.

## Retro-Infinity OS (ISO Linux)

Sistema completo, baseado no Ubuntu 22.04 e só com software livre, que liga direto no Retro-Infinity em tela cheia, sem área de trabalho. Dá para usar só com joystick. Precisa de um PC de 64 bits com 2 GB de RAM; com UEFI, desligue o Secure Boot.

1. Grave o `Retro-Infinity-OS-vX-x86_64.iso` num pendrive com o [balenaEtcher](https://etcher.balena.io/), o Rufus ou o `dd`, ou num DVD.
   - **No Rufus, use o modo DD.** Ao clicar em "Iniciar", escolha **"Gravar no modo Imagem DD"**. No modo ISO (o "recomendado" dele), o boot para numa tela preta com `GRUB _`.
2. Ligue o PC pelo pendrive. O menu de boot tem três opções:
   - **Retro-Infinity OS:** roda ao vivo, sem tocar no disco; o que for gravado some ao desligar;
   - **vídeo em modo seguro:** para placas que não mostram imagem na opção normal;
   - **Instalar no disco:** apaga o disco escolhido (pede para digitar `APAGAR`) e deixa o PC ligando direto no Retro-Infinity.
3. Os jogos ficam em `/home/retro/Retro-Infinity/roms/<plataforma>`. Também dá para enviá-los pelo celular: **Menu → Conteúdo e downloads → Receber jogos pela rede**. Os emuladores são baixados com internet por cabo.

No menu do Retro-Infinity OS:
- **Desligar / Reiniciar** fica no lugar de "Sair".
- **Interface e tema → Resolução da tela:** troca a resolução, pergunta se mantém e, sem resposta em 15 segundos, volta à anterior.
- **Sistema → Abrir console:** abre um terminal (usuário `retro`, `sudo` sem senha, `nmtui` para o Wi-Fi). O `exit` volta ao programa.

## Atualizações

A partir da v0.5.0, o programa se atualiza sozinho por esta página. O modo fica em **Menu → Sistema → Atualização do programa**:
- **automática:** procura ao abrir e instala sozinha;
- **manual:** só procura quando você pedir;
- **desligada:** nunca procura.

Só os arquivos do programa são trocados. Jogos, BIOS, saves e configurações ficam como estão.

## ISO do Windows 7 com o Retro-Infinity

Com o kit `Retro-Infinity-vX-kit-iso-windows7.zip` você monta, **a partir da sua própria ISO do Windows 7 SP1**, um instalador que deixa o PC pronto para jogar. Depois de instalado:
- o Windows fica enxuto;
- a conta entra sozinha, com login automático;
- o Retro-Infinity abre junto com o Windows.

A ISO do Windows não é distribuída aqui (é da Microsoft). Cada um monta a sua com o kit, e a ISO gerada não deve ser compartilhada.

### Do que precisa

- Windows 8.1, 10 ou 11, com o **PowerShell como administrador**.
- Uma ISO de instalação do **Windows 7 SP1**: 64 bits (recomendada) ou 32 bits. A original nunca é alterada.
- Um gravador de ISO, um dos dois:
  - **Windows ADK**: só a parte "Ferramentas de Implantação" (traz o `oscdimg.exe`);
  - **MSYS2** ([msys2.org](https://www.msys2.org)) com o pacote `xorriso`.

  **Não precisa instalar antes.** Se faltar o gravador, o script avisa que é pré-requisito e pergunta se pode instalar o MSYS2 (uns 500 MB) e o `xorriso`. Respondendo **N**, ele encerra sem alterar nada. *(A partir da próxima release.)*
- Espaço livre de umas 2,2 vezes o tamanho da ISO.
- Internet: o script baixa a última versão do Retro-Infinity desta página.

### Passo a passo

1. Baixe o `Retro-Infinity-vX-kit-iso-windows7.zip` da última [release](https://github.com/leydassilva/retro-infinity_releases/releases/latest) e descompacte. Por exemplo, em `C:\kit-iso-windows7`.
2. Abra o **PowerShell como administrador**: menu Iniciar → digite *PowerShell* → *Executar como administrador*.
3. Entre na pasta do kit e rode o script, informando a sua ISO:

   ```powershell
   cd C:\kit-iso-windows7
   Set-ExecutionPolicy -Scope Process Bypass
   .\montar_iso.ps1 -IsoOriginal D:\pt_windows_7_ultimate_with_sp1_x64_dvd.iso
   ```

   A etapa "Gerando install.wim" demora alguns minutos. A ISO nova sai ao lado da original, com `_retro-infinity` no nome. Nada é sobrescrito.
4. Grave a ISO num pendrive com o [Rufus](https://rufus.ie) (ou num DVD) e dê boot por ela no PC que vai virar o console.
5. A instalação segue sozinha. **Só a escolha do disco é manual**, para nunca apagar um disco por engano. Confira antes de formatar.

### Opções do script

| Parâmetro | Para que serve |
|---|---|
| `-IsoOriginal` | a sua ISO do Windows 7 SP1 (obrigatório) |
| `-Saida` | caminho da ISO nova |
| `-Edicao` | edição a instalar. Padrão: `Windows 7 ULTIMATE`. Se não existir, o script lista as edições da ISO. Exemplo: `-Edicao "Windows 7 HOMEPREMIUM"` |
| `-PastaRetroInfinity` | usa uma instalação sua (com jogos, BIOS...) em vez de baixar daqui. Log, cache e `multijogos.ini` ficam de fora. **Não compartilhe a ISO gerada assim** |
| `-IncluirIni` | com `-PastaRetroInfinity`, leva também o `multijogos.ini`, que pode ter a sua conta do ScreenScraper |
| `-PastaTrabalho` | pasta temporária. Padrão: `%TEMP%` |

### O que a instalação deixa pronto

- **Idioma e conta:** português do Brasil, conta **Retro** sem senha e com login automático.
- **Programa:** Retro-Infinity em `C:\Retro-Infinity`, abrindo junto com o Windows e liberado no firewall da rede de casa (para receber jogos pelo celular).
- **Windows enxuto.** O que é desligado ou tirado:
  - uns 60 serviços sem uso num console: busca, Superfetch, Defender, temas e Aero, compartilhamento de arquivos, área de trabalho remota, Bluetooth, entre outros;
  - recursos opcionais: Media Center, jogos do Windows, Internet Explorer, impressão, fax e outros;
  - tarefas agendadas, restauração do sistema, UAC, hibernação e autoplay de pendrive;
  - menu e animação de boot;
  - backup do Service Pack, que é apagado.
- **Continuam ligados:** som, vídeo, rede, USB e joysticks.
- O que foi feito fica registrado em `C:\Windows\Setup\Scripts\RetroInfinity.log`.

Os emuladores são baixados na primeira vez que o programa abre com internet. Drivers da placa de vídeo, se o Windows 7 não tiver, são por sua conta.

## CD do Windows XP com o Retro-Infinity

O kit `Retro-Infinity-vX-kit-iso-windowsxp.zip` faz o mesmo que o do Windows 7, a partir da **sua ISO do Windows XP SP3 de 32 bits**, com a versão de 32 bits do Retro-Infinity. *(A partir da próxima release.)*

### Do que precisa

- PowerShell no Windows 7, 8.1, 10 ou 11. **Não precisa de administrador**, a não ser para instalar o MSYS2.
- Uma ISO de instalação do **Windows XP SP3 de 32 bits**. A original nunca é alterada.
- A **chave do produto** do seu XP. O script pergunta. Se deixar em branco, a instalação pede durante a cópia dos arquivos.
- O **xorriso** (MSYS2). Se faltar, o script avisa que é pré-requisito e pergunta se pode instalar. Respondendo **N**, encerra sem alterar nada.

### Passo a passo

1. Baixe o `Retro-Infinity-vX-kit-iso-windowsxp.zip` da última [release](https://github.com/leydassilva/retro-infinity_releases/releases/latest) e descompacte. Por exemplo, em `C:\kit-iso-windowsxp`.
2. No PowerShell, rode:

   ```powershell
   cd C:\kit-iso-windowsxp
   Set-ExecutionPolicy -Scope Process Bypass
   .\montar_iso.ps1 -IsoOriginal D:\pt-br_windows_xp_professional_with_service_pack_3_x86_cd.iso
   ```

   Digite a chave quando o script pedir, ou passe `-ChaveProduto XXXXX-XXXXX-XXXXX-XXXXX-XXXXX`. A ISO nova sai ao lado da original, com `_retro-infinity` no nome.
3. **Grave num CD** ou use numa máquina virtual. O Rufus não grava a instalação do XP em pendrive; para isso existe o WinSetupFromUSB.
4. A instalação segue sozinha. **Só a escolha do disco é manual.**

As opções `-Saida`, `-PastaRetroInfinity`, `-IncluirIni` e `-PastaTrabalho` funcionam como no kit do Windows 7.

### Atenção em PCs modernos

- **Disco SATA:** o XP não tem driver para discos SATA em modo AHCI. A instalação dá tela azul `0x7B`. Antes de instalar, ponha o disco em modo **IDE / Compatível / Legacy** na BIOS.
- **Ativação:** a ativação online do XP não funciona mais. Mídias de licença por volume (VLK) não pedem ativação; as outras podem exigir ativação por telefone.
- **Segurança:** o XP não recebe atualizações desde 2014. Use o "console" só na rede de casa.

### O que a instalação deixa pronto

- **Idioma e conta:** português do Brasil, conta **Retro** sem senha e com login automático.
- **Programa:** Retro-Infinity em `C:\Retro-Infinity`, abrindo junto com o Windows e liberado no firewall da rede local.
- **O que não é instalado:** jogos do Windows, MSN Explorer, Windows Messenger, Outlook Express, Fax e acessórios.
- **O que é desligado:** uns 35 serviços, entre eles a Central de Segurança, as Atualizações Automáticas, a Restauração do Sistema, os temas, a impressão, o compartilhamento de arquivos e o autoplay.
- **Continuam ligados:** som, vídeo, rede com e sem fio, USB e joysticks.
- O que foi feito fica registrado em `C:\WINDOWS\RetroInfinity.log`.

## O que não vem no pacote

Jogos (ROMs), BIOS, capas e vídeos dos jogos não acompanham o programa: são protegidos por direitos autorais dos fabricantes. Use apenas cópias de jogos que você possui, ou jogos de distribuição livre (o menu **Jogos de arcade livres** baixa os liberados pelos donos no mamedev.org).

Desenvolvido por leydassilva.
