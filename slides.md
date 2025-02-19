---
# Options: 'default', 'seriph', 'apple-basic'
# theme: seriph
theme: ./theme #customized ejected seriph theme
themeConfig:
  primary: '#0097a7'
  darkMode: false
# background image
background: /header.jpg
# some information about your slides (markdown enabled)
title: Charting Multi-Scale Brain Phenotypes Using Spectral Normative Models
info: |
  ## Slides for ISMRM Diffusion Workshop
  Charting Multi-Scale Brain Phenotypes Using Spectral Normative Models
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
transitionDuration: 2000
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
katex: true
---

## Charting Multi-Scale Brain Phenotypes Using
# **Spectral Normative Models**

Presentation slides for the [ISMRM Workshop on 40 Years of Diffusion](https://www.ismrm.org/workshops/2025/Diffusion40/)

<div class="abs-br m-6 text-xl">
  <a href="https://sina-mansour.github.io/" target="_blank" class="slidev-icon-btn">
    <carbon:user-avatar-filled />
  </a>
  <a href="https://github.com/sina-mansour" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<div class="abs-bl m-6 flex items-center gap-2">
  <img src="./assets/Avatar_v1.png" alt="Avatar photo" width="80">
  <div>
    <div class="text-4 text-left">Sina Mansour L.</div>
    <div class="text-2 text-left italic">National University of Singapore & The University of Melbourne</div>
    <div class="text-2 text-left italic"><carbon:email /> sina.mansour.lakouraj@gmail.com</div>
  </div>
</div>

<div class="abs-tr m-6 text-sm">
  <carbon:calendar /> Feb. 19. 2025
</div>

---
layout: section
transition: fade-out
---

# Declaration of Financial Interests or Relationships

Speaker Name: Sina Mansour L.

I have no financial interests or relationships to disclose with regard to the subject matter of this presentation. {.text-left .text-2xl}

---
layout: default
transition: slow-fade
---

# Overview

<ul class="text-6" v-click="1" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2">
    <div class="text-cyan-500" v-click="[2,3]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Big data in brain imaging, and the importance of dimensionality reduction</div>
  </li>
  <li class="flex gap-2">
    <div class="text-cyan-500" v-click="[3,4]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div> A primer on Graph Signal Processing (GSP)</div>
  </li>
  <li class="flex gap-2">
    <div class="text-cyan-500" v-click="[4,5]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Diffusion MRI and brain connectivity eigenmodes</div>
  </li>
  <li class="flex gap-2">
    <div class="text-cyan-500" v-click="[5,6]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Leveraging eigenmodes for Spectral Normative Modeling (SNM)</div>
  </li>
  <li class="flex gap-2">
    <div class="text-cyan-500" v-click="[6,7]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Empirical application: personalized brain charting of Alzheimer’s Disease</div>
  </li>
  <li class="flex gap-2">
    <div class="text-cyan-500" v-click="7" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Concluding remarks and future directions</div>
  </li>
</ul>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Big data in brain imaging

<ul class="text-6" v-click="1" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="1" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="[1,2]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Brain scans are inherently large files</div>
  </li>
  <li class="flex gap-2" v-click="2" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="[2,3]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Sample sizes are limited relative to exemplary AI models</div>
  </li>
  <li class="flex gap-2 text-rose-600" v-click="7" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="7" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Importance of dimensionality reduction for AI in neuroimaging</div>
  </li>
</ul>

<div class="mt-6 border" v-click="[3,7]" v-motion :initial="{ y: 50 }" :enter="{ y: -50 }" :leave="{ y: 50 }">
  <table>
    <thead>
      <tr>
        <th>Example</th>
        <th v-click="4" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><div class="flex justify-center items-center"><img src="./assets/deepseek.png" alt="Deepseek-R1" width="120"></div></th>
        <th v-click="5" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><div class="flex justify-center items-center"><img src="./assets/stable_diffusion.png" alt="Stable Diffusion" width="150"></div></th>
        <th v-click="6" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><div class="flex justify-center items-center"><img src="./assets/biobank.png" alt="UK Biobank" width="120"></div></th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Total data</td>
        <td class="text-center" v-click="4" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">45 terabytes</td>
        <td class="text-center" v-click="5" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">400 terabytes</td>
        <td class="text-center" v-click="6" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">90 terabytes</td>
      </tr>
      <tr>
        <td>Tokens (sample size)</td>
        <td class="text-center" v-click="4" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">~15 trillion</td>
        <td class="text-center" v-click="5" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">~2 billion</td>
        <td class="text-center" v-click="6" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">~45 thousand</td>
      </tr>
      <tr>
        <td>Single token size</td>
        <td class="text-center" v-click="4" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">~3 bytes</td>
        <td class="text-center" v-click="5" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">~200 kilobytes</td>
        <td class="text-center" v-click="6" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">~2 gigabytes</td>
      </tr>
    </tbody>
  </table>
</div>


<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Graph Signal Processing (GSP)

<ul class="text-6" v-click="1" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="1" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="[1,2]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>A field of signal processing dedicated to analyzing signals on graphs</div>
  </li>
  <li class="flex gap-2" v-click="4" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="4" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Generalization of discrete signal processing ideas to the realm of networks</div>
  </li>
</ul>

<div v-click="[2,4]" class="absolute top-3/5 left-1/2 -translate-x-1/2 -translate-y-1/2 flex w-full max-w-screen-lg">
  <div v-click="2" v-motion :initial="{ y: 50 }" :enter="{ y: 0 }" :leave="{ y: 50 }" class="w-1/2 bg-slate-100 m-4 p-4 text-center text-cyan-500">
    <div>Discrete-time signal</div>
    <div class="flex justify-center items-center m-4"><img src="./assets/dts.png" alt="Discrete-time signal" width="280"></div>
  </div>
  <div v-click="3" v-motion :initial="{ y: 50 }" :enter="{ y: 0 }" :leave="{ y: 50 }" class="w-1/2 bg-slate-100 m-4 p-4 text-center text-cyan-500">
    <div><span class="font-bold text-xl">Graph Signal:</span> Vector of values over the nodes</div>
    <div class="flex justify-center items-center m-4"><img src="./assets/gs.png" alt="Graph Signal" width="280"></div>
    <div class="italic">Shuman et al. (2013)</div>
  </div>
</div>

<div v-click="5" class="absolute top-21/32 left-1/2 -translate-x-1/2 -translate-y-1/2 flex w-full max-w-screen-lg">
  <div v-click="5" v-motion :initial="{ y: 50 }" :enter="{ y: 0 }" :leave="{ y: 50 }" class="w-1/2 bg-slate-100 m-4 p-4 text-center text-cyan-500">
    <div>Discrete Fourier Transform</div>
    <div class="flex justify-center items-center m-4"><img src="./assets/dfteqn.png" alt="Fourier Transform" width="380"></div>
    <div v-mark="{ at: 7, color: '#D76', type: 'circle'}" class="absolute top-31 left-18 transform -translate-x-1/2 -translate-y-1/2 w-16 h-20"></div><!-- freq circ -->
    <div v-click="7" class="absolute top-53 left-18 transform -translate-x-1/2 -translate-y-1/2 w-32 h-20 text-rose-600">Frequency domain</div>
    <div v-mark="{ at: 6, color: '#D76', type: 'circle'}" class="absolute top-32 left-60 transform -translate-x-1/2 -translate-y-1/2 w-12 h-10"></div><!-- time circ -->
    <div v-click="6" class="absolute top-50 left-60 transform -translate-x-1/2 -translate-y-1/2 w-22 h-20 text-rose-600">Time domain</div>
  </div>
  <div v-click="5" v-motion :initial="{ y: 50 }" :enter="{ y: 0 }" :leave="{ y: 50 }" class="w-1/2 bg-slate-100 m-4 p-4 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/fourier_transform.png" alt="Fourier Transform" width="380"></div>
  </div>
</div>

<div v-click="8" class="absolute top-21/32 left-1/2 -translate-x-1/2 -translate-y-1/2 flex w-full max-w-screen-lg">
  <div v-click="8" v-motion :initial="{ y: 0 }" :enter="{ y: 0 }" :leave="{ y: 50 }" class="w-1/2 bg-slate-100 m-4 p-4 text-center text-cyan-500">
    <div>Inverse Discrete Fourier Transform</div>
    <div class="flex justify-center items-center m-4"><img src="./assets/idfteqn.png" alt="Fourier Transform" width="380"></div>
    <div v-mark="{ at: 10, color: '#D76', type: 'circle'}" class="absolute top-30 left-17 transform -translate-x-1/2 -translate-y-1/2 w-12 h-10"></div><!-- freq circ -->
    <div v-click="10" class="absolute top-47 left-17 transform -translate-x-1/2 -translate-y-1/2 w-22 h-20 text-rose-600">Time domain</div>
    <div v-mark="{ at: 9, color: '#D76', type: 'circle'}" class="absolute top-30 left-65 transform -translate-x-1/2 -translate-y-1/2 w-11 h-19"></div><!-- time circ -->
    <div v-click="9" class="absolute top-52 left-65 transform -translate-x-1/2 -translate-y-1/2 w-22 h-20 text-rose-600">Frequency domain</div>
  </div>
  <div v-click="8" class="w-1/2 bg-slate-100 m-4 p-4 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/fourier_transform.png" alt="Fourier Transform" width="380"></div>
  </div>
</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Graph Fourier Transform (GFT)

<ul class="text-6" v-click="1" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="1" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="[1,2]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Analogous to DFT, but for graphs</div>
  </li>
  <li class="flex gap-2" v-click="2" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="[2,3]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>GFT is defined using a graph shift operator</div>
  </li>
  <li class="flex gap-2" v-click="3" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="[3,4]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Graph Fourier basis via singular value decomposition of shift operator</div>
  </li>
</ul>

<div v-click="[1,2]" v-motion :initial="{ y: 50 }" :enter="{ y: 0 }" :leave="{ y: 50 }" class="absolute top-1/3 left-1/16 w-7/8 h-64 flex flex-col items-center bg-slate-100 p-2 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/gft_basis.png" alt="GFT basis" width="940"></div>
    <div class="flex w-180">
      <div class="w-1/2 text-left">Lower graph frequency</div>
      <div class="w-1/2 text-right">Higher graph frequency</div>
    </div>
</div>

<div v-click="[2,3]" v-motion :initial="{ y: 50 }" :enter="{ y: 0 }" :leave="{ y: 50 }" class="absolute top-60 left-1/8 w-3/4 h-44 flex flex-col items-center bg-slate-100 p-4 text-center text-cyan-500">
    <div class="text-xl">Shift Operator: symmetric normalized Laplacian</div>
    <div class="flex justify-center items-center m-4"><img src="./assets/shift_operator.png" alt="shift operator" width="640"></div>
</div>

<div v-click="[3,4]" v-motion :initial="{ y: 50 }" :enter="{ y: 0 }" :leave="{ y: 50 }" class="absolute top-72 left-1/3 w-1/3 h-36 flex flex-col items-center bg-slate-100 p-4 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/svd.png" alt="SVD" width="240"></div>
</div>

<div v-click="[4,7]" v-motion :initial="{ y: 50 }" :enter="{ y: 0 }" :leave="{ y: 50 }" class="absolute top-72 left-2/7 w-3/7 h-48 flex flex-col items-center bg-slate-100 p-4 text-center text-cyan-500">
    <div class="text-xl">Graph Fourier Transform</div>
    <div class="flex justify-center items-center m-4"><img src="./assets/gfteqn.png" alt="GFT" width="240"></div>
    <div class="italic">Huang et al. (2018)</div>
    <div v-mark="{ at: 5, color: '#D76', type: 'circle'}" class="absolute top-28 left-76 transform -translate-x-1/2 -translate-y-1/2 w-12 h-12"></div><!-- gs circ -->
    <div v-click="5" class="absolute top-29 left-92 transform -translate-x-1/2 -translate-y-1/2 w-22 h-20 text-rose-600">Graph signal domain</div>
    <div v-mark="{ at: 6, color: '#D76', type: 'circle'}" class="absolute top-28 left-29 transform -translate-x-1/2 -translate-y-1/2 w-10 h-16"></div><!-- gf circ -->
    <div v-click="6" class="absolute top-29 left-11 transform -translate-x-1/2 -translate-y-1/2 w-22 h-20 text-rose-600">Graph frequency domain</div>
</div>

<div v-click="7" v-motion :initial="{ y: 50 }" :enter="{ y: 0 }" :leave="{ y: 50 }" class="absolute top-72 left-2/7 w-3/7 h-48 flex flex-col items-center bg-slate-100 p-4 text-center text-cyan-500">
    <div class="text-xl">Inverse Graph Fourier Transform</div>
    <div class="flex justify-center items-center m-4"><img src="./assets/igfteqn.png" alt="iGFT" width="240"></div>
    <div class="italic">Huang et al. (2018)</div>
    <div v-mark="{ at: 8, color: '#D76', type: 'circle'}" class="absolute top-26 left-76 transform -translate-x-1/2 -translate-y-1/2 w-12 h-18"></div><!-- gs circ -->
    <div v-click="8" class="absolute top-26 left-94 transform -translate-x-1/2 -translate-y-1/2 w-22 h-20 text-rose-600">Graph frequency domain</div>
    <div v-mark="{ at: 9, color: '#D76', type: 'circle'}" class="absolute top-27 left-30 transform -translate-x-1/2 -translate-y-1/2 w-11 h-16"></div><!-- gf circ -->
    <div v-click="9" class="absolute top-27 left-14 transform -translate-x-1/2 -translate-y-1/2 w-22 h-20 text-rose-600">Graph signal domain</div>
</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Graph Filters

<ul class="text-6" v-click="1" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="1" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="[1,2]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Idea: Reconstruct particular frequency bands of the signal</div>
  </li>
</ul>

<div v-click="[2,3]" v-motion :initial="{ y: 50 }" :enter="{ y: 0 }" :leave="{ y: 50 }" class="absolute top-44 left-1/3 w-1/3 h-78 flex flex-col items-center bg-slate-100 p-0 text-center text-cyan-500 justify-center">
    <div class="flex justify-center items-center m-4"><img src="./assets/temporal_filters.png" alt="Temporal filter" width="340"></div>
</div>

<div v-click="3" v-motion :initial="{ y: 50 }" :enter="{ y: 0 }" :leave="{ y: 50 }" class="absolute top-44 left-1/8 w-3/4 h-78 flex flex-col items-center bg-slate-100 p-0 text-center text-cyan-500 justify-center">
    <div class="text-xl">Graph Filter G</div>
    <div class="flex justify-center items-center m-4"><img src="./assets/graph_filtering.png" alt="Graph filter" width="640"></div>
    <div class="italic">Huang et al. (2018)</div>
    <div v-mark="{ at: 4, color: '#D76', type: 'underline'}" class="absolute top-38 left-24 transform -translate-x-1/2 -translate-y-1/2 w-20 h-16"></div><!-- line 1 -->
    <div v-click="4" class="absolute top-58 left-24 transform -translate-x-1/2 -translate-y-1/2 w-22 h-20 text-rose-600">GFT</div>
    <div v-mark="{ at: 4, color: '#D76', type: 'underline'}" class="absolute top-44 left-85 transform -translate-x-1/2 -translate-y-1/2 w-22 h-16"></div><!-- line 2 -->
    <div v-click="4" class="absolute top-66 left-85 transform -translate-x-1/2 -translate-y-1/2 w-22 h-20 text-rose-600">Filtering</div>
    <div v-mark="{ at: 4, color: '#D76', type: 'underline'}" class="absolute top-38 left-152 transform -translate-x-1/2 -translate-y-1/2 w-20 h-16"></div><!-- line 3 -->
    <div v-click="4" class="absolute top-58 left-152 transform -translate-x-1/2 -translate-y-1/2 w-22 h-20 text-rose-600">iGFT</div>
</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Network Neuroscience and GSP on brain graphs

<ul class="text-6" v-click="1" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="1" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="[1,2]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Modeling anatomical brain networks</div>
  </li>
</ul>

<div v-click="1" v-motion :initial="{ x: 50 }" :enter="{ x: 0 }" :leave="{ x: 50 }" class="absolute top-1/5 left-140 text-rose-600"><img src="./assets/cajal.jpeg" alt="Cajal" width="300"></div>

<div v-click="2" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }" class="absolute top-40 left-10 text-rose-600"><img src="./assets/brain_graph.png" alt="Brain Graph" width="500"></div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Diffusion MRI data

