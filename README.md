# IsometricAnalyzer

NOTE: THIS PROJECT IS IN BETA STATUS. CODE HAS NOT BEEN EXTENSIVELY TESTED FOR STABILITY, ACCURACY, OR OTHERWISE. 

A Labview program to analyze isometric squat and isometric mid thigh pull files from a force plate. Currently able to import and parse csv files with comma or tab separation that were collected at 1000Hz sampling rate. 

## Getting Started

**If you have Labview 2016 or newer installed:**  
The primary parent folder contains the source code for the main Labview Project and Primary VI "Main.vi". If you're interested in seeing the source, you can fork/pull/download the entire repository to view/use/edit. You will need a full version of Labview 2016 or newer to use.

**If you don't have Labview 2016 installed or don't want to mess with all of the labview files:**  
You will need to first download and install Labview Runtime 2016 to be able to run the executable. It can be found here: http://www.ni.com/download/labview-run-time-engine-2016/6066/en/ Next, head to the [Releases Page](https://github.com/excellentsport/IsometricAnalyzer/releases), scroll to whatever the latest release is, click "Assets", then download the Zip file in the latest release that is NOT entitled "Source Code". Extract all files to a folder somewhere, then doubleclick "Isometric Analyzer.exe" to start the program.

## How to use

1. Start the program by clicking the right arrow in the upper left corner.
2. Select a file to analyze (I recommend starting with one of the ones included in the "Examples" folder).
3. Enter relevant data about your subject.
4. Change any default analysis options if you need to (default is 1000ms period to determine standing weight, 5SD of standing weight as contraction onset threshold).
5. On the primary "Force-Time Trace" graph:
	- Drag the yellow bar to approximately 1-2 second before the onset of the contraction (i.e. when the subject is pulling/pushing)
	- Drag the green bar to slightly before the onset of the contraction
	- Drag the red bar to after the contraction where the force value is lower than the starting value. 
6. Figure out the standing weight segment
	- Click over to the "SW Segment" tab
	- Drag around the yellow cursor a bit - this analyzes a 1000ms (can be changed on the parameters tab) segment immediately following the yellow cursor to determine the standing weight. Try to keep this as close to the start of the pull as you can, but find one that is as stable as possible (and keeps the red light off). Try not to go farther than about 2 seconds behind the start of the pull. If you have a segment that is too variable, the red light will turn on. 
	- Leave the cursor there when done
7. Check out the "Pull Start ID" tab to verify that the pull start is correctly identified.
	- If not, verify that you have cursors correctly placed, and that the red button on the SW Segment tab isn't lit.
	- If yes, move on.
8. Verify on the "Intra-cursor Segment" graph on the "Intra-cursor" tab that the end of pull/push tab is at the same height as the automatically identified contraction onset (that it comes back down the the green horizontal line). If it isn't, then drag the red cursor to a later time point on the main "Force-time Trace" graph.
8. Verify that all your entered data on the "Data Entry and Saving" tab is correct.
9. Analyzed data from multiple trials and subjects can be saved into a single file. If you don't have a file to save all of this in yet, click the "Create Blank Save file"
10. If you already have a file to save data in (i.e. you already created a save file using this program previously), then click "Choose New Save Target" to select this file. This will be pre-populated if you have already analyzed another file this session.
11. Click the "Save results to Save Target" button to save all of the analyzed data to the save target you chose in the previous step.
12. Click the "Load new file to analyze" button to select your next isometric trial to analyze, then head to step 3.

## How the Auto-Detection Thresholds Work

There are a few different ways that you can automatically detect the "onset of contraction". All methods (save manual identification), use a threshold value to identify the start. Basically, as soon as the force value on the trace rises above the standing weight value by greater than the threshold value (i.e. standing weight + threshold value), that causes the rest of the calculations to start at that identified sample. If you wish to use manual identification, choose the "Manual Identification" option, and the start of the pull will be "forced" to start at the position of the green cursor.

## How standing weight is calculated

The "Standing Weight" cursor defines the starting point for the samples that are used for estimating standing weight. From the cursor, the next 1000 samples are averaged to estimate standing weight. The length of the sample period can be modified from the "Parameter Adjustment" tab.

## How to ensure that your trials will be accurately analyzed

The following instructions outline the basics of what you need to do in an isometric squat or isometric mid thigh pull for this program to analyze it correctly.
- Have the subject get into the correct body position, with minimal pre-tension. 
- The subject must stand in position for a period of a minimum of 1 second prior to initiating the trial (i.e. the contraction) so that there is a period from which standing weight can be calculated (note that 2-3 seconds is probably ideal). They should stay perfectly still during this period.
- From the standing weight period until the contraction, they should be stable (i.e. no swaying, repositioning, or any "dip"). Redo the trial if they do any of these things.
- Subject should pull as "fast and as hard as possible" for 5-6 seconds, after which they should relax.

## Authors

* **George Beckham, PhD**  - [GitHub](https://github.com/ExcellentSport), [Personal Website](https://www.georgebeckham.com)


## License

Isometric Analyzer is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version. Isometric Analyzer is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.
