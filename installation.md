 

 
Step 1 Installation platform scripts (by git repository) 
=======================================================
----------------------------------------------------------------------------------
### Command to clone

msandro@pool:/dsk5/dsk5> cd /dsk5/dsk5  
msandro@pool:/dsk5/dsk5> git clone https://github.com/FemusPlatform/NumericPlatform.git  
or  
msandro@pool:/dsk5/dsk5> git clone https://github.com/FemusPlatform/NumericPlatform.git   numericplatform   
to create directly with name
  
------------------------ 

    Cloning into 'NumericPlatform'...  
    remote: Enumerating objects: 302, done.  
    remote: Total 302 (delta 0), reused 0 (delta 0), pack-reused 302  
    Receiving objects: 100% (302/302), 69.20 KiB | 502.00 KiB/s, done.  
    Resolving deltas: 100% (201/201), done.  

------------------------

----------------------------------------------------------------------------------
----------------------------------------------------------------------------------

### Directory content 

msandro@pool:/dsk5/dsk5> ls  

    .....  NumericPlatform  .......  
    
msandro@pool:/dsk5/dsk5> mv NumericPlatform/  numericplatform  




msandro@pool:/dsk5/dsk5> cd numericplatform/  
msandro@pool:/dsk5/dsk5/numericplatform> ls  

    platform_init.sh  PLAT_BUILD  plat_scripts README.md  

msandro@pool:/dsk5/dsk5/numericplatform> ls ./PLAT_BUILD/  

    buildgui_dowload.sh  buildgui_package.sh  install_scripts buildgui_guide.sh  buildgui_vers.sh  buildgui.sh



msandro@pool:/dsk5/dsk5/numericplatform> ls  -a   

    .  ..  .git  .gitignore  howtodo.md  .howtodo.md.kate-swp  init_platform.sh  PLAT_BUILD  README.md  

msandro@pool:/dsk5/dsk5/numericplatform> ls ../PLAT_BUILD/install_scripts/  

    code_versions.sh  foam_repo.sh  libmesh.sh       medCoupling9.sh  plat_conf_template.sh  salome8.sh  
    dragondonjon.sh   getfem.sh     med3.sh          openmpi.sh       platform.sh            salome9.sh  
    fblaslapack.sh    gmsh.sh       med4.sh          petsc_dbg.sh     qhull.sh               utility.sh  
    femus.sh          lapack.sh     medCoupling8.sh  petsc_opt.sh     requirements.sh  

----------------------------------------------------------------------------------


Step 2: Installation platform   structure (by platform_init.sh)  
=======================================================

msandro@pool:/dsk5/dsk5/numericplatform> source platform_init.sh  


    Stage 1/2 -------- check requirements (platform1_reqs.sh script)
    Check linux distribution 
    NAME="openSUSE Leap"
    VERSION="15.3"
    ID="opensuse-leap"
    ID_LIKE="suse opensuse"
    VERSION_ID="15.3"
    PRETTY_NAME="openSUSE Leap 15.3"
    ANSI_COLOR="0;32"
    CPE_NAME="cpe:/o:opensuse:leap:15.3"
    BUG_REPORT_URL="https://bugs.opensuse.org"
    HOME_URL="https://www.opensuse.org/"
    Check dialog: dialog present 
    Check gcc: gcc present 
    Check g++: g++ present 

    Stage 1/2 Check requirements completed 
    Press enter to continue installation