<ul class="text-6" v-click="1" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="1" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="[1,2]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Enables mapping in-vivo anatomical wiring networks</div>
  </li>
</ul>

<div v-click="2" class="absolute top-50 left-12"><img src="./assets/dmri.jpg" alt="Diffusion MRI" width="600"></div>
<div v-click="2" class="absolute top-116 left-22 italic text-cyan-500">Tournier 2019</div>
<div v-click="[0,3]" class="absolute top-40 left-62 w-50 h-70 bg-white"></div><!-- mask1 -->
<div v-click="[0,4]" class="absolute top-40 left-113 w-50 h-70 bg-white"></div><!-- mask2 -->
<div v-click="5" class="absolute top-46 left-165"><img src="./assets/tractography-sag.png" alt="Sagital tractography" width="300"></div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# GSP in brain imaging

<ul class="text-6" v-click="1" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="1" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="[1,2]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>GSP methods have been used to study brain signals in the past decade</div>
  </li>
  <li class="flex gap-2" v-click="2" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="2" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Different terminologies: harmonics, eigenmodes, gradients, …</div>
  </li>
</ul>

<div v-click="1" v-motion :initial="{ y: 50 }" :enter="{ y: 0 }" :leave="{ y: 50 }" class="absolute top-55 left-10 w-60 h-60 flex flex-col items-center bg-slate-100 p-0 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/atasoy.png" alt="Atasoy et al." width="240"></div>
    <div class="italic">Atasoy et al. (2016)</div>
