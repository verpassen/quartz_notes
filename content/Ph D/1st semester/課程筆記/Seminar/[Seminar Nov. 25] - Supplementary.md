---
title: '[Seminar Nov. 25] - Supplementary'
updated: 2025-12-27 01:07:34Z
created: 2025-11-25 21:40:16Z
---

# Seminar Nov. 25 - Supplementary 

## seminar speach draft 

Hello everyone, my name is Brent. Today i am going to introduce/ share my research with you. 
The topics today I want to discuss is Physics-informed neural network applied in Direct energy deposition. Here is my outline. Because of the limited time, i would not talk about the details of methods or results. Let’s start 

1. Introduction of the DED

My research focus on a process called “Direct energy deposition”, which is one of the category of addtivie manufacturing. Direct Energy Deposition is an additive manufacturing process that uses a focused thermal source, like a laser, to melt and bond material—often metal powder—onto a substrate. It's essentially a form of high-precision welding used to build or repair components.

The concept is quite simple. The problem is DED is a complex process. The result we can take it as the outcome for these three factors : 

a. system specification
b. feedstock parameters
c. deposition variables 

All these factors are tightly coupled, making control difficult.
As shown on this slide, for different material, there are different process parameters region for each one. 
We use process maps like this to identify the safe operating windows for different materials. 
Deviating from this zone, whether by changing the energy density or the powder feed rate, 
leads to critical defects like Keyholing or Lack of Fusion." (Skip the formulas and specific material list.)
If I broke down the DED procedure, I would say , 1st moving heat source, 2nd powder feeding flux distribution and the interaction with laser beam , last but not least, the melt pool dynamics. 
The melt pool shape and and the phase transformation. 
Furthermore, when we care about the microstructure, then we will need to understand the cooling rate and the growth rate with the microstructure’s relationships. 
 


2. Introduction of the PINN 

As we just mentioned, because of the DED is a complex and coupled physics system. Therefore, to find the equations and at the same time, obtaining the experiment data is a expensive as well. 
wrapping up all thsee thing that I mentioned, i am looking help from my good friends , AI. 
I plan to use the advantage of the machine learning model to find the insight behind these data. 
From expertise system , optimization algorithm and with neural network, we’ve embrace the power of these tools to explore the insigts from data.
I choose Physics-informed neural network as my main tools to explore. 
OK, so , why PINNs? 

Traditional simulations are 'White Box' (pure physics) or 'Black Box' (pure data). 
PINN is a 'Grey Box' approach. It leverages the power of deep learning, but uses the governing Physical Laws (PDEs) as a direct constraint in the loss function, meaning it learns within the bounds of physics.  The core advantage is that we use Automatic Differentiation (AutoDiff) to compute derivatives for the physics residual without needing a mesh, making it a mesh-free solver."
Strength: PINNs needs less experimental data than traditional methods, and it is uniquely capable of solving forward and inverse problems. 
Challenge: We still face issues with robustness and scalability for complex, large-scale systems.



3. Literature review 

This is first finding that apply PINN in DED application
In 2020, Zhu et al . take the PINN architechture to simulate the single bead depsotiion. And he compare the heat history with the Finite element outcome. Got a quite good result.  
In 2024 , Peng and Panesar try a more complex structure. He try to simulate a multilayer processing in 3D dimension. 特別的是 , he used a moving frame to adjust the focus region for the boundary. 

In 2025, Guo , We see PINN's capability extended to complex problems: simulating Multi-Layer Deposition thermal fields (Peng & Panesar, Slide 18) and coupling networks to predict Temperature and Residual Stress simultaneously (Guo et al.)


4. Research gap 

Back to the main scenario 
In the DED application, we would like to know what parameters that I can apply on this material powder? Why we care about the temperature gradient , the thermal history ? because this affect the microstructure , the mechanical properties of  the buidling parts. 
Therfore, I would like to use three questions to wrap up the finding after the review.

1. how to define the suitable process parameters before processing?
2. How to implement the in-situ process monitoring and process control? 
3. how we optimize the process through these information from experiment and simulations ?  

5. what is my approach 

What i plan to do is combine the real-time data(videos from ccd and pyrometer) and the pre-defined parameters into the trained model to predict the results.
Keep monitoring the deviation between prediction and the true value to modify the machine. 
(Mainly will change process parameters) 

Now i roughly idea to implement this system. One to build up a database through experiment and CFD simulaitons. 
2nd Trainging the model through the data to verify the performance of the model.

last one to integrate all these factors to obtain a better process control. 

But now i still at the very beginning stage. so there is not so much results could share with you. 

I think this is all my present today. Thank you for all your attentions. 

----


