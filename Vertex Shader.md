- OpenGL only processes 3D coordinates when they're in a specific range between `-1.0` and `1.0` on all 3 axes (`x`, `y` and `z`)
- All coordinates within this so called **normalized device coordinates** range will end up visible on your screen (and all coordinates outside this region won't).


## NDC
![[Screenshot 2025-08-24 095142.png | center | 500]]



-  vertex buffer objects (VBO) that can store a large number of vertices in the GPU's memory
- The advantage of using those buffer objects is that we can send large batches of data all at once to the graphics card, and keep it there if there's enough memory left, without having to send data one vertex at a time
- Sending data to the graphics card from the CPU is relatively slow, so wherever we can we try to send as much data as possible at once
- Once the data is in the graphics card's memory the vertex shader has almost instant access to the vertices making it extremely fast
