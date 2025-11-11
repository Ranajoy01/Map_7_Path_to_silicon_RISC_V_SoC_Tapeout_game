[Go to Map List of the Game](https://github.com/Ranajoy01/Map_List_Path_to_silicon_RISC_V_SoC_Tapeout_game)

---

[Go to Level List of the Map-7](https://github.com/Ranajoy01/Map_7_Path_to_silicon_RISC_V_SoC_Tapeout_game)

---

[Go to Previous Level](../Level_2/readme.md)

<div align="center">:star::star::star::star::star::star:</div> 

# Level-3: Design Library cell using Magic Layout and ngspice characterization
  
<div align="center">:star::star::star::star::star::star:</div> 

## :zap: Clone custom CMOS inverter cell design and open Cell Layout
### 1) Clone inverter cell design in openlane directory-
```bash
$ git clone https://github.com/nickson-jose/vsdstdcelldesign.git
```
### 2) Open cell layout-
```bash
magic -T ./libs/sky130A.tech sky130_inv.mag &
```
### 3) Command logs-
![log1](images/log1.png)
### 4) Layout result-
![lt1](images/lt1.png)

### 5) CMOS inverter structure verification-
#### 5.1) NMOS check-
![51](images/51.png)
#### 5.2) PMOS check-
![52](images/52.png)
#### 5.3) NMOS drain and PMOS drain connectivity check-
![53](images/53.png)
#### 5.4) NMOS source to Vgnd check-
![54](images/54.png)
#### 5.5) PMOS source to Vpwr check-
![55](images/55.png)

<div align="center">:star::star::star::star::star::star:</div> 

## :zap: CMOS inverter layout design process reference and DRC check
### 1) Go through the [vsdstdcelldesign repository readme file](https://github.com/nickson-jose/vsdstdcelldesign) to understand the layout design process
- Generally 16 mask CMOS fabrication process is used.
- Importance of different layers
   - pwell
   - nwell
   - metal layers
   - local interconnect
   - contact (cross marked region)
   - diffusion region
### 2) DRC check
- Magic tool is very much dependent on design rule check
- Now delete a portion of layer to observe DRC error-
  
``` Select box using mouse and click the scroll wheel```

![drc_er](images/drc_er.png)
  
<div align="center">:star::star::star::star::star::star:</div> 

## :zap: Extract spice netlist for custom inverter-
### 1) Commands used
```bash
# Generate .ext file from layout
extract all
# Consider parasitics
ext2spice cthres 0 rthres 0
# Convert .ext to .spice
ext2spice
```
### 2) Command log
![log2](images/log2.png)
### 3) Generated netlist-
![ext2sp](images/ext2sp.png)

<div align="center">:star::star::star::star::star::star:</div> 

## :trophy: Level Status: 

- All objectives completed.
- I have learned about timing paths ,timing graph, setup and hold analysis, slack, critical path, interpretetion of timing report ,variation in real case.
- 🔓 Next level unlocked 🔜 [Level-4: Pre-layout timing analysis and importance of good clock tree](../Level_4/readme.md).
  
<div align="center">:star::star::star::star::star::star:</div> 



