
Mise en place d'un projet Plotly sous linux
# Installer anaconda

## Prerequisites
```
sudo apt-get install libgl1-mesa-glx libegl1-mesa libxrandr2 libxrandr2 libxss1 libxcursor1 libxcomposite1 libasound2 libxi6 libxtst6
```
puis
```
cd /tmp
curl -O https://repo.continuum.io/archive/Anaconda3-2020.02-Linux-x86_64.sh

bash Anaconda3-2020.02-Linux-x86_64.sh

source ~/.bashrc
```

Ouvrir un nouveau projet avec  IDE pyCharm-community-anaconda :

[install pyCharm-community-anaconda ](https://download-cf.jetbrains.com/python/pycharm-community-anaconda-2019.3.3.tar.gz)


# Installer plotly et le serveur Orca
Dans le terminal de l'environement virtuel conda :

```
conda install -c plotly plotly plotly-orca psutil requests plotly-geo
conda install jupyterlab notebook ipywidgets
conda install -c anaconda numpy ipython pandas
conda install -c conda-forge matplotlib nbformat
```

# Configurer Orca pour les export d'image statiques

```
sudo chown root [pathToCondaEnvProject]/lib/orca_app/chrome-sandbox
sudo chmod 4755 [pathToCondaEnvProject]/lib/orca_app/chrome-sandbox
```

## Tester l'installation

dans un terminal lancer
```
orca -help
```
un autre test :

```


import plotly.graph_objects as go

import numpy as np
np.random.seed(1)

# Generate scatter plot data
N = 100
x = np.random.rand(N)
y = np.random.rand(N)
colors = np.random.rand(N)
sz = np.random.rand(N) * 30

# Build and display figure
fig = go.Figure()
fig.add_trace(go.Scatter(
    x=x,
    y=y,
    mode="markers",
    marker={"size": sz,
            "color": colors,
            "opacity": 0.6,
            "colorscale": "Viridis"
            }
))

fig.show()

```

puis l'export lui même avec orca

```
import plotly.io as pio
from IPython.display import SVG, display
img_bytes = pio.to_image(fig, format="svg")
display(SVG(img_bytes))
```
