# Retro-Infinity Multi-System — versões

Downloads do **Retro-Infinity Multi-System**, um frontend de emuladores (libretro) para Windows com interface de TV, feito para controle ou teclado.

Os pacotes ficam na página [Releases](https://github.com/leydassilva/retro-infinity_releases/releases).

| Pacote | Para |
|---|---|
| `Retro-Infinity-vX-WindowsXP-32bits.zip` | Windows XP SP3 em diante (32 ou 64 bits) |
| `Retro-Infinity-vX-Windows7-64bits.zip` | Windows 7 64 bits em diante; inclui PlayStation 2, GameCube, Wii e Xbox |
| `Retro-Infinity-vX-scraper.zip` | ferramenta opcional para baixar imagens, vídeos e descrições num PC moderno |
| `Retro-Infinity-vX-kit-iso-windows7.zip` | kit para montar um instalador do Windows 7 enxuto, com o Retro-Infinity, a partir da sua ISO ([instruções](#iso-do-windows-7-com-o-retro-infinity)) |

## Como instalar

1. Descompacte a pasta `Retro-Infinity` onde quiser (ex.: `C:\Retro-Infinity`).
2. Abra `multijogos.exe`. Na primeira vez, com internet, o programa baixa sozinho os emuladores das plataformas que tiverem jogos.
3. Coloque os jogos em `roms\<plataforma>`, ou envie pelo celular: **Menu → Conteúdo e downloads → Receber jogos pela rede**, e aponte a câmera para o QR code.
4. Algumas plataformas precisam da BIOS do console: veja `sistema\LEIA-ME - BIOS.txt`.

O manual completo está no `LEIA-ME.md`, dentro do pacote.

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
  - **Windows ADK**: instale só a parte "Ferramentas de Implantação" (traz o `oscdimg.exe`);
  - **MSYS2** ([msys2.org](https://www.msys2.org)): no terminal dele, rode `pacman -S xorriso`.
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

## O que não vem no pacote

Jogos (ROMs), BIOS, capas e vídeos dos jogos não acompanham o programa: são protegidos por direitos autorais dos fabricantes. Use apenas cópias de jogos que você possui, ou jogos de distribuição livre (o menu **Jogos de arcade livres** baixa os liberados pelos donos no mamedev.org).

Desenvolvido por leydassilva.
