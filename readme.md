# Generativ Computer Graphics Journal

## Week 01 — Lesson 01: Introduction & Foundations

### Exploration
This week, I started exploring p5.js and created my first small generative graphic. Although it was simple, I felt proud because I understood what I was doing and I could change small things to control the outcome. We also played the game **Sprouts** and experimented with randomized pictures on paper. This helped me think more freely about systems, randomness, and how a few simple rules can create complex results.

#### First p5.js graphic
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/wQgYe9mHZ" width="55%" height="425" frameborder="no"></iframe> {% endraw %}


We also played the game *Sprouts* and experimented with randomized pictures on paper, which helped me think more freely about generative processes and randomness in design.

#### Sprouts Game
picture of Sproutss Game


### References
This was my starting point, so I did not use a specific reference yet. I focused on understanding the basics and building confidence.

### Algorithmic Thinking
- A sketch is a system: the same instructions run every time, but changing parameters changes the result.
- Even in a simple first sketch, I already started thinking in “rules”:
  - define a canvas
  - choose shapes
  - set position and size
  - try changing a variable to see the visual effect

### Reflection
I liked that p5.js felt approachable. Even small changes in values immediately changed the visual output, which made me excited to keep experimenting. The Sprouts exercise also showed me that “random-looking” drawings can still come from clear rules, which fits well with generative design.



## Week 02 — Lesson 01: Interaction & Foundations

### Exploration
In the second week I learned how to make sketches respond to input like mouse presses and how to animate shapes by updating coordinates over time. It was exciting to see shapes move on their own and follow simple rules. I also worked with conditions (if-statements), for example to make an object bounce when it hits the edge of the canvas.

#### Sketch 1: Paint Brush 
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/SiOmD1lwA" width="55%" height="425" frameborder="no"></iframe> {% endraw %}

**What it does**
- Click + drag draws circles at the mouse location.
- Color and size vary randomly, so the stroke looks playful and organic.
- Nothing is drawn when the mouse is not pressed.

**How to change things**
- Fixed color: replace random fill() with one chosen color.
- Brush size: change the random range (e.g., random(5, 20)).
- Conditional brush: combine mousePressed with a key check (keyIsPressed).

#### Sketch 2: Bouncing Ball
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/zkZ3TfS1_" width="55%" height="425" frameborder="no"></iframe> {% endraw %}


#### Failure / Excursion
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/LUEE0Ozbm" width="55%" height="425" frameborder="no"></iframe> {% endraw %}
I used a single noise value for both x and y, and I also scaled/offset it so the circle sometimes goes outside the canvas. This breaks the intended smooth 2D wandering because the motion collapses into a predictable diagonal path with frequent edge clipping instead of exploring the full area, and I found it really interesting to test around with the bouncing ball because you can really manipulate physics.

**What it does**
- A circle moves by adding velocity (vx, vy) to position (x, y) each frame.
- If the circle reaches a canvas edge, the velocity direction flips.
- The background clears each frame, so you see one moving ball without trails.

**How to change things**
- Speed: change vx, vy.
- Start point: change initial x, y.
- Trails: remove the full background clear or use alpha background

### References
My main “reference” this week was my own experimentation: trying to recreate the feeling of drawing on paper and understanding how interaction changes the result.

### Algorithmic Thinking
- Input → rule → output:
  - if mouse is pressed → draw at mouse position
  - each frame → update position by velocity
  - if hitting a boundary → invert velocity
- Key idea: a small set of variables (x, y, vx, vy) can generate continuous motion.

### Reflection
This week made the sketches feel alive. I realized that interactivity changes the whole experience, because I am not only looking at an image — I am controlling a system. I also learned that a few simple conditions can create convincing behavior.



## Week 03 — Lesson 02: Grids & Iterative Patterns

In week three, I learned how loops and transformations can create patterns. I explored how `translate()` and `rotate()` change the coordinate system, which makes it easier to build complex arrangements. Once I understood that the origin can move and the canvas can rotate, it became much easier to design structured patterns.

### Starburst Lines

