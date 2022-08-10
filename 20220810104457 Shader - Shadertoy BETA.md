---
title: Shader - Shadertoy BETA
tags: android blog rtrvl
author: retr0ville
source: https://www.shadertoy.com/view/lsl3RH
---
Shader - Shadertoy BETA  
Shadertoy  
Browse New Sign In  
No WebGL available :(  
0.00 00.0 fps 0 x 0  
Views: 0 , Tags:  
Created by in  

Shader Inputs  

```
uniform vec3      iResolution;           // viewport resolution (in pixels)
uniform float     iTime;                 // shader playback time (in seconds)
uniform float     iTimeDelta;            // render time (in seconds)
uniform int       iFrame;                // shader playback frame
uniform float     iChannelTime[4];       // channel playback time (in seconds)
uniform vec3      iChannelResolution[4]; // channel resolution (in pixels)
uniform vec4      iMouse;                // mouse pixel coords. xy: current (if MLB down), zw: click
uniform samplerXX iChannel0..3;          // input channel. XX = 2D/Cube
uniform vec4      iDate;                 // (year, month, day, time in seconds)
uniform float     iSampleRate;           // sound sample rate (i.e., 44100)
```

Compiled in 0.0/0.0 secs  
0 chars  
XS S M L XL XXL  

Filter nearestlinearmipmap   
Wrap clamprepeat   
VFlip  
iChannel0  

Filter nearestlinearmipmap   
Wrap clamprepeat   
VFlip  
iChannel1  

Filter nearestlinearmipmap   
Wrap clamprepeat   
VFlip  
iChannel2  

Filter nearestlinearmipmap   
Wrap clamprepeat   
VFlip  
iChannel3  
Comments ( 0)   
Sign in to post a comment.   

Community Forums

* Official Events
* [In Facebook (english)](https://www.facebook.com/groups/147749602472741)
* [In Facebook (korean)](https://www.facebook.com/groups/1339783682699494)
* [In Discord](https://discord.gg/XtmMN6E) ([direct link](https://discordapp.com/channels/578696555612209173/579531723348639754))  
Feedback and Support

* [Facebook](https://www.facebook.com/Shadertoy)
* [Twitter](https://twitter.com/shadertoy)
* [Patreon](https://www.patreon.com/shadertoy)
* [Roadmap](https://trello.com/b/5hM0CjId)  
Shadertoy

* Store
* Documentation
* Terms \& Privacy
* About  
Apps and Plugins

* [Official iPhone App](https://itunes.apple.com/us/app/shadertoy/id717961814) by Reinder
* [Screensaver](https://steamcommunity.com/sharedfiles/filedetails/?id=1726697188) by Kosro
* [Shadertoy plugin](https://chrome.google.com/webstore/detail/shadertoy-unofficial-plug/ohicbclhdmkhoabobgppffepcopomhgl) by Patu  
Tutorials

* [Shader coding intro](https://www.youtube.com/watch?v=0ifChJ0nJfM) by iq
* [Shadertoy Unofficial](https://shadertoyunofficial.wordpress.com/) by FabriceNeyret2  
We use cookies to give you the best experience on our website. If you continue using Shadertoy, we'll assume that you are happy to receive all cookies on this website. For more information, please review our Terms \& Privacy.  
Accept  
Select input for iChannel  
* Misc
* Textures
* Cubemaps
* Volumes
* Videos
* Music

|-------------------------------------|-------------------------------------|-------------------------------------|
| |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | |
| |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | |
| |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | |

<br />

<br />

|-------------------------------------|-------------------------------------|-------------------------------------|
| |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | |
| |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | |
| |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | |

<br />

<br />

|-------------------------------------|-------------------------------------|-------------------------------------|
| |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | |
| |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | |
| |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | |

<br />

<br />

|-------------------------------------|-------------------------------------|-------------------------------------|
| |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | |
| |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | |
| |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | |

<br />

<br />

|-------------------------------------|-------------------------------------|-------------------------------------|
| |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | |
| |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | |
| |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | |

<br />

<br />

|-------------------------------------|-------------------------------------|-------------------------------------|
| |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | |
| |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | |
| |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | | |---|-----------| |   | by <br /> | |

<br />

<br />

GLSL Help  
This help only covers the parts of GLSL ES that are relevant for Shadertoy. For the complete specification please have a look at [GLSL ES specification](https://www.khronos.org/registry/OpenGL/specs/es/3.0/GLSL_ES_Specification_3.00.pdf)   

Language:
---------

* **Version:** WebGL 2.0
* **Arithmetic:** ( ) + - ! \* / %
* **Logical/Relatonal:** \~ \< \> \<= \>= == != \&\& \|\|
* **Bit Operators:** \& \^ \| \<\< \>\>
* **Comments:** // /\* \*/
* **Types:** void bool int uint float vec2 vec3 vec4 bvec2 bvec3 bvec4 ivec2 ivec3 ivec4 uvec2 uvec3 uvec4 mat2 mat3 mat4 mat?x? sampler2D, sampler3D, samplerCube
* **Format:** float a = 1.0; int b = 1; uint i = 1U; int i = 0x1;
* **Function Parameter Qualifiers:** \[none\], in, out, inout
* **Global Variable Qualifiers:** const
* **Vector Components:** .xyzw .rgba .stpq
* **Flow Control:** if else for return break continue switch/case
* **Output:** vec4 fragColor
* **Input:** vec2 fragCoord
* **Preprocessor:** # #define #undef #if #ifdef #ifndef #else #elif #endif #error #pragma #line

<br />

Built-in Functions:
-------------------

|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| * type radians (type degrees) * type degrees (type radians) * type sin (type angle) * type cos (type angle) * type tan (type angle) * type asin (type x) * type acos (type x) * type atan (type y, type x) * type atan (type y_over_x) * type sinh (type x) * type cosh (type x) * type tanh (type x) * type asinh (type x) * type acosh (type x) * type atanh (type x) <!-- --> * type pow (type x, type y) * type exp (type x) * type log (type x) * type exp2 (type x) * type log2 (type x) * type sqrt (type x) * type inversesqrt (type x) <!-- --> * type abs (type x) * type sign (type x) * type floor (type x) * type ceil (type x) * type trunc (type x) * type fract (type x) * type mod (type x, float y) * type modf (type x, out type i) * type min (type x, type y) * type max (type x, type y) * type clamp (type x, type minV, type maxV) * type mix (type x, type y, type a) * type step (type edge, type x) * type smoothstep (type a, type b, type x) <!-- --> * float length (type x) * float distance (type p0, type p1) * float dot (type x, type y) * vec3 cross (vec3 x, vec3 y) * type normalize (type x) * type faceforward (type N, type I, type Nref) * type reflect (type I, type N) * type refract (type I, type N,float eta) * float determinant(mat? m) * mat?x? outerProduct(vec? c, vec? r) * type matrixCompMult (type x, type y) * type inverse (type inverse) * type transpose (type inverse) | * vec4 texture( sampler? , vec? coord \[, float bias\]) * vec4 textureLod( sampler, vec? coord, float lod) * vec4 textureLodOffset( sampler? sampler, vec? coord, float lod, ivec? offset) * vec4 textureGrad( sampler? , vec? coord, vec2 dPdx, vec2 dPdy) * vec4 textureGradOffset sampler? , vec? coord, vec? dPdx, vec? dPdy, vec? offset) * vec4 textureProj( sampler? , vec? coord \[, float bias\]) * vec4 textureProjLod( sampler? , vec? coord, float lod) * vec4 textureProjLodOffset( sampler? , vec? coord, float lod, vec? offset) * vec4 textureProjGrad( sampler? , vec? coord, vec2 dPdx, vec2 dPdy) * vec4 texelFetch( sampler? , ivec? coord, int lod) * vec4 texelFetchOffset( sampler?, ivec? coord, int lod, ivec? offset ) * ivec? textureSize( sampler? , int lod) <!-- --> * type dFdx (type x) * type dFdy (type x) * type fwidth (type p) <!-- --> * type isnan (type x) * type isinf (type x) * float intBitsToFloat (int v) * uint uintBitsToFloat (uint v) * int floatBitsToInt (float v) * uint floatBitsToUint (float v) * uint packSnorm2x16 (vec2 v) * uint packUnorm2x16 (vec2 v) * vec2 unpackSnorm2x16 (uint p) * vec2 unpackUnorm2x16 (uint p) <!-- --> * bvec lessThan (type x, type y) * bvec lessThanEqual (type x, type y) * bvec greaterThan (type x, type y) * bvec greaterThanEqual (type x, type y) * bvec equal (type x, type y) * bvec notEqual (type x, type y) * bool any (bvec x) * bool all (bvec x) * bvec not (bvec x) |

<br />

How-to
------

* **Use structs:** struct myDataType { float occlusion; vec3 color; }; myDataType myData = myDataType(0.7, vec3(1.0, 2.0, 3.0));
* **Initialize arrays:**float\[\] x = float\[\] (0.0, 0.1, 0.2, 0.3, 0.4, 0.5, 0.6);
* **Do conversions:** int a = 3; float b = float(a);
* **Do component swizzling:** vec4 a = vec4(1.0,2.0,3.0,4.0); vec4 b = a.zyyw;
* **Access matrix components:** mat4 m; m\[1\] = vec4(2.0); m\[0\]\[0\] = 1.0; m\[2\]\[3\] = 2.0;

<br />

Be careful!
-----------

* **the *f* suffix for floating pont numbers:** 1.0f is illegal in GLSL. You must use 1.0
* **saturate():** saturate(x) doesn't exist in GLSL. Use clamp(x,0.0,1.0) instead
* **pow/sqrt:** please don't feed sqrt() and pow() with negative numbers. Add an abs() or max(0.0,) to the argument
* **mod:** please don't do mod(x,0.0). This is undefined in some platforms
* **variables:** initialize your variables! Don't assume they'll be set to zero by default
* **functions:** don't call your functions the same as some of your variables

<br />

Shadertoy Inputs
----------------

|---------------|-----------------------------|--------------------|----------------------------------------------------------------|
| **vec3**      | **iResolution**             | image/buffer       | The viewport resolution (z is pixel aspect ratio, usually 1.0) |
| **float**     | **iTime**                   | image/sound/buffer | Current time in seconds                                        |
| **float**     | **iTimeDelta**              | image/buffer       | Time it takes to render a frame, in seconds                    |
| **int**       | **iFrame**                  | image/buffer       | Current frame                                                  |
| **float**     | **iFrameRate**              | image/buffer       | Number of frames rendered per second                           |
| **float**     | **iChannelTime\[4\]**       | image/buffer       | Time for channel (if video or sound), in seconds               |
| **vec3**      | **iChannelResolution\[4\]** | image/buffer/sound | Input texture resolution for each channel                      |
| **vec4**      | **iMouse**                  | image/buffer       | xy = current pixel coords (if LMB is down). zw = click pixel   |
| **sampler2D** | **iChannel{i}**             | image/buffer/sound | Sampler for input textures i                                   |
| **vec4**      | **iDate**                   | image/buffer/sound | Year, month, day, time in seconds in .xyzw                     |
| **float**     | **iSampleRate**             | image/buffer/sound | The sound sample rate (typically 44100)                        |

<br />

Shadertoy Outputs
-----------------

Image shaders: fragColor is used as output channel. It is not, for now, mandatory but recommended to leave the alpha channel to 1.0.   

Sound shaders: the mainSound() function returns a vec2 containing the left and right (stereo) sound channel wave data.   

<br />

Share your shader  
Yes  
No  
BBCode Help  

Codes:
------

You can format your comments by using standard [BBCode](http://en.wikipedia.org/wiki/BBCode). The following tags are implemented in Shadertoy:   

|--------|---|------------------------------------------------------------------------|
| Bold   |   | **\[b\]** this text goes in bold**\[/b\]**                             |
| Italic |   | **\[i\]** this text goes in italic**\[/i\]**                           |
| Images |   | **\[img\]** url_to_image**\[/img\]**                                   |
| Url    |   | **\[url\]** http://www.shadertoy.com**\[/url\]**                       |
| Url    |   | **\[url=** http://www.shadertoy.com**\]** Shadertoy**\[/url\]**        |
| Code   |   | **\[code\]** fixed-width text**\[/code\]**                             |
| Video  |   | **\[video\]** http://www.youtube.com/watch?v=0ifChJ0nJfM**\[/video\]** |

<br />

Emoticons:
----------

|------------------|---|---|
| :)               |   |   |
| :(               |   |   |
| :D               |   |   |
| :love:           |   |   |
| :octopus:        |   |   |
| :octopusballoon: |   |   |

<br />

Symbols:
--------

|-----------|---|---|
| :alpha:   |   | α |
| :beta:    |   | β |
| :delta:   |   | Δ |
| :epsilon: |   | ε |
| :nabla:   |   | ∇ |
| :square:  |   | ² |
| :cube:    |   | ³ |
| :limit:   |   | ≐ |

<br />

Share your shader  
**Direct link:**   

Just copy and paste this URL below:   

**Embed:**   

\<iframe width="640" height="360" frameborder="0" src="https://www.shadertoy.com/embed/lsl3RH?gui=true\&t=10\&paused=true\&muted=false" allowfullscreen\>\</iframe\>  
Add to playlist  
