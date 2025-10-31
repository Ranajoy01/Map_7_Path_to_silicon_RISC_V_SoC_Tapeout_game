[Go to Map List of the Game](https://github.com/Ranajoy01/Map_List_Path_to_silicon_RISC_V_SoC_Tapeout_game)

---

[Go to Level List of the Map-7](https://github.com/Ranajoy01/Map_7_Path_to_silicon_RISC_V_SoC_Tapeout_game)

---

[Go to Previous Level](../Level_1/readme.md)

<div align="center">:star::star::star::star::star::star:</div> 

# Level-2: Good Floorplan vs Bad Floorplan and introduction to library cells


## List of Objectives

- :microscope: <b>Pracical Objective-1:</b> []()

  
<div align="center">:star::star::star::star::star::star:</div> 

## :microscope: 1 : : `picorv32a` chip floorplanning and related terms
### :zap: 1.1 : : Run floorplan using openlane flow
- In openlane flow after synthesizing the design, we can perform floorplan. Synthesis is done in the previous level. Now run floorplan using the following command in docker shell-
#### Command 
```bash
$ run_floorplan
```
#### Start Floorplan log
![1_fst](images/1_fst.png)
#### End Floorplan log
![1_fen](images/1_fen.png)

- Def file is generated `~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/31-10_08-28/results/floorplan/picorv32a.floorplan.def` 

---

### :zap: 1.2 : : Load the generated def (design exchange format) file in magic and visualize floorplan layout 
#### Command and log
```bash
$ magic -T ~/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/31-10_08-28/tmp/merged.lef def read ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/31-10_08-28/results/floorplan/picorv32a.floorplan.def &
```
![1_fp_lg](images/1_fp_lg.png)

- tech file, lef file and def files are provided to magic
- & at the last specify that end prompt after opening layout in magic

#### Floorplan Layout
![1_fp_lt](images/1_fp_lt.png)

- picorv32a floorplan layout is visualized
- A command shell also opened

---

### :zap: 1.3 : : (Floorplan Operation-1) Define die and core area
#### Synthesized netlist to die and core definition
- Different cell size of same cell provide different speed.
- So as per logic and speed requirement the cells are selected.
- Total cell occupied area and utilization factor help in die size calculation. 

#### Utilization factor and aspect ratio 
- Priority order (highest first) of the configuration files are shown below
   - 1) ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/sky130A_sky130_fd_sc_hd_config.tcl
   - 2) ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/config.tcl
   - 3) ~/Desktop/work/tools/openlane_working_dir/openlane/configuration/floorplan.tcl

- In the file-3 we see that

![1_hpr](images/1_hpr.png)
- In the file-1 we see that

![1_hpr_1](images/1_hpr_1.png)
- <p align="center">
$$
\text{Utilization Factor} = \frac{\text{Area of all netlist cells}}{\text{Area of core}}
$$
 </p>
- Utilization = 50 %
- Aspect ratio =1 (Width and height same, square shape)
- Vertical metal layer fo I/O = 3 (actually one more than the specified value)
- Horizontal metal layer for I/O =4 (actually one more than the specified value)

 
- In the floorplan log we can see that-

![1_dc](images/1_dc.png)

- Die height -> 671.405 micron
- Die width -> 660.685 micron
- Core height -> 647.36 micron
- Core width -> 649.52 micron
- Die area -> 4,43,587.212425 square micron
- Core are -> 4,20,473.2672 

---

### :zap: 1.4 : : (Floorplan Operation-2) Preplaced cells
#### Importance of preplace cell
- Reusable, layout ready blocks are preplaced during floorplan
- Macros, Special IPs are preplaced cells 
- These are like black box, block I/O s are present.

---

### :zap: 1.5 : : (Floorplan Operation-3) Decoupling capacitor
#### Importance of Decap
- If power supply is very far from the circuit then voltage fluctuation due to wire R and L.
- To avoid this fluctuation and unstability decoupling capacitor are placed between Vdd and Vgnd.
- Works as local chanrge and energy storage.

#### Decap cells in floorplan layout
![1_fp3](images/1_fp3.png)

--- 
### :zap: 1.6 : : (Floorplan Operation-4) Power planning 
#### Importance of power planning
- Ground bounce and voltage droop is caused due to long power network
- Power rail grid is used for providing stable power to all cells
- Generally power distribution network is part of floorplan but in opeenlane flow it is performed after CTS.

---
### :zap: 1.7 : : (Floorplan Operation-5) Pin placement and logic cell placement blockage
#### Importance of pin placement and blockage
- Where to place I/O pins are defined by user near the edges of die
- Data pins are smaller than clk pins for providing fast clk (less resistance path)
- Logic cell placement blockage is the region where no logic cells can be placed (pins are placed there)
#### Pin placement in floorplan layout
![1_fp5](images/1_fp5.png)

- Pins are placed in equal distance from eachother
- Vertical pins in metal layer 2
![1_fp51](images/1_fp51.png)
- Horizontal pins in metal layer 3
![1_fp52](images/1_fp52.png)
---
### :zap: 1.8 : : (Floorplan Operation-6) Tapcell placement
#### Importance of tapcell
- Connect n- well to Vdd and substrate to ground to avoid latch-up
- Surrounding tapcells are diagonally equidistant.
#### Tap cells in floorplan layout
![1_fp6](images/1_fp6.png)


<div align="center">:star::star::star::star::star::star:</div> 

## :trophy: Level Status: 

- All objectives completed.
- I have learned about timing paths ,timing graph, setup and hold analysis, slack, critical path, interpretetion of timing report ,variation in real case.
- 🔓 Next level unlocked 🔜 [Level-3: Design Library cell using Magic Layout and ngspice characterization](../Level_3/readme.md).
  
<div align="center">:star::star::star::star::star::star:</div> 



