# List of Reshade shaders working with vkBasalt

I started by wanting to know which Reshade shaders work with vkbasalt.  
Let me define 'work'. If vkmark completed and the screen was not black they are classed as working.  
I tested all the shaders, which can be installed with the reshade application (bar the 'legacy' ones), both with `depthCapture = off` and `depthCapture = on`  
As I wanted them all in one folder I had to rename custom ReShade.fxh's and edit the shaders concerned in a few cases.  
One shader name clashed and was renamed Fubax_Cursor.fx  
vkmark was used to test the shaders.  
`vkmark -p immediate -b :duration=1`  
All shaders were tested using the default settings within each shader.  
The performance figures were just something I thought I might as well note whilst doing this.  
While they may give an indication as to which shaders have more of a hit than others in the real world you probably won't see performance drops like below. For example I use vkBasalt with 6 shaders (LiftGammaGain.fx,Vibrance.fx,Tonemap.fx,Vignette.fx,Curves.fx & LumaSharpen.fx),with RDR2, and see hardly any performance hit at all. About 1-2%.  
The main point to this is just the list of working shaders. I accept my methodology probably sucks :)   

## Easily fixable shaders  

|Shader|Problem|Fix|
|:-----|:-----|:--|
|AdaptiveFog.fx| Blackscreen| link Reshade.fxh to ReShade.fxh|
|Cursor.fx| Crash vkmark| link Textures/cursor.png to Textures/Cursor.png|
|MultiLUT.fx| Crash vkmark| link Textures/MultiLut_Atlas1.png to Textures/MultiLut_atlas1.png|

## Shaders that don't work and why (to a degree!) 
See notes below

|Shader|Problem|Error message or why|
|:-----|:----- |:-------------------|
|ArtisticVignette.fx|Crash vkmark| ?|
|BeforeAfter.fx|Blackscreen| Two techniques|
|CanvasMask.fx|Blackscreen| Two techniques |
|CAS.fx|Blackscreen| error X3004: undeclared identifier or no matching intrinsic overload for 'tex2DgatherR'|
|Checkerboard.fx|Crash vkmark| terminate called after throwing an instance of 'std::bad_alloc'|
|CheckerboardInterlace.fx| Blackscreen| CheckerboardInterlace.fx(175- 14): error X3000: syntax error: unexpected 'identifier'|
|ColorMask.fx|Blackscreen| Two techniques |
|ContrastStretch.fx|Blackscreen| error X3004: undeclared identifier or no matching intrinsic overload for 'tex2Dfetch'|
|Deband.fx|Blackscreen| error X3004: undeclared identifier 'BUFFER_COLOR_BIT_DEPTH' (Can try hardcoding to 8 or 10)|
|DeepFry.fx|Blackscreen| error X3004: undeclared identifier or no matching intrinsic overload for 'tex2Dfetch'|
|DepthAlpha.fx|Crash vkmark| terminate called after throwing an instance of 'std::bad_alloc'|
|FastFourierTransform.fx|Blackscreen| Three techniques|
|FFTCompute.fx|Crash vkmark| FFTCompute.fx(119- 1): error X3000: syntax error: unexpected 'identifier'|
|GaussianBlurCS.fx|Crash vkmark| GaussianBlurCS.fx(61- 1): error X3000: syntax error: unexpected 'identifier'|
|GloomAO.fx|Crash vkmark| terminate called after throwing an instance of 'std::bad_alloc'|
|Histogram.fx|Blackscreen| Two techniques |
|HistogramCompute.fx|Crash vkmark| HistogramCompute.fx(29- 1): error X3000: syntax error: unexpected 'identifier'|
|LiquidLens.fx|Blackscreen| terminated by signal SIGSEGV (Address boundary error)|
|LocalContrastCS.fx|Crash vkmark| LocalContrastCS.fx(67- 1): error X3000: syntax error: unexpected 'identifier'|
|MagicHDR.fx|Blackscreen| terminate called after throwing an instance of 'std::bad_alloc'|
|NeoBloom.fx|Crash vkmark| terminate called after throwing an instance of 'std::bad_alloc'|
|NormalMap.fx|Blackscreen| terminated by signal SIGSEGV (Address boundary error)|
|OpticalFlow.fx|Blackscreen| error X3004: undeclared identifier or no matching intrinsic overload for 'tex2Dfetch'|
|PandaFX.fx|Crash vkmark| Needs a Textures/hd_noise.png (not provided)|
|PD80_01A_RT_Correct_Contrast.fx|Blackscreen| error X3004: undeclared identifier or no matching intrinsic overload for 'tex2Dfetch'|
|PD80_01B_RT_Correct_Color.fx|Blackscreen| error X3004: undeclared identifier or no matching intrinsic overload for 'tex2Dfetch'|
|PD80_06_Luma_Fade.fx|Blackscreen| Two techniques|
|PixelValueDebugger.fx|Blackscreen| error X3004: undeclared identifier or no matching intrinsic overload for 'tex2Dfetch'|
|qUINT_deband.fx| Blackscreen| qUINT_deband.fx(97- 40): error X3004: undeclared identifier 'BUFFER_COLOR_BIT_DEPTH' (Can try hardcoding to 8 or 10)|
|RadiantGI.fx|Crash vkmark| error X3004: undeclared identifier or no matching intrinsic overload for 'tex2Dfetch'|
|ReVeil.fx|Crash vkmark| error X3000: syntax error: unexpected 'identifier'|
|SharpContrast.fx|Crash vkmark| SharpContrast.fx(83- 1): error X3000: syntax error: unexpected 'identifier'|
|Splitscreen.fx|Blackscreen| Two techniques|
|Stats.fx|Blackscreen| Two techniques|
|Template.fx|Crash vkmark| terminated by signal SIGSEGV (Address boundary error)|
|UIDetect.fx|Blackscreen mainly| four techniques|
|UIMaskCreator.fx|Blackscreen| ?|
|UIMask.fx|Blackscreen| Possibly just needs Textures/UIMask.png (not provided) |
|VRS_Map.fx|Crash vkmark| error X3004: undeclared identifier or no matching intrinsic overload for 'tex2Dfetch'|

