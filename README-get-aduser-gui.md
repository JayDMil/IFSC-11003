Making an EXE from `get-aduser-gui.ps1`

Options

1) ps2exe (recommended)
   - Converts a PowerShell script into a single EXE wrapper.
   - Command-line tool available from PSGallery.
   - Result is a portable EXE but still depends on a compatible PowerShell/.NET runtime and required modules (ActiveDirectory). 

2) Packager / installer
   - Use Inno Setup or MSI to bundle the script + PowerShell runtime installer + prerequisites.

3) Commercial GUI packagers
   - PowerShell Studio (SAPIEN) can build signed EXEs and installers (paid).

Quick ps2exe steps

1. Install ps2exe (run once):

```powershell
Install-Module -Name ps2exe -Scope CurrentUser
```

2. Build EXE (from the script folder):

```powershell
Import-Module ps2exe
Invoke-PS2EXE -InputFile .\get-aduser-gui.ps1 -OutputFile .\get-aduser-gui.exe -NoConsole -IconFile .\logo.ico -Force
```

Notes & Caveats

- The target machine still needs a compatible PowerShell runtime and the ActiveDirectory module (RSAT).
- ExecutionPolicy/antivirus: unsigned EXEs made this way can trigger warnings. Consider code signing.
- Test on a clean machine before distribution.

If you want, I can build the EXE for you now (I will run the commands locally). Reply "build it" and I'll proceed. If you want me to proceed with code signing or an installer, tell me and I will outline next steps.