----------------------------------------------------------------------------------
---------------------------------------------------------------------------------- 


    Stage 2/2 -- Check plat_conf.sh script (must be generated by platform_set.sh)

    platform_script : Script platform set up 
    platform_script: 1b set up: Check main installation directories:
    Directory /dsk5/dsk5/prova/PLAT_BUILD/packages_targz dir dos not already exists
    Check main installation directories 1 level = 1
    platform_script: make level 1 directories:
    
    platform_scripts : 1c Platform set up 1 Level directory  ------> platform_conf.sh: summary 
    -----------------------------------------------------------------------------------------
    platform_scripts : 1c Platform DIR (platform or software or ...) is =  /dsk5/dsk5/prova

    platform_scripts : 1c BUILD dir (BUILD_DIR) is                      =  /dsk5/dsk5/prova/PLAT_BUILD
    platform_scripts : 1c INSTALL_BUILD_TAR_DIR (package archive dir)   =  /dsk5/dsk5/prova/PLAT_BUILD/packages_targz/
    platform_scripts : 1c INSTALL_PLAT_LOG_DIR  (log dir)               =  /dsk5/dsk5/prova/PLAT_BUILD/package_logs

    platform_scripts : 1c PLAT_THIRD_PARTY_DIR  (third party code dir)  =  /dsk5/dsk5/prova/PLAT_THIRD_PARTY
    platform_scripts : 1c PLAT_USERS_DIR  (users dir)                   =  /dsk5/dsk5/prova/PLAT_USERS
    platform_scripts : 1c PLAT_CODES_DIR  (codes dir)                   =  /dsk5/dsk5/prova/PLAT_CODES
    platform_scripts : 1c PLAT_VISU  (visualization dir)                =  /dsk5/dsk5/prova/PLAT_VISU
    -----------------------------------------------------------------------------------------

    platform_conf.sh  generated

    NumericPlatform alias is already in your ~/.bashrc
    platform_conf.sh generated
    MPI    LIB not installed
    PETSC  LIB not installed
    HDF5   LIB not installed
    MED    LIB not installed
    QHULL    LIB not installed
    LAPACK    LIB not installed
    GMSH code not installed
    FEMUS   code not installed
    LIBMESH code not installed
    OpFOAM  code not installed
    DRDONJ  code not installed
    GETFEM  code not installed
    Stage 2/2 platform_conf.sh found and environment configured
    Press enter to continue installation

----------------------------------------------------------------------------------
----------------------------------------------------------------------------------    
    

   





Remember, since we change the platfrom dir in bashrc.sh  
alias numericplatform='export NUPLAT_DIR=/dsk5/dsk5/numericplatform && cd $NUPLAT_DIR && source plat_conf.sh && cd - '  

    



----------------------------------------------------------------------------------
----------------------------------------------------------------------------------

### Directory content 

msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls  
    
    buildgui_dowload.sh  buildgui_install_package.sh  install.sh    packages_targz  
    buildgui_guide.sh    install_scripts      buildgui_vers.sh   package_logs  plat_requirements.log  
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD>   

    >

----------------------------------------------------------------------------------

### Remark 1  init_platform.sh file

init_platform content:

    cd PLAT_BUILD  
    source install.sh  

----------------------------------------------------------------------------------

### Remark 2: display main menu 

    dialog --clear  --backtitle " Platform installer " \  
    --title "[ INSTALLATION MENU ]" \  
    --menu "Choose the TASK" 25 70 10 \  
    Download       "Dowload packages" \  
    InstThirdParty "Install Third Party Packages" \  
    InstCodes      "Install Numerical Codes" \  
    Guide          "Installation guide " \  
    Editor         "Start a text editor" \  
    Exit           "Exit to the shell" 2>"${INPUT}"  

----------------------------------------------------------------------------------

Step 3: Third-party software (Salome openmpi petsc )
=======================================================

msandro@pool:/dsk5/dsk5/numericplatform> source init_platform.sh   

------------------------
    (see Remark 1)  
    Check linux distribution ....  
    ......
    Check dialog: dialog present   
    Check gcc: gcc present   
    Check g++: g++ present   

    Check requirements completed   
    Press enter to continue installation  

----------------------------------------------------------------------------------
----------------------------------------------------------------------------------

AN INSTALLATION MENU APPEARS  (see Remark 2)  
CLICK ON  
SetUpPlatform  "third party software"   

    [x]  "SALOME"          
    [ ]  "openmpi"         
    [ ]  "petsc-dbg"       
    [ ]  "petsc-opt"       
    [ ]  "med"             
    [ ]  "medCoupling"     
    [ ]  "gmsh"            
    [ ]    "qhull"         
    [ ]    "lapack"         


--------------------------------------------------------
-------------------------------------------------------

copy  /dsk5/dsk5/numericplatform/PLAT_BUILD/packages_targz/Salome-V9.3.0-univ_public.run  
salome  2 ->  2a install -> 2c links  
salome  2a Now installing   

++++++++++++++++++++++++++++++++++++++++   
Self Extracting Salome V9_3_0 Installer  
++++++++++++++++++++++++++++++++++++++++  

