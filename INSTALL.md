## Description plus détaillée de l'installation et des dépendances
# Création de l'environnement : 
```
conda create --name myenv python=3.8.0
conda activate myenv
```

# SCIP solver
Installation de scipoptsuite-6.0.1.tgz qui contient SCIP 6.0.1 / SoPlex version 4.0.1
https://www.scipopt.org/index.php#download

Une fois ceci fait : extracter seulement le fichier de scip et soplex dans le projet

Set-up a desired installation path for SCIP / SoPlex (e.g., `/opt/scip`):
```
export SCIPOPTDIR='/opt/scip'
```

## SoPlex

SoPlex 4.0.1 (free for academic uses)
```
cd soplex/
mkdir build
cmake -S . -B build -DCMAKE_INSTALL_PREFIX=$SCIPOPTDIR
make -C ./build -j 4
make -C ./build install
cd ..
```

## SCIP

SCIP 6.0.1 (free for academic uses)

https://scip.zib.de/download.php?fname=scip-6.0.1.tgz

```
cd scip-6.0.1/
```
```
mkdir build
cmake -S . -B build -DSOPLEX_DIR=$SCIPOPTDIR -DCMAKE_INSTALL_PREFIX=$SCIPOPTDIR
make -C ./build -j 4
make -C ./build install
cd ..
```

## Cython

Required to compile PySCIPOpt
```
pip install Cython==3.0.0a11
```

## PySCIPOpt

SCIP's python interface (modified version)

```
pip install git+https://github.com/ds4dm/PySCIPOpt.git@branch-search-trees
```

