# Installer anaconda / miniconda pour Linux

## Prerequis
```
sudo apt-get install libgl1-mesa-glx libegl1-mesa libxrandr2 libxrandr2 libxss1 libxcursor1 libxcomposite1 libasound2 libxi6 libxtst6
```

Pour installer anaconda :
```
cd /tmp
curl -O https://repo.continuum.io/archive/Anaconda3-2020.02-Linux-x86_64.sh

bash Anaconda3-2020.02-Linux-x86_64.sh

source ~/.bashrc
```

Pour installer minconda :
```

cd /tmp
curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
source ~/.bashrc
```


Ouvrir un nouveau projet avec  IDE pyCharm-community-anaconda :

[install pyCharm-community-anaconda ](https://download-cf.jetbrains.com/python/pycharm-community-anaconda-2019.3.3.tar.gz)


## Installer Jupyter et jupyterLab

jupyter est déjà présent avec miniconda, pour démarrer le server notebook
 lancer
```
jupyter notebook
```

jupyterLab :
```
conda install -c conda-forge jupyterlab
```
