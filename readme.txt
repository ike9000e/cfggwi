
CFG.G.W.I. - Config GUI Window
========================================

Provides message-box' like functionality for shell scripts and
outputs user input via defined GUI controls.
A Program that can display custom controls, configured from simple format text files.
Takes one config file on input and creates another as output.
Namelly, input is JSON format text file and output is INI.
In addition, there is a way to setup default values for GUI items being created.


Usage
================

	-c or --controls
		Required. JSON formated config file for GUI controls.
		See example file "user_ctrls.json" for documentation.

	-d or --defaults
		Optional. JSON formated config for default values of actual GUI controls.
		By default, JSON file format is assumed, but if extension is ".ini", file 
		is correctly parsed as such as well.

	-o or --output
		Required. Set output file where settings will be saved. After user confirm with OK button.
		Default written format will be JSON but if extension is .ini and format is not 
		arbitrarly specified through "--controls" file, correct INI format is written.

	--mainicon <filenme>
		Optional. This is by default set to "mainicon.tga" and window 
		icon is set if file exists. Executable directory ("argv[0]") is also checked.
		Can be set to "none" to disable window icon.
		Actual icon file must be an uncompressed 32-bit RGBA TGA image.
		Recommended icon pixel dimensions are images around 48x48 size.
		
	--fltk--
		This separator-like argument may be placed to indicate that following arguments
		are to be passed to the underlying FLTK library.
		They are briefly as follows:
			-bg2 color             -bg color              -di[splay] host:n.n    
			-dn[d]                 -fg color              -g[eometry] WxH+X+Y
			-i[conic]              -k[bd]                 -na[me] classname
			-nod[nd]               -nok[bd]               -not[ooltips]
			-s[cheme] scheme       -ti[tle] windowtitle   -to[oltips]
			
	-bErlvZeroOnCancel
		Reverses meaning of shell return value. 0 is returned on user OK.
		Not recommended. Provided for backward compatibility.
		
	--LXColorsFix
		This is a fix, specific for LXDE Lubuntu linux distro. Because by default, 
		color scheme of desktop enviroment isn't determined properly by FLTK there.
		Not recomended for use on any other DEs.

	CFGGUIAPP_CMDLINE
		On application start, name of optional enviroment variable with alternate 
		command-line arguments. Simply, a string that contains arguments as if they 
		were passed via original command-line. If original command line comes with 
		arguments as well, CFGGUIAPP_CMDLINE ones are appended.

	--mSelectFile
		Switch mode to a select file mode, browse for file using Select File window.
		If this parameter is used, most of commandline parameters for CFGGWI 
		configuration is changed and no configuration file is used.
		Unchanged parameter(s):
			* --LXColorsFix
			* CFGGUIAPP_CMDLINE env var
		New parameter(s):
			* --szSFTitle TEXT  --  set title of the Select File window.
			* --szSFFName PATH  --  set starting directory and default selected file.
			* --bSFDir          --  browse for a directory instead, default is file.
		Path of Selected file is returned to STDOUT as a single line.

	--bStdout 1
		Writes config to STDOUT.
	
	--bConfMode 1
		Output config is in INI|CONF format (default is JSON format).
		This is automatically assumed if extension of output file (--output)
		is ".ini" or ".conf".

	--fUiScale FLOAT
		Default is 1.0 and makes no scaling.
		Requires scalable font to be set using '--bFontS2' parameter.
	
	--bFontS2 1
		Try find and use scalable font, from the system.
		This font is used by all GUI elements.
	
	--szFS2Needle TEXT
		Needle text to use when searching foe scalable font using 
		'--bFontS2' in turn. Default is "*", which searches in all fonts 
		provided by the system.


Notes
==========
	* All text files are assumed to be in ASCII format.
	* When user presses the OK button, value returned to shell is integer 0
	  (this can be changed by "-bErlvZeroOnCancel").


Changelog
============
2.0
	* Using FLTK as window library (previous version used Qt).
	* Linux platform is now primary.
	* Changelog from version prior 2.0 is removed since some features are being dropped.
2.1
	* Returns value 2 on user cancel.
	* New config property: main.szWindowTitle - sets main window title.
2.2
	* Can set or turn off main window icon. must be uncompressed TGA image, RGBA format.
	  See also "--mainicon".
	* New readme.txt
2.3
	* Added F4 and F5 key functions, in edit box, shows Select File window (F5 selects directory).
	* Added new mode, argument "--mSelectFile". Opens the browse-for-file dialog-box. 
2.4
	* Added context menu for text-edits
	* Added "Path to Relative" for text-edits
	* Added --bStdout and --bConfMode
2.5
	* Added command line options for GUI scaling: "--fUiScale", "--bFontS2"
	  and "--szFS2Needle".
	  
