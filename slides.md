---
theme: seriph
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
transition: slide-left
title: Large-scale production in complex equipment manufacturing
mdc: true
---



# Large-scale production in complex equipment manufacturing

Ziyang Shao

<!-- <div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div> -->

<!-- <div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div> -->

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->
---
layout: default
---

# Table of contents



<Toc maxDepth="1"></Toc>

---
transition: fade-out
---

# Scope of the Project 
## Background
or reasons for doing this project

-  **importance of scheduling** - for manufacture industry and companies
-  **gap between theory and practice** - 
-  **complexity increased** - with different constrains and larger scale


<br>
<br>


<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
Here is another comment.
-->



---
transition: slide-up
level: 2
---

# Scope of the Project 
## Aim
Develop an algorithm to efficiently solve large-scale production scheduling problems with many machines and parts which needs to consider the priority of the parts. 


## Ojectives
- Conduct a literature review on production scheduling methods, particularly for large problems 

Identify limitations of existing solution approaches for large instances 

- Develop a mathematical model to represent the scheduling problem 

- Find an algorithm to find near-optimal solutions  

- Implement the algorithm and test on benchmark instances 

- Analyze the algorithm's performance and scalability 


---
transition: slide-up
level: 2
layout: image-right
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# Literature Review
## Problems facing

- complexity increased & gap between theory and practice（Same as mentioned in the background）


- lack of research focus on large-scale scheduling problems
- limitation of widely used method like metaheuristics (Only partly optimal solutions can be found, but global optimal solutions cannot be found)



---
transition: slide-up
level: 2
---

# Literature Review
## Methods
- Heuristics
  -  Heuristics
  - Metaheuristic 
  - Combined Metaheuristics
- Machine learning
- Constraint programming

---
transition: slide-up
level: 2
layout: image-right
image: ./image.png
---

# Project Work Plan
1. Further research and Literature Review (November 2023 - January 2024) 

2. Development of Mathematical Model (November 2023 - February 2024) 

3. Algorithm Development (January 2024 - March 2024) 

4. Testing and Analysis (March 2024 - April 2024) 

5. Documentation of the algorithm and results (February 2024 - April 2024) 


---
layout: center
class: text-center
---

# END

thanks for listening





