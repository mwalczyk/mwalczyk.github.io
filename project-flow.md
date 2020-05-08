---
layout: default
---

# Flow
🔮 A GPU-based progressive path tracer written in Vulkan. 

<p align="center">
  <img src="https://raw.githubusercontent.com/mwalczyk/flow/master/screenshots/screenshot.png" alt="screenshot" width="300" height="auto"/>
</p>

## Description
For the time being, `flow` uses a single render pass instance with two distinct subpasses. The first subpass involves two floating-point images in a "ping-pong" arrangement. This is how the light accumulates over the course of many frames, leading to a well-converged image. Whichever of the two images was used as a color attachment during this first subpass serves as an input attachment to the next (and final) subpass. Input attachments are unique to Vulkan and allow a render pass attachment to be read in a fragment shader stage during a subpass. Input attachments come with several restrictions and do not support random access like a typical `sampler2D`, for example.

The second subpass simply reads from this input attachment and writes to one of the swapchain images that are presented to the screen. 

As such, there are two separate graphics pipelines - one that runs the main path tracing routine and another that normalizes the accumulated light (converts it from HDR to `[0..1]`) and writes to the corresponding swapchain image.

Built on top of [vkstarter](https://github.com/mwalczyk/vkstarter).

<p align="center">
  <img src="https://raw.githubusercontent.com/mwalczyk/flow/master/screenshots/render_0.png" alt="screenshot" width="200" height="auto"/>
  <img src="https://raw.githubusercontent.com/mwalczyk/flow/master/screenshots/render_1.png" alt="screenshot" width="200" height="auto"/>
  <img src="https://raw.githubusercontent.com/mwalczyk/flow/master/screenshots/render_2.png" alt="screenshot" width="200" height="auto"/>
</p>

[back](./)