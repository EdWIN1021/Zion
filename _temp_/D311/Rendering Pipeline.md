---
id: Rendering Pipeline
aliases: []
tags: []
---


# Rendering Pipeline

![[Screenshot 2025-12-20 183725.png]]

## Input Assembler

The input assembler (IA) stage reads geometric data (vertices and indices) from memory and uses it to assemble geometric primitives.

- Vertex buffer
- Indices


## Tessellation

## Vertex Shader

- The Vertices are usually read from a Vertex Buffer
- `ID3D11DeviceContext:Draw( 3, 0)`  the vertex shader will run 3 times