Installation of Salome V9_3_0 in /dsk5/dsk5/numericplatform/PLAT_BUILD/Salome-V9_3_0-x86_64-univ ...  
Verifying archive integrity...  
All good.  
100%[=======================================================================]   


--------------------------------------------------------
--------------------------------------------------------

CLICK ON  
SetUpPlatform  "third party software"   

    [ ]  "SALOME"          
    [x]  "openmpi"         
    [ ]  "petsc-dbg"       
    [ ]  "petsc-opt"       
    [ ]  "med"             
    [ ]  "medCoupling"     
    [ ]  "gmsh"            
    [ ]   "qhull"         
    [ ]   "lapack"         

--------------------------------------------------------
--------------------------------------------------------

openmpi-3.1.4/orte/orted/pmix/pmix_server.h  
openmpi-3.1.4/orte/orted/pmix/Makefile.am  
...  
...  
openmpi : 2b starting configure command  
openmpi : 2c Configuration ended, now compiling  
openmpi : 2c Compilation ended, now installing  

--------------------------------------------------------
--------------------------------------------------------

CLICK ON  

SetUpPlatform  "third party software"   

    [ ]  "SALOME"          
    [ ]  "openmpi"         
    [ ]  "petsc-dbg"       
    [x]  "petsc-opt"       
    [ ]  "med"             
    [ ]  "medCoupling"     
    [ ]  "gmsh"            
    [ ]  "qhull"         
    [ ]  "lapack"         
                                 

--------------------------------------------------------
--------------------------------------------------------

    --------- Start petsc_opt.sh script --------   

    petsc : inst dir package= /dsk5/dsk5/numericplatform/PLAT_BUILD/petsc-git_rep                 
    Cloning into 'petsc-git_rep'...                                                               
    remote: Counting objects: 804889, done.                                                       
    remote: Compressing objects: 100% (184111/184111), done.                                     
    remote: Total 804889 (delta 616925), reused 804889 (delta 616925)                            
    Receiving objects: 100% (804889/804889), 128.56 MiB | 9.49 MiB/s, done.                      
    Resolving deltas: 100% (616925/616925), done.                                                  
    petsc : 2a prefix=/dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/petsc-git_rep/linux-opt          
    petsc : 2a logdir=/dsk5/dsk5/numericplatform/PLAT_BUILD/package_logs/                          
    petsc : 2 Compiling petsc-git_rep in debug mode                                                 
    petsc : 2 script-> 2a prefix -> 2b configure-> 2c make-> 2d test -> 2e install                  
    petsc : 2b starting configuration                                                             
    petsc : 2c Configuration ended, now compiling     
    petsc : 2c Compiling ended, now installing     


-------------------------------------------------------
                                                                                                            
      
                                                                                                          
### Directory content after  Salome platform installation


msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../  

    .git/             howtodo.md        PLAT_BUILD/       plat_conf.sh      PLAT_USERS/       README.md
    .gitignore        init_platform.sh  PLAT_CODES/       PLAT_THIRD_PARTY/ PLAT_VISU/        
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_BUILD  

    gui_dowload.sh  gui_install_package.sh  install.sh    packages_targz         Salome-V9_3_0-x86_64-univ
    gui_guide.sh    install_scripts         package_logs  plat_requirements.log  
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_BUILD/packages_targz  

    Salome-V9.3.0-univ_public.run  
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_BUILD/package_logs/  
    
    > 

msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_THIRD_PARTY/  

    hdf5  med  MED_coupling  MED_mod  salome  
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_CODES/  

    >  

--------------------------------------------------------

### Directory content after  openmpi LIB installation

msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../  
    
    howtodo.md        PLAT_BUILD  plat_conf.sh      PLAT_USERS  README.md
    init_platform.sh  PLAT_CODES  PLAT_THIRD_PARTY  PLAT_VISU  

msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_BUILD  
    
    gui_dowload.sh  gui_install_package.sh  install.sh     package_logs    plat_requirements.log
    gui_guide.sh    install_scripts         openmpi-3.1.4  packages_targz  Salome-V9_3_0-x86_64-univ  
    
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD>  ls ../PLAT_BUILD/packages_targz  

    openmpi-3.1.4.tar.gz  Salome-V9.3.0-univ_public.run  
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_BUILD/package_logs/

    openmpi_compile.log  openmpi_config.log  openmpi_install.log  
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD>  ls ../PLAT_THIRD_PARTY  

    hdf5  med  MED_coupling  MED_mod  openmpi  openmpi-3.1.4  salome  
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_CODES/  

    >   


