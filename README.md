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

 ## steps to get tluplus file from itf files using icc2
  1. `grdgenxo -itf2TLUplus -i <.ITF file> -o  <.TLU+ file>`


You can get  
  - **LEF/DEF/.db(.lib file)** file from [Skywater github repo](https://github.com/google/skywater-pdk)/ few .db files specific to your design
  -  Gate level netlist - is the RTL synthesized file(post-synthesis RTL file).
  -  the other files can be found [here](https://github.com/bharath19-gs/synopsys_ICC2flow_130nm/tree/main/synopsys_skywater_flow_nominal)
 


## Steps for using skywater130nm files for design stage on synopsys's ICC2(for physical design).

  1. first set up the synopsys icc2 with a common setup file
    - the following happens in a setup file, [click here](https://github.com/kunalg123/icc2_workshop_collaterals/blob/master/standaloneFlow/icc2_common_setup.tcl) for reference.
      - set design name
      - set library name 
      - set design and reference library using (in this case [this file](https://github.com/bharath19-gs/synopsys_ICC2flow_130nm/blob/main/synopsys_skywater_flow_nominal/LEF/sky130_v5_7magic.lef))
      - read verilog netlist files if any(synthesised netlist files)
      - set mcmm file (multi corner multi mode file)
      - set the tech file (.tf file)
      - set routing layer direction offset list(setting each metal with one direction)
      -- rest can be reffered from [here](https://github.com/kunalg123/icc2_workshop_collaterals/blob/master/standaloneFlow/icc2_common_setup.tcl)
  
  2. secondly, use a dp_setup file 
  
  Now referring the main [tcl file](https://github.com/kunalg123/icc2_workshop_collaterals/blob/master/standaloneFlow/top.tcl), the important steps 
  3. NDM Library creation
  4. Read Synthesized Verilog
  5. Technology setup for routing layer direction, offset, site default, and site symmetry.
  6. Specify a Tcl script to read in your TLU+ files by using the read_parasitic_tech command
  7. Routing settings(setting min and max layers for routing)
  8. Checking design : Pre-floor planning
  9. Floorplanning 
  10. Power Grid pin connections 
  11. Input/Output pin placement
  12. Memory placement
  13. Placing macro's
  14. Configuring placement
  15. Reading parastic files(TLU+ files)
  16. Read constraints
  17. Create power
  18. Pin placement 
  19. Timing estimation 
  20. Place
  21. Clock Tree synthesis
  22. Routing 
  
  final GDSII file is generated and given for chip fabrication!
  
  
  ## References 
  1. [ICC2 collaterals](https://github.com/kunalg123/icc2_workshop_collaterals), [Kunal Gosh](https://www.linkedin.com/in/kunal-ghosh-vlsisystemdesign-com-28084836/) - VSD FOUNDER

  ## Thank you

  ## Author
  Bharath G S, VLSI enthusiast 