</div>

<div v-click="1" v-motion :initial="{ y: 50 }" :enter="{ y: 0 }" :leave="{ y: 50 }" class="absolute top-55 left-75 w-52 h-60 flex flex-col items-center bg-slate-100 p-0 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/robinson.png" alt="Robinson et al." width="220"></div>
    <div class="italic">Robinson et al. (2016)</div>
</div>

<div v-click="1" v-motion :initial="{ y: 50 }" :enter="{ y: 0 }" :leave="{ y: 50 }" class="absolute top-55 left-132 w-38 h-60 flex flex-col items-center bg-slate-100 p-0 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/tarun.png" alt="Tarun et al." width="220"></div>
    <div class="italic">Tarun et al. (2019)</div>
</div>

<div v-click="1" v-motion :initial="{ y: 50 }" :enter="{ y: 0 }" :leave="{ y: 50 }" class="absolute top-55 left-175 w-58 h-60 flex flex-col items-center bg-slate-100 p-0 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/preti.png" alt="Preti et al." width="220"></div>
    <div class="italic">Preti et al. (2019)</div>
</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# High-resolution connectome eigenmodes

<ul class="text-6" v-click="1" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="1" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="[1,2]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Perform tractography over a large sample (e.g. HCP YA)</div>
  </li>
  <li class="flex gap-2" v-click="2" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="[2,3]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Map high-resolution connectomes (at the granularity of voxels or vertices)</div>
  </li>
  <li class="flex gap-2" v-click="3" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="[3,4]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Group-average connectome; shared anatomical connectivity backbone</div>
  </li>
  <li class="flex gap-2" v-click="4" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="4" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Perform GSP; map graph Laplacian eigenmodes as an information basis</div>
  </li>