--------------------------------------------------------

### Directory content after  petsc_opt LIB installation

msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../  
    
    howtodo.md        PLAT_BUILD  plat_conf.sh      PLAT_USERS  README.md
    init_platform.sh  PLAT_CODES  PLAT_THIRD_PARTY  PLAT_VISU  

msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_BUILD  
    
    gui_dowload.sh  gui_install_package.sh  install.sh  openmpi-3.1.4  packages_targz  plat_requirements.log  
    gui_guide.sh    install_scripts     package_logs   petsc-git_rep   Salome-V9_3_0-x86_64-univ  
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_BUILD/packages_targz  

    fblaslapack-v3.4.2-p3.tar.gz  openmpi-3.1.4.tar.gz  Salome-V9.3.0-univ_public.run  
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_BUILD/package_logs/  

    med_compile.log  openmpi_compile.log  openmpi_install.log      petsc-opt_config.log   petsc-opt_testing.log
    med_install.log  openmpi_config.log   petsc-opt_compiling.log  petsc-opt_install.log  
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_THIRD_PARTY  

    hdf5   med  MED_coupling  MED_mod openmpi  openmpi-3.1.4  petsc  petsc-git_rep  salome      
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD>  ls ../PLAT_CODES/  

    >   


------------------------------------------------------

## Remark 1: display main menu

Dialog --clear  --backtitle " Platform installer "   

    --title "[ INSTALLATION MENU ]"  
    --menu "Choose the TASK" 25 70 10   
    Download       "Dowload packages" 
    SetUpPlatform  "Set up Numerical Platform structure"   
    InstThirdParty "Install Third Party Packages" 
    InstCodes      "Install Numerical Codes" 
    Guide          "Installation guide " 
    Editor         "Start a text editor"   
    Exit           "Exit to the shell" 2>"${INPUT}"  

---------------------------------------------------------------------------------


## Remark 2: display GUI install package

Please install the packages with the proposed following order" 20 61 10   

       "SALOME"           "$SalomeLast" off    
       "openmpi"          "$OpenmpiLast"  off   
       "petsc-dbg"        "$PetscLast" off   
       "petsc-opt"        "$PetscLast" off   
       "med"              "4.0.0"  off   
       "medCoupling"      "$SalomeLast"  off   
       "gmsh"             "4.2.2"  off   
       "qhull"            "2015.2" off   
       "lapack"           "3.8.0" off 
       
       
---------------------------------------------------------------------------------        
----------------------------------------------------------------------------------

Step 4: MED third party software (Med MedCoupling )
=======================================================

msandro@pool:/dsk5/dsk5/numericplatform> source init_platform.sh   

Check requirements completed   
Press enter to continue installation  

AN INSTALLATION MENU APPEARS   

-------------------------------------------------------
-------------------------------------------------------

CLICK on                                              
SetUpPlatform  "third party software"                   

    [ ]  "SALOME"          
    [ ]  "openmpi"         
    [ ]  "petsc-dbg"       
    [ ]  "petsc-opt"       
    [x]  "med"             
    [ ]  "medCoupling"     
    [ ]  "gmsh"            
    [ ]  "qhull"         
    [ ]  "lapack"         
                                                  
    download ...                                                                            
    Cloning into 'med-4.0.0'...                                                             
    remote: Enumerating objects: 6541, done.                                                
    remote: Total 6541 (delta 0), reused 0 (delta 0), pack-reused 6541                       
    Receiving objects: 100% (6541/6541), 35.95 MiB | 5.76 MiB/s, done.                       
    Resolving deltas: 100% (4441/4441), done.                                              
    med : 2 -> 2b configure-> 2c make-> 2d install                                                          
    med : 2b starting configure command from /dsk5/dsk5/numericplatform/PLAT_BUILD/med-4.0.0 with ccmake   
    med-4.0.0

