---
title: TOTK-Mods-collection
date: 2023-05-20T12:14:54+08:00
draft: False
featuredImage: https://wallpaperhub.app/api/v1/get/12155/0/1080p
featuredImagePreview: https://wallpaperhub.app/api/v1/get/12155/0/1080p
---

# [HolographicWings/TOTK-Mods-collection](https://github.com/HolographicWings/TOTK-Mods-collection)

# TOTK-Mods-collection

## :exclamation:**WARNING : Read the compatible version of the game on the prefix of the mods name.

</br>

<div align="center">
  
### [Download latest release](https://github.com/HolographicWings/TOTK-Mods-collection/releases)
</div>

</br>Mod description & usage :

- **FPS** : Changes the game's framerate lock  
If you get under the framerate lock defined by the mod, the game will be in slow motion.  
Vice versa if you get over the defined framerate lock.  
Cinematics will be sped up when you go over 30FPS.  
We recommend the 30fps version as the 60fps version is still a work in progress, 15 and 20 FPS being experimental and potentially useless.  
*Why should I use the 30fps mod ?* : In vanilla, the game seems to lock to 25 or 20 fps when you hit 29fps (This remains to be proven).  
</br>

- **Dynamic FPS** : Matches the game clock to your framerate and fixes slow motion when under the framerate lock, works well when coupled with any of the FPS mods above.  
This allows using it alongside the 30FPS mod and to uncheck the "Limit Speed Percent" in General settings as well as setting "VSync Mode" to OFF in Graphics settings (yuzu).  
This way, going over the framerate lock defined by the FPS mod will not 'speed up' your game.  
You can toggle the "Limit Speed Percent" with the "Ctrl + U" shortkey on yuzu.  
When you get a cinematic, enable back the "Limit Speed Percent" to avoid faster cutscenes.  
**BEWARE !** When you use Dynamic FPS mod under 15 FPS, the physics will break ! (Maybe fixed since v1.4, must check).  
**BEWARE !** Incompatible with FPS++.  
</br>

- **FPS++** : An edited version of the Dynamic FPS mod by somerandompeople, fix cinematics above 30fps, increase FPS cap to 60, so 60FPS is not required, need testing and more documentation.
Do not increase Performances.  
**BEWARE !** Incompatible with Dynamic FPS.  
</br>

- Fix - **Cutscene Fix**: Sets the framerate lock to 30 FPS automatically during FMV cutscenes.  
You must have the Yuzu framerate lock enabled for this to work, and it needs to be paired with the FPS "60fps V3.7.2" mod.
</br>

- Fix - **Over 30FPS Blackscreen Fix**: Fix blackscreen menu bug when playing above 30fps.  
:exclamation:Overwrites "Common.Product.110.Nin_NX_NVN.blarc", don't install two mods overwriting the same file.  
This mod is present in the Xbox UI and Playstation UI mods, and should be disabled if using either of those, to avoid issues.  
</br>


- Graphics - **Disable Internal FSR Downscaling** : This mod disables the game's FSR, Yuzu has its own FSR in the "Window Adapting Filter" in Graphics settings.  
FSR is an optimisation method that reduces the game's internal resolution, and then upscales it using an algorithm (similar to DLSS but without advanced AI).  
FSR increases GPU performance, at the cost of some details and potential graphical artifacts on small geometry like leaves or grass.
</br>

- Graphics - **Disable Internal FSR Sharpening Shader** : This mod disables the sharpening effect of post processed FSR Downscaling internally.  
GPU Performance cost is extremely low so use it will not improve it, but could do an ugly render if you use it without the FSR Downscaling.  
**BEWARE !** It seems that this mod could be responsible for crashes on Ryujinx.  
</br>

- Graphics - **Disable Internal FXAA** : Disable internal FXAA and change "Anti-Aliasing Method" to "None" in order to increase GPU performance (?).
FXAA smoothes certain edges to avoid aliasing (jagged edges) and costs very little GPU performance.  
Yuzu has its own FXAA in the "Anti-Aliasing Method" in Graphics settings, however, it has color banding issues currently, so we recommend SMAA, which currently is a better implementation of anti-aliasing, but uses a bit more GPU performance.  
:exclamation:Overwrites "Bootup.Nin_NX_NVN.pack.zs", don't install two mods overwriting the same file.  
</br>

