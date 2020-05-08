---
layout: default
---

# SDFPerf
🔌 A node-based editor for experimenting with signed distance fields and raymarching.

<p align="center">
  <img src="https://raw.githubusercontent.com/mwalczyk/sdfperf/master/screenshots/all_operators.PNG" width="200" height="auto"/>
</p>

## Description
<p align="center">
  <img src="https://raw.githubusercontent.com/mwalczyk/sdfperf/master/screenshots/user_interface.gif" width="500" height="auto"/>
</p>

`sdfperf` is a work-in-progress node-based editor for creating and manipulating signed-distance fields (SDFs). Currently, the system supports basic SDF primitives (spheres, cubes, planes, toruses) as well as basic domain manipulation (translations, scales, bends, twists) and CSG operations (unions, intersections, differences, smooth-minimums). 

Each time a new connection is made, the underlying shader graph is re-built and a new raymarching shader string is generated. 

## To Use
<p align="center">
  <img src="https://raw.githubusercontent.com/mwalczyk/sdfperf/master/screenshots/graph.png" width="500" height="auto"/>
</p>

The UI displays a virtual preview of the final scene, which can be navigated with simple camera controls. Additionally, the user can switch between 5 distinct shading modes with the number keys (1-5): normals, ambient occlusion (AO), diffuse, z-depth, and ray depth. Certain nodes, such as the `translation` operator, have parameters that can be manipulated with the arrow keys.

[back](./)