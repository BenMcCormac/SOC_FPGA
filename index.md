---
layout: home
title: FPGA VGA Driver Project
tags: fpga vga verilog
categories: final blog
---

Welcome to my FPGA VGA project. In this blog I explain my project and the steps I took towards the final project. Using a Basys3 board to demonstrate the ability to code Verilog and set up a FPGA.

## **Template VGA Design**
### **Project Set-Up**
The project is set-up with a design folder, a constraint folder and a simulation folder. Under the design folder is VGATop, this file manages and declares relations and labels of the variables and registers used in its three 
sub-files. The sub-files include a clock wizard, VGASync and the file that holds all the main logic of the VGA, the CoulourCycle. In ColourCycle I have a simple albeit lengthy nested if statement that defines which colour goes in which 10 by 10 cube. It also defines the colours used by defining it in one of seven arrays, allowing me to change the colours at will. Initially I intended to include code allowing me to invert the colours by switching one of the switches on the board but I scrapped the idea in favour of time. VGASync contains the parameters of the screen in use as well as the code for the logic used in the hardware e.g. multiplexors. The Clock wizard is self-explanatory, it defines the clock used throughout VGATop. In the constraint folder lies a file called "Basys3_Master.xdc", this contains code intended to interface dirrectly with the basys3 board. It defines the peripherals of the bourd to be used by the design folder.

<img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/Summary.png"> <img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/Screenshot 2024-12-10 142510.png">
<img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/Screenshot 2024-12-05 173950.png"> <img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/Screenshot 2024-12-10 153546.png">

## **Template Code**
To teach the class about verilog and to give us starting points from which we can adapt into our own code, we were given two itterations of sample code, one called VGA_ColourCycle and another called VGA_ColourStripes. These provided me with the platform from which I sought to develope my own code. 

VGA_ColourStripes in particular was very helpful as it demonstrated how to isolate sections of the screen. VGA_ColourStripes used if statements to say, 'in simple terms', fill from here to there with a colour. By saving col and row as arrays it could identify which pixels lie where, thus through the if statement define colour between row/col numbers. Below is my adaptation of the code to make boxes instead of stripes.

<img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/C.Boxes.PNG">

 VGA_ColourCycle was also very useful as it demonstrated the use of counters in verilog. I didn't use this in my final project but something i did use was the particular method of displayin the colour. In this code there is a register/array called colour, this is used the entre 12 bit sequence that serve as the RGB values. This was very handy in my own code to implement a feature i'll talk about later.

### **Simulation**
Explain the simulation process. Reference any important details, include a well-selected screenshot of the simulation. Guideline: 1/2 short paragraphs.
Simulation is the process of using its titular feature in Vivado to predict or simulate the input/output values of the registers defined in your testbench code. Below I provide an example of a JK Flip Flop testbench code, this code when simulated would provide its ouput diagram

<img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/TestBench.png">

### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.
Synthesis is the process of converting the high-level Verilog code into gate-level representations suitable for physical implementation on FPGAs or ASICs. [1]. Additionally, in Vivado after synthesis you can have it generate a hardware schematic of your code. In verilog code is a direct representation of code to hardware which allows it to generate these schematics for us.

<img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/SYNTH.png">

## **My VGA Design Edit**
Introduce your own design idea. Consider how complex/achievabble this might be or otherwise. Reference any research you do online (use hyperlinks).
For my own design I decided to make a piece of pixel art in the confines of the FPGA, but I am not very artistically talented so I borrowed a portion of a pice of art I found online [2]. I recreated the cropping of the image inside the software and then added a wa to use the switches on the chip we were using to have it shift between inverted colours and greyscale. In theory this was quite the easy piece of code to produce and it was, the problem lies within the method length. Pixel art though simplistic in appearance is suppriisingly difficult to keep track of, especially in code, despite mt best efforts to reduce the workload, the finished project was about 2500 lines long, yet still quite feasible.

### **Code Adaptation**
In the beginning I took the VGA_ColourStripes template code, and by utilising nested if statments I specified the colours used in each square. To make the process quicker and to reduce the workload, I labelled the seven colours used in varaibles ONE-SEVEN. This was inspired by VGA_ColourCycle code that stored the RGB values like this `COLOUR <= 12'b000000000000`. Adapting it to look like this: `ONE <= 110100110100 ...  COLOUR <= ONE`. This had the unintentionable effect of also allowing for easier code to be used for the colour changing function of my project, by doing it this way I was able to make a state machine based on active switches that allowed for colour switching at any time.

### **Synthesis**
My project's generated schematic has some obvious differences from the template, mainly towards the end where each of the three colour registers have four gates that represent the switches I use to define if it should invert and/or greyscale the colours of the ouput. Y Take notice of the three blocks representing the three main components of VGA_Top, VGA_Sync which manages communication between the cells, VGA_ColourCycle is where my code lies (unfortunately not renamed) and clk_wiz which is the clock that handles timings for the project

<img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/Screenshot 2024-12-10 151514.png">

Unfortunately due to the extreme lengthy nature of my code the implementation diagram is quite large bearing over 10000 nets. This all cultivates to the expected ouput of my piixel art snippet.

<img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/Screenshot 2024-12-10 142228.png"> <img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/Screenshot 2024-12-10 142806.png">
### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.
Initially I didn't realise that in doing my method of colour loading I unintentially made the output a lot more blue than expected

<img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/Failed_Blue.png">

Fortunately I realised in time that the values put into the colour register are read LSB first, I rectified the project resulting in these final outputs.

<img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/Success1.png"><img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/Success2.png">
<img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/Success3.png"><img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/Success4.png">

## **References**

[1] Unrepo, [online]. Available: [https://www.unrepo.com/verilog/verilog-simulation-and-synthesis-a-detailed-tutorial](https://www.unrepo.com/verilog/verilog-simulation-and-synthesis-a-detailed-tutorial). [Accessed 13/12/2024].            
[2] Pixilart, [online]. Available: [https://www.pixilart.com/art/scara-new-soundtrack-58308b5297eb195?ft=topic&ft_id=5](https://www.pixilart.com/art/scara-new-soundtrack-58308b5297eb195?ft=topic&ft_id=5). [Accessed 21/11/2024].
