# IsometricAnalyzer

NOTE: THIS PROJECT IS IN ALPHA STATUS. CODE HAS NOT BEEN TESTED FOR STABILITY, ACCURACY, OR OTHERWISE. UNLESS YOU ARE FAMILIAR WITH LABVIEW, I STRONGLY RECOMMEND SAVING THIS LINK AND CHECKING BACK IN A FEW WEEKS/MONTHS.

A Labview program to analyze isometric squat and isometric mid thigh pull files from a force plate. Currently able to import and parse csv files with comma or tab separation. 

## Getting Started

**If you have Labview 2016 or newer installed:**  
The primary parent folder contains the source code for the main Labview Project and Primary VI "Main.vi". If you're interested in seeing the source, you can fork/pull/download the entire repository to view/use/edit. You will need a full version of Labview 2016 or newer to use.

**If you don't have Labview 2016 installed:**  
The folder "Builds" contains the "Isometric Analyzer.exe" and all of the primary dependencies for running said executable, with the exception of Labview Runtime 2016. You will need to first download and install Labview Runtime 2016 to be able to run the executable. It can be found here: http://www.ni.com/download/labview-run-time-engine-2016/6066/en/

## How to use

1. Start the program by clicking the right arrow in the upper left corner.
2. Select a file to analyze (I recommend using one of the ones included in the "Examples" folder, or making copies of real force plate outputs and analyzing those.)
3. Enter relevant data about your subject.
4. On the primary "Force Time Trace" graph:
	- Drag the yellow bar to approximately 1 second before the start of the pull
	- Drag the green bar to slightly before the pull
	- Drag the red bar to after the pull, where the force value is lower than the starting value (just eyeball it, or verify on the "Intracursor Segment" graph on the "intra-cursor" tab that the pull force trace comes back down the the green horizontal line. There will also be a green cursor on this graph to let you know it has ID'd the final value.
5. Figure out the standing weight segment
	- Click over to the "SW Segment" tab
	- Drag around the yellow cursor a bit - this analyzes a 1000ms (can be changed on the parameters tab) segment immediately following the yellow cursor to determine the standing weight. Try to keep this as close to the start of the pull as you can, but also play around with moving it back a bit to find a segment with as low a "SW Segment Range" that you can (don't go farther than about 2 seconds behind the start of the pull). If you have a segment that is too variable, the red light will turn on. 
	- Leave the cursor there when done
6. Check out the "Pull Start ID" tab to verify that the pull start is correctly identified.
	- If not, verify that you have cursors correctly placed, and that the red button on the SW Segment tab isn't lit.
	- If yes, move on
7. Verify that all your entered data on the "Data Entry and Saving" tab is good.
8. If you don't have a file to save all of this in yet, click the "Create Blank Save file"
9. If you already have a file to save these in (i.e. you already created a save file using this program previously, then closed the entire program out), then click "Choose New Save Target" to select this file.
10. Hit Save results.
11. Hit the stop button, then click the start button again to restart the process. The program will save your previously selected save target if you don't close the program.

## How the start thresholds work

There are a few different ways that you can automatically detect the "onset of contraction". All methods (save manual identification), use a threshold value to identify the start. Basically, as soon as the force value on the trace rises above the standing weight value (i.e. standing weight + threshold value), that causes the rest of the calculations to start at that identified sample. If you wish to use manual identification, choose the "Manual Identification" option, and the start of the pull will be "forced" to start at the position of the green cursor.


### Prerequisites

Labview 2016 or newer to view the source.
Labview 2016 run time libraries to run the executable (http://www.ni.com/download/labview-run-time-engine-2016/6066/en/)

## Authors

* **George Beckham, PhD**  - [ExcellentSport](https://github.com/ExcellentSport)
