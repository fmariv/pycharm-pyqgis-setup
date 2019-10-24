# PyCharm PyQGIS setup guide

**Guide to setting up Pycharm for QGIS development.**

1. Create a .bat file in *C:\OSGeo4W64\bin* and name it pycharm.bat
1. Copy the code showed below: 
```@echo off
SET OSGEO4W_ROOT=C:\OSGeo4W64
call "%OSGEO4W_ROOT%"\bin\o4w_env.bat
call "%~dp0\o4w_env.bat"
call qt5_env.bat
call py3_env.bat
@echo off
path %OSGEO4W_ROOT%\apps\qgis\bin;%PATH%
set QGIS_PREFIX_PATH=%OSGEO4W_ROOT:\=/%/apps/qgis
set GDAL_FILENAME_IS_UTF8=YES
SET PYCHARM="C:\Program Files\JetBrains\PyCharm Community Edition 2018.3.7\bin\pycharm.exe"

set PYTHONPATH=C:\OSGeo4W64\apps\qgis\python
set PYTHONHOME=C:\OSGeo4W64\apps\Python37
set PYTHONPATH=%PYTHONPATH%;%OSGEO4W_ROOT%\apps\Python37\Lib\site-packages;

rem Set VSI cache to be used as buffer, see #6448
set VSI_CACHE=TRUE
set VSI_CACHE_SIZE=1000000
set QT_PLUGIN_PATH=%OSGEO4W_ROOT%\apps\qgis\qtplugins;%OSGEO4W_ROOT%\apps\Qt5\plugins
start "PyCharm aware of QGIS" /B %PYCHARM% %*
```
3. Create a desktop shortcup to the bat and launch it

[x]**Important**: do not install PyCharm v2019, it's bugged and doesn't launch correctly for QGIS development.
