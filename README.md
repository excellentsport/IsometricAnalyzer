# IsometricAnalyzer

**NOTE: THIS PROJECT IS IN BETA STATUS. CODE HAS NOT BEEN EXTENSIVELY TESTED FOR STABILITY, ACCURACY, OR OTHERWISE.**

A Labview program to analyze isometric squat and isometric mid thigh pull files from a force plate. Currently able to import and parse csv files with comma or tab separation that were collected at 1000Hz sampling rate.

![Screenshot of main screen](/Screenshots/WholeProgram.png) 

### Downloading and Running the Program

- If you don't have the the full version of Labview 2016 or newer installed you will need to first download and install Labview Runtime 2016 to be able to run the executable. It can be found here:
[Labview 2016 Runtime Engine](http://www.ni.com/download/labview-run-time-engine-2016/6066/en/).
- The most recent version of the software can be found on the [Releases Page](https://github.com/excellentsport/IsometricAnalyzer/releases): scroll to the latest release (at the top), click the "Assets" collapsible menu if the files are not already showing, then download the Zip file named “Isometric.Analyzer[xx.yy.zz].zip" (do not download the Source Code.zip file). 
- Extract all files to your desired destination folder. 
- Open the destination folder and double click "Isometric Analyzer.exe" to start the program.

### View/Use/Edit the Source Code
- In order to work from source code, the full version of Labview must be installed (version 2016 or later). It will not work with just the runtime libraries. 
- You can download source code from the latest release using the directions above, or fork/clone the github repository. Any source code in the repo is being actively worked on, so it may not work as intended. I recommend starting with source code from the releases page.
- Note that if you're running from source, you must open both the "IsometricAnalyzer.lvproj" and "Main.vi" files.
- If you're interested, please feel free to contribute!

## How to use

1. Start the program by clicking the right arrow in the upper left corner.
2. Select a file to analyze (I recommend starting with one of the ones included in the "Examples" folder if you haven't used it before).
3. Enter relevant data about your subject in the pop-up window, then hit "OK".  
![User input Popup Image](/Screenshots/UserPrompt.png)
4. Change any default analysis options if you need to (default is 1000ms period to determine standing weight, 5SD of standing weight as contraction onset threshold).  
![General settings Image](/Screenshots/GeneralSettings.png)
5. On the primary "Force-Time Trace" graph:
	- Drag the yellow cursor to just before the quiet standing period. This will search for a period after this cursor that has the lowest variability, and will use this period for the standing weight and SD value for contraction onset ID.
	- Drag the green bar to slightly before the onset of the contraction.
	- Drag the red bar to a point after the contraction where the force value is lower than the starting value.  
 ![Primary Graph Image](/Screenshots/PrimaryGraph.png)  
6. Verify the standing weight segment
	- Click on the "SW Segment" tab
	- The yellow cursor on this graph is the start of the SW segment that has the lowest variability. Eyeball it to verify it accurately represents a quiet standing period
7. Check out the "Pull Start ID" tab to verify that the pull start is correctly identified.
        - If not, verify that you have cursors correctly placed, and that the red button on the SW Segment tab isn't lit.
8. Verify on the "Intra-cursor Segment" graph on the "Intra-cursor" tab that the end of pull/push tab is at the same height as the automatically identified contraction onset (that it comes back down the the green horizontal line). If it isn't, then drag the red cursor to a later time point on the main "Force-time Trace" graph.   
![Early Cutoff example](/Screenshots/EarlyCutoff.png)
8. Verify that all your entered data on the "Data Entry and Saving" tab is correct.
9. Analyzed data from multiple trials and subjects can be saved into a single file. If you don't have a file to save all of this in yet, click the "Create Blank Save file"
10. If you already have a file to save data in (i.e. you already created a save file using this program previously), then click "Choose New Save Target" to select this file. This will be pre-populated if you have already analyzed another file this session.
11. Click the "Save results to Save Target" button to save all of the analyzed data to the save target you chose in the previous step.
12. Click the "Load new file to analyze" button to select your next isometric trial to analyze, then head to step 3.

### How the Auto-Detection Thresholds Work

There are a few different ways that you can automatically detect the "onset of contraction".  All methods (save manual identification), use a threshold value to identify the start. 
- Basically, as soon as the force value on the trace rises above the standing weight value by greater than the threshold value (i.e. standing weight + threshold value), that causes the rest of the calculations to start at that identified sample. 
- If you wish to use manual identification, choose the "Manual Identification" option, and the start of the pull will be "forced" to start at the position of the green cursor.

### How standing weight is calculated

- The "Standing Weight" cursor on the main graph defines the starting point for finding the period that has the lowest variability in the quiet standing section of the graph. 
- From this cursor, the program scans through "windows" of pre-determined length (the "# of samples averaged for system weight..." on the "Parameter Adjustment" tab) that has the lowest variability.   
- The samples within this identified period are then averaged to estimate standing weight, and the SD of the samples of this period is used for contraction onset identification (if you're using the 5SD method).

### How to ensure that your trials will be accurately analyzed

The following instructions outline the basics of what you need to do in an isometric squat or isometric mid thigh pull for this program to analyze it correctly: 

1. Have the subject get into the correct body position, with minimal pre-tension.   
2. The subject must stand in position for a period of a minimum of 1 second prior to initiating the trial (i.e. the contraction) so that there is a period from which standing weight can be calculated (note that 2-3 seconds is probably ideal).   
3. From the start of the standing weight period until the contraction, they should be stable (i.e. no swaying, repositioning, or any "dip"). You will be able to see these motions on the force-time trace. Redo the trial if they do any of these things. 
4. Subject should pull as "fast and as hard as possible" for 5-6 seconds, after which they should relax.

## A final note
I strongly recommend you check out the review we did in 2019 on the optimal methods for using the isometric mid thigh pull. The recommendations we laid out in there can also be applied to the isometric squat, in my opinion.

[Comfort et al. (2019) Standardization and Methodological Considerations for the Isometric Midthigh Pull](https://journals.lww.com/nsca-scj/Citation/2019/04000/Standardization_and_Methodological_Considerations.10.aspx).


## Authors

**George Beckham, PhD**  [GitHub](https://github.com/ExcellentSport), [Personal Website](https://www.georgebeckham.com)  
**Eric Martin, PhD**


## License

Isometric Analyzer is a free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version. Isometric Analyzer is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.