### Base Color
- Texture Sample
### Metallic [0,1]
- A scalar value that defines whether a surface behaves like a metal or a non-metal (dielectric) in terms of light reflection.
### Specular [0,1]
- A scalar value that controls the intensity of specular reflection on a non-metallic surface.
### Roughness [0,1]
- A scalar value that defines how rough or smooth a surface is, determining the spread and intensity of specular highlights.
### Normal
- **Modify the surface normal direction to affect lighting and shadows**, simulating bumps and grooves **without increasing geometry complexity**
- Texture Sample (NRM)
### Emissive Color
- A color input in Unreal Materials that makes a surface appear self-illuminated
- Texture Sample (EM)
## ORM 
- ORM (Occlusion, Roughness, Metallic)
- Texture Sample
![[Screenshot 2025-12-17 121453.png | center]]



---


### Blend Mode
- Masked: 材质的像素要么完全可见（不透明），要么完全不可见（透明），中间没有半透明效果。
### Shading Model
- Unlit: 表示材质完全不受光照影响，只显示你输入的颜色或贴图本身。
### Two Sided
- 是一个材质属性选项，通常用于决定一个材质是否从背面也可见（默认只显示正面）。
--- 
### Emissive Color
- **让物体看起来自己在“发光”**，不依赖任何灯光照射。

### Opacity Mask
- 用于控制每个像素是“显示”还是“隐藏”
--- 
### TwoSidedSign
- 正面（面向摄像机的面）输出 `+1`
- 背面（背向摄像机的面）输出 `-1`