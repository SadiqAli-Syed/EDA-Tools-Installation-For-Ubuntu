1)SuperUser -
su
sudo nano /etc/sudoers
#add the username to the root data below in the format userName ALL=(ALL) ALL
usermod -aG sudo <userName>

--------------------------------------------------------------------
2)FullScreen -

sudo apt update 
sudo apt install build-essential gcc perl dkms linux-headers-$(uname -r)  
<Insert guest Additions Diskvfrom options and open it and open in terminal> 
findmnt  
 <Copy the VBox_Gas Full DIrectory> 
 sudo <Directory>/VBoxLinuxAdditions.run
 sudo reboot

--------------------------------------------------------------------
3)Pre-Requisite Packages -

sudo apt update
sudo apt upgrade
sudo apt install gcc g++ clang vim git

sudo apt install python3 python3-pip python3-tk git cmake build-essential libboost-dev libboost-iostreams-dev libboost-python-dev swig libfftw3-dev libgsl-dev python3-gi-cairo python3-scipy python3-matplotlib python3-pyqt5 python3-pyqt5.qtsvg python3-pyqt5.qtwebkit python3-pyqt5.qtserialport python3-lxml python3-yaml

4)EDA Tools Installation -

git clone https://github.com/kunalg123/vsdflow.git
cd vsdflow
chmod 777 opensource_eda_tool_install.sh
./opensource_eda_tool_install.sh

./vsdflow spi_slave_design_details.csv 
./vsdflow picorv32_design_details.csv

5)Testing - 

cd outdir_spi_slave
qflow display spi_slave

<------------------List of Tools installed-------------------->

1) Yosys - RTL Synthesis
2) blifFanout - High fanout net (HFN) synthesis
3) graywolf - Placement
4) qrouter - Detailed routing
5) magic - VLSI Layout tool
6) netgen - LVS
7) OpenTimer and OpenSTA - Static timing analysis tool