#### Sketch 1: Starburst Lines
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/czBR9FgVu" width="55%" height="425" frameborder="no"></iframe> {% endraw %}

**What it does**
- Moves origin to the center with `translate(width/2, height/2)`.
- Draws a line, then rotates the canvas and repeats.
- A loop + rotation creates symmetry very efficiently.

**How to change things**
- More lines: increase loop count and adjust rotation angle.
- Different look: change stroke/background colors.
- Different lengths: change the line end coordinates.

#### Failure / Excursion 
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/hEFdOCVFB" width="55%" height="425" frameborder="no"></iframe> {% endraw %}
I moved the origin to a corner-ish position and drew each line from an offset start point instead of (0,0), plus I changed the rotation step from PI/4 to PI/6. This makes the “burst” fail because the lines no longer converge in the center and the angles don’t evenly distribute, so it looks like a weird off-center spiral rather than a symmetric starburst.


### Isometric Cubes

#### Rough Sketch
<img src=„images/IsometricCubesDrawing.jpeg“>

#### Sketch 2: Isometric Cube Grid (Depth Gradient)
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/_7V401ulP" width="80%" height="600" frameborder="no"></iframe> {% endraw %}

**What it does**
- Nested loops create a grid of cubes (rows/columns).
- Each cube is built from 3 faces (top/left/right) to fake 3D.
- Offsets every second row to pack more naturally.
- Cube size grows across the canvas, creating a depth gradient.

**How to change things**
- Density: change number of rows/cols and spacing steps.
- Depth effect: change the lerp range for cube size.
- 3D illusion: increase/decrease shading contrast between faces.

### References
This was the first week where I actively looked at pattern references to guide the visual direction.
- **Sol LeWitt** — systematic drawings and simple instruction sets  
- **M. C. Escher** — tiling/tessellation thinking (for structured repetition)  
- **Victor Vasarely / Op Art** — optical rhythm through repetition

### Algorithmic Thinking
- “Pattern = repetition + variation”
  - repeat a simple element with a loop
  - change one variable each step (rotation, size, position)
- Transformations make systems easier:
  - translate to center → symmetry becomes simple
  - rotate a little each iteration → radial patterns appear
 
### Reflection
This week was a big step for me because I saw how quickly complexity can grow from simple rules. I also noticed that the hardest part is controlling variation: too much randomness looks chaotic, but small structured changes look intentional.



## Week 04 — Lesson 03: Noise Textures

### Exploration
Week four introduced me to **Perlin noise**, which felt like “structured randomness.” Unlike `random()`, noise changes smoothly, which makes it useful for organic motion and textures. I experimented with noise-driven movement and a static noise grid texture.

#### Sketch 1: Noise Motion
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/p8Ce9X1gH" width="55%" height="425" frameborder="no"></iframe> {% endraw %}

**What it does**
- Uses `noise(t)` and `noise(t+100)` to generate x/y positions.
- Increases `t` slowly so motion stays smooth.
- Uses a transparent background to create fading trails.

**How to change things**
- Motion speed: change how fast `t` increases.
- Trail length: change the alpha value in background.
- Different paths: change noise offsets (like `t+200`).

#### Sketch 2: Random Noise Grid
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/L-yfzTyAV" width="55%" height="425" frameborder="no"></iframe> {% endraw %}

**What it does**
- Divides the canvas into small rectangles.
- Each cell gets a grayscale value from 2D noise.
- The result looks cloudy and organic instead of random static.

**How to change things**
- Detail scale: change the noise multiplier (0.02).
- Color noise: map different noise values to RGB/HSB.
- Animated noise: add a time dimension in noise and update in `draw()`.

### References
- **Daniel Shiffman (The Coding Train)** — tutorials/examples using noise for motion/texture
- **Sarah Ridgley**

### Reflection
Noise felt like a “control upgrade” for randomness. The output looked more natural without me drawing anything by hand. I also learned that tiny parameter changes (like noise scale or t step) completely change the final feeling.



## Week 05 — Lesson 04: Drawing Machines

