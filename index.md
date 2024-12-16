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



 VGA_ColourCycle was also very useful as it demonstrated the use of counters in verilog. I didn't use this in my final project but something i did use was the particular method of displayin the colour. In this code there is a register/array called colour, this is used the entre 12 bit sequence that serve as the RGB values.

### **Simulation**
Explain the simulation process. Reference any important details, include a well-selected screenshot of the simulation. Guideline: 1/2 short paragraphs.
### **Synthesis**
Describe the synthesis and implementation processes. Consider including 1/2 useful screenshot(s). Guideline: 1/2 short paragraphs.
### **Demonstration**
Perhaps add a picture of your demo. Guideline: 1/2 sentences.

## **My VGA Design Edit**
Introduce your own design idea. Consider how complex/achievabble this might be or otherwise. Reference any research you do online (use hyperlinks).
### **Code Adaptation**
Briefly show how you changed the template code to display a different image. Demonstrate your understanding. Guideline: 1-2 short paragraphs.
### **Simulation**
Show how you simulated your own design. Are there any things to note? Demonstrate your understanding. Add a screenshot. Guideline: 1-2 short paragraphs.
### **Synthesis**
Describe the synthesis & implementation outputs for your design, are there any differences to that of the original design? Guideline 1-2 short paragraphs.
### **Demonstration**
If you get your own design working on the Basys3 board, take a picture! Guideline: 1-2 sentences.

## **More Markdown Basics**
This is a paragraph. Add an empty line to start a new paragraph.

Font can be emphasised as *Italic* or **Bold**.

Code can be highlighted by using `backticks`.

Hyperlinks look like this: [GitHub Help](https://help.github.com/).

A bullet list can be rendered as follows:
- vectors
- algorithms
- iterators

Images can be added by uploading them to the repository in a /docs/assets/images folder, and then rendering using HTML via githubusercontent.com as shown in the example below.

<img src="https://raw.githubusercontent.com/melgineer/fpga-vga-verilog/main/docs/assets/images/VGAPrjSrcs.png">
