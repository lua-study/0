plotGrav
=========
Matlab GUI tool for processing & visualization of various time series.  
The toolbox was developed for processing of gravimeter time series but can be used for arbitrary input.  

### Features
* load 4 different data files at once in diverse formats such as [TSoft](http://seismologie.oma.be/en/downloads/tsoft), Campbell Logger, or [Dygraphs](http://dygraphs.com/tutorial.html) csv
* export & print time series
* use scripts (instead of GUI)
* compute statistics such as correlation
* apply ML methods such as regression or principle component analysis
* apply corrections (e.g., steps, gaps)
* filter time series
* compute spectral analysis
* do some algebra on all input series (e.g., add, subtract, divide time series)
* download & process [Atmacs](http://atmacs.bkg.bund.de) atmospheric model data
* compute polar motion and length of day gravity effect
* introduce time shifts and re-sample the data (new temporal resolution)
* automatically fill missing data (interpolate or set to constant)
* estimate gravimeter calibration parameters
* superimpose plots with latest Earthquake records
* stack multiple files into one (for gravimeter records)

### Usage
* Run `plotGrav.m` or see `plotGrav_TestScript.plg` for scripting

### Dependency
* Tested and developed under Matlab R2015b
  * Some functions use statistics, curve fitting, and signal processing toolboxes
* The GUI appearance depends on Matlab version and screen resolution (optimized for 1920x1080)

### GUI
![](aux_files/gui.png)


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)