### Exploration
This week I focused on building a **drawing machine** instead of generating one finished picture. I wanted a tool that reacts to my input but still has its own “personality,” so the output feels partly controlled and partly surprising.

I started from a simpler drawing approach I developed earlier (especially the brush idea from week 2). I liked it a lot, so I continued improving it by experimenting with stamping behaviors, rotation, and small variations through randomness. I also used ChatGPT as a support tool to refine and upgrade parts of the system (structure and implementation), while the concept and direction stayed mine.

#### Sketch 1: Drawing Machine With Help
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/OQyHBfukB" width="120%" height="700" frameborder="no"></iframe> {% endraw %}

**What it does**
- Stamps shapes along the mouse movement path.
- Brush size varies, making the output less repetitive.
- Click changes the stamp shape (different modes).
- Rotation follows movement direction, making it feel more mechanical/dynamic.

**How to change things**
- Stamp density: adjust the step calculation.
- Calm vs chaotic: adjust the brush size random range.
- More/less modes: change the number of stamp cases.
- Mood: adjust hue behavior and alpha.

### References
This week is strongly connected to “machines that draw.” 
- **Jean Tinguely** — mechanical drawing machines
- **Sougwen Chung**
- **Harold Cohen (AARON)** — rule-based drawing as a system

### Algorithmic Thinking
- The system is not “one image,” but a generator:
  - input = mouse movement
  - rule = stamp every N pixels, rotate by direction, vary size
  - output = a unique drawing depending on how I move
- Parameters become artistic controls:
  - density, rotation sensitivity, shape set, color logic
 
### Reflection
I enjoyed this week a lot because it felt like I was designing a creative tool. I also noticed that “interesting” often comes from constraints: when I limit shapes or palettes, the system feels more intentional. This week also connected well to my later final project idea.



## Week 06 — Lesson 05: Reflection / Collect / Prepare

### Exploration
This week I focused on reviewing what I had already done and preparing for upcoming work. I looked through older sketches and tried small improvements (cleaning visuals and refining ideas). I also compared my work with classmates’ approaches, which gave me new perspectives.

### References
No new specific references this week — the focus was mainly on collecting, reviewing, and preparing.

### Reflection
It was helpful to pause and review. I noticed that I prefer systems that are interactive or that produce variety from one set of rules. I also started thinking about a clock-based sketch but decided to pause the idea until I had a clearer concept.



## Week 07 — Lesson 06: Faces / Parametric Generators

### Exploration
This week I worked on a **parametric face generator**. Because I already had experience working with ChatGPT from earlier weeks, I could test ideas faster. Since I understand the code myself, I could decide precisely what to change and what should stay fixed. I used ChatGPT mainly to support structure and refinement, while the concept and experimentation came from my own interests.

#### Failure / Excursion
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/nPgPYhxVR" width="100%" height="800" frameborder="no"></iframe> {% endraw %}
I rotated and misplaced the facial components (mask, planes, nose, mouth, neck) much more aggressively, and I redesigned the eyes with extreme squashing plus drifting pupils and mismatched geometry. This causes the piece to “fail” as a readable cubist face because the features no longer align like a portrait and the eyes become distorted symbols rather than believable facial anchors.

#### Sketch 1: Face Generator
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/0CS0X1UYN" width="100%" height="800" frameborder="no"></iframe> {% endraw %}

**What it does**
- Generates an abstract face from layered shapes and parameters.
- Pressing space/click regenerates a new variation (new randomness seed / palette / outlines).
- The face stays recognizable because key elements follow rules, even though details vary.

**How to change things**
- Mood: edit palettes in `PALETTES`.
- More/less abstraction: adjust random ranges for size/rotation/position.
- Style: toggle outlines or change stroke weight.
- Expand vocabulary: add new shapes for eyes/hair/masks.

### References
For this week, the visual direction is connected to cubist portrait styles. Possible references to cite:
- **Pablo Picasso** — cubist faces and fragmented portrait planes
- **Georges Braque** — early cubism and simplified facial structures

