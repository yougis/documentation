Installer python 3
créer un alias
alias python='/usr/bin/python3'


/ pyqt5 (en global pas en local sinon il y aura des conflits au démarage de QGIS )



sudo apt-get install python3-pyqt5

pyrcc5 devrait fonctionner

python libs

python -m pip install --user urllib


#With IDEA (not ready yet)
installer plugin pycharm dans idea
télécharger et installer pycharm-debug.egg et déposer dans les site-packages

#Avec Winpd sur Debian 9


## installer wxPython
python -m pip install --user -U \
-f https://extras.wxpython.org/wxPython4/extras/linux/gtk3/debian-9/ \
wxPython

## installer winpdb-reborn

python -m pip install --user winpdb-reborn


# run debuger
python -m winpdb ~/.local/share/QGIS/QGIS3/profiles/default/python/plugins/psudgeodata/PsudGeoData.py

# dans le script plugin
import rpdb2
rpdb2.start_embedded_debugger('qgis')



~/.local/share/QGIS/QGIS3/profiles/default/python/plugins/PsudGeoData/src/psud_tree.py
~/.local/share/QGIS/QGIS3/profiles/default/python/plugins/PsudGeoData/src/psud_identify_tool.py
~/.local/share/QGIS/QGIS3/profiles/default/python/plugins/PsudGeoData/src/psud_layer.py

~/.local/share/QGIS/QGIS3/profiles/default/python/plugins/PsudGeoData/src/connectors/propertiesdialog.py

~/.local/share/QGIS/QGIS3/profiles/default/python/plugins/PsudGeoData/src/josso/Josso_session.py


pyrcc5 -o ~/Apps/psud/qgis/qgis-python-plugin/PsudGeoData/resources.py ~/Apps/psud/qgis/qgis-python-plugin/PsudGeoData/resources.qrc && rm -rf ~/.local/share/QGIS/QGIS3/profiles/default/python/plugins/PsudGeoData && cp -r ~/Apps/psud/qgis/qgis-python-plugin/PsudGeoData/ ~/.local/share/QGIS/QGIS3/profiles/default/python/plugins/PsudGeoData && pyrcc5 -o ~/Apps/psud/qgis/qgis-python-plugin/PsudPartageProjets/resources.py ~/Apps/psud/qgis/qgis-python-plugin/PsudPartageProjets/resources.qrc && rm -rf ~/.local/share/QGIS/QGIS3/profiles/default/python/plugins/PsudPartageProjets && cp -r ~/Apps/psud/qgis/qgis-python-plugin/PsudPartageProjets/ ~/.local/share/QGIS/QGIS3/profiles/default/python/plugins/PsudPartageProjets




Pour Qgis 2.18 sous debian  9


sudo apt-get install python-pip