## Shaders that do work, vkmark scores and percentage hit on the score  
(vkmark scored an average of 10118 run without vkBasalt)  

|Shader|Score Depth off|Perf. Hit %|Score Depth on|Perf. Hit %|
|:-----|:--------------|:---------|:-------------|:---------|
|3DToElse.fx|5170|48.90%|5144|49.16%|
|AdaptiveFog.fx|5858|42.10%|5973|40.97%|
|AdaptiveTint.fx|7827|22.64%|8040|20.54%|
|AdaptiveTonemapper.fx|5982|40.88%|6253|38.20%|
|ArcaneBloom.fx|2944|70.90%|2956|70.78%|
|AreaCopy.fx|8118|19.77%|8086|20.08%|
|ASCII.fx|7436|26.51%|7608|24.81%|
|AspectRatioComposition.fx|8107|19.88%|8101|19.93%|
|AspectRatio.fx|8110|19.85%|8105|19.90%|
|AspectRatioSuite.fx|8097|19.97%|8093|20.01%|
|BilateralComic.fx|6404|36.71%|6369|37.05%|
|BloomingHDR.fx|3748|62.96%|3748|62.96%|
|Border.fx|8142|19.53%|7937|21.56%|
|BulgePinch.fx|7972|21.21%|7878|22.14%|
|CanvasFog.fx|5366|46.97%|5360|47.03%|
|Cartoon.fx|7899|21.93%|7890|22.02%|
|Chromakey.fx|8084|20.10%|7966|21.27%|
|ChromaticAberration.fx|8044|20.50%|8030|20.64%|
|CinematicDOF.fx|2423|76.05%|2485|75.44%|
|Clarity.fx|4633|54.21%|4650|54.04%|
|ColorfulPoster.fx|7992|21.01%|8020|20.74%|
|ColorIsolation2.fx|8025|20.69%|8050|20.44%|
|ColorIsolation.fx|8078|20.16%|8057|20.37%|
|ColorLab.fx|8046|20.48%|8030|20.64%|
|ColorMatrix.fx|8103|19.92%|8085|20.09%|
|Comic.fx|6972|31.09%|6667|34.11%|
|Composition.fx|8095|19.99%|8053|20.41%|
|CRT.fx|6412|36.63%|6395|36.80%|
|CRT_Lottes.fx|6583|34.94%|6570|35.07%|
|CRT_Yee64.fx|7467|26.20%|7443|26.44%|
|CRT_Yeetron.fx|7972|21.21%|7970|21.23%|
|Cursor.fx|8045|20.49%|7972|21.21%|
|Curves.fx|8098|19.96%|8055|20.39%|
|Daltonize.fx|8089|20.05%|8083|20.11%|
|Dehaze.fx|5030|50.29%|4996|50.62%|
|Depth_Cues.fx|5989|40.81%|5984|40.86%|
|DepthHaze.fx|5240|48.21%|5132|49.28%|
|Depth_Tool.fx|5154|49.06%|5013|50.45%|
|Dimension_Plus.fx|6931|31.50%|6710|33.68%|
|DirectionalDepthBlur.fx|3636|64.06%|3638|64.04%|
|DisplayDepth.fx|7964|21.29%|7801|22.90%|
|Dither.fx|7681|24.09%|7684|24.06%|
|DLAA_Plus.fx|3325|67.14%|3329|67.10%|
|DPX.fx|7912|21.80%|7915|21.77%|
|DrawOverlay.fx|7930|21.62%|7801|22.90%|
|Emphasize.fx|8068|20.26%|7791|23.00%|
|EyeAdaption.fx|6250|38.23%|6183|38.89%|
|FakeHDR.fx|7099|29.84%|7038|30.44%|
|FilmGrain.fx|8066|20.28%|7890|22.02%|
|FilmicAnamorphSharpen.fx|7887|22.05%|7900|21.92%|
|FilmicSharpen.fx|7888|22.04%|7901|21.91%|
|Flair.fx|3521|65.20%|3529|65.12%|
|Flashlight.fx|8038|20.56%|7962|21.31%|
|FlexibleCA.fx|8033|20.61%|8045|20.49%|
|Flipbook.fx|7998|20.95%|8001|20.92%|
|Flip.fx|8094|20.00%|8109|19.86%|
|FocalDOF.fx|6784|32.95%|6779|33.00%|
|FogRemoval.fx|3367|66.72%|3368|66.71%|
|FramerateLimiter.fx|6804|32.75%|6958|31.23%|
|FreezeShot.fx|5551|45.14%|5565|45.00%|
|Fubax_Cursor.fx|7861|22.31%|7896|21.96%|
|FXAA.fx|6769|33.10%|6801|32.78%|
|GrainSpread.fx|8015|20.78%|8024|20.70%|
|HexLensFlare.fx|6452|36.23%|6534|35.42%|
|HotsamplingHelper.fx|8054|20.40%|8093|20.01%|
|Image.fx|7361|27.25%|7314|27.71%|
|Interlaced.fx|7300|27.85%|7297|27.88%|
|Layer.fx|7887|22.05%|7856|22.36%|
|Letterbox.fx|8139|19.56%|7860|22.32%|
|Levels.fx|8099|19.95%|7440|26.47%|
|LiftGammaGain.fx|8088|20.06%|7583|25.05%|
|Limbo_Mod.fx|5704|43.63%|5559|45.06%|
|LumaSharpen.fx|7898|21.94%|7744|23.46%|
|LUT.fx|7881|22.11%|7800|22.91%|
|LUTTools.fx|8053|20.41%|8101|19.93%|
|MagicBorder.fx|8005|20.88%|7952|21.41%|
|MBMB.fx|6854|32.26%|6838|32.42%|
|MeshEdges.fx|7607|24.82%|7340|27.46%|
|MinimalColorGrading.fx|8082|20.12%|8060|20.34%|
|Monochrome.fx|8099|19.95%|7727|23.63%|
|Mouse.fx|8325|17.72%|8324|17.73%|
|MultiFX.fx|8099|19.95%|8103|19.92%|
|MultiLUT.fx|7904|21.88%|7899|21.93%|
|MultiTonePoster.fx|7825|22.66%|7861|22.31%|
|NFAA.fx|6835|32.45%|6991|30.91%|
|Nostalgia.fx|7711|23.79%|7870|22.22%|
|Oilify.fx|1124|88.89%|1357|86.59%|
|Overlay.fx|7777|23.14%|7844|22.47%|
|PD80_01_Color_Gamut.fx|7985|21.08%|7984|21.09%|
|PD80_02_Bloom.fx|3815|62.29%|3833|62.12%|
|PD80_02_Bonus_LUT_pack.fx|7537|25.51%|7589|25.00%|
|PD80_02_Cinetools_LUT.fx|7459|26.28%|7589|25.00%|
|PD80_02_LUT_Creator.fx|7994|20.99%|8007|20.86%|
|PD80_03_Color_Space_Curves.fx|7834|22.57%|7707|23.83%|
|PD80_03_Curved_Levels.fx|7492|25.95%|7894|21.98%|
|PD80_03_Filmic_Adaptation.fx|6018|40.52%|6084|39.87%|
|PD80_03_Levels.fx|7863|22.29%|7917|21.75%|
|PD80_03_Shadows_Midtones_Highlights.fx|7949|21.44%|7963|21.30%|
|PD80_04_BlacknWhite.fx|7659|24.30%|7675|24.15%|
|PD80_04_Color_Balance.fx|8095|19.99%|8109|19.86%|
|PD80_04_Color_Gradients.fx|5968|41.02%|6047|40.24%|
|PD80_04_Color_Isolation.fx|7805|22.86%|8073|20.21%|
|PD80_04_Color_Temperature.fx|8010|20.83%|8051|20.43%|
|PD80_04_Contrast_Brightness_Saturation.fx|7927|21.65%|7975|21.18%|
|PD80_04_Magical_Rectangle.fx|6831|32.49%|6738|33.41%|
|PD80_04_Saturation_Limit.fx|8072|20.22%|8083|20.11%|
|PD80_04_Selective_Color.fx|7915|21.77%|7926|21.66%|
|PD80_04_Selective_Color_v2.fx|5908|41.61%|5911|41.58%|
|PD80_04_Technicolor.fx|8078|20.16%|8098|19.96%|
|PD80_05_Sharpening.fx|6314|37.60%|6424|36.51%|
|PD80_06_Chromatic_Aberration.fx|6471|36.04%|6708|33.70%|
|PD80_06_Depth_Slicer.fx|8022|20.72%|7987|21.06%|
|PD80_06_Film_Grain.fx|5640|44.26%|5740|43.27%|
|PD80_06_Posterize_Pixelate.fx|6288|37.85%|6341|37.33%|
|PerfectPerspective2.fx|7777|23.14%|7789|23.02%|
|PerfectPerspective.fx|8005|20.88%|8014|20.79%|
|PiecewiseFilmicTonemap.fx|7980|21.13%|7996|20.97%|
|Polynomial_Barrel_Distortion_for_HMDs.fx|6369|37.05%|6532|35.44%|
|Pong.fx|7012|30.70%|7149|29.34%|
|Prism.fx|7639|24.50%|7676|24.14%|
|qUINT_bloom.fx|4653|54.01%|4746|53.09%|
|qUINT_dof.fx|3595|64.47%|3947|60.99%|
|qUINT_lightroom.fx|6342|37.32%|6316|37.58%|
|qUINT_mxao.fx|3630|64.12%|3212|68.25%|
|qUINT_sharp.fx|7012|30.70%|6971|31.10%|
|qUINT_ssr.fx|4509|55.44%|4664|53.90%|
|RemoveTint.fx|5257|48.04%|5259|48.02%|
|RetroFog.fx|7665|24.24%|7671|24.18%|
|RetroTint.fx|8069|20.25%|8067|20.27%|
|SCurve.fx|8056|20.38%|8096|19.98%|
|Sepia.fx|8070|20.24%|8110|19.85%|
|SimpleGrain.fx|8027|20.67%|8064|20.30%|
|Sketch.fx|6541|35.35%|6577|35.00%|
|SlitScan.fx|7817|22.74%|7717|23.73%|
|SMAA.fx|5572|44.93%|5789|42.79%|
|Smart_Sharp.fx|6326|37.48%|6344|37.30%|
|SnowScape.fx|2146|78.79%|2110|79.15%|
|StageDepthPlus.fx|7878|22.14%|7914|21.78%|
|StageDepthPlus_WithDepthBufferMod.fx|7892|22.00%|7721|23.69%|
|SunsetFilter.fx|8062|20.32%|8062|20.32%|
|SuperDepth3D.fx|4210|58.39%|4178|58.71%|
|SuperDepth3D_VR+.fx|3214|68.23%|3203|68.34%|
|SuperDepth3D_WoWvx.fx|4787|52.69%|4787|52.69%|
|Swirl.fx|7883|22.09%|7848|22.44%|
|Technicolor2.fx|7922|21.70%|8099|19.95%|
|Technicolor.fx|7798|22.93%|8098|19.96%|
|Temporal_AA.fx|5569|44.96%|5558|45.07%|
|TiltShift.fx|5574|44.91%|5600|44.65%|
|TinyPlanet.fx|7132|29.51%|7252|28.33%|
|Tonemap.fx|8057|20.37%|8058|20.36%|
|TrackingRays.fx|5618|44.48%|5624|44.42%|
|Trails.fx|6224|38.49%|6235|38.38%|
|UnrealLens.fx|6459|36.16%|6465|36.10%|
|Unsharp.fx|3706|63.37%|3707|63.36%|
|Vibrance.fx|8065|20.29%|7850|22.42%|
|Vignette.fx|8099|19.95%|8046|20.48%|
|VirtualNose.fx|5207|48.54%|5171|48.89%|
|VirtualResolution.fx|7412|26.74%|7371|27.15%|
|Wave.fx|7971|21.22%|7833|22.58%|
|WhitepointFixer.fx|8094|20.00%|7991|21.02%|
|ZigZag.fx|7921|21.71%|7835|22.56%|

### Notes
Where it is multiple techniques preventing a shader from working it may be possible to delete uneeded techniques, create seperate versions of the shaders with diferent names etc.  
I couldn't find an instance where `depthCapture = on` made a shader work when a didn't with `depthCapture = off`.  
I did mean to turn off vkBasalts logging but forgot until to late,debug logging on in all test shown, so there you have it.  