</ul>

<div v-click="[2,3]" v-motion :initial="{ x: -100, scale:0.5 }" :enter="{ x: 0, scale:1.0 }" :leave="{ x: -100, scale:0.5 }" class="absolute top-50 left-10 text-rose-600"><img src="./assets/full-mesh.png" alt="Brain Mesh" width="370"></div>

<div v-click="[2,3]" v-motion :initial="{ x: 100, scale:0.5 }" :enter="{ x: 0, scale:1.0 }" :leave="{ x: 100, scale:0.5 }" class="absolute top-50 right-10 text-rose-600"><img src="./assets/half-mesh-tract.png" alt="Brain Mesh + streamlines" width="380"></div>

<div v-click="[3,4]" v-motion :initial="{ x: -100, scale:0.5 }" :enter="{ x: 0, scale:1.0 }" :leave="{ x: -100, scale:0.5 }" class="absolute top-70 left-10 text-rose-600"><img src="./assets/group_tract.png" alt="Group Average connectome" width="450" class="transform scale-x-[-1]"></div>

<div v-click="4" v-motion :initial="{ x: -100, scale:0.5 }" :enter="{ x: 0, scale:1.0 }" :leave="{ x: -100, scale:0.5 }" class="absolute top-80 left-10 text-rose-600"><img src="./assets/eigenmodes_subfigure.png" alt="Brain Connectivity Eigenmodes" width="900"></div>

