
# Installation

https://holoviz.org/installation.html


## créer un environement conda

```
conda create -n holoviz-tutorial python=3.7
conda activate holoviz-tutorial
```

## installer holoviz

```
conda install -c pyviz holoviz
```

## Compatibilité bidirectionnelle avec jupyter et jupyterLab

Installer NPM ou nodeJS 5+ puis l'extention holoviz

```
conda install nodejs
jupyter labextension install @pyviz/jupyterlab_pyviz
```
