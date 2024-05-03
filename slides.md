---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://images.unsplash.com/photo-1619976553580-0d3ffc09fb86?q=80&w=3872&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
# some information about your slides, markdown enabled
title: Large-scale production in complex equipment manufacturing
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply any unocss classes to the current slide
class: text-center
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# https://sli.dev/guide/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/guide/syntax#mdc-syntax
mdc: true
---

# Large-scale production in complex equipment manufacturing

### Ziynag Shao
### Supervisor: Peng Guo

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out
---

# Backgorund 
<div>
this project focuses on a provider of rail transit maintenance equipment, The company produces 38 kinds of large-scale rail transit operation and maintenance vehicles, each model involves more than 10,000 structural parts, and the materials, priorities, processes and other requirements of different parts are different. In the long-term implementation process of manual production scheduling in its structural branch plant, problems such as low efficiency and poor accuracy are gradually exposed
  <img
  class="absolute  -right-7 w-80 "
  src="https://img2.imgtp.com/2024/05/03/hr69HxmA.png"
  alt=""
  />
</div>



- 📝 **importance of efficient scheduling** 
  - reduce production times, 
  - minimize costs, 
  - increase overall factory efficiency
  
- **Limitation of current solutions** 
  - traditional heuristic algorithms alostuggle to handle complex multi-objective optimization
  - only partly optimal solutions can be found in some situation





---
transition: slide-up
level: 2
---

# Aim

<h5>Design a scheduling algorithm and build up its mathematic model to efficiently solve large scale parallel machine scheduling problems.
To tackle the challenges of large-scale parallel machine scheduling, particularly in high-end equipment manufacturing industries, this project proposes the design of an scheduling algorithm. The mathematical model underpinning this algorithm is aimed at optimizing several critical aspects of production processes: priority handling, material type management, and the processing numbers of parts. The objective is to minimize the total completion time of scheduled jobs while optimizing the allocation and utilization of resources.
</h5>

# Assuptions made
- Homogeneous parallel machine problem
- Single Operation Per Machine
- Consistent Machine Operation
- Negligible Transport Time
- Exclusion of Assembly Time





---
transition: slide-up
level: 2
---

# Mathmatic model
### Stage1 model: to minimise the total completion time using simulated annealing

<div w-200 flex>
<img 
  w-100
  src='https://img2.imgtp.com/2024/05/03/d4dFveZm.png'
/>
<img 
  h-50
  src='https://img2.imgtp.com/2024/05/03/YILQcgjP.png'
/>

</div>


---
transition: slide-up
level: 2
---

# Mathmatic model
### Stage 2 model: 3 objectives
1. Minimize the number of material changes during the processing of parts.
2. Prioritize the processing of parts with a higher priority
3. Prioritize the processing of parts with higher priority within the same project
<div w-200 flex>
<img 
  w-98
  src='https://img2.imgtp.com/2024/05/03/1QU91Djw.png'
/>
<div>
<img 
  h-62
  src='https://img2.imgtp.com/2024/05/03/hZ4E0BIi.png'
/>
<img 
  h-12
  src='https://img2.imgtp.com/2024/05/03/RsjcunG9.png'
/>
</div>
</div>

---
transition: slide-up
level: 2

---
### Implementation of optimization algorithm
Flow char of general algorithm
<div w-200 flex justify-center>
 <img  w-80 src='https://img2.imgtp.com/2024/05/03/0ENcQnqt.png'/>
</div>
---
transition: slide-up
level: 2

---
### Implementation of optimization algorithm
simulate annealing with chaotic operator

$\ x_{n+1}=r×x_{n}×(1-x_n)$
<div flex>
  <div w-110>
    20 job with random processing time between 1 and 100 on 5 machines
    <img h-60 src='https://img2.imgtp.com/2024/05/03/rKtguE7z.png' />
  </div>
  <div w-110 m-x-2>
    30 job with random processing time between 1 and 100 on 15 machines
    <img h-60 src='https://img2.imgtp.com/2024/05/03/1xm8swkp.png' />
  </div>
</div>

---
transition: slide-up
level: 2

---
### Implementation of optimization algorithm
flow chart of simulate annealing 
<div w-200  flex justify-center>
    <img h-105 src='https://img2.imgtp.com/2024/05/03/NT82wT6p.png' />
  </div>
---
transition: slide-up
level: 2

---

#### Implementation of optimization algorithm
Code of simulate annealing with chaotic operator

```py 
def simulated_annealing(initial_temp, cooling_rate, max_iterations):
    current_solution = np.random.randint(0, num_machines, size=num_tasks)
    current_cmax, _ = calculate_cmax_and_schedule(current_solution)
    best_solution = current_solution.copy()
    best_cmax = current_cmax
    chaotic_var = np.random.rand()
    for i in range(max_iterations):
        temp = initial_temp * (cooling_rate ** i)
        chaotic_var = logistic_map(chaotic_var)
        new_solution = generate_new_solution(current_solution, chaotic_var)
        new_cmax, _ = calculate_cmax_and_schedule(new_solution)
        energy_diff = new_cmax - current_cmax
        if energy_diff < 0 or np.exp(-energy_diff / temp) > np.random.rand():
            current_solution = new_solution.copy()
            current_cmax = new_cmax

            if new_cmax < best_cmax:
                best_solution = new_solution.copy()
                best_cmax = new_cmax
    best_cmax, best_schedule = calculate_cmax_and_schedule(best_solution)
    return best_solution, best_cmax, best_schedule
```

---
level: 2
---

### Implementation of optimization algorithm
data used for test
<div w-200  flex justify-center>
    <img h-170 src='https://img2.imgtp.com/2024/05/03/rFg39LX7.png' />
  </div>

---
level: 2
---

### Implementation of optimization algorithm
Gantt chart of schedule results of simulate annealing
<p >number at top: id of the part, number at the middle: priority, and the number in the bottom represents the part processing quantity. </p>
<div w-200  flex justify-center>
    <img h-90 src='https://img2.imgtp.com/2024/05/03/8gulEpss.png' />
  </div>


---

### Implementation of optimization algorithm
code of local greedy search
<div  flex justify-center>
    <img h-110 src='https://img2.imgtp.com/2024/05/03/yNRHL0nT.png' />
</div>


---
class: px-20
---

### Implementation of optimization algorithm
flow chart of random neighborhood search
<div  flex justify-center>
    <img h-105 src='https://img2.imgtp.com/2024/05/03/Jf2CvyTe.png' />
</div>



---

### Implementation of optimization algorithm
results of second stage optimization
<div  flex justify-center>
    <img h-100 src='https://img2.imgtp.com/2024/05/03/JDBucjpD.png' />
</div>

---

# Summary

#### Key Achievements
- Development of a two-stage optimization algorithm and reach the optimization requirement
- Integration of chaotic simulated annealing for improved convergence
- Implementation of local greedy and random neighborhood searches
- Performance evaluation with Gantt charts

#### Future Work
- Incorporation of dynamic scheduling capabilities
- Development of a user-friendly software interface
- Make the algorithm more scaleable to suit different situations

---
layout: center
class: text-center
---

# END

thanks for listening