<div v-click="4" v-motion :initial="{ x: -100, scale:0.5 }" :enter="{ x: 0, scale:1.0 }" :leave="{ x: -100, scale:0.5 }" class="absolute top-112 left-60 text-rose-600"><img src="./assets/reconstruction_eqn.png" alt="Information reconstruction" width="500"></div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Signal reconstruction via eigenmodes:

<img v-click="0" v-motion :initial="{ x: -100, scale:0.5, rotate: -90 }" :enter="{ x: 0, scale:1.0, rotate: -90 }" :leave="{ x: -100, scale:0.5, rotate: -90 }" class="absolute top-65 left--10 text-rose-600" src="./assets/reconstruction_eqn.png" alt="Information reconstruction" width="360">

<img v-click="1" class="absolute top-25 left-50 text-rose-600" src="./assets/signal_reconstruction.png" alt="Brain Signal Reconstruction" width="560">
<div v-click="[0,2]" class="absolute top-49 left-48 w-145 h-24 bg-white"></div><!-- mask1 -->
<div v-click="[0,3]" class="absolute top-73 left-48 w-145 h-24 bg-white"></div><!-- mask2 -->
<div v-click="[0,4]" class="absolute top-97 left-48 w-145 h-24 bg-white"></div><!-- mask2 -->

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Conceptual analogy with autoencoders:

<img v-click="0" class="absolute top-25 left-1/2 transform -translate-x-1/2 text-rose-600" src="./assets/autoencoder.png" alt="Autoencoder" width="400">

<div v-mark="{ at: 1, color: '#D76', type: 'circle'}" class="absolute top-33 left-98 transform -translate-x-1/2 -translate-y-1/2 w-14 h-4"></div><!-- circ 1 -->
<div v-click="1" class="absolute top-32 left-101 transform -translate-x-1/2 -translate-y-1/2 w-14 h-20 text-rose-600">SLP</div>
<div v-mark="{ at: 1, color: '#D76', type: 'circle'}" class="absolute top-33 left-144 transform -translate-x-1/2 -translate-y-1/2 w-14 h-4"></div><!-- circ 2 -->
<div v-click="1" class="absolute top-32 left-147 transform -translate-x-1/2 -translate-y-1/2 w-14 h-20 text-rose-600">SLP</div>
<div v-mark="{ at: 2, color: '#D76', type: 'circle'}" class="absolute top-116 left-87 transform -translate-x-1/2 -translate-y-1/2 w-16 h-4"></div><!-- circ 3 -->
<div v-click="2" class="absolute top-130 left-88 transform -translate-x-1/2 -translate-y-1/2 w-14 h-20 text-rose-600 text-center">Brain Signal</div>
<div v-mark="{ at: 3, color: '#D76', type: 'circle'}" class="absolute top-33 left-122 transform -translate-x-1/2 -translate-y-1/2 w-13 h-8"></div><!-- circ 4 -->
<div v-click="3" class="absolute top-55 left-122 transform -translate-x-1/2 -translate-y-1/2 w-20 h-20 text-rose-600 text-center text-sm">Graph Frequency Domain</div>
<div v-mark="{ at: 4, color: '#D76', type: 'circle'}" class="absolute top-116 left-158 transform -translate-x-1/2 -translate-y-1/2 w-30 h-6"></div><!-- circ 5 -->
<div v-click="4" class="absolute top-110 left-185 transform -translate-x-1/2 -translate-y-1/2 w-20 h-20 text-rose-600 text-center">Low-pass filtered signal</div>


<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Spectral Normative Modeling

<img v-click="1" v-motion :initial="{ scaleX:2.5, scaleY:0.1 }" :enter="{ scaleX:1.0, scaleY:1.0 }" :leave="{ scaleX:2.5, scaleY:0.1 }" class="absolute top-50 left-52 text-rose-600 transition duration-100" src="./assets/stream.png" alt="connector" width="600">
<div v-click="1" v-motion :initial="{ x:-500 }" :enter="{ x:0 }" :leave="{ x:-500 }" class="absolute top-65 left-15 w-30 h-20 text-cyan-600 font-bold text-center text-2xl transition duration-100">Bain Eigenmodes</div>
<div v-click="1" v-motion :initial="{ x:500 }" :enter="{ x:0 }" :leave="{ x:500 }" class="absolute top-65 right-15 w-30 h-20 text-cyan-600 font-bold text-center text-2xl transition duration-100">Normative Modeling</div>
<div v-click="1" v-motion :initial="{ scaleX:2.5, scaleY:0.1 }" :enter="{ scaleX:1.0, scaleY:1.0 }" :leave="{ scaleX:2.5, scaleY:0.1 }" class="absolute top-40 left-112 w-30 h-20 text-cyan-600 font-bold text-center text-4xl transition duration-100">SNM</div>


