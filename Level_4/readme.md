[Go to Map List of the Game](https://github.com/Ranajoy01/Map_List_Path_to_silicon_RISC_V_SoC_Tapeout_game)

---

[Go to Level List of the Map-7](https://github.com/Ranajoy01/Map_7_Path_to_silicon_RISC_V_SoC_Tapeout_game)

---

[Go to Previous Level](../Level_3/readme.md)

<div align="center">:star::star::star::star::star::star:</div> 

# Level-4: Pre-layout timing analysis and importance of good clock tree
  
<div align="center">:star::star::star::star::star::star:</div> 

## :zap: Use the custom inverter cell in PnR for picorv32
### 1) Fix issues related to layout for custom inverter to use in Openlane flow
#### Check the tracks info for PVT corner
![tr_inf](images/tr_inf.png)
#### Grid parameter change
##### Command
```
help grid
grid 0.46um 0.34um 0.23um 0.17um
```
##### Log
![gr_l](images/gr_l.png)
##### New grid
![gr_i](images/gr_i.png)

#### Cell layout condition for use in the PVT corner
#### A) Ports should be in the cross section of horizontal and vertical track to be considered as pins and properly routed
![cn_1](images/cn_1.png)

---
![cn_2](images/cn_2.png)
#### B) Cell width should be odd multiple of X pitch
- Consider the inner white rectangle
- Width of this is 3 grid box
#### C) Cell height should be odd multiple of Y pitch
- Consider the inner white rectangle
- Height of this is 8 grid box

### 2) Generate lef file
```
save sky130_vsdinv.mag
lef write
```
![lef](images/lef.png)

### 3) Add lef file and library files in `~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src`
### 4) Add these commands to config.tcl file
```
set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
```
#### Previous
![prec](images/prec.png)
#### After adding these
![postc](images/postc.png)

### 5) Use some extra line of codes for using custom cell in openlane flow
```
$ docker
$ ./flow.tcl -interactive
$ package require openlane 0.9
$ prep -design picorv32a
//extra lines start for include custom inverter
$ set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
$ add_lefs -src $lefs
//extra lines end for include custom inverter
$ run_synthesis
```
#### sky130_vsdinv is used during synthesis
![cin_1](images/cin_1.png)
#### Post synthesis timing analysis
![cin_2](images/cin_2.png)
<div align="center">:star::star::star::star::star::star:</div> 

## :trophy: Level Status: 

- All objectives completed.
- 🔓 Next level unlocked 🔜 [Level-5: Final steps for RTL2GDS using TritonRoute and OpenSTA](../Level_5/readme.md).
  
<div align="center">:star::star::star::star::star::star:</div> 



