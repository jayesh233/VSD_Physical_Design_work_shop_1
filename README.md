# VSD_Physical_Design_workshop_1
It was a 5 day workshop, which was based on VLSI back end flow, where we worked on RTL to GDS flow with open source EDA tools and 180nm technology library (osu_018 library).
The tools included:
1. Yosys: for Sythesis (.v) generation.
2. Graywolf: for Floorplaning, Placement and CTS (clock tree synthesis).
3. Qrouter: for complete routing of design.
4. Opentimer: for STA (Static Time Analysis).
5. Magic: for Layout view, extraction, DRC.
6. Ngspice: for spice simulation.
7. Qflow: all the above tools are appended in this GUI.

The main idea of the workshop was that each day everyone who had signed up got indiviual assingments which included a MCQ test, videos on the concepts of the MCQ and lab instruction and the MQC test also included questions based on lab and to complete the back end flow for RISC-V SOC.

# The 1st day lab consisted of:
1. Cloning the directory from Github.
2. Making sure wee had all the files (file count).
3. To check if all the tools were downloaded properly.

![1](https://user-images.githubusercontent.com/80053020/110277474-58e73b80-7ffb-11eb-8dda-1df7fcdd3786.png)

![file_cunt](https://user-images.githubusercontent.com/80053020/110277843-17a35b80-7ffc-11eb-92dc-5a319cf445e0.png)

![yosys](https://user-images.githubusercontent.com/80053020/110278012-74067b00-7ffc-11eb-87a9-fdbf4dcdcdcd.png)

Snap of one of the tools invoked in the terminal.


# The 2nd day consisted of:
1. Studing inverter and its transfer characteristics.
2. Simulation on ngspice of spice model of the cmos inverter.
3. Generating the sysnthesis file for the SOC.
4. Completing placement stage for the SOC

![SPICE_1](https://user-images.githubusercontent.com/80053020/110279817-bda49500-7fff-11eb-8fc5-7774c10e4d19.png)

The spice file consists of 4 main sections which are the model/component defination, stimulus, simulation command and library model assigning.
The components M1 reprensents Pmos with its width as 0.5u and leangth as 0.25u and the connection for its drain, gate, source, substrate respectively (out, in, Vdd, Vdd) followed by the technology file name (pmos).
The components M2 reprensents Nmos with its width as 0.375u and leangth as 0.25u and the connection for its drain, gate, source, substrate respectively (out, in, 0, 0).
The capacitor load connected between nodes out and 0 (gnd) with a value=10fF (femto farads). The Vdd and Vin connected between the respective nodes.
The dc simulation was carried out with the dc voltage going from 0-2.5 in steps of 0.05.

![spice_simu](https://user-images.githubusercontent.com/80053020/110279332-f3954980-7ffe-11eb-8409-d5b645b85dda.png)

The transfer characteristics of the cmos inverter with the switching threshold where the Vin=Vdd. So when the input is zero the nmos is off and the pmos is on, the output is connected to the Vdd through pmos and as a result output is high. When the input is high the pmos is off and the nmos is on so the ouput is connected to gnd through the nmos and hence output is low. The curve in the output is due to RC components where the pmos and nmos represents R and the output load represents C.

![SYNT_rep](https://user-images.githubusercontent.com/80053020/110279552-44a53d80-7fff-11eb-9613-270e14d87762.png)

Synthesis report of the RISC-V SOC, we can see the number of the components used in the SOC and the wires used. The Synthesis (.v) file consists of all the components (sequential and combinational) and their respective connections.

![pre_place](https://user-images.githubusercontent.com/80053020/110280869-94850400-8001-11eb-99df-82eda257d92f.png)

The starting view at the time of placement. The placement stage is the stage after the floorplanning (where all macro blocks, in/out pads, power planning is done) stage, where all the logic cells are placed in the core region with the aim that all the cells should have an unique position in the core. 

![place_rep](https://user-images.githubusercontent.com/80053020/110280668-33f5c700-8001-11eb-94b9-a7d72da318a9.png)

The placement log file.

# The 3rd day consisted of:
1. Spice simulation for inverter circuit wtih different capacitor load.
2. Spice simulation of a 12 transistor cmos circuit.
3. Completing the layout for the above circuit.
4. Analysing the .lib file for slew.

![rise_delay](https://user-images.githubusercontent.com/80053020/110308423-18e97e00-8026-11eb-8a8e-dc67cf872f81.png)

Simutlation of inverter circuit with 10fF load capacitor. when input is high (blue) the output (red) is low and vice versa. The ouput is little curved and not exact shape as input, this is due to RC components, The output is due to charging and discharging of the load capacitor. When the capacitor is charged or discharged completely the output than settles at that particular level and no longer a curve shape.

![rise_delay_20fF](https://user-images.githubusercontent.com/80053020/110308513-37e81000-8026-11eb-8e00-309288dc1154.png)

Simulation of the inverter circuit with the load capacitor as 20fF. We can see that the charging and discharging of the capacitor takes a longer time from 0v to Vdd and Vdd to 0 as compared to the 10fF load. This is bacause as the capacitance increases the settling time (tau) increases. where Tau=R*C.

![100](https://user-images.githubusercontent.com/80053020/110307828-60bbd580-8025-11eb-9514-c1f10a5d1e46.png)

The cmos transistor circuit along with its Euler path for the pmos and nmos part respectively. 

![spice_prelayout_code](https://user-images.githubusercontent.com/80053020/110307202-a88e2d00-8024-11eb-8b3f-cae3005e85d4.png)

A prelayout Spcie netlist for the 12 transitor cmos circuit.

![spice_prelayout](https://user-images.githubusercontent.com/80053020/110310339-6f57bc00-8028-11eb-9c31-0702f1585b78.png)

The prelayout simulation.

![spice_postlayout](https://user-images.githubusercontent.com/80053020/110309114-f146e580-8026-11eb-855e-534ee9925f54.png)

The Simulation after layout with inclusion of the extracted parasitics. We can a clear difference wrt the above output waveform.

![magic_1](https://user-images.githubusercontent.com/80053020/110309616-95309100-8027-11eb-932a-b25ff184ea32.png)

Generated by sourcing the tcl script.

![magic_layout_area](https://user-images.githubusercontent.com/80053020/110309686-a8dbf780-8027-11eb-8110-4626630b6682.png)

Finished layout.

![upper_treshhold](https://user-images.githubusercontent.com/80053020/110316861-569fd400-8031-11eb-8672-d822c4d67d21.png)

The std cell library for osu 180nm used for the RISC-V SOC.

# The 4th and 5th day consisted of:

1. Completing the routing stage of the SOC.
2. Timing analysis of the SOC.

![routin](https://user-images.githubusercontent.com/80053020/110316622-0294ef80-8031-11eb-9e7f-e27583dde851.png)

The routing stage for the RISC-V SOC.

![routin_rep](https://user-images.githubusercontent.com/80053020/110316694-13456580-8031-11eb-95cd-106241b88d43.png)
Routing report for the SOC.

![STA_SLACK](https://user-images.githubusercontent.com/80053020/110351771-2e2ccf80-805b-11eb-88b1-2ca97a1a604b.png)

The setup slack for the SOC without clock network delay propagated.

![sta_hold_whole](https://user-images.githubusercontent.com/80053020/110352769-510bb380-805c-11eb-818c-a8839028b77c.png)

Hold timings for the different data paths in the SOC without clock network delay propagated.

![propageted](https://user-images.githubusercontent.com/80053020/110352114-85cb3b00-805b-11eb-8f18-ed3e180063b1.png)

The setup slack with the clock network delay propagted.

![sta_whole](https://user-images.githubusercontent.com/80053020/110352847-697bce00-805c-11eb-8bc0-16b986b463a0.png)

Hold timings for the different data paths in the SOC with clock network delay propagated.

![hold_slack](https://user-images.githubusercontent.com/80053020/110352953-844e4280-805c-11eb-838a-321b55fc02e6.png)

The hold slack with the clock network delay propagted.

![sta_log](https://user-images.githubusercontent.com/80053020/110352676-32a5b800-805c-11eb-8722-23777e7f2456.png)

STA log file after timing analysis.

![pre_sta_freq](https://user-images.githubusercontent.com/80053020/110352993-916b3180-805c-11eb-8d8b-ca997ef5c808.png)

The prelayout frequency of the SOC.

![post_sta_freq](https://user-images.githubusercontent.com/80053020/110353118-b495e100-805c-11eb-9b69-25652f9cdad2.png)

The postlayout frequency of the SOC.

# Acknowledgement
Thanking Kunal Ghosh sir for his guidance and support.













