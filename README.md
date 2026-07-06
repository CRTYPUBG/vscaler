<div align="center">


</div>

## Table of Contents

**1.** [**About**](#about)  
**2.** [**How it works?**](#how-it-works)  
**3.** [**Supported APIs and Upscalers**](#which-apis-and-upscalers-are-supported)  
**4.** [**Installation**](#installation)  
**5.** [**Known Issues**](#known-issues)  
**6.** [**Compilation and Credits**](#compilation)  
**7.** [**Wiki**](https://github.com/CRTYPUBG/cscaler/wiki)

<br />
<div align="center">
  <a href="https://discord.gg/"><img src="https://img.shields.io/badge/CScaler-blue?style=for-the-badge&logo=discord&logoColor=white&logoSize=auto&color=5865F2" alt="Discord invite"></a>
  <a href="https://github.com/CRTYPUBG/cscaler/releases/latest"><img src="https://img.shields.io/badge/Download-Stable-green?style=for-the-badge&logo=github&logoSize=auto" alt="Stable release"></a>
  <a href="https://github.com/CRTYPUBG/cscaler/releases/tag/vnightly"><img src="https://img.shields.io/badge/Download-vnightly-purple?style=for-the-badge&logo=github&logoSize=auto" alt="vnightly release"></a>
  <a href="https://github.com/CRTYPUBG/cscaler/wiki"><img src="https://img.shields.io/badge/Documentation-blue?style=for-the-badge&logo=gitbook&logoColor=white&logoSize=auto" alt="Wiki"></a>
</div>
<div align="center">
  <a href="https://github.com/CRTYPUBG/cscaler/releases"><img src="https://img.shields.io/github/downloads/CRTYPUBG/cscaler/total?style=for-the-badge&logo=gitextensions&logoSize=auto&label=Total" alt="Total DL"></a>
  <a href="https://github.com/CRTYPUBG/cscaler/releases/latest"><img src="https://img.shields.io/github/downloads/CRTYPUBG/cscaler/latest/total?style=for-the-badge&logo=gitextensions&logoSize=auto&label=Stable&color=green&logoColor=white" alt="Stable DL"></a>
  <a href="https://github.com/CRTYPUBG/cscaler/releases/tag/vnightly"><img src="https://img.shields.io/github/downloads/CRTYPUBG/cscaler/vnightly/total?style=for-the-badge&logo=gitextensions&logoColor=white&logoSize=auto&label=vnightly&color=purple" alt="vnightly DL"></a>
  <a href="https://github.com/CRTYPUBG/cscaler/stargazers"><img src="https://img.shields.io/github/stars/cscaler/cscaler?style=for-the-badge&logo=githubsponsors&logoColor=white&label=S.T.A.R.S." alt="Stars"></a>
</div>


## About

**cscaler** is a tool that lets you replace upscalers in games that ***already support DLSS2+ / FSR2+ / XeSS*** ($`^1`$), as well as manage ***frame generation*** in already mentioned games _(either by replacing existing FG options or enabling it in DX12 games through experimental ***VFG***)_. It also offers extensive customization options for all users, including those with Nvidia GPUs using DLSS.

> [!CAUTION]
> * We've been informed about some **FAKE websites** presenting themselves as cscaler team, so we would like to strongly highlight that we **DO NOT HAVE an official website!**
> * **We DON'T have an official manager app**, so please be careful when downloading or using them!
> * Only **LEGIT places** are this Github, our Discord server and Nitec's NexusMods page.  
> * cscaler is **FREE**, any kind of monetary requirements are scams!  

> [!TIP]
> _For example, if a game has DLSS only, cscaler can be used to replace DLSS with XeSS or FSR 3.1 (also works for FSR2-only games, like The Outer Worlds Spacer's Choice, albeit requires manually providing nvngx_dlss.dll)._

**Key aspects of cscaler:**
- Enables usage of XeSS, FSR2, FSR3, **FSR4**$`^2`$ (_officially, RDNA4 only_) and DLSS in (temporal) upscaler-enabled games
- Allows users to fine-tune their upscaling experience with a wide range of tweaks and enhancements (RCAS & MAS, Output Scaling, DLSS Presets, Ratio & DRS Overrides etc.)
- Since v0.7.0+, added ***experimental DX12*** frame generation support with possible HUDfix solution ([**VFG**](#VFG--hudfix-experimental-hud-ghosting-fix))
- Supports [**Fakenvapi**](#installation) integration - enables Reflex hooking and injecting _Anti-Lag 2_ (RDNA1+ only), _LatencyFlex_ (LFX) or _XeLL_ (Intel only) - _bundled since 0.9_  
- Since v0.7.7, added support for **Nukem's** FSR3-FG mod [**dlssg-to-fsr3**](#installation), only supports games with ***native DLSS-FG*** - _bundled since 0.9_
- Since v0.7.8, added **ASI plugin loading** support (_disabled_ by default (`LoadAsiPlugins=` in INI), loads from customisable folder, default `plugins`)
- New project - [**VPatcher**](https://github.com/CRTYPUBG/VPatcher) - an ASI Plugin for cscaler for enabling DLSS and DLSSG inputs without spoofing in ***supported games***.
- Since v0.7.8, cscaler is now automatically applying certain game patches for a better out-of-the-box experience
- Since v0.9.0, separated FG Inputs and Outputs, added XeFG and FSR4-FG support, as well as bundled Fakenvapi and Nukem's FSR3-FG mod
- For a detailed list of all features, check [Features](Features.md)


> [!IMPORTANT]
> _**Always check the [Wiki Compatibility list](https://github.com/CRTYPUBG/cscaler/wiki) for known game issues and workarounds.**_  
> Also please check the  [***cscaler known issues***](#known-issues) at the end regarding **RTSS** compatibility.  
> A separate [***FSR4 Compatibility list***](https://github.com/CRTYPUBG/cscaler/wiki/FSR4-Compatibility-List) is available for community-sourced tested games.  
> ***[3]** For **not bundled** items, please check [Installation](#installation).*  

> [!NOTE]
> ### Upscaler notes
> <details>
>  <summary><b>Click for [1], [2] </b></summary>  
>  
> **[1]** For **Unreal Engine** games, only UE XeSS -> Opti XeSS/FSR4 work  
>  
> *Regarding **XeSS** inputs, since **Unreal Engine plugin** does not provide depth, replacing in-game XeSS breaks other upscalers (e.g. Redout 2 as a XeSS-only game), but you can still apply RCAS sharpening to XeSS to reduce blurry visuals.* 
>
> *Regarding **FSR inputs**, FSR 3.1 is the first version with a fully standardised, forward-looking API and should be fully supported. Since FSR2 and FSR3 support custom interfaces, game support will depend on the developers' implementation. With Unreal Engine games, you might need [ini tweaks](https://github.com/CRTYPUBG/cscaler/wiki/Unreal-Engine-Tweaks) for FSR inputs.*  
>
> **[2]** *Regarding **FSR4**, please check [FSR4 Compatibility list](https://github.com/CRTYPUBG/cscaler/wiki/FSR4-Compatibility-List) for known supported games and general info.*
> 
> </details>


## Official Discord Server: [cscaler](https://discord.gg/D9KSuuyHzR)

*This project is based on [PotatoOfDoom](https://github.com/PotatoOfDoom)'s excellent [CyberFSR2](https://github.com/PotatoOfDoom/CyberFSR2).*

## How it works?
* cscaler acts as a middleware, it intercepts upscaler calls from the game (_**Inputs**_) and redirects them to the chosen upscaling backend (_**Output**_), allowing user to replace one technology with another one. **Inputs -> cscaler -> Outputs**  
* _Or put more bluntly, **Input** is the upscaler used in game settings, and **Output** the one selected in Opti Overlay._
* _Same goes for FG options which are separated into **FG Source** and **FG Output**._

> [!NOTE]
> * Pressing **`Insert`** should open the cscaler **Overlay** in-game with all of the options (_`ShortcutKey=` can be changed in the INI file, or under **Keybinds** in the overlay_). 
> * Pressing **`Page Up`** shows the performance stats overlay in the top left, and can be cycled between different modes with **`Page Down`** (_keybinds customisable in the overlay_).  
> * If Opti overlay is instantly disappearing after trying Insert a few times, maybe try **`Alt + Insert`** ([reported workaround](https://github.com/CRTYPUBG/cscaler/issues/484) for alternate keyboard layouts).

![inputs_and_outputs](https://github.com/user-attachments/assets/49ba1459-e628-481f-92f2-3a42348c9580)

## Which APIs and Upscalers are Supported?
Currently **cscaler** can be used with DirectX 11, DirectX 12 and Vulkan, but each API has different sets of supported upscalers.  
[**VFG**](#VFG--hudfix-experimental-hud-ghosting-fix) currently **only supports DX12** and is explained in a separate paragraph.

#### For DirectX 12
- XeSS (Default)
- FSR 2.1.2, 2.2.1
- FSR 3.X (and FSR 2.3.X)
- FSR 4.X (via FSR3.X update, _officially RDNA4 only_)
- DLSS

#### For DirectX 11
- FSR 2.2.1 (Default, native DX11)
- FSR 3.1.2 (unofficial port to native DX11)
- DLSS (native DX11)
- XeSS 2.X (native DX11, _Intel ARC only_)
- XeSS, FSR 2.1.2, 2.2.1, FSR 3.X w/Dx12 (_via D3D11on12_)$`^1`$
- FSR 4.X (via FSR 3.X w/Dx12 update, _officially RDNA4 only_)

> [!NOTE]
> <details>
>  <summary><b>Expand for [1]</b></summary>
>
> _**[1]** These implementations use a background DirectX12 device to be able to use DX12-only upscalers. There's a performance penalty up to 10-ish % for this method, but allows many more upscaler options. Also native DX11 implementation of FSR 2.2.1 is a backport from Unity renderer and has its own problems of which some were fixed by cscaler._
> </details>

#### For Vulkan
- FSR 4.X (via FSR 3.X w/Dx12 update, _officially RDNA4 only_)
- FSR2 2.1.2 (Default), 2.2.1
- FSR3 3.1 (and FSR2 2.3.2)
- DLSS
- XeSS 2.x

#### VFG + HUDfix (experimental HUD ghosting fix) 
**VFG** was added with **v0.7** and is **only supported in DX12**. 
It's an **experimental** way of adding FG to games without native Frame Generation, or can also be used as a last case scenario if the native FG is not working properly.  
* Currently supports FSR3-FG (requires HUDfix to avoid HUD ghosting), XeFG and FSR4-FG (ML model deals with the HUD, so may or may not require HUDfix).

For more information on VFG and how to use it, please check the Wiki page - [VFG](https://github.com/CRTYPUBG/cscaler/wiki/VFG).


## Installation
> [!CAUTION]
> _**Warning**: **Do not use this mod with online games.** It may trigger anti-cheat software and cause bans!_

> [!IMPORTANT]
> **For installation steps, please check the [**Wiki**](https://github.com/CRTYPUBG/cscaler/wiki)**  

## Configuration
Please check [this](Config.md) document for configuration parameters and explanations. If your GPU is not an Nvidia one, check [GPU spoofing options](Spoofing.md) *(Will be updated)*

## Known Issues

> [!NOTE]
> **For a list of known issues, please check the [**Wiki**](https://github.com/CRTYPUBG/cscaler/wiki)**.
> 
> Also worth checking the [Compatibility List](https://github.com/CRTYPUBG/cscaler/wiki/Compatibility-List) for possible game issues and their fixes.

## Compilation

### Requirements
* Visual Studio 2022

### Instructions
* Clone this repo with **all of its submodules**.
* Open the cscaler.sln with Visual Studio 2022.
* Build the project

## Credit
This project uses [FreeType](https://gitlab.freedesktop.org/freetype/freetype) licensed under the [FTL](https://gitlab.freedesktop.org/freetype/freetype/-/blob/master/docs/FTL.TXT)