<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Normative Modeling

<ul class="text-6" v-click="1" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="1" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="1" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Characterizes population-level phenotype distribution to detect individual deviations from the norm.</div>
  </li>
</ul>

<div v-click="1" class="absolute top-3/5 left-1/2 -translate-x-1/2 -translate-y-1/2 flex w-200 max-w-screen-lg">
  <div v-click="1" class="w-1/2 bg-slate-100 m-4 p-1 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/nm1.png" alt="normative chart" width="280"></div>
  </div>
  <div v-click="1" class="w-1/2 bg-slate-100 m-4 p-1 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/nm2.png" alt="normative heterogeneity" width="280"></div>
  </div>
</div>

<div v-click="1" class="absolute top-116 left-1/2 -translate-x-1/2 italic text-cyan-600">Marquand et al. (2019)</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Normative Modeling & Personalized Medicine

<ul class="text-6" v-click="0" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="0" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="0" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Enables exploration of individual-level differences and heterogeneity of pathological deviations.</div>
  </li>
</ul>

<div v-click="0" class="absolute top-3/5 left-1/2 -translate-x-1/2 -translate-y-1/2 flex w-240 max-w-screen-lg">
  <div v-click="0" class="w-full bg-slate-100 m-4 p-1 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/heterogeneity_pathology.png" alt="heterogeneity" width="880"></div>
  </div>
</div>

<div v-click="0" class="absolute top-116 left-1/2 -translate-x-1/2 italic text-cyan-600">Marquand et al. (2016)</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Conventional Normative Models (Direct Models)

<ul class="text-6" v-click="1" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="1" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="[1,2]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Trained to infer normative ranges of a <span class="font-bold">predefined fixed phenotype (y)</span> from a set of covariates (X).</div>
  </li>
</ul>

<div v-click="[1,2]" class="absolute top-3/5 left-1/2 -translate-x-1/2 -translate-y-1/2 flex w-200 max-w-screen-lg">
  <div class="w-full bg-slate-100 m-4 p-1 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/nmeq.png" alt="NM equation" width="880"></div>
  </div>
</div>

<div v-click="[1,2]" class="absolute top-116 left-1/2 -translate-x-1/2 italic text-cyan-600">Dinga et al. (2021)</div>

<div v-click="2" class="absolute top-3/5 left-1/2 -translate-x-1/2 -translate-y-1/2 flex w-180 max-w-screen-lg">
  <div class="w-full bg-slate-100 m-4 p-1 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/directnm.png" alt="Direct NM" width="800"></div>
  </div>
</div>

<div v-click="2" class="absolute top-116 left-1/2 -translate-x-1/2 italic text-cyan-600">Mansour L. et al. (2025)</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Spectral Normative Modeling (SNM)

<ul class="text-6" v-click="1" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="1" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="[1,2]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div><span class="font-bold">Idea:</span> Use GSP as means to compress and reconstruct normative ranges.</div>
  </li>
</ul>

<div v-click="2" class="absolute top-78 left-1/2 -translate-x-1/2 -translate-y-1/2 flex w-180 max-w-screen-lg">
  <div class="w-full bg-slate-100 m-4 p-1 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/snm.png" alt="SNM" width="800"></div>
  </div>
</div>

<div v-click="2" class="absolute top-120 left-1/2 -translate-x-1/2 italic text-cyan-600">Mansour L. et al. (2025)</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# SNM performance

<ul class="text-6" v-click="1" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="1" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="1" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>With at least <span class="font-bold">1000 modes</span> SNM achieves comparable estimates to that of a direct model.</div>
  </li>
</ul>

<div v-click="1" class="absolute top-86 left-1/2 -translate-x-1/2 -translate-y-1/2 flex w-240 max-w-screen-lg">
  <div class="w-full bg-slate-100 m-10 p-0 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/performance.png" alt="Performance" width="800"></div>
  </div>
</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# High-resolution normative modeling

<ul class="text-6" v-click="1" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="1" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="1" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Efficiently estimate charts at <span class="font-bold">vertex-resolution</span> across human lifespan.</div>
  </li>
</ul>

<div v-click="1" class="absolute top-80 left-1/2 -translate-x-1/2 -translate-y-1/2 flex w-240 max-w-screen-lg">
  <div class="w-full bg-slate-100 m-10 p-0 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/hrcharts.png" alt="High-resolution charts" width="800"></div>
  </div>
</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# High-resolution normative modeling

<ul class="text-6" v-click="0" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="0" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="0" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Enables derivation of <span class="font-bold">individualized</span> vertex-resolution abnormality scores.</div>
  </li>
</ul>

<div v-click="0" class="absolute top-80 left-1/2 -translate-x-1/2 -translate-y-1/2 flex w-240 max-w-screen-lg">
  <div class="w-full bg-slate-100 m-10 p-0 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/individual_score.png" alt="High-resolution charts" width="800"></div>
  </div>
</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# High-resolution normative modeling

<ul class="text-6" v-click="0" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="0" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="0" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>For vertex-resolution NMs, SNM achieves <span class="font-bold">100x to 10,000x</span> speedup.</div>
  </li>
