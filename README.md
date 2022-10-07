
# Micro Challenge 1: Flexure Experimentation

## Links
- [Micro Challenge I - FabAcademy BCN Local Documentation](https://fablabbcn-projects.gitlab.io/learning/fabacademy-local-docs/challenge/c_1/)
- [Jeremy's post](https://publish.obsidian.md/jeremyparadie/%F0%9F%8C%90+Website/MDEF/MDEF+Academy/Micro+Challenge+1)

## Concept
I was interested in flexures as an inexpensive alternative to precision linear rails in machine tools. This video had me interested [XY HiPER NaP - YouTube](https://youtu.be/AJ7IHvOEr2o?t=15). I had no experience with flexures, so, with Santi's approval, I decided to model a bunch of different flexure configurations to be cut with a laser to provide me some intuition for how the parameters affect flexure performance.

## Design proposal
Parameters:
- Quantity of flexible elements
- Length of flexible elements
- Width of flexible elements
- Separation between two sets of elements, measured from the center of the two innermost flexible elements

Performance characteristics:
- Displacement per unit force
- Fragility
- Compactness

The relationships I find between the parameters and the performance characteristics will inform me about the feasibility of attempting to create a compact flexure-based precision linear motion platform with displacements at the scale of 100s of mm. 

I want to test:
- Different flexure lengths, including extremes
- Different flexure widths of the same quantity
- And of the same cross sectional area
- Different counts of parallel flexures
- Different distances between parallel flexures

## Planning
| Day              | Description   |
|:---------------- |:------------- |
| 2022-02-15 · Tue | Concept       |
| 2022-02-16 · Wed | Start design  |
| 2022-02-17 · Thu | Finish design |
| 2022-02-18 · Fri | Cut on laser  |

## Design process
![Pasted image 20220218152853](https://user-images.githubusercontent.com/14352758/190920755-2876b7f6-5435-40f6-8471-03b50089b317.png)

I've spent some time making everything parametric with the configurations feature in Onshape so I can easily generate all the test parts I want in an assembly. I also figured out how to get the text of those parameters embossed in the parts so it is easy to make comparisons, and it is all parametric- I can select or change the configuration I want for a particular part while in the assembly. 

![Pasted image 20220218155725](https://user-images.githubusercontent.com/14352758/190920756-0aa5befc-1594-40b4-9983-5007497c6c21.png)

I should probably do kerf compensation, but that might make it unnecessarily complicated.

Multiple parametric text generation processes on the same surface geometry is a huge pain because the surface geometry that I am passing to the text generation feature changes to be something different for every configuration because the last text generation process produced a different output for this configuration in comparison to all the others, so I need to make a separate part for each parametric text and boolean them together in two boolean features. Dealing with this took the majority of my time.

The parts laid out in the assembly in preparation for cutting with the laser:

![Pasted image 20220218152454](https://user-images.githubusercontent.com/14352758/190920754-2dbf3b56-46d4-42ce-bfc5-34c47a7cf434.png)

I tried FEA for the first time in Onshape with CAEplex:
![Pasted image 20220218165505](https://user-images.githubusercontent.com/14352758/190920751-f2ffb4dc-9e9f-4d30-a8d6-307ce10520cf.png)
CAEplex in Onshape is quite limited and seems to have bugs and I can't figure out how to select a particular configuration.

## Issues
![Pasted image 20220218144202](https://user-images.githubusercontent.com/14352758/190920753-2d0d3df5-4a24-46e5-98f1-afb9645a04d9.png)
Onshape is having trouble inserting my assembly into a drawing.
`An internal error has occurred; support code 726b5e304f6ab52225bd6808`

I am trying to see if I can get it as a sketch instead using an in-context part studio
oh dear. It does not like that either. `Onshape encountered a problem with your last operation. If the problem persists, please contact support. Support code 2c02f9b8ac93fb65b61c73eb.`

Whelp. Onshape has completely stopped responding- I can't even open the assembly any more. 

Luckily Onshape has good version control, so I reverted to before I started creating a drawing, and now I can at least open the assembly again. I might have to contact Onshape to see what is going on. 

Eventually, a few days later, it sorted itself out.

## Bill of materials
The MDF board I have is 612mm x 992mm x 2.6mm.

## Design files
- [Onshape project](https://cad.onshape.com/documents/cc54481488b53f500060c184/v/db58cddde439ec22f75fce03/e/e00a19d179e8e2f0cc177022?renderMode=0&uiState=620fb8b41a44f95f51dc22c5)
- [Drawing for cutting](https://github.com/JeremyParadie/MDEF-Academy-Micro-Challenge-1/blob/main/Drawing%20for%20cutting.svg)
- [Drawing for engraving](https://github.com/JeremyParadie/MDEF-Academy-Micro-Challenge-1/blob/main/Drawing%20for%20engraving.svg)

## Future development
I ran out of time this week and I was not able to actually cut the final design on the laser cutter. The next step is to do that, and then play around with the different flexures and get intuition for how the parameters effect flexure performance. I'd like to clamp them to a table and get out a dial indicator and maybe make a spreadsheet and compare deflection at various forces. 