- Graphics - **Disable Dynamic resolution** when low FPS : Prevents the resolution being downscaled when your framerate is low.
</br>

- Graphics - **LOD Patch** when low FPS : Prevents the LOD decreasing when your framerate is low.  
LOD (Level Of Detail) displays higher quality models when you are close to them, and lower quality models when they are further away.  
By default, when your framerate is low, the game lowers the LOD to increase GPU performance.  
Reported to fix some graphical issues with LOD, but would like image evidence.  
</br>

- Graphics - **Disable Targeting DOF** Disables the DOF blurring effect when targeting.  
DOF (Depth-of-Field is an effect that blur the background when an object is focused by the camera.  
</br>

- Graphics - **Shadows** : changes the resolution of shadows. 
256 and 512 would increase GPU performance a lot.   
1024 being vanilla resolution, it is useless by default, but it can fix some graphical issues on certain setups.

  <div>
    <a href="https://imgsli.com/MTc5MTM1">
      Shadow stuttering issue took by Lux using a Radeon RX 580 8Gb - with & without Shadows x512
      <img src="https://imgsli.com/i/4f323aa4-343b-48b8-8744-e2126e89a011.jpg">
    </a>
    <a href="https://imgsli.com/MTc5MTYx">
      Gloom issue took by Red_BY using a RTX 2080 at 3x render scale - with & without Shadows x1024
      <img src="https://imgsli.com/i/7a0a0a8a-9ce2-4968-bcce-8d00741c70ed.jpg">
    </a>
  </div>
</br>

- Graphics - **Anisotropic Filtering fix** : Fixes Anisotropic Filtering issues ( black line artifacts on textures viewed at oblique angles). Set Anisotropic Filtering to 16 in Yuzu advanced graphics settings.  
[Difference Off/On](https://imgsli.com/MTc5MzQ0)
</br>

- **Resolution** : Changes internal render resolution, Vanilla is 1600x900 when the switch is docked.  
1080p (1920x1080) can only be scaled in 'doubles', or it will break Ambient Occlusion (AO) but increases GPU performance, which is useful for Reshade MXAO.  
Ambient occlusion is a shading and rendering technique used to calculate how exposed each point in a scene is to ambient lighting.  
For example, the interior of a tube is typically more occluded (and hence darker) than the exposed outer surfaces, and becomes darker the deeper inside the tube one goes. It has a GPU performance cost.  
1008p increase resolution to 1792x1008 without breaking Ambiant Occlusion
1026p increase resolution to 1836x1026 without breaking Ambiant Occlusion
:exclamation:Overwrites "Bootup.Nin_NX_NVN.pack.zs", don't install two mods overwriting the same file.  
360p, 540p and 720p require to change the "Resolution" scaling in Yuzu graphics settings (This setting is just called 'resolution'), but they look a bit blurry.  
  - 540p and x2 = 1080p
  - 540p and x4 = 4K
  - 540p and x8 = 8K
  - 720p and x2 = 1440p
  - 720p and x3 = 4K
  - 720p and x6 = 8K
To experience the best quality, we advise you to use the double of your monitor's resolution.  
You can use them with x1 Resolution scale to increase GPU performance.
</br>

- **Ratio** : Experimental - change the aspect ratio from 16:9.
  - You have to change "Aspect Ratio" in Graphics Yuzu settings to 21:9, 16:10 or "Stretch to Window" if the desired ratio doesn't exist.  
  - Fixes the 3D scene render, but will stretch the HUD.
</br>

- **Combos** : They are all-in-one mods, don't combine then with unspecified mods, if you don't know what you are doing.
  - **30/60fps + Dynamic FPS** are a simple Combo of these two mods, into one.
  - **Light pack and Unlimited FPS** : Pack made by HolographicWings, combine Dynamic FPS, 1008p and Disable FSR, it's a minimal pack for a clean experience.  
You can use it with any Graphics other pack, ratio and cheats but it's not recommended.  
In order to play above 30 FPS, press Ctrl + U in game to unlock your framerate, like that you can play at 60, or more, with normal game speed.  
Don't forget to press Ctrl + U again, to lock back your framerate to 30fps, when you get a cutscene.
  - Lazy Pack are made by Hover and merge several useful mods.  
:exclamation:The versions without "UI Mod compatible" in their name Overwrites "Common.Product.110.Nin_NX_NVN.blarc.zs", don't install two mods overwriting the same file.  
</br>


<h4>"Lazy Packs"</h4>
<b>A patch containing over a dozen fixes and mods, with the intent of "just making it work like its supposed to".</b><br>
"Lazy packs" are customized according to resolution, framerate, and UI mod compatibility.
UI compatibility means that the patch is compatible with mods such as the Xbox UI mod below.
Otherwise, blackscreenfix is enabled in the non-compatible versions, for use with normal Nintendo UI.
Using an non-compatible version, along with a UI mod, will result in the UI mod largely not functioning, or not at all.
Please see below for details on how to use, and below that, the exact contents of the patch, and credits to the developers of them.
<br><br>

<details>
<summary> Click to view how to use the lazy pack</summary>
<a href="https://github.com/HolographicWings/TOTK-Mods-collection/tree/main/Guide">Follow this guide to configure Yuzu correctly for Tears of the Kingdom.</a><br>
Install Tears of the Kingdom Patch 1.1.0.<br>
Decide on a framerate. 30 or 60?<br>
Decide on a resolution. 720p, 1080, 1440p, 4K or 8K?<br>
Decide if you want to use the Nintendo controller UI, or a UI mod, such as the Xbox and Playstation mods linked above.<br>
<br>

Take this pack as an example:
1.1.0 - Lazy Pack - <b>60 FPS</b> - <b>720P 1X</b> - <b>1440P 2X</b> - <b>4K 3X</b> - <b>8K 6X</b> - scaling - <b>UI Mod compatible</b>
- This patch features 60 FPS.
- It scales between 720p, 1440p, 4K and 8K, depending on what resolution scaling you choose in Yuzu's graphics settings, as shown in picture 7 in the guide below, for reference.
- And it features compatibility with UI controller mods, such as the Xbox or Playstation mods linked above.

If you were to decide to target <b>30 FPS</b>, <b>1080p</b>, and you would like the <b>Steam Deck UI</b>, you should choose:
1.1.0 - Lazy Pack - <b>30 FPS</b> - <b>1080P 1X scaling</b> - <b>UI Mod compatible</b>

And, if you were to decide to play on a beefy <b>1080p</b> PC at <b>60 FPS</b>, using your Switch Pro controller, and you would like the <b>Normal, Nintendo controller UI</b>, you should choose:
1.1.0 - Lazy Pack - <b>60 FPS</b> - <b>1080P 1X scaling</b>

The non-compatible versions contain Blackscreen-fix, which is incompatible with UI mods.
</details>

<details>
<summary>Click to view the patches included in the lazy pack </summary>

// Credit: @Wollnashorn<br>
// Force bilinear terrain samplers to be trilinear<br>
// Set mipmap filter to nearest on shadow map sampler<br>

// Credit: @Marethyu<br>
// Blackscreen-fix<br>

// Credit: @ChucksFeedAndSeed<br>
// Disable Dynamic Resolution<br>
// Disable FSR sharpening filter<br>
// Shadow Resolution set to 1024<br>
// FXAA disabled<br>
// LOD fix<br>

// Credit: @Patchanon<br>
// Disable FSR up/downscaling<br>
// Disable LOD reduction when framerate dips<br>
// 1080p with broken ambient occlusion above 1x scaling<br>

// Credit: @somerandompeople<br>
// SOURCED FROM https://gbatemp.net/download/loz-tears-of-the-kingdom-20fps-30fps-60fps-patch.37996/ <br>
// 30/60 FPS++<br>

// Credit: @ChanseyIsTheBest<br>
// Docked 720p<br>
</details><br>
<br> <br>

- Cheats :
  - 10x Durability overwrites all Weapons, Bows, Shields, don't install two mods overwriting the same file.
  - The Movement Speed cheats breaks the game time (time will be wrong when saving)
  - Stamina cheat doesn't seem to work.
  - Infinite amiibo usage is pointless since yuzu has a similar feature, go in Yuzu settings → Controls → Advanced and check "Use random Amiibo ID".
  - Beware, all cheats can cause unwanted side effects.

</br>
</br>The main TOTK performance issue comes from the CPU and not the GPU, but unfortunately we don't have an easy way of increasing CPU performance.  
</br>
</br>
</br>Other good mods :

- [Xbox UI + Blackscreenfix](https://gamebanana.com/mods/443354) by Alerion921

- [Playstation UI + Blackscreenfix](https://gamebanana.com/mods/443201) by Alerion921

- [Steam Deck UI](https://gamebanana.com/mods/443702) by Fayaz

- [Amiibo Anti-RNG](https://gamebanana.com/mods/443894) by JordanBTucker

- [Updated 1.1.1 Cheat Codes](https://github.com/bad1dea/NXCheats/tree/main/The%20Legend%20of%20Zelda%20Tears%20of%20the%20Kingdom/0100F2C0115B6000%20for%20Yuzu) by bad1dea


</br>Useful links :

- [Save Editor](https://www.marcrobledo.com/savegame-editors/zelda-totk/) by Marc Robledo
</br>

> Thanks to [ChucksFeedAndSeed](https://www.reddit.com/user/ChucksFeedAndSeed/) for the *majority* of the mods in this collection.

</br>Copyright and source of mods :

- [20/30 and 60 fps v3](https://gbatemp.net/download/loz-tears-of-the-kingdom-20fps-30fps-60fps-patch.37996/) : Authors are "ChucksFeedAndSeed, patchanon and somerandompeople"

- [DynamicFPS v1.31 & 1.4](https://www.reddit.com/r/NewYuzuPiracy/comments/13fjv8r/totk_dynamic_fps_mod_beta_has_some_issues/) : ChucksFeedAndSeed

- [FPS++](https://www.reddit.com/r/NewYuzuPiracy/comments/13fjv8r/totk_dynamic_fps_mod_beta_has_some_issues/) : somerandompeople

- [1008p resolution](https://www.reddit.com/r/NewYuzuPiracy/comments/13deav1/comment/jjk9m60/) : ChucksFeedAndSeed

- [Combo - VisualFixes](https://gbatemp.net/download/loz-tears-of-the-kingdom-20fps-30fps-60fps-patch.37996/) : Authors are "ChucksFeedAndSeed, patchanon and somerandompeople"

- All Graphic pactches : Authors are "ChucksFeedAndSeed, patchanon and somerandompeople", theses patches are split from the VisualFixes, FSR Disabler is especially from patchanon

- [Aspect Ratio](https://gamebanana.com/mods/443462) : From Fayaz

- [Graphics - Anisotropic filtering fix](https://github.com/Wollnashorn/switch-mods/tree/master/0100F2C0115B6000) : @Wollnashorn

- [FPS - Cutscene-fix] : theboy181

- [Graphic - Disable Targeting DOF] : theboy181

- [Fix - Over 30FPS Blackscreen Fix](https://www.reddit.com/r/NewYuzuPiracy/comments/13hq70a/60_fps_mod_black_screen_fix_not_thoroughly_tested/) : by MarethyuX

- [Cheat - Durability (10x)] : SweetMini

- [Graphics - Disable Internal FXAA] : Zeikken

- [Resolution - 1008p and 1026p] : Zeikken

- Others : A real mystery. We gather mods found on the yuzu reddit and discord, if you are the owner of one of them, please contact us, so we can give you the credit that you deserve!