### Algorithmic Thinking
- “Generator rules”:
  - define a face bounding area
  - place facial features relative to that area
  - randomize within controlled ranges
  - keep constraints so the output still reads as a face
- This is a balance between:
  - fixed structure (face anatomy)
  - variable parameters (shape, palette, distortion)

### Reflection
I liked that one sketch can produce many outcomes. It made me think more like a designer of systems rather than a maker of single images. The challenge was making variation feel intentional, not just random, so I tried to keep strong structural rules.



## Week 08 — Self Study: Clock / Time

### Exploration
In week 8, I developed my clock concept further. I wanted to combine something I personally like (space themes) with the idea of time. I started with Earth in the center, a star background, satellites, and a working digital clock. After the first version worked logically, I upgraded the sketch so time is not only shown, but also drives events in the scene over time. I used ChatGPT as a support tool to help me expand the idea and improve the realism and playfulness of the system, while still controlling the overall direction myself. This led to the final version, where the clock is no longer just displayed, but actively drives what happens in the scene over time.

#### Rough Sketch
<img src=„images/ClockDrawing_Cut.jpeg“ >

#### Failure / Excursion
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/jkBQXY5LO" width="110%" height="650" frameborder="no"></iframe> {% endraw %}
I set the satellite orbit radius to be smaller than the Earth radius (so they fly “inside” the planet) and I changed the clock timezone from Europe/Zurich to UTC. This fails because the satellites no longer clearly orbit around Earth and the displayed time is not Zurich time, even though the scene still looks like an Earth clock.


#### Sketch 1: Clock Graphic 
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/QvxOEfCyk" width="110%" height="650" frameborder="no"></iframe> {% endraw %}

I created this sketch as a first working version of my clock idea, and I was already quite happy with the overall concept and structure. However, the result still felt a bit static and unfinished, as not much was happening visually over time. Because of that, I wanted to further develop the sketch and add more life and interaction to it, so that time would not only be displayed but also actively influence the scene.

#### Sketch 2: Clock Graphic With Help
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/4NwhC7FTI" width="110%" height="650" frameborder="no"></iframe> {% endraw %}

**What it does**
- The clock is integrated into the scene (inside the Earth).
- Seconds/minutes/hours trigger different events:
  - satellites orbit continuously
  - minute = meteor impact + crater + particle burst
  - hour = reset craters with a bigger explosion
- Time becomes visible through changes, not only numbers.

**How to change things**
- Frequency: trigger events on seconds instead of minutes.
- Persistence: remove the hourly reset so craters accumulate.
- Mood: change colors for stars, Earth, satellites, craters.
- Complexity: adjust number/speed of satellites and particles.

### References
I did not follow one specific artwork here. The main idea came from my own interests (space).

### Algorithmic Thinking
- Map real time → visual events:
  - if second changes → update movement and small changes
  - if minute changes → create a new meteor event
  - if hour changes → clear and reset a state (craters)
- State is important:
  - craters are stored and updated over time
  - the scene “remembers” past events

### Reflection
This sketch helped me understand that time-based systems are more interesting when they have memory and consequences. I liked that the clock became part of a small narrative system instead of a simple display.



## Week 09 — Second Checkpoint

### Exploration
In week 9, we had individual conversations about our journals. I used the time mainly to refine my graphics. During this time, I completed my face generator and further developed my clock graphic. I also exchanged ideas with classmates about challenges and solutions.

### References
No new references this week — the focus was on feedback and refinement.

### Algorithmic Thinking
- Refinement work is often:
  - debugging systems
  - tightening parameter ranges
  - cleaning visual composition
  - making the code more readable for iteration
 
### Reflection
This checkpoint helped me see that my journal is strongest when I document decisions and changes clearly. It also motivated me to keep polishing my sketches, not only creating new ones.

## Week 10 — Lesson 07: Pixels

### Exploration
By week 10 I felt more confident and started experimenting more freely. I really enjoyed working with pixels because it feels like manipulating the raw material of an image, not just drawing shapes on top. I tried two approaches: a flowing color gradient and a pixel drift distortion.

#### Rough Sketch
<img src=„images/ColorGradientPicture_Cut.jpeg“ >

#### Sketch 1: Color Gradient
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/PQveq8zCR" width="100%" height="450" frameborder="no"></iframe> {% endraw %}

**What it does**
- Sets every pixel color directly (pixel-level image generation).
- Hue follows a gradient, animated by sine functions.
- The whole image continuously shifts like a flowing waterfall.

**How to change things**
- Speed: change how fast `t` increases.
- Strength: change sine multipliers.
- Direction: map hue to x instead of y.

#### Sketch 2: Random Pixel Drift
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/CvRoABq63" width="100%" height="450" frameborder="no"></iframe> {% endraw %}

**What it does**
- Creates a base image in code.
- Reassigns pixel colors by shifting sampling coordinates.
- Noise drives the drift so it feels fluid, not jittery.

**How to change things**
- Distortion strength: adjust the multiplier on dx/dy.
- Wave scale: adjust noise scale (0.01).
- Motion speed: change `t += ...`.

### References
- **Ryoji Ikeda** — data/pixel intensity and minimal visuals
- **Rafael Rozendaal** — simple generative web visuals and gradients
- **Casey Reas** — rule-based systems that feel like “living images”

### Algorithmic Thinking
- Pixels as data:
  - loop through x/y
  - compute color from a formula (position + time)
  - write into the pixel array
- Distortion as remapping:
  - for each pixel, sample from a shifted coordinate
  - noise creates smooth displacement fields

### Reflection
This week made me realize that even “simple math” can create complex motion when applied to every pixel. I liked how direct pixel manipulation gives a completely different look than drawing shapes, even though it is still rule-based.

## Week 11 - 14

### Project work

### Exploration
In weeks 11 to 14, I mainly focused on developing my final project. I explored different ideas, and then decided quite early to work on a drawing machine, because I enjoyed building these systems in earlier weeks. I started with a first iteration and refined the project across multiple versions, mostly focusing on the final project while making only small journal updates each week.

### References
My main inspiration for the final project direction was **Jackson Pollock** and the idea of expressive paint splatters / action painting.

### Algorithmic Thinking
- Final project focus:
  - build a system that creates variety (unique splatters every time)
  - keep a strong rule set so it stays coherent
  - turn parameters into “art controls” (palette, density, drip/bleed behavior)

### Reflection
Working on one project over multiple weeks showed me how important iteration is. The most convincing results came from testing, failing, and tuning parameters, not from the first attempt.



## Final Project


### Idea
The idea for my final project was to create a generative drawing system that feels similar to paint splatters, combining randomness with a clear underlying structure. I was inspired by abstract painting, especially the work of **Jackson Pollock**, and by the drawing machine exercise we did during the course. I wanted to build a system that is not just a static image, but an interactive process where each input creates a unique visual result.

### Iterations
I developed the project through several iterations. First I made a rough sketch on paper. After that I started my first iteration. I focused only on generating random shapes with random colors to get a feeling for composition, scale, and interaction.


#### Rough Sketch
<img src=„images/DrawingFInalProject.jpeg“ >


#### First Iteration
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/k3TFG9PRe" width="100%" height="450" frameborder="no"></iframe> {% endraw %}


In the second iteration, I added droplets around the main shapes to simulate paint splattering outward in different directions.

#### Second Iteration
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/rk0-Vrgzv" width="100%" height="450" frameborder="no"></iframe> {% endraw %}


In the third iteration, I refined the splatter system by adding more variation to the droplets and introducing different sizes, directions, and densities.

#### Third Iteration
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/lrSmuTyy7" width="100%" height="450" frameborder="no"></iframe> {% endraw %}


Finally, I extended the system with animated elements such as dripping paint and ink bleeding to create a more realistic and dynamic result.

#### Fourth Iteration
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/gAVFZaKfg" width="100%" height="450" frameborder="no"></iframe> {% endraw %}



