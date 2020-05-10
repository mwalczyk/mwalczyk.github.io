---
layout: default
---

# Silhouette Refinement
🎃 A partial implementation of the paper [Silhouette Smoothing for Real-Time Rendering of Mesh Surfaces](https://www.researchgate.net/publication/5483804_Silhouette_smoothing_for_real-time_rendering_of_mesh_surfaces).

<p align="center">
  <img src="assets/img/misc/silhouette-refinement.gif" width="500" height="auto"/>
</p>

## Description

Often times, the silhouette of a triangle mesh will appear jagged due to low polygon count or other factors. Rather than increasing the triangle density across the entire mesh, it may be desirable to "augment" the mesh at run-time in such a way that it _appears_ smooth(er), from the perspective of the viewer.

One way to achieve this effect is outlined in the paper [Silhouette Smoothing for Real-Time Rendering of Mesh Surfaces](https://www.researchgate.net/publication/5483804_Silhouette_smoothing_for_real-time_rendering_of_mesh_surfaces). We first determine the "visibility status" of each triangle by performing a dot product between the view vector at each vertex (i.e. a vector pointing from each vertex back towards the camera) and its corresponding normal vector. Triangles that contain vertices with differing visible statuses are said to be part of the silhouette of the mesh. 

We then perform local re-meshing at each of the offending triangles, approximating the "smooth" silhouette with a series of 3D curves that are reconstructed at run-time. There are probably many ways to implement this algorithm, but I chose to use OpenGL geometry shaders, since each vertex needs to have access to neighboring vertices. The .gif above shows the result.

This project was prototyped in Derivative's TouchDesigner. However, the geometry shader code is written in GLSL and should be fairly portable. It can be found below:

<script src="https://gist.github.com/mwalczyk/448da6b8c828b7dce7f8bc52e88bf9f9.js"></script>

[back](./)