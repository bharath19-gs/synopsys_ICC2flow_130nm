# synopsys_ICC2flow_130nm
This repo is for synopsys icc2 flow for skywater 130nm PDK

What are the files needed?

the following files needed are as shown in the image 

![image](https://user-images.githubusercontent.com/76478624/213088789-8b139a29-bd20-4c49-82ca-4fc602e5ba2f.png)


1. LEF file - The LEF file is the abstract view of cells. It only gives the idea about PR boundary, pin position and metal layer information of a cell. 

2. Milkyway file/ Technology file 
  - Interconnet technology file(.itf) -  It defines cross section profile of the process this is an ordered list of conductor and dielectric layer definition statements the layers are defined from topmost dielectric layer to the bottom most dielectric layer excluding substrate.  
  - Technology file(.tf) - Technology File is the most critical input for physical design tools. It provides technology-specific information like the names and physical and electrical characteristics of each metal/via layers and the routing design rules.
  
3. TLU/TLU+ files - These modles are set of models contains advanced process effects that can be used by parasitic extractor in PnR tools for modelling these are generated from ITF filesTLUPlus is a binary table format that stores the RC coefficients. The TLUPlus models enable accurate RC extraction results by including the effects of width, space, density, and temperature on the resistance coefficients.(.itf is used to generate these files)


You can get the LEF file from [Skywater github repo](https://github.com/google/skywater-pdk) and the other files [here](https://github.com/bharath19-gs/synopsys_ICC2flow_130nm/tree/main/synopsys_skywater_flow_nominal)
 



## Thank you
