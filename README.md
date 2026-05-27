# Glass Shader for Unity 

This project was created for the Perception of Materials in VR research study (uses URP).  
  1. Personal Repo Link: https://github.com/13HarshithaK/Perception-of-Materials-in-VR  
  2. CVR repo link: https://github.com/Centre-for-Vision-Research/SOM-Perception-of-Materials-in-VR  

In order to render realistic looking glass on par with other materials rendered using the AmbientCG to Unity material converter 2.0 (found here: https://discussions.unity.com/t/free-ambientcg-to-unity-material-converter-2-0-1800-free-pbr-materials/902324), a few different resources available online were utilized. Some were tutorials on YouTube and one was from another git project. A total of 4 shaders were tested and deemed less than satisfactory for the sake of this project.  

Using components from those 4 shaders, 2 new shaders (shaders 6 and 7) were created (one of which was finally used for the project).  

The factors that were considered for the glass shader include:
  1. IOR/Refraction: whether this was visible/apparent and if it could be adjusted
  2. Reflection: if the shader was reflecting light and other objects nearby
  3. Transparency/tint: if the glass object had any color to it or was in any way more opaque than required/intended
  4. Shadows: if the object the shader was applied to allowed the object to create shadows
  5. Interaction with other glass objects: If a glass object was placed behind another and one were to view the first object through the second, would the first object be visible?

Shader 1:
  1. Accounts for it in some way but no actual effect observed in the output. When this value is changed, it seems to affect the reflection of the objects on its surface.
  2. Reflections scale based on zooming/panning around the scene and appear inaccurate.
  3. The rendered glass object itself is too transparent. This may be a good feature in some cases, but not for this project. It's hard to discern if a glass object is present at all in the scene.
  4. No shadows
  5. Other glass objects can be seen through it (barely)

Shader 2:
  1. Doesn't take input for IOR and doesn't account for it at the backend
  2. None (maybe adding a separate reflection probe will solve the issue)
  3. No tint, it's too transparent
  4. YES!
  5. Can see other glass objects through itself but because of the high level of transparency it's a little hard to

Shader 3:   
Taken from: @omid3098, https://github.com/omid3098/Unity-URP-GlassShader   
Has a lot of inputs, highly customizable, can also make it a textured glass surface (objects seen through it appear a little pixelated/diffused as an effect but that seems to be the intended end result. See the readme in the folder labeled attempt 3, or visit the link above ^)

  1. Some distortion is observed but if that counts as refraction remains uncertain (original creator's note: No refraction and only distorts behind the glass.)
  2. Faintly reflects light and ground plane
  3. A little dark tint
  4. No shadows
  5. Second glass object disappears when viewed through the first

Shader 4:  
  1. IOR is preset but refraction is not very evident
  2. Good reflections, of ground plane, of light sources and of other objects
  3. Perfect amount of tint, looks realistic for a glass object
  4. YES!
  5. Glass object behind is visible

<img width="60%" alt="glass 4" src="https://github.com/user-attachments/assets/5dd84daf-78ce-419d-a62f-bc5c349617cb" />  

We can see that different glass objects are visible when placed in front of each other. We can also see how other objects are reflected on the glass objects.

<img width="40%" alt="glass 4 refraction" src="https://github.com/user-attachments/assets/6fd96c4f-b011-48b5-85be-62b3277bf0ae" />  

(The red cube seen through the glass sphere demonstrates the shader's refraction)

Shader 7: Improves on shader 4 but adds a white tint instead. On the backend the IOR is lessened to the actual scientific value and isn't really evident because of that (this value needs to be exaggerated a little to make the simulation a little more realistic).    

<img width="60%" alt="Glass 7" src="https://github.com/user-attachments/assets/4db3e096-a661-4a6c-ba24-4704ddfe53b3" />  

We can see that different glass objects are visible when placed in front of each other. We can also see how other objects are reflected on the glass objects.

<img width="40%" alt="Glass 7 refraction" src="https://github.com/user-attachments/assets/c26c9162-60d8-49a8-b5ad-3978573f3244" />  

Shader 5:
  1. YES! Adjustable IOR!!
  2. Minimal to no reflections (maybe adding a reflection probe will help)
  3. Minimal but good, can distinguish it as a present glass object in a scene and isn't too hard to spot
  4. Yes to shadows
  5. Glass object behind primary glass object disappears and isn't visible.  

<img width="60%" alt="Glass 5" src="https://github.com/user-attachments/assets/409af212-d6f9-4cbe-bcbd-b7f2ad98204f" />  

We can see that different glass objects are NOT visible when placed in front of each other. But we do see better/more visible refraction. 

<img width="40%" alt="Glass 5 refraction" src="https://github.com/user-attachments/assets/f42bac19-8104-41c2-9a2b-0b4c165c1499" />    

Shader 6: Improves on shader 5 and makes sure that the glass object behind the other glass object is visible!

**Shader 7 was used for the project.**  
In order to use this shader, copy the shader file and place it in your project's material's folder.  

(Pictures to be added)

--------------------
NOTE:
The development of the experiment and its components (including the glass shader) took place between 2022-2023 and the sources for these resources were not recorded at the time. The git project's files have remained largely untouched, including the original creator's note. Unfortunately, the other 3 shaders can't be credited at this time. If the original creators can recognize their work, they are encouraged to reach out to me so they can be credited.
