- Upgrading powershell 5.x to 7.x
- To display major and minor version `$PSVersionTable.PSVersion`.
### To override the default powershell command:
- Download PowerShell 7.x, Go to the official PowerShell GitHub Releases page.
- Find the latest PowerShell 7.x version, Scroll down Windows x64: PowerShell-7.x.x-win-x64.msi (for 64-bit systems)
- start the installation, Choose installation path `C:\Program Files\PowerShell\7\`
- Open Settings → System → About → Advanced system settings.
- Click Environment Variables.
- In System variables, find Path, select it, and click Edit.
- Move C:\Program Files\PowerShell\7\ to the top.

## Change the Default PowerShell Version  

### Set PowerShell 7 as the Default Shell  

If you're using **Windows Terminal**, follow these steps:  

1. Open **Windows Terminal** (`wt.exe` from Run or Start Menu).  
2. Click the **dropdown arrow (`v`)** in the title bar and select **Settings**.  
3. Under **Profiles**, find **PowerShell** and click on it.  
4. Change **Command line** from: `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe` to `C:\Program Files\PowerShell\7\pwsh.exe`
5. Click Save.