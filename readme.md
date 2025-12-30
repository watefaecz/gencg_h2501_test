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



## Week 02 — Lesson 02: Interaction & Motion

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

## Week 03 — Lesson 03: Grids & Iterative Patterns

In week three, I learned how loops and transformations can create patterns. I explored how `translate()` and `rotate()` change the coordinate system, which makes it easier to build complex arrangements. Once I understood that the origin can move and the canvas can rotate, it became much easier to design structured patterns.

#### Drawning 

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
This was the first week where I actively looked at pattern references to guide the visual direction. Possible references that fit this week (you can choose 1–2 to cite):
- **Vera Molnár** — grid-based variation and rule-driven repetition  
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


## Week 04

### Lesson 03 - Noise Textures

Week four introduced me to Perlin noise, which is a kind of structured randomness. Unlike the random() function’s jumpy unpredictability, noise() produces smoothly changing values that are great for organic motion and textures. I was amazed at how changing a single number gradually (like time) and feeding it into noise can create gentle, natural movements or patterns. It opened my eyes to a new way of controlling randomness. This week, I tried using noise to move shapes and to generate a patterned background. The results felt much more fluid and natural compared to using pure random values.

#### Sketch 1: Noise Motion

{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/p8Ce9X1gH" width="55%" height="425" frameborder="no"></iframe> {% endraw %}

*What it does:* This sketch uses Perlin noise to move a circle around smoothly. The variables x and y are set by calling noise() with a changing parameter t (and t+100 for y to ensure they use different noise sequences). The values noise() returns are between 0 and 1, so multiplying by width or height gives a position on the canvas. As t increases slowly, x and y wander in a smooth, leisurely way rather than jumping randomly. The background is drawn with a translucent black each frame (background(0, 20) uses an alpha value of 20 out of 255), which causes old frames to fade rather than instantly clearing. This creates a fading trail effect behind the moving circle. The overall impression is of a white orb drifting fluidly around in a dark space.

*How to change things:* - Adjust the speed of movement by changing the increment to t. A larger step (like t += 0.05) will make the motion less smooth and faster, while a smaller step will slow it down further. - The trail effect can be controlled by the second parameter in background(). Using a lower alpha (closer to 0) will make the trail last longer (more persistence), whereas a higher alpha (closer to 255) will make the trail shorter or even no trail at all if you use background(0) fully opaque. - To explore different paths, you can change the offsets added to t for x and y. Right now, y uses t+100 which is an arbitrary offset into the noise space; using different offsets (or even using one noise dimension for both x and y but with a phase shift) can create looping or diagonal motions.

#### Sketch 2: Random Noise Grid

{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/L-yfzTyAV" width="55%" height="425" frameborder="no"></iframe> {% endraw %}

*What it does:* This sketch generates a static textured pattern using 2D Perlin noise. It divides the canvas into a grid of 10x10 pixel cells. For each cell at position (x, y), it calculates a noise value c based on the x and y coordinates (scaled down by a factor of 0.02 to make the noise vary slowly across the canvas). The noise output (0 to 1) is multiplied by 255 to get a grayscale color value. Each cell is then drawn as a rectangle filled with that gray value. The result is an organic-looking cloudy texture across the canvas – areas of light and dark blend smoothly into each other, unlike a random checkerboard. It almost looks like a topographic height map or a cloudy sky in black and white.

*How to change things:* Changing the scale of the noise (the 0.02 factor) will change how smooth or detailed the texture is. A smaller factor (e.g. 0.005) will make very large, slow gradients (bigger blotches of light and dark), while a larger factor (e.g. 0.1) makes the pattern more tightly varied (smaller noise details). - You can use color instead of grayscale by taking separate noise values for different color channels. For example, you could do fill(noise(x*0.02, y*0.02)*255, noise(x*0.02, y*0.02, 100)*255, 150) to add some color variation. - Try using noise in the draw() loop to continuously change the texture over time (you’d use a third parameter in noise for time). This would create a slowly shifting pattern, like evolving clouds, though it will be more computationally intensive to update every frame.

## Week 05

### Lesson 04 - Drawing Machines

In this week I focused on building a drawing machine instead of generating a finished picture immediately. I wanted a tool that reacts to my input but still has its own “personality”, so the output feels partly controlled and partly surprising. I experimented with different brush behaviors, like stamping shapes, rotating them based on movement direction, and adding small variations through randomness. Compared to earlier weeks, this felt like a step forward because I wasn’t just drawing a static pattern anymore — I was building a system that can create many different results depending on how I use it.

At first, I worked with a very simple drawing machine that I had already developed earlier in the course, where it could only stamp a single shape and only varied in brush size while drawing. I liked this approach a lot and therefore decided to continue working with it and improve it further in this week. To do so, I used ChatGPT to help me upgrade my drawing machine from week 2 and explore ways of making it more interesting and expressive, especially by turning it into a more dynamic and responsive system rather than a static stamp. I still defined the idea and the core behavior myself, but I used ChatGPT to support the refinement of the system

#### Sketch 1: Drawing Machine With Help

{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/OQyHBfukB" width="120%" height="700" frameborder="no"></iframe> {% endraw %}

*What it does:* This sketch turns the mouse into a drawing machine that stamps shapes along my movement path. While I paint, the brush size constantly varies between 0.5 and 3, which makes the stroke feel more organic and less repetitive. Every time I click the mouse, the stamp shape changes, so I can switch styles while staying inside the same system. The stamps also rotate based on the direction of my movement, which makes the output feel more dynamic and “mechanical” instead of static.

*How to change things:* If I want denser or lighter drawing, I can change the step calculation int(d / 6) to a smaller or larger value, because that controls how many stamps are placed between mouse positions. I can make the brush size calmer or more chaotic by editing random(0.5, 3.0) to a narrower or wider range. If I want the shapes to change more or less often, I can adjust how many modes exist by changing % 5 and adding or removing stamp cases inside the stamp() function. I can also change the overall mood by shifting the color behavior in hueBase or by increasing the alpha value if I want stronger strokes.

## Week 06

### Lesson 05 - Reflection / Collect / Prepare

In this week, the focus was on reflecting on what I had already done and preparing for the upcoming lectures. I went through my sketches from the previous weeks and tried to improve them by cleaning up the visuals and refining some of the ideas. I also talked with classmates and looked at what they were working on, which helped me see different approaches and gave me new perspectives on my own work. During this week, I started experimenting with a clock graphic, but I did not yet arrive at a result that felt useful or convincing. I therefore decided to pause this idea and continue working on it later, which eventually allowed me to develop it further during the self-study week, when I had more time and a clearer concept.

## Week 07

### Lesson 06 - Faces / Parametric Generators

In this week, I started to work on a parametric face generator. Because I had already worked with ChatGPT in the previous weeks, I found the process especially enjoyable, as it allowed me to generate and test my ideas much faster. Since I understand the programming language myself, I could precisely control what I wanted to change and what should stay the same, instead of relying on AI to decide everything for me. This made the collaboration feel productive rather than limiting. I used ChatGPT mainly to help refine my ideas and structure the system, while the overall concept, visual direction, and experimentation came from my own interests. The result of this process is the face generator presented here, which represents my final outcome for this topic.

#### Sketch 1: Face Generator

{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/0CS0X1UYN" width="100%" height="800" frameborder="no"></iframe> {% endraw %}

*What it does:* This sketch generates an abstract, cubist-inspired face using a set of parametric rules and random values. Each time the sketch is refreshed, the proportions, positions, and shapes of facial elements such as the eyes, nose, mouth, hair, and mask change, while still maintaining a recognizable face structure. The generator works with layered geometric shapes and color planes, which creates a fragmented and painterly look inspired by cubist portraits. By pressing the space bar or clicking the mouse, a new “face variation” is generated, which changes the color palette, randomness seed, and whether outlines are drawn. This allows the sketch to produce a wide range of visually distinct faces from the same underlying system.

*How to change things:* The overall appearance of the faces can be changed by editing the color palettes in the PALETTES array, which directly affects the mood and contrast of the generated portraits. The amount of variation between faces can be increased or reduced by adjusting how much randomness is applied to sizes, rotations, and positions inside the individual face-part functions. If I want the faces to look more structured, I can narrow the random ranges, whereas wider ranges lead to more abstract and distorted results. The outline behavior can be controlled through the outlines variable, which makes the faces feel either more graphic or more painterly. Additionally, by modifying or adding new shape functions for elements like eyes, hair, or masks, the generator can be expanded to create an even larger visual vocabulary.

## Week 08

### Self Study - Clock / Time 

In week 8, I finally arrived at an idea for my clock graphic that really worked for me. I started with a simple concept: an Earth in the center of the canvas, a dark space background with stars, and satellites orbiting around the planet, combined with a working digital clock. At this stage, the clock logic itself already worked, but visually the sketch still felt unfinished and quite static. After I had this basic version running, I decided to further develop it and make it more engaging. I used ChatGPT as a support tool to help me expand the idea and improve the realism and playfulness of the system, while still controlling the overall direction myself. This led to the final version, where the clock is no longer just displayed, but actively drives what happens in the scene over time.


#### Sketch 1: Clock Graphic 

{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/QvxOEfCyk" width="110%" height="650" frameborder="no"></iframe> {% endraw %}

I created this sketch as a first working version of my clock idea, and I was already quite happy with the overall concept and structure. However, the result still felt a bit static and unfinished, as not much was happening visually over time. Because of that, I wanted to further develop the sketch and add more life and interaction to it, so that time would not only be displayed but also actively influence the scene.

#### Sketch 2: Clock Graphic With Help

{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/4NwhC7FTI" width="110%" height="650" frameborder="no"></iframe> {% endraw %}

*What it does:* This sketch visualizes time through a small narrative system set in space. At its core, it shows a stylized Earth placed in the center of the canvas, surrounded by a blinking star field and multiple satellites orbiting at different speeds. The digital clock inside the Earth displays the current time, and the progression of seconds, minutes, and hours directly affects what happens in the scene. Every second, satellites move forward in their orbits and the stars subtly change, which gives the impression of a living environment. Every minute, a meteor travels through space from outside the visible area and hits the Earth, creating a colorful crater and a short particle explosion at the impact point. Every hour, all existing craters are removed again through a larger explosion effect, which resets the surface of the planet. Through these interactions, time is not only shown as numbers but translated into visible events and changes.

*How to change things:* The overall behavior of the clock can be adjusted by changing how often events are triggered based on seconds, minutes, or hours. For example, meteor impacts could happen more frequently by reacting to seconds instead of minutes, or the hourly reset could be removed to allow the planet to slowly accumulate more damage over time. The visual style can be influenced by modifying the colors of the Earth, stars, satellites, and craters, which would immediately change the mood of the scene. The number of satellites, their orbit radius, and their speed ranges can also be adjusted to make the space around the planet feel calmer or more chaotic. Additionally, the particle explosion at the impact point can be made stronger or subtler by changing the number, speed, and lifetime of the particles. By tweaking these parameters, the same system can express very different interpretations of time.


## Week 09

### Second Checkpoint

In week 9, Guillaume gave us the opportunity to have individual face-to-face conversations about our journals. For me, most things were already clear, so I did not need specific help and instead focused on refining my graphics. During this time, I completed my face generator and further developed my clock graphic. I also talked with classmates about their projects, discussed different approaches, and exchanged ideas about challenges and solutions, which helped put my own work into a broader context.

## Week 10 

### Lesson 07 - Pixels

By week 10 I already had some skills in creating generative graphics, so I started to experiment more freely instead of only following one strict recipe. I really enjoyed working with pixels because it feels like manipulating the raw material of an image, not just drawing shapes on top. I tried two different approaches: one where pixels become a mosaic grid, and another where pixels are transformed into a drifting distortion. Both sketches helped me understand how small pixel-level changes can completely change the feeling of an image, even when the code stays relatively simple.

#### Drawing of Color Gradient

.png

#### Sketch 1: Color Gradient

{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/PQveq8zCR" width="100%" height="450" frameborder="no"></iframe> {% endraw %}

*What it does:* This sketch treats pixels as the main material of the image by directly assigning a color to every pixel on the canvas in each frame. The base color follows a rainbow gradient from top to bottom, while animated sine functions add horizontal and vertical motion, creating a waterfall-like flow. Because the hue values are recalculated every frame, the colors continuously change and shift across the entire image. This makes the gradient feel alive and dynamic rather than static.

*How to change things:* The speed of the color changes can be adjusted by modifying the value added to t each frame, where higher values result in faster motion. The strength of the waterfall effect can be controlled by changing the multipliers of the sine functions, which affects how strongly the colors bend and ripple. If I want a calmer result, I can reduce these values, and if I want a more energetic and chaotic look, I can increase them. Mapping the hue to the horizontal position instead of the vertical one would also completely change the visual direction of the gradient.

#### Sketch 2: Random Pixel Drift

{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/CvRoABq63" width="100%" height="450" frameborder="no"></iframe> {% endraw %}

*What it does:* This sketch first creates a simple base image directly in code, and then it transforms the image by shifting where each pixel reads its color from. The distortion is driven by noise, which makes the drift feel fluid instead of random static. Because the pixels are being reassigned every frame, the whole image looks like it is melting or glitching in a controlled way.

*How to change things:* The strength of the distortion is mainly controlled by the * 10 multiplier in dx and dy, so increasing it makes the drift stronger and more chaotic, while lowering it makes the effect subtle. The noise scale 0.01 controls the size of the distortion waves, so smaller values create big smooth warps and larger values create fine noisy jitter. If I want the motion to be slower or faster, I can change t += 0.01 to a smaller or bigger value.

## Week 11 - 14

### Project work

In weeks 11 to 14, I mainly focused on developing my final project. In week 11, I explored different ideas and thought about what kind of project I wanted to create. Quite early on, I decided to work on a drawing machine, as I had enjoyed creating and experimenting with these systems in the earlier weeks of the course. I started with a first iteration of the project and then continued to refine and develop it over the following weeks. During this time, my focus was mostly on the project itself, while I only made smaller updates to my journal. I will describe the project work and my process in more detail in the Final Project section.

## Final Project

### Idea

The idea for my final project was to create a generative drawing system that feels similar to paint splatters, combining randomness with a clear underlying structure. I was inspired by abstract painting, especially the work of Jackson Pollock, and by the drawing machine exercise we did during the course. I wanted to build a system that is not just a static image, but an interactive process where each input creates a unique visual result. The goal was to explore how structured algorithms can produce expressive and organic-looking graphics.

### Iterations

I developed the project through several iterations. In the first iteration, I focused only on generating random shapes with random colors to get a feeling for composition, scale, and interaction.

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

{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/gAVFZaKfg" height="450" frameborder="no"></iframe> {% endraw %}



### Failures / Excursions

I do not see the problems I encountered as failures, but rather as experiments that helped me understand the limits of the system. At one point, I exaggerated the dripping effect too much, which caused the paint to dominate the entire canvas and destroy the composition. In another experiment, I pushed the bleeding effect too far, so the shapes dissolved into the background. These extreme versions helped me find a balance between realism and control and informed the decisions I made for the final version.

#### First Excursion (Dripping Effect)

{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/NROVmDGpA" width="100%" height="450" frameborder="no"></iframe> {% endraw %}

#### Second Excursion (Bleed Effect)

{% raw %} <iframe src="https://editor.p5js.org/lukas01werner/full/VZzVet2x-" width="100%" height="450" frameborder="no"></iframe> {% endraw %}


### Code Explanation

The project is implemented in p5.js as an interactive generative drawing system. Different keybinds control the behavior of the system: A activates a warm color palette, S a cool palette, D a grayscale/ink palette, and F fully random colors. The C key clears the canvas, P saves the current image as a PNG, while R and B toggle the dripping and bleeding effects on and off.

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

For my journal, I used ChatGPT mainly as a support tool to help improve the clarity and structure of my written explanations. I always wrote the text myself first and then used ChatGPT to refine the wording, and I clearly referenced its use in every sketch where AI support was involved. What I really appreciated about this module was that it strongly encouraged me to work with my own code instead of relying on AI to generate everything for me. Over the weeks, I could clearly see my own progress, both in how I structured my sketches and in how confidently I experimented with generative systems.

Because I had to work on Tuesday mornings, it was not always possible for me to attend every lecture in person, although I joined online whenever I could. I worked on my journal on a weekly basis and continuously built on ideas from the course. In some weeks, the topics in my journal do not directly match the exact focus of the lecture, which is because I started to follow my own interests more strongly. For example, although clocks were introduced in week 4, I became particularly interested in noise textures at that time and explored them in more depth, while I later developed my clock-based graphic during the self-study week. This approach allowed me to stay motivated and to engage more deeply with topics that genuinely interested me, while still building on the core ideas of the module.
