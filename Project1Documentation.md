### Computer Graphics Project 1 Documentation
# By Ryan Sippy & Jason Bellerjeau

## Project Overview
[Here](https://sippyr.github.io/ComputerGraphics/Project1.html) is the link to the project, and [Here](https://github.com/SippyR/ComputerGraphics/blob/main/Project1.html) is the link to the GitHub repository for the project.

The goal of this project was to create a simple 3D graphics application that utilizes basic rendering techniques to display a 3D scene in the form of a game.  The project was implemented in an HTML webpage using simple JavaScript.  The project allows users to move objects in a 3D environment, and interact with them using basic controls.  The project showcases fundamental concepts of computer graphics, including 3D transformations, rasterization, and camera projection.

## Project Design Plan
Our project was initially designed to be a trench run game, where the player would be consantly moving through a trench and would have to aim and shoot at targets. A whiteboard sketch of our initial design is shown below. Along with some notes on the design, and how we planned to implement the cube objects and rasterization of the scene.

![Project1_InitialDesign](./Images/Project1_InitialDesign.JPG)

![JasonNotesProject1](./Images/JasonNotesProject1.png)

However, throughout the development process, we decided against the trench run aspect of the game, and instead focused on creating a space shooter game where the player can move objects in a 3D environment and shoot at targets. The final design of the project in both rasterized and wireframe formats is shown below.

![RasterizedPreview](./Images/RasterizedPreview.png)

![WireframePreview](./Images/WireframePreview.png)

## Project Details
The player sits in a ship cockpit (drawn as a static frame on screen) with a small targeting square in the middle. Cubes and diamonds spawn at a random x/y position far in front of the player and move one unit closer every turn. The game is turn-based, so hazards only move when the player moves or shoots. A new hazard spawns every 5 moves. If a hazard reaches the camera, the game ends and the final score is shown.
## Implementation
- **Projection:** Each vertex is moved into camera space by subtracting the camera position, then projected by dividing x and y by z. The result is scaled to the grid size and centered. The v coordinate is flipped since the canvas origin is in the top-left corner.
- **Lines:** Edges are drawn by stepping along the longer axis of the line and setting a pixel at each step. The ship frame, targeting square, and wireframe mode all use this.
- **Rasterization:** Each object's faces are split into triangles. For each triangle, we loop over the pixels in its bounding box and use a barycentric (area comparison) test to decide whether a pixel is inside it. If it is, the pixel gets the face's color.
- **Depth:** We use the painter's algorithm. Objects are sorted by their average z, and faces within each object are sorted by average depth, so farther things get drawn first and closer things draw over them.
- **Shooting:** When the player hits space, each hazard's vertices are projected to find its 2D bounding box. If that box overlaps the targeting square, the hazard is removed and the score goes up.
- **Background:** Stars are single pixels that shift as the ship moves and wrap around the edges of the screen.
## Future Work
- **New Objects:** Create more diverse objects with different properties (ie needs to be shot twice, moves faster, etc)
- **Music:** Implement a small music loop that plays as the game progresses
- **SFX:** Sound effects for when the player shoots and the objects blow up
## Demo Video
[Computer Graphics Project 1 Demo](https://youtu.be/ilgxW7lQyIg?si=RtiiIiGtI6SiYOt1)