CCMAKE START                                                                                           
c -> compile                                                                                           
please change ...

    CMAKE_CXX_COMPILER_AR -> /dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/openmpi/bin/mpicxx                 
    CMAKE_CXX_COMPILER_RANLIB -> /dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/openmpi/bin/mpicxx             
    CMAKE_C_COMPILER_AR -> /dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/openmpi/bin/mpicc                  
    CMAKE_C_COMPILER_RANLIB -> /dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/openmpi/bin/mpicc                   
    CMAKE_Fortran_COMPILER_AR -> /dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/openmpi/bin/mpif90                
    CMAKE_Fortran_COMPILER_RANLIB -> /dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/openmpi/bin/mpif90            
                                                                                                                  
 -------------------------------------------------------
--------------------------------------------------------

CLICK ON                                                
SetUpPlatform  "third party software"                   

    [ ]  "SALOME"          
    [ ]  "openmpi"         
    [ ]  "petsc-dbg"       
    [ ]  "petsc-opt"       
    [ ]  "med"             
    [x]  "medCoupling"     
    [ ]  "gmsh"            
    [ ]  "qhull"         
    [ ]  "lapack"         
                                                                                                                             
-------------------------------------------------------     
      
    Getting the evironment Platform set up 1 Level directory from   plat_conf.sh script                         

Configuration for medCoupling in                                                             

    LIB med  in /dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/med                                  
    medCoupling : 2 -> 2b configure-> 2c make-> 2d install                                         
    download ...                                                                                   
    Cloning into 'medCoupling-9.3.0'...                                                                  
    remote: Enumerating objects: 1399, done.                                                               
    remote: Counting objects: 100% (1399/1399), done.                                                       
    remote: Compressing objects: 100% (937/937), done.                                                      
    remote: Total 1399 (delta 452), reused 1399 (delta 452), pack-reused 0                              
    Receiving objects: 100% (1399/1399), 7.81 MiB | 5.11 MiB/s, done.                                        
    Resolving deltas: 100% (452/452), done.                                                                  
                                                                                                         
medCoupling : 2b starting configure command from /dsk5/dsk5/numericplatform/PLAT_BUILD/medCoupling-9.3.0 with ccmake  

    MEDCOUPLING-9.3.0                 
    ccmake -DCMAKE_INSTALL_PREFIX=/dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/medCoupling-9.3.0 -DBOOST_ROOT_DIR=/dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/salome/prerequisites/Boost-1580 -DLIBXML2_ROOT_DIR=/dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/salome/prerequisites/Libxml2-291 -DMEDCOUPLING_PARTITIONER_METIS=OFF -DMEDCOUPLING_PARTITIONER_SCOTCH=OFF -DMEDCOUPLING_ENABLE_PYTHON=OFF -DMEDCOUPLING_BUILD_DOC=OFF -DCMAKE_CXX_COMPILER=/dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/openmpi/bin/mpicxx -DCMAKE_C_COMPILER=/dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/openmpi/bin/mpicc -DCMAKE_Fortran_COMPILER=/dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/openmpi/bin/mpif90 ./MEDCOUPLING-9.3.0     


medCoupling : 2c Configuration ended, now compiling

      --------------------------------------------

CCMAKE START                                                                                           
c -> compile                                                                                           
please change ...

    CMAKE_CXX_COMPILER_AR -> /dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/openmpi/bin/mpicxx                 
    CMAKE_CXX_COMPILER_RANLIB -> /dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/openmpi/bin/mpicxx             
    CMAKE_C_COMPILER_AR -> /dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/openmpi/bin/mpicc                  
    CMAKE_C_COMPILER_RANLIB -> /dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/openmpi/bin/mpicc                   
    CMAKE_Fortran_COMPILER_AR -> /dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/openmpi/bin/mpif90                
    CMAKE_Fortran_COMPILER_RANLIB -> /dsk5/dsk5/numericplatform/PLAT_THIRD_PARTY/openmpi/bin/mpif90            



--------------------------------------------------------

### Directory content after  med installation

msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../  

    howtodo.md        PLAT_BUILD  plat_conf.sh      PLAT_USERS  README.md
    init_platform.sh  PLAT_CODES  PLAT_THIRD_PARTY  PLAT_VISU  

--------------------------------------------------------

msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_BUILD                                                

    gui_dowload.sh  gui_install_package.sh  install.sh  openmpi-3.1.4  packages_targz  plat_requirements.log 
    gui_guide.sh    install_scripts         med-4.0.0   package_logs   petsc-git_rep   Salome-V9_3_0-x86_64-univ         
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_BUILD/packages_targz                               

    fblaslapack-v3.4.2-p3.tar.gz  openmpi-3.1.4.tar.gz  Salome-V9.3.0-univ_public.run                                       
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_BUILD/package_logs/                                      

    med_compile.log  openmpi_compile.log  openmpi_install.log      petsc-opt_config.log   petsc-opt_testing.log             
    med_install.log  openmpi_config.log   petsc-opt_compiling.log  petsc-opt_install.log
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_THIRD_PARTY

    hdf5  med  med-4.0.0  MED_coupling  MED_mod  openmpi  openmpi-3.1.4  petsc  petsc-git_rep  salome                     
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD>  ls ../PLAT_CODES/                                              

    >                                                                      
                                                                                                                         
                         
--------------------------------------------------------                         
                         
### Directory content after  MedCoupling  installation                        
                         
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../                           

    howtodo.md        PLAT_BUILD  plat_conf.sh      PLAT_USERS  README.md
    init_platform.sh  PLAT_CODES  PLAT_THIRD_PARTY  PLAT_VISU                           
                         
--------------------------------------------------------                         
                         
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD>  ls ../PLAT_BUILD                                                       

    gui_dowload.sh          install_scripts  medCoupling-9.3.0  packages_targz         Salome-V9_3_0-x86_64-univ
    gui_guide.sh            install.sh       openmpi-3.1.4      petsc-git_rep
    gui_install_package.sh  med-4.0.0        package_logs       plat_requirements.log   
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_BUILD/packages_targz                                             

    fblaslapack-v3.4.2-p3.tar.gz  openmpi-3.1.4.tar.gz  Salome-V9.3.0-univ_public.run                                               
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_BUILD/package_logs/                                                

    med_compile.log          med_install.log      openmpi_install.log      petsc-opt_install.log 
    medCoupling_compile.log  openmpi_compile.log  petsc-opt_compiling.log  petsc-opt_testing.log
    medCoupling_install.log  openmpi_config.log   petsc-opt_config.log                                                                  
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_THIRD_PARTY                                                               

    hdf5  med-4.0.0     medCoupling-9.3.0  openmpi        petsc          salome
    med   MED_coupling  MED_mod            openmpi-3.1.4  petsc-git_rep                                                          
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD>  ls ../PLAT_CODES/                                                        

    >                                                                           
                                                                                                                                       
----------------------------------------------------------------------------------


Step 5: Installation platform code LIBMESH (gencase)
=======================================================                                                                                                                                 

=======================================================

msandro@pool:/dsk5/dsk5/numericplatform> source init_platform.sh   

    Check requirements completed   
    Press enter to continue installation  
    
----------------------------------------------------------------------------------
----------------------------------------------------------------------------------
    
AN INSTALLATION MENU APPEARS   
CLICK ON                                                                                                          
InstCodes      "Install Numerical Codes"                  

    [X] LIBMESH                                                  
                                      
----------------------------------------------------------------------------------
----------------------------------------------------------------------------------                                    

    ............. done extracting ............................................  
    libmesh : 2b starting configure command  
    libmesh : 2c Configuration ended, now compiling                      
    libmesh : 3 Compiling ended, now installing                                           
                         
--------------------------------------------------------                         
                         
