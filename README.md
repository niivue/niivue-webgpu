## niivue-webgpu

[NiiVue](https://github.com/niivue/niivue) uses WebGL2 to visualize medical imaging data. WebGL2 uses [ANGLE](https://en.wikipedia.org/wiki/ANGLE_(software)) to leverage the optimal graphics language for a device: OpenGL, DirectX, Metal, or Vulkan. WebGL2 [does not allow inefficient legacy features](https://en.wikipedia.org/wiki/OpenGL)  such as immediate mode, direct-mode rendering, or geometry shaders. This repository is designed to be a playground to see if NiiVue can be enhanced by adopting [WebGPU](https://en.wikipedia.org/wiki/WebGPU). Our goal is to start with the [elegant minimal demo from Will Usher](https://github.com/Twinklebear/webgpu-volume-raycaster) and slowly explore porting NiiVue shaders and functions to WebGPU.

Several considerations to bear in mind:

 - WebGPU is unlikely to ever support OpenGL-based devices. One of the aims for NiiVue is to empower users who do not have access to the latest hardware.
 - The WebGPU specification has not been finalized, and it remains a moving target.
 - It took over five **years** after the stable specification of WebGL2 was finalized for it to be supported by all major browsers.
 - For visualization, the primary benefit of WebGPU over WebGL2 is the efficiency of a command buffer instead of many separate draw calls. However, NiiVue uses only a handful of draw calls, with the fragment shader being the main bottleneck. Therefore, WebGL and WebGPU are likely to provide similar visualization performance.
 - WebGPU promises to revolutionize the use of graphics hardware for compute tasks. While NiiVue already uses WebGL2 for some compute tasks, there is scope to enhance these functions. The primary interest in WebGPU for NiiVue is for compute, not visualization.

## Building

```bash
git clone https://github.com/niivue/niivue-webgpu
cd niivue-webgpu
npm install
npm run serve
```

** Warning: the WebGPU language has been changed: you must run Chrome 113 or later **

** As of Mid-April 2023 you may need to run [Chrome Canary](https://www.google.com/chrome/canary/) instead of the current Chrome release **

A local live demo will be hosted on `localhost:8080`.