</ul>

<div v-click="0" class="absolute top-80 left-1/2 -translate-x-1/2 -translate-y-1/2 flex w-100 max-w-screen-lg">
  <div class="w-full bg-slate-100 m-10 p-0 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/efficiency.png" alt="High-resolution charts" width="800"></div>
  </div>
</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Clinical application: AD dementia

<ul class="text-6" v-click="1" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="1" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="[1,2]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Train SNM on a healthy normative sample (HCP Lifespan)</div>
  </li>
  <li class="flex gap-2" v-click="2" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="[2,3]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Transfer learning: freeze demography covariates, fine-tune site effects (harmonization)</div>
  </li>
  <li class="flex gap-2" v-click="3" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="3" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Clinical data: Healthy Controls (HC), Mild Cognitive Impairment (MCI), & Alzheimer's Disease (AD)</div>
  </li>
</ul>

<div v-click="[2,3]" class="absolute top-90 left-1/2 -translate-x-1/2 -translate-y-1/2 flex w-220 max-w-screen-lg">
  <div class="w-full bg-slate-100 m-10 p-0 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/transfer_learning.png" alt="High-resolution charts" width="800"></div>
  </div>
</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Clinical application: AD dementia

<ul class="text-6" v-click="0" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="0" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="0" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Population-level evaluations: Cortical correlates of cognitive decline</div>
  </li>
</ul>

<div v-click="0" class="absolute top-80 left-1/2 -translate-x-1/2 -translate-y-1/2 flex w-190 max-w-screen-lg">
  <div class="w-full bg-slate-100 m-10 p-0 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/group_level_AD.png" alt="High-resolution charts" width="800"></div>
  </div>
</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Clinical application: AD dementia

<ul class="text-6" v-click="0" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="0" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="0" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Individual-level evaluations: Heterogeneous landscape of dementia-induced cortical atrophy</div>
  </li>
</ul>

<div v-click="0" class="absolute top-85 left-1/2 -translate-x-1/2 -translate-y-1/2 flex w-240 max-w-screen-lg">
  <div class="w-full bg-slate-100 m-10 p-0 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/individual_report.png" alt="High-resolution charts" width="800"></div>
  </div>
</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Clinical application: AD dementia

<ul class="text-6" v-click="0" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="0" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="0" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Hypothetical patterns of interindividual variability</div>
  </li>
</ul>

<div v-click="0" class="absolute top-75 left-1/2 -translate-x-1/2 -translate-y-1/2 flex w-240 max-w-screen-lg">
  <div class="w-full bg-slate-100 m-10 p-0 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/hypothetical_variability.png" alt="High-resolution charts" width="800"></div>
  </div>
</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Clinical application: AD dementia

<ul class="text-6" v-click="0" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="0" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="0" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Empirical variability</div>
  </li>
</ul>

<div v-click="0" class="absolute top-75 left-70 -translate-x-1/2 -translate-y-1/2 flex w-120 max-w-screen-lg">
  <div class="w-full bg-slate-100 m-10 p-0 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/hypothetical_variability.png" alt="High-resolution charts" width="800"></div>
  </div>
  <div class="absolute top-13 left-12 w-68 h-30 bg-slate-100 bg-opacity-80"></div><!-- mask1 -->
</div>

<div v-click="0" class="absolute top-75 left-180 -translate-x-1/2 -translate-y-1/2 flex w-110 max-w-screen-lg">
  <div class="w-full bg-slate-100 m-10 p-0 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/empirical_variability.png" alt="High-resolution charts" width="800"></div>
  </div>
</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Clinical application: AD dementia

<ul class="text-6" v-click="0" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2" v-click="0" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }">
    <div class="text-cyan-500" v-click="0" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Individual heterogeneity</div>
  </li>
</ul>

<div v-click="0" class="absolute top-75 left-170 -translate-x-1/2 -translate-y-1/2 flex w-150 max-w-screen-lg">
  <div class="w-full bg-slate-100 m-10 p-0 text-center text-cyan-500">
    <div class="flex justify-center items-center m-4"><img src="./assets/individual_heterogeneity.png" alt="High-resolution charts" width="800"></div>
  </div>
  <div v-click="[0,1]" class="absolute top-13 left-12 w-29 h-68 bg-slate-100 bg-opacity-80"></div><!-- mask1 -->
  <div v-click="[0,2]" class="absolute top-13 left-106 w-30 h-98 bg-slate-100 bg-opacity-80"></div><!-- mask2 -->
  <div v-click="[0,3]" class="absolute top-81 left-12 w-95 h-31 bg-slate-100 bg-opacity-80"></div><!-- mask3 -->
</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Clinical application: AD dementia

<div class="absolute top-75 left-1/2 -translate-x-1/2 -translate-y-1/2 flex w-180 max-w-screen-lg bg-slate-100">
  <img src="./assets/video.apng" alt="High-resolution charts"></img>
</div>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>

---
layout: default
transition: slow-fade
---

# Concluding remarks

