# Unity Cube Simulator 3x3x3

![alt text](http://i.imgur.com/nlIc6H1.png "Game Scene")

___
#### Download Project
To download the whole project you can get it from the following link:

[Unity Rubik's Cube Simulator 3x3x3 - Unity 5 Edition](http://www.mediafire.com/download/r7i3a8a15e2jc2o/Cube_Simulator_3x3x3%282%29.7z)
___
#### Guide
Welcome to the Cube Simulator starter guide.

This is a short guide where I will be explaining how I made this simulator and the methodology behind it as well some technical things , it is recommended before you start that you have basic to average understanding of Unity and at least average experience in scripting/programming using C# , you should note that this guide will not discuss the source code from scratch but will only highlight major points where a developer will need to know in order to understand the flow of the simulator.
___
####Table of Contents :
___
**I.    Cube Construction**

**II. 	2D Cube Logic**

**III. 	3D Cube Logic**

**IV. 	Cube Scrambling Algorithm**

**V.    Cube Solving Algorithm**

**VI. 	Trail Rendering**

**VII. 	Inputs**
___
___
___
**I. Cube Construction**

Creating the cube is a very simple and straight forward process, you only need to use cubes, 26 of them and place them just like how the rubik cube looks , then you will need tiles which can be again formed from cubes themselves , these tiles are used in order to represent the cell color. You essentially need 3 tiles for each corner piece , 2 tiles for each edge piece , 1 tile for each center piece , you need to make sure you map and parent them correctly to their respective cubes, you may see the hierarchy in the project at Game scene or prefab for a better understanding. Materials are finally used to paint the cube , simple drag and drop operation , no biggy. :)

After creating all your pieces , remember to give each of them a tag. Ie (Center Piece 1 , Corner Piece 4...etc) , you also need to parent all the cubies under one parent which is Rubik_cube or whatever name you like , that is where you will throw in the CubeController script.

___
**II. 2D Cube logic (Cube2D.cs)**

Now you might be asking , why do we need this? Isn't it easier to just use colliders and triggers to detect cubies on some face and then parent them to that face and rotate the face?

This is also correct and can be done , however the main reason we need a 2D Cube Logic is because we might want to add extra functionality in the future , take for example detecting the "Solved" state of the cube , there also might be people who would like to practice solving certain states of the cube , a small convinient script can be written for that too , so it's just simply for future improvements and this is why I will be using it in the project.

There are different approaches that can be used to simulate a 2D cube , one of the easiest approaches is to represent the cube in 2D manner having three 3x3 arrays to represent the cubes , as we're using unity it will be easier to simply use tags and in this case we can fill the array with just the tag names respectively.

Next  in the code we simulate the 2D cube rotations via swapping , here's a snippet to rotate the red face:


```C#
if (face == 3) { //red
    //rotate corners
    string temp = cube1[0, 0];
    cube1[0, 0] = cube1[2, 0];
    cube1[2, 0] = cube1[2, 2];
    cube1[2, 2] = cube1[0, 2];
    cube1[0, 2] = temp;

    //rotate edges
    temp = cube1[0, 1];
    cube1[0, 1] = cube1[1, 0];
    cube1[1, 0] = cube1[2, 1];
    cube1[2, 1] = cube1[1, 2];
    cube1[1, 2] = temp;
}
```



Another thing that is needed which is to give out the selected face tags to the Cube Controller class that will use this information to map cubies to the selected to be rotated face, here's a snippet :

```C#
public string[,] getRedFace(){
        string[,] arr = new string[3,3];
        for(int i = 0;i   Rotate the white face.
- D / Down		 -> Rotate the yellow face.
- R / Right	 	 -> Rotate the blue face.
- L / Left 		 -> Rotate the green face.
- F / Front		 -> Rotate the red face
- B / Back	 	 -> Rotate the orange face.
- S / Solve		 -> Solves the cube.
- Left CTRL / Reverse	 -> Changes face rotation from clockwise to anti-clockwise and vice versa.

**UI Buttons**

- Scramble 		 -> Rotates 30 randomly selected faces clockwise or anti-clockwise.
- Reset 			 -> Resets the cube.
- Solve			 -> Solves the cube.

**Toggles**

- Trails			 -> Enable/Disable Trail Renderer.
- BGM			 -> Enable/Disable BGM.
- SFX 			 -> Enable/Disable SFX.

**Others**

- Speed 			 -> Dropdown list with rotation speeds using factors of 90.
- Timer			 -> Press space bar to start the timer count from 0 , press again to stop counting.
- Whole Cube Rotation   -> Hold right click and drag to rotate the cube in the direction you're dragging.


___
This was all there is regarding this cube simulator, the rest such as sound and canvas as well buttons manipulation can be learned from other tutorials as this guide's objective is to focus on the rubik's cube logic implementation in Unity.

If you feel this guide is missing or needs further explanation regarding something I overlooked , you may send me a message at Fahad@NoCakeNoCode.com and I will be more than happy to take a look at it and answer you back as soon as possible.
___





 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)