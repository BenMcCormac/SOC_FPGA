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

<img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/Summary.png">
<img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/Screenshot 2024-12-10 142510.png">
<img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/Screenshot 2024-12-05 173950.png">
<img src="https://raw.githubusercontent.com/BenMcCormac/SOC_FPGA/main/docs/assets/images/Screenshot 2024-12-10 153546.png">

## **Template Code**
Outline the structure and design of the Verilog code templates you were given. What do they do? Include reference to how a VGA interface works. Guideline: 2/3 short paragraphs, consider including screenshot(s).
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
