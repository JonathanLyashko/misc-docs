# Installing oh-my-posh

This is the one stop guide to making your windows terminal look like more that a collection of characters. I created this file as I encountered some errors while going through the original documentation. This file includes a step which allows you to manually update the theme. 

---

## 1. Install Nerd Fonts

- Go to this Github repo: <a href="https://github.com/ryanoasis/nerd-fonts/" style="display:inline-block; background-color:#0078D4; color:white; padding:6px 12px; text-align:center; text-decoration:none; font-size:16px; border-radius:32px; font-family:Arial, sans-serif;">Explore Nerd Fonts</a>

- On the right side of the page, find the releases tab
- Select latest, scroll down, and click on a font. I personally use FiraCode.zip
- After the zip file installs, extract all, then select all, then hit download.
- Open terminal, open settings, under profiles, select defaults, select appearance, and select your font face

---

## 2. oh-my-posh

- Download the package via winget: 
    ```bash
   winget install JanDeDobbeleer.OhMyPosh -s winget
   ```
    - This installs oh-my-posh.exe and themes
- To reload the PATH, restart your terminal. If oh-my-posh is not a recognized command, manually add it to PATH: 
    ```bash
    $env:Path += ";C:\Users\user\AppData\Local\Programs\oh-my-posh\bin"
    ```
- Activate the default themes:
    ```bash
    oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\jandedobbeleer.omp.json" | Invoke-Expression
    ```
- To view all available themes, run: 
    ```bash
    Get-PoshThemes
    ```
    - Or visit <a href="https://ohmyposh.dev/docs/themes" style="display:inline-block; background-color:#0078D4; color:white; padding:6px 12px; text-align:center; text-decoration:none; font-size:16px; border-radius:32px; font-family:Arial, sans-serif;">Explore Themes</a>
- You will be promted with something along the lines of the following:
    ```bash
    To change your theme, adjust the init script in C:\Users\[YOUR USERNAME]\OneDrive\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1.
    Example:
    oh-my-posh init pwsh --config 'C:\Users\[YOUR USERNAME]\AppData\Local\Programs\oh-my-posh\themes\jandedobbeleer.omp.json' | Invoke-Expression
    ```
    - replace "jandedobbeleer" with the name of your desired theme
    - if this returns an error, we can update the variables manually.

#### 2.1 Manually update theme
###### IMPORTANT: Do this even if the previous step worked

- If you are using powershell, complete the following. Otherwise, use this tool and documentation to find the next steps. <a href="https://ohmyposh.dev/docs/installation/prompt" style="display:inline-block; background-color:#0078D4; color:white; padding:6px 12px; text-align:center; text-decoration:none; font-size:16px; border-radius:32px; font-family:Arial, sans-serif;">Find Shell</a>
- Run:
    ```bash
    notepad $PROFILE
    ```
    - if this returns an error, run the following: 
    ```bash
    New-Item -Path $PROFILE -Type File -Force
    ```
- Add the following to the end of the file now open in your notepad:
    ```
    oh-my-posh init pwsh | Invoke-Expression
    ```
- To manually update your theme, add this instead:
    ```
    oh-my-posh init pwsh --config 'C:\Users\[YOUR USERNAME]\AppData\Local\Programs\oh-my-posh\themes\[YOUR THEME NAME].omp.json' | Invoke-Expression
    ```
- Run: 
    ```bash
    . $PROFILE
    ```

--- 

#### For the full, original documentation, visit:
<a href="https://ohmyposh.dev/docs/installation/windows" style="display:inline-block; background-color:#0078D4; color:white; padding:6px 12px; text-align:center; text-decoration:none; font-size:16px; border-radius:32px; font-family:Arial, sans-serif;">View Documentation</a>

