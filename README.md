A)SuperUser -
1)su
2)sudo nano /etc/sudoers
**add the username to the root data below in the format userName ALL=(ALL) ALL.|||  
3)usermod -aG sudo <userName>

--------------------------------------------------------------------
B)FullScreen & Bidirectional Clipboard+Drag&Drop -

1)sudo apt update 
2)sudo apt install build-essential gcc perl dkms linux-headers-$(uname -r)  
**Insert guest Additions Diskvfrom options and open it and open in terminal.|||  
3)findmnt  
**Copy the VBox_Gas Full DIrectory.||| 
4)sudo <Directory>/VBoxLinuxAdditions.run
5)sudo reboot
6)

--------------------------------------------------------------------
C)Pre-Requisite Packages -

1)sudo apt update
2)sudo apt upgrade
3)sudo apt install gcc g++ clang vim git build-essential cmake libgsl-dev libboost-dev libboost-program-options-dev
4)sudo apt install python3 python3-pip python3-tk git cmake build-essential libboost-dev libboost-iostreams-dev libboost-python-dev swig libfftw3-dev libgsl-dev python3-gi-cairo python3-scipy python3-matplotlib python3-pyqt5 python3-pyqt5.qtsvg python3-pyqt5.qtwebkit python3-pyqt5.qtserialport python3-lxml python3-yaml

D)EDA Tools Installation -

1)git clone https://github.com/kunalg123/vsdflow.git
2)cd vsdflow
3)chmod 777 opensource_eda_tool_install.sh
4)./opensource_eda_tool_install.sh

4)./vsdflow spi_slave_design_details.csv 
5)./vsdflow picorv32_design_details.csv

E)Testing - 

1)cd outdir_spi_slave
2)qflow display spi_slave

<------------------List of Tools installed-------------------->

1) Yosys - RTL Synthesis
2) blifFanout - High fanout net (HFN) synthesis
3) graywolf - Placement
4) qrouter - Detailed routing
5) magic - VLSI Layout tool
6) netgen - LVS
7) OpenTimer and OpenSTA - Static timing analysis tool


