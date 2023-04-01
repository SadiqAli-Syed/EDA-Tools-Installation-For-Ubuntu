-----------This Readme consists of solutions to Issues with OpenSource EDA_Tools installation that I, as newbie, have Faced and couldn't find a goto solution---------
                                Addressed:
                                A)Superuser permission aka not in Sudoers file,
                                B)Running Virtual Machine in FullScreen and Copy-Pasting text btw Windows and Linux,
                                C)Installing all required packages,
                                D)EDA tools installation(Same as VSD's Method),Breaks the gcc and g++ packages by the end on of it in an attempt to turn
                                  them to gcc--7, g++--7 versions and make them compatible with cmake,Fix available in next Step,
                                E)Fixing some issues with the above method ("Especially OpenTimer"),
                                f)Testing if all mentioned Packages have been installed properly.


-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
A)Becomming a SuperUser (sudo capable) -Run the Following Commands in Terminal(One at a Time)

1)su
2)sudo nano /etc/sudoers
-----------------------add the username to the root data below in the format <UserName> ALL=(ALL) ALL, Replace <UserName with your username--------------------
3)usermod -aG sudo <UserName>
  For further Assistance in case of failure, refer YT Tutorials on "How to add user to sudoers file/How to become a Superuser in Ubuntu virtual machine"

---------------------------------------------------------------------------------------------------------------------------------------------------------------
B)FullScreen & BiDirectional Clipboard-

1)sudo apt update 
2)sudo apt install build-essential gcc perl dkms linux-headers-$(uname -r) 
  
--From "Devices" option in top bar,Click Insert guest Additions Disk & wait for few secs and click on cd Icon in Docker,Rightclick & open in terminal--
3)findmnt  
------------------------Copy the Full DIrectory "/media/<UserName>/VBox_Gas_XYZ and paste in below int he position of <Directory>-----------------------------
4)sudo <Directory>/VBoxLinuxAdditions.run
5)sudo reboot
6)PowerOff the ubuntu virtual machine and click settings Icon on right in the Oracle VM VirtualBox app,Navigate to General>Advanced>Shared Clipboard and select Bidirectional

--------------------------------------------------------------------------------------------------------------------------------------------------------------
C) Installing Pre-Requisite Packages/Dependencies -

1)sudo apt update
2)sudo apt upgrade
3)sudo apt install gcc g++ clang vim git build-essential cmake libgsl-dev libboost-dev libboost-program-options-dev
4)sudo apt install python3 python3-pip python3-tk git cmake build-essential libboost-dev libboost-iostreams-dev libboost-python-dev swig libfftw3-dev libgsl-dev python3-gi-cairo python3-scipy python3-matplotlib python3-pyqt5 python3-pyqt5.qtsvg python3-pyqt5.qtwebkit python3-pyqt5.qtserialport python3-lxml python3-yaml

  -------------------------------------------------------------------------------------------------------------------------------------------------------------
D) EDA Tools Installation -

1)git clone https://github.com/kunalg123/vsdflow.git
2)cd vsdflow
3)chmod 777 opensource_eda_tool_install.sh
4)./opensource_eda_tool_install.sh

 --------------------------------------------------------------------------------------------------------------------------------------------------------------
E)Errors and Failure with OpenTimer:-
  
     $ "Cmake ../" or "make" Errors:
          Run the following commands (1,2)
          
          1) sudo apt install --reinstall gcc g++ clang vim git build-essential cmake libgsl-dev libboost-dev libboost-program-options-dev
          2) sudo apt install --reinstall python3 python3-pip python3-tk git cmake build-essential libboost-dev libboost-iostreams-dev libboost-python-dev swig libfftw3-dev libgsl-dev python3-gi-cairo python3-scipy python3-matplotlib python3-pyqt5 python3-pyqt5.qtsvg python3-pyqt5.qtwebkit python3-pyqt5.qtserialport python3-lxml python3-yaml
  
    Try to run 'cmake ../' again in the ~vsdflow/work/tools/OpenTimer/build Directory 
                     ------------------------------------------------------------------------------------------------------------------------------
      If error presists,Use ChatGPT as Suggested Below
          3)Use ChatGPT to get Commands to add packages to Environment and Paths, Verify if they are properly configured with commands 
  
                <Package_Name> --version   #Replace Package with specific name like gcc,g++... EX:-  python3 --version
                 which <Package_Name>      #Replace <Package_Name> with specific name like gcc,g++,clang...  EX:-  which python3
             
            Try to run 'cmake ../' again in the ~vsdflow/work/tools/OpenTimer/build Directory ,If Error Continues,Proceed to Step 4.
                  
          4)Paste errors in the ChatGPT dialogue box and ask for Commands and step by step procedure with explanation to fix it.
  
     (2) $OpenTimer      ***Command Outputs Nothing***
          
          You can fix it by Following the steps below 
                  1)Check whether the OpenTimer(~/vsdflow/work/tools/OpenTimer) folder has folder named "bin" and 4files inside it with names -(ot-shell, ot-tau15, ot-tau18, ot-utility ) by using "ls" command in respective directories,It=f they exist proceed directly to step4,else copy paste the whole step 2 in terminal
                  
                  2)cd ~/vsdflow/work/tools/
                    sudo rm -r OpenTimer
                    git clone https://github.com/OpenTimer/OpenTimer.git
                    cd OpenTimer
                    mkdir build
                    cd build
                    cmake ../
                    make
                    sudo make install
                  
                  3)Repeat the step1 
                  4)cd ~/vsdflow/work/tools/OpenTimer/bin
                  5) sudo cp * /usr/local/bin
                  6) sudo nano ~/.bashrc
                  ----------Go to the bottom and copy paste the following line----------
                  alias opentimer='/usr/local/bin/ot-shell'
                  
                  ----------hit Ctrl+O, Enter, Ctrl+X to save and Exit------------------
                              
                  7)source ~/.bashrc
                  8)opentimer
                  ----------exit bit by typing "exit" without "-------------------------
               

F)Testing,Run One by One.--------You can exit programs by typing exit-------------------

1)magic
2)graywolf
3)yosys
4)qrouter
5)opentimer
6)cd outdir_spi_slave
7)qflow display spi_slave
                  

<----------------------------------------------------------------List of Tools installed-------------------------------------------------------------------------->

                     1) Yosys - RTL Synthesis
                     2) blifFanout - High fanout net (HFN) synthesis
                     3) graywolf - Placement
                     4) qrouter - Detailed routing
                     5) magic - VLSI Layout tool
                     6) netgen - LVS
                     7) OpenTimer and OpenSTA - Static timing analysis tool


