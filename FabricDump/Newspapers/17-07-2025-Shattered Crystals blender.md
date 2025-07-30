
https://www.youtube.com/watch?v=aeDwADt4C7I

This video provides a comprehensive tutorial on creating dynamic, fragmented, shattered crystal effects in Blender. It covers the entire process from initial setup and object fracturing using the Cell Fracture add-on to advanced material shading for a glowing, glassy appearance, and tips for artistic manipulation.

### Video Summary

#### [00:00:00] Introduction & Effect Overview
The video demonstrates how to create **fragmented, shattered crystal-like objects** in Blender, showcasing examples of its application. The technique is described as easy, highly customizable, and enjoyable to implement, requiring no high-end computer.

#### [00:00:27] Scene Setup
*   **[00:00:27] Background:** Start with a new, empty scene and set up a *dark background* as it generally enhances the visual appeal of these effects.
*   **[00:00:53] Initial Object:** Use a simple sphere for demonstration, but note that *any shape can be shattered*. Shade the object smooth.

#### [00:01:10] Using Cell Fracture
*   **[00:01:10] Basic Application:** Select the object, go to `Object > Quick Effects > Cell Fracture`. Clicking outside the menu will cancel settings.
*   **[00:01:23] Manipulating Fractured Pieces:**
    *   **[00:01:23] Individual Origins:** Change the `Transform Pivot Point` to *Individual Origins* to scale pieces independently.
    *   **[00:01:38] Effect Only Locations:** Enable `Effect Only Locations` (found in the proportional editing menu, but applies generally) to move/scale pieces without changing their individual scale, effectively "exploding" them outwards.

#### [00:02:18] Advanced Cell Fracture Settings
*   **[00:02:18] Recursion:** This is the most impactful setting. Increasing *recursion* shatters already fractured pieces into even smaller fragments, leading to more intricate and complex results.
    *   **[00:03:02] Recursion Level 1 Example:** Shows the initial effect of one level of recursion.
    *   **[00:03:49] Clamp Recursion:** Limits the maximum number of objects generated. Higher values can cause lag but allow for more detailed fractures.
*   **[00:04:40] Controlling Shatter Distribution:**
    *   **[00:04:40] Cursor Close/Far:** This setting allows you to control where the smaller, more recursive fractures occur relative to the 3D cursor.
    *   **[00:05:05] Placing the 3D Cursor:** Use `Shift + Right-Click` to position the 3D cursor.
    *   **[00:05:25] Applying Cursor Close:** When set to *Cursor Close*, smaller pieces will concentrate near the cursor, leaving larger chunks further away.

#### [00:06:05] Organizing & Manipulating the Shattered Object
*   **[00:06:05] Parenting to an Empty:** Select all fractured pieces, then the *Empty* (add `Shift + A > Empty > Sphere`), and parent them using `Ctrl + P > Object (Keep Transform)`. This allows easy movement of the entire fractured object.
*   **[00:06:40] Collections:** Move the fractured pieces to a new collection (`M > New Collection`) for better scene organization.
*   **[00:07:05] Manipulating Shape with Proportional Editing:**
    *   **[00:07:05] Proportional Editing:** Enable proportional editing (`O` key) to move multiple pieces together within a customizable radius (scroll wheel to adjust).
    *   **[00:07:45] Effect Only Locations (Proportional Editing):** Combine proportional editing with `Effect Only Locations` to scale or move pieces *outward* from a central point without altering their individual scale, creating an "explosion" effect.
    *   **[00:08:15] Falloff Types:** Experiment with different falloff types (e.g., Random, Sphere) for varied distribution effects.

#### [00:08:33] Lighting & Shading: Creating the Crystal Material
*   **[00:08:33] Initial Emission Attempt:** Simply increasing emission results in a flat, white glow, not the desired crystal effect.
*   **[00:09:25] Goal: Half Glass, Half Emission:** The desired look is a material that is *glassy in the middle and emissive/glowing on the edges*.
*   **[00:09:40] Pure Glass Material Setup:**
    *   Set `Transmission` to 1 and `Roughness` to a low value for a clear glass look.
    *   **[00:10:00] Grunge Effect:** Add a `Noise Texture` connected to a `Color Ramp` and then to the `Roughness` input for variation and a "grungy" appearance.
*   **[00:10:40] Driving Emission with Layer Weight:**
    *   Use a **`Layer Weight` node** (or Fresnel) to control emission strength. The *Facing* output of Layer Weight becomes brighter when edges face the camera and darker when surfaces face the camera.
    *   Connect the `Facing` output to the `Emission Strength` input of the Principled BSDF.
    *   **[00:11:15] Fine-tuning Emission:** Insert a `Color Ramp` and a `Math` node (set to *Multiply*) between the `Layer Weight` and `Emission Strength` to precisely control the glow's intensity and blend.
*   **[00:12:05] Adding Image Texture for Emission Color:** Connect an `Image Texture` (e.g., from Unsplash) to the `Emission Color` input for complex and varied glow colors.
*   **[00:12:35] Adding Volumetrics:**
    *   Add a large `Cube` to the scene.
    *   For its material, delete the `Principled BSDF` and add a `Volume Scatter` node, connecting it to the `Volume` output of the `Material Output`.
    *   Set `Density` to a low value (e.g., 0.01) and `Anisotropy` to 0.7 for atmospheric glow.
    *   Increase `Volumetric Light Bounces` in Render Properties (`Render > Light Paths > Volume`) for better volumetric lighting.
*   **[00:13:00] UV Unwrapping:** For image textures, ensure the shattered object is properly UV unwrapped (e.g., `Cube Projection`) to control how the texture maps to the pieces.

#### [00:13:40] Final Tips & Experimentation
The video concludes by encouraging viewers to **experiment** with different:
*   **Cell fracture settings** (recursion, noise, etc.)
*   **Object shapes** (cylinders, triangles, custom meshes)
*   **Material variations** (metallic versions, different glow colors, image textures)
*   **Environments** (placing abstract crystals in human-made scenes).

The main message is to use the techniques as a **starting point** for unique and creative renders by continuously trying new approaches and combinations.