# VSD_Physical_Design_workshop_1
It was a 5 day workshop, which was based on VLSI backend flow, where we worked on RTL to GDS flow with open source EDA tools and 180nm (osu_018 library).
The tools included:
1. Yosys: for Sythesis (.v) generation.
2. Graywolf: for Floorplaning, Placement and CTS (clock tree synthesis).
3. Qrouter: for complete routing of design.
4. Opentimer: for STA (Static Time Analysis).
5. Magic: for Layout view, extraction, DRC.
6. Ngspice: for spice simulation.
7. Qflow: all the above tools are appended in this GUI.

The main idea of the workshop was that each day everyone who had signed up got indiviual assingments which included a MCQ test, videos on the concepts of the MCQ and lab instruction and the MQC test also included questions based on lab and to complete the backend flow for RISC-V based Raven SOC.

The 1st day lab consisted:
1. Cloning the directory from Github.
2. Making sure wee had all the files (file count).
3. To check if all the tools were downloaded properly.
![1](https://user-images.githubusercontent.com/80053020/110277474-58e73b80-7ffb-11eb-8dda-1df7fcdd3786.png)

![file_cunt](https://user-images.githubusercontent.com/80053020/110277843-17a35b80-7ffc-11eb-92dc-5a319cf445e0.png)

![yosys](https://user-images.githubusercontent.com/80053020/110278012-74067b00-7ffc-11eb-87a9-fdbf4dcdcdcd.png)


# The 2nd day consisted:
1. Studing inverter and its transfer characteristics.
2. Simulation on ngspice of the spice model of the inverter.
3. Generating the sysnthesis file for the SOC.
4. Completing placement stage for the SOC

![SPICE_1](https://user-images.githubusercontent.com/80053020/110279817-bda49500-7fff-11eb-8fc5-7774c10e4d19.png)
The spice file consists of 4 main sections which the model/component defination, stimulus, simulation command and library model assigning.

![spice_simu](https://user-images.githubusercontent.com/80053020/110279332-f3954980-7ffe-11eb-8409-d5b645b85dda.png)

![SYNT_rep](https://user-images.githubusercontent.com/80053020/110279552-44a53d80-7fff-11eb-9613-270e14d87762.png)

![pre_place](https://user-images.githubusercontent.com/80053020/110280869-94850400-8001-11eb-99df-82eda257d92f.png)

![place_rep](https://user-images.githubusercontent.com/80053020/110280668-33f5c700-8001-11eb-94b9-a7d72da318a9.png)


The 3rd day consisted:
1. 









