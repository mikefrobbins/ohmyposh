# Configure Oh My Posh for use with PowerShell in Windows Terminal

The following instructions walk you through the process of configuring
[Oh My Posh](https://ohmyposh.dev/) with a one line prompt that automatically changes to a two line
prompt when in a Git repo.

![oh-my-posh-custom-prompt.jpg](images/oh-my-posh-custom-prompt.jpg)

## Prerequisites

- [Windows Terminal](https://docs.microsoft.com/windows/terminal/install)
- [PowerShell 7](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-on-windows)
- [posh-git PowerShell module](https://www.powershellgallery.com/packages/posh-git/)

PowerShell 7 is not required, although it is recommended.

## Installation and configuration

1. Install Oh My Posh:

   ```powershell
   winget install JanDeDobbeleer.OhMyPosh
   ```

1. Install the [CaskaydiaCove](https://github.com/ryanoasis/nerd-fonts/releases/) nerd font.

1. Configure Windows Terminal to use the CaskaydiaCove font:

```json
   "font":
   {
       "face": "CaskaydiaCove Nerd Font"
   }
   ```

1. Add the following to your PowerShell profile. The referenced theme can be found in the themes folder
of this repo.

   ```powershell
   oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\mikefrobbins.omp.yaml" | Invoke-Expression
   $env:POSH_GIT_ENABLED = $true
   ```

## Additional notes

Oh My Posh adds the following environment variables:

```powershell
$env:POSH_GIT_ENABLED
$env:POSH_THEME
$env:POSH_THEMES_PATH
$env:POWERLINE_COMMAND
```

Determine the path to the Oh My Posh executable.

```powershell
(Get-Command -Name oh-my-posh.exe).Source
```

The Oh My Posh executable may need to be added to the exclusions of your antivirus software or
Windows Defender if you're experiencing performance issues.

## Disclaimer

All data and information provided in this GitHub repository is for informational purposes only. The
author is not affiliated with Oh My Posh and makes no representations as to accuracy, completeness,
currentness, suitability, or validity of any information in this repo and will not be liable for any
errors, omissions, or delays in this information or any losses, injuries, or damages arising from
its display or use. All information is provided on an as-is basis.