### Failures / Excursions
I do not see the problems I encountered as failures, but rather as experiments that helped me understand the limits of the system. At one point, I exaggerated the dripping effect too much, which caused the paint to dominate the entire canvas and destroy the composition. In another experiment, I pushed the bleeding effect too far, so the shapes dissolved into the background. These extreme versions helped me find a balance between realism and control.

#### First Excursion (Dripping Effect)

{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/NROVmDGpA" width="100%" height="450" frameborder="no"></iframe> {% endraw %}

#### Second Excursion (Bleed Effect)

{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/VZzVet2x-" width="100%" height="450" frameborder="no"></iframe> {% endraw %}


### Code Explanation
The project is implemented in p5.js as an interactive generative drawing system. Different keybinds control the behavior of the system: **A** activates a warm color palette, **S** a cool palette, **D** a grayscale/ink palette, and **F** fully random colors. **C** clears the canvas, **P** saves the current image as a PNG, while **R** and **B** toggle the dripping and bleeding effects on and off.

Whenever a key is pressed, a new splatter is generated. If the mouse is inside the canvas, the splatter appears near the mouse position with a small random offset; otherwise, it is placed at a random location. Each splatter consists of an irregular main blob created using Perlin noise and random rotation, which ensures visual variation. Around the blob, smaller droplets are distributed in biased directions to create a sense of movement.

Some droplets turn into animated drips after a short delay. These drips move downward, slightly rotate, and gradually become thinner and more transparent, simulating drying paint. In addition, an ink bleed effect causes the paint to softly spread into the background, imitating absorption by paper. All elements accumulate over time on the canvas, reinforcing the idea of a drawing machine rather than a traditional brush tool.

### Final Graphic

The final graphic is an accumulation of many individual interactions, resulting in a complex composition that feels organic and painterly. Each splatter is unique in shape, size, color, and behavior, yet the overall image remains coherent due to the structured rules of the system. The combination of static splatters, droplets, drips, and subtle bleeding creates depth and motion while maintaining visual balance.

#### Final Project Graphic
{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/eQseZGzM1" width="100%" height="450" frameborder="no"></iframe> {% endraw %}


### Project Reflection
I really enjoyed working with drawing machines during the course, and this project was my attempt to create a more sophisticated and expressive version of one. I was especially interested in the tension between randomness and structure, where the system feels unpredictable but is still clearly controlled by rules. The first three iterations of the project were developed independently by me, focusing on shape generation, interaction, and basic splatter behavior. During these early stages, I only used ChatGPT in a limited way, mainly to help with defining color palettes in the code.

After completing the third iteration, I decided to work with ChatGPT to further refine the system and push it toward a more realistic and convincing result. Together, we explored advanced behaviors such as dripping paint, ink bleeding, timing, and parameter tuning. While the conceptual direction, experimentation, and final decisions remained mine, ChatGPT supported me in improving and polishing the implementation. I am very happy with the final outcome and realized through this process how powerful generative computer graphics can be as a creative medium. Overall, this project strengthened my interest in generative systems and confirmed that algorithms can function as expressive artistic tools rather than just technical solutions.



## Final Reflection
For my journal, I used ChatGPT mainly as a support tool to help improve the clarity and structure of my written explanations. I always wrote the text myself first and then used ChatGPT to refine the wording, and I clearly referenced its use in every sketch where AI support was involved. What I really appreciated about this module was that it encouraged me to work with my own code instead of relying on AI to generate everything for me. Over the weeks, I could clearly see my own progress, both in how I structured my sketches and in how confidently I experimented with generative systems.

Because I had to work on Tuesday mornings, it was not always possible for me to attend every lecture in person, although I joined online whenever I could. I worked on my journal on a weekly basis and continuously built on ideas from the course. In some weeks, the topics in my journal do not directly match the exact focus of the lecture, which is because I started to follow my own interests more strongly. For example, although clocks were introduced earlier, I became particularly interested in noise textures at that time and explored them in more depth, while I later developed my clock-based graphic during the self-study week. This approach allowed me to stay motivated and to engage more deeply with topics that genuinely interested me, while still building on the core ideas of the module.
