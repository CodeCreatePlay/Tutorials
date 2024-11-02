## "Isolated lighthouse level design"

Welcome to the "Isolated Lighthouse Level Design" tutorial! In this tutorial, you'll learn to model and texture a production-ready level using Blender and Unity. We'll start by creating our level in Blender using the ANT landscape, Blender sculpting tools and displacement modifiers. Next, we'll use the Cycles rendering engine to generate texture maps, using the included SplatMap shader, before exporting everything to Unity for final rendering and playtesting.

> 🪧**This is a beginner friendly tutorial and no prior knowledge of advanced tools and features of either Blender or Unity are required, join [GirlsDevGames discord sever](https://discord.com/invite/WZ3GZCvVtg) to join chat with other artists and developers. Although I am using Blender (4.1) and Unity, however the concepts and techniques apply to other software and workflows as well.**

***

## Creating the base terrain mesh

Make sure you have the ANT landscape addon enabled **Edit > Preferences > Add-ons > AddMesh: ANT landscape** and add a new landscape **Add > Mesh > Landscape**. Change the settings in ANT landscape panel to get a island shape or copy my settings, you can see the results below.  

**ANT landscape settings:-**
- **Operator Present** = Mesa  
- **Noise Type** = fBm Fractal, **Random Seed** = 288, **Offset X and Y** = 75 and 50 respectively, **Dimension** = 1.20
- **Strata amount** = 2.10

The terrain at this stage is of quite low resolution. You can use proportional editing or the sculpt draw brush to modify the base shape, it becomes more challenging as you progress. For example, I corrected the narrow strips connecting the far left and right sides to the main terrain using the sculpt draw brush, along with a few minor adjustments, for example using the Smooth brush, I smoothed out some really rough pointy edges using. Remember, this is a creative, iterative process— it took me about an hour of reviewing the terrain from different angles to achieve a shape I was satisfied with. Finally, I added a subdivided plane with a 'Displace' modifier and applied a Perlin Noise texture to visualize water.

Let’s wrap up the modeling phase by UV mapping the level, although it’s not strictly necessary since the shader we'll use for baking textures employs tri-planar texturing technique, it’s still useful to have the level UV-mapped. This becomes important if you're using a shader in Unity that calculates slope and other data interactively for texturing.
- First apply transformation **Object > Apply > Rotation & Scale**.
- Apply UV-Mapping **Edit Mode > UV > Unwrap**.
- Optionally, add a checker texture to visualize stretching.


> At this stage, it would be really useful to create a backup copy of the original model. This way, if something goes wrong during later stages and you want to restart, you can easily revert to the original version.

***

## Creating the detailed version of terrain

Now let’s move on to creating the high-poly, detailed version of the level. The main areas needing attention are the vertical rock and cliff sides, which currently look flat. We'll use the 'Draw' brush to project details using alpha textures. You'll need some rock and cliff alpha brushes, which are included in the project files—append them to your project **xx > yy**.

- For the alpha brushes to project high-quality details, the polygonal mesh needs to be dense. In this case, a poly count of around 4 million should give good results. Use the 'Subdivision Surface' modifier **Modifiers > Add Modifier > Generate > Subdivision Surface** to subdivide the mesh. Increase both the Viewport and Render levels to 3, then apply the modifier.
-  Switch to sculpt mode, select the Draw brush (from the linked brushes panel), and choose a cliff brush (I used Cliff_03 for its large, broad-stroke details, perfect for the first detail pass).
- Set stroke method to Anchored, then right-click and drag along the vertical surfaces to begin adding detail. This is a creative process, so take your time and use reference images of rock and cliff formations for inspiration. You can see my results in the image below.