<ul class="text-5" v-click="1" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2">
    <div class="text-cyan-500" v-click="[1,2]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>GSP & brain eigenmodes provide a powerful basis for compression.</div>
  </li>
  <li class="flex gap-2">
    <div class="text-cyan-500" v-click="[2,3]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>These techniques facilitate processing big data in neuroimaging datasets.</div>
  </li>
  <li class="flex gap-2">
    <div class="text-cyan-500" v-click="[3,4]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Spectral Normative Modeling showcases is a simple exemplary application.</div>
  </li>
  <li class="flex gap-2">
    <div class="text-cyan-500" v-click="[4,5]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>SNMs unlock new possibilities for personalized medicine in brain imaging.</div>
  </li>
</ul>

<div class="pt-4">
  <h1>Future Directions</h1>
</div>

<ul class="text-5" v-click="5" v-motion:initial="{ x: -20 }":enter="{ x: -20 }">
  <li class="flex gap-2">
    <div class="text-cyan-500" v-click="[5,6]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Extending SNM to larger sample sizes & more modalities.</div>
  </li>
  <li class="flex gap-2">
    <div class="text-cyan-500" v-click="[6,7]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Utilizing SNM to chart brain connectivity.</div>
  </li>
  <li class="flex gap-2">
    <div class="text-cyan-500" v-click="[7]" v-motion :initial="{ x: -50 }" :enter="{ x: 0 }" :leave="{ x: -50 }"><carbon:direction-straight-right /></div>
    <div>Utilizing deeper NN architectures, e.g. using GNNs.</div>
  </li>
</ul>

<div class="abs-br m-6 flex items-center gap-2">
  <div class="text-3 text-left text-slate-400"><carbon:chat /> {{ $slidev.configs.title }} </div>
</div>


---
layout: statement
transition: fade-out
---


---
layout: statement
transition: fade-out
---

<img src="./assets/cool.png" class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-260 opacity-80">
<img src="./assets/brainnet.png" class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-170" style="filter: drop-shadow(0 0 5px rgba(158, 228, 228, 0.8));">

<img src="./assets/andrew-zalesky.png" class="absolute left-136 top-11 rounded-full w-27 object-cover border-4 border-gray-400 bg-cyan-400 shadow-lg">
<img src="./assets/thomas-yeo.png" class="absolute left-59 top-26 rounded-full w-20 object-cover border-4 border-gray-400 bg-lime-400 shadow-lg">
<img src="./assets/Maria-Di-Biase.png" class="absolute left-96 top-6 rounded-full w-20 object-cover border-4 border-gray-400 bg-lime-400 shadow-lg">
<img src="./assets/Helen-Zhou.jpg" class="absolute left-91.5 top-36.5 rounded-full w-20 object-cover border-4 border-gray-400 bg-lime-400 shadow-lg">
<img src="./assets/Christopher-Chen.png" class="absolute left-53 top-75 rounded-full w-20 object-cover border-4 border-gray-400 bg-amber-400 shadow-lg">
<img src="./assets/hongwei.png" class="absolute left-136 top-75.2 rounded-full w-20 object-cover border-4 border-gray-400 bg-violet-300 shadow-lg">
<img src="./assets/aihuiping.png" class="absolute left-96 top-66 rounded-full w-14 object-cover border-4 border-gray-400 bg-violet-300 shadow-lg">
<img src="./assets/aaron.png" class="absolute left-171 top-27 rounded-full w-18 object-cover border-4 border-gray-400 bg-violet-300 shadow-lg">
<img src="./assets/dimitri.jpg" class="absolute left-125.5 top-56.2 rounded-full w-16 object-cover border-4 border-gray-400 bg-violet-300 shadow-lg">
<img src="./assets/rob.jpeg" class="absolute left-148 top-45 rounded-full w-21 object-cover border-4 border-gray-400 bg-violet-300 shadow-lg">
<img src="./assets/hamid.jpeg" class="absolute left-177 top-64 rounded-full w-15 object-cover border-4 border-gray-400 bg-violet-300 shadow-lg">
<img src="./assets/caio.jpg" class="absolute left-99 top-89 rounded-full w-15 object-cover border-4 border-gray-400 bg-violet-300 shadow-lg">

<img src="./assets/unimelb.png" class="absolute right-50 bottom-5 w-20 object-cover">
<img src="./assets/nus.png" class="absolute right-10 bottom-1 w-40 object-cover">

---
layout: statement
transition: fade-out
---

## Charting Multi-Scale Brain Phenotypes Using
# **Spectral Normative Models**

Presentation slides for the [ISMRM Workshop on 40 Years of Diffusion](https://www.ismrm.org/workshops/2025/Diffusion40/)

<div class="abs-br m-6 text-xl">
  <a href="https://sina-mansour.github.io/" target="_blank" class="slidev-icon-btn">
    <carbon:user-avatar-filled />
  </a>
  <a href="https://github.com/sina-mansour" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<div class="abs-bl m-6 flex items-center gap-2">
  <img src="./assets/Avatar_v1.png" alt="Avatar photo" width="80">
  <div>
    <div class="text-4 text-left">Sina Mansour L.</div>
    <div class="text-2 text-left italic">National University of Singapore & The University of Melbourne</div>
    <div class="text-2 text-left italic"><carbon:email /> sina.mansour.lakouraj@gmail.com</div>
  </div>
</div>

