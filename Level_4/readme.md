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
#### B) Cell width should be odd multiple of X pitch
![cn_2](images/cn_2.png)
#### C) Cell height should be odd multiple of Y pitch
![cn_3](images/cn_3.png)

<div align="center">:star::star::star::star::star::star:</div> 

## :trophy: Level Status: 

- All objectives completed.
- 🔓 Next level unlocked 🔜 [Level-5: Final steps for RTL2GDS using TritonRoute and OpenSTA](../Level_5/readme.md).
  
<div align="center">:star::star::star::star::star::star:</div> 