### Directory content after LIBMESH (gencase)   installation                       
                         
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../      

    howtodo.md        PLAT_BUILD  plat_conf.sh      PLAT_USERS  README.md
    init_platform.sh  PLAT_CODES  PLAT_THIRD_PARTY  PLAT_VISU                           
                         
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD>  ls ../PLAT_BUILD                                           

    gui_dowload.sh          install_scripts  med-4.0.0          package_logs    plat_requirements.log                                        
      gui_guide.sh            install.sh       medCoupling-9.3.0  packages_targz  Salome-V9_3_0-x86_64-univ                                      
      gui_install_package.sh  libmesh-1.5.1    openmpi-3.1.4      petsc-git_rep                                      
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD>  ls ../PLAT_BUILD/packages_targz                                        

    fblaslapack-v3.4.2-p3.tar.gz  libmesh-1.5.1.tar.gz  openmpi-3.1.4.tar.gz  Salome-V9.3.0-univ_public.run                                      
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_BUILD/package_logs/                                         

    libmesh_compile.log  medCoupling_compile.log  openmpi_config.log       petsc-opt_install.log                                      
    libmesh_config.log   medCoupling_install.log  openmpi_install.log      petsc-opt_testing.log                                      
    libmesh_install.log  med_install.log          petsc-opt_compiling.log                                      
    med_compile.log      openmpi_compile.log      petsc-opt_config.log                                      
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_THIRD_PARTY                                        

    hdf5     libmesh-1.5.1  med-4.0.0     medCoupling-9.3.0  openmpi        petsc          salome                                      
    libmesh  med            MED_coupling  MED_mod            openmpi-3.1.4  petsc-git_rep                                      
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD>   ls ../PLAT_CODES/                                              

    libmesh                                                       

     
 ----------------------------------------------------------------------------------

Step 6: Installation platform code FEMus
=======================================================                                                                                                                                 
=======================================================

msandro@pool:/dsk5/dsk5/numericplatform> source init_platform.sh   

Check requirements completed   
Press enter to continue installation  

----------------------------------------------------------------------------------
----------------------------------------------------------------------------------

AN INSTALLATION MENU APPEARS   
CLICK ON                                                
InstCodes      "Install Numerical Codes"                  

    [X] FEMus                                                  
                                                         
----------------------------------------------------------------

                         
    Cloning into 'femus'...                                                                  
    remote: Enumerating objects: 193, done.                                                    
    remote: Counting objects: 100% (193/193), done.                                            
    remote: Compressing objects: 100% (161/161), done.                                       
    remote: Total 2803 (delta 76), reused 106 (delta 31), pack-reused 2610                 
    Receiving objects: 100% (2803/2803), 3.09 MiB | 4.79 MiB/s, done.                       
    Resolving deltas: 100% (1855/1855), done.                                               
    Setting environment for femus                                                         
    On branch master                                                                     
    Your branch is up to date with 'origin/master'.                                       
                                                                                      
    nothing to commit, working tree clean                                               
    Compiling femus library for 2D geometry                                                      

-------------------------------------------------------                                       

    Configuring application                                                                       
    Application path is  /dsk5/dsk5/numericplatform/PLAT_CODES/femus/applications/lib_femus2D   
    Application name is lib_femus2D                                                             
    Method is opt                                                                                
    Application configured                                                                       

--------------------------------------------------------                         
                         
### Directory content after Femus      installation                     
                         
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../                           

    howtodo.md        PLAT_BUILD  plat_conf.sh      PLAT_USERS  README.md
    init_platform.sh  PLAT_CODES  PLAT_THIRD_PARTY  PLAT_VISU                           
                         
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD>  ls ../PLAT_BUILD   

    gui_dowload.sh          install_scripts  med-4.0.0          package_logs    plat_requirements.log
    gui_guide.sh            install.sh       medCoupling-9.3.0  packages_targz  Salome-V9_3_0-x86_64-univ
    gui_install_package.sh  libmesh-1.5.1    openmpi-3.1.4      petsc-git_rep
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD>  ls ../PLAT_BUILD/packages_targz  

    fblaslapack-v3.4.2-p3.tar.gz  libmesh-1.5.1.tar.gz  openmpi-3.1.4.tar.gz  Salome-V9.3.0-univ_public.run
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_BUILD/package_logs/   

        libmesh_compile.log  medCoupling_compile.log  openmpi_config.log       petsc-opt_install.log
        libmesh_config.log   medCoupling_install.log  openmpi_install.log      petsc-opt_testing.log
        libmesh_install.log  med_install.log          petsc-opt_compiling.log
        med_compile.log      openmpi_compile.log      petsc-opt_config.log
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD> ls ../PLAT_THIRD_PARTY  

    hdf5     libmesh-1.5.1  med-4.0.0     medCoupling-9.3.0  openmpi        petsc          salome
    libmesh  med            MED_coupling  MED_mod            openmpi-3.1.4  petsc-git_rep
msandro@pool:/dsk5/dsk5/numericplatform/PLAT_BUILD>   ls ../PLAT_CODES/   

    femus  libmesh

                 
                              
                              