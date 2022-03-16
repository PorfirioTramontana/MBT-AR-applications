# Model Based Testing of AR Mobile applications
Before describing the steps by which to replicate the carried out tests, we illustrate the files and folders in the repository. At the beginning of the hierarchy there are three folders:
* log analysis, containing the .jar file, necessary for the analysis of the log files (as will be shown below), and the related source code folder;
* Safari Animal AR;
* Point AR.

This repository is a fork of the ([original one] https://github.com/danilobevilacqua/TesiMagistrale) deveoped by Ing. Sabato Danilo Bevilacqua during his Laurea Degree Thesis, where further information about his work can be found (in italian).

The two folders, Safari Animal AR and Point AR, relate to the applications of the same name ([Safari AR] (https://github.com/abdullahibneat/SafariAnimalsAR) and [Point AR] (https://github.com/abdullahibneat/ PointAR)) which were used as case studies. Inside the Safari Animal AR folder there is:
* the application folder containing the apk and the log and interaction files for each type of coverage (both within the respective folder);
* the mutant folder 1 containing the modified application apk (the movement error was injected, i.e. by moving the pad to the right the animal moves to the left and vice versa), the interaction files within the respective folders and the modified script causes the error;
* the mutant folder 2 containing the apk of the modified application (the error of multiple presence of animals on the scene has been injected, i.e. by choosing any animal, other than the zebra, it will not be alone on the scene but will be co-present with the zebra), the interaction files within their respective folders and the modified script causing the error;
* the probes folder containing the original scripts of the application to which the probes for checking the coverage of the code and the script that allows their insertion have been added (SondaManager);
* the results of executed tests (testAllOneLoopPathsCoverageNew.air, testAllStateCoverageNew.air, testAllTransitionsCoverageNew.air and testAllTransitionsCoverageEstesoNew.air);
* the marker.

Similarly, inside the Point AR folder there is:
* the application folder containing the apk and the log and interaction files for each type of coverage (both within the respective folder);
* the mutant folder 1 containing the modified application apk (the error of not opening the drop-down menu has been injected, i.e. it is not possible to open it to select the translation language), the interaction files within the respective folders and the image showing which check was removed from the Unity IDE to cause this error;
* the mutant folder 2 containing the apk of the modified application (the error of incorrect translation of marker 1 has been injected, i.e. by selecting the Lithuanian language the marker 1 will be translated into Italian), the interaction files within the respective folders and the modified script cause the error;
* the probes folder containing the original scripts of the application to which the probes for checking the coverage of the code and the script that allows their insertion have been added (SonadaManager);
* the results of the executed tests (testAllOneLoopPathsCoverageAttesa.air, testAllOneLoopPathsCoverageMarker1.air, testAllOneLoopPathsCoverageMarker2.air, testAllStatesCoverageMarker1.air, testAllStllatesCoverageMarker1.air, testAllStllatesCoverageMarker1.air, testAllStllatesCoverageMarker1.air
* the markers.

Having described the content of the repository, we move on to detail how to replicate what is described in the thesis.

## Tools installation
We start by installing the necessary environments:
1. installation of the Unity engine version 2018.4.30f1, downloadable from the [official website] (https://unity3d.com/get-unity/download/archive). It is also necessary to install UnityHub (always from the same link) since it allows the management of different versions of Unity and the addition of any modules;
2. after installing UnityHub, start it and choose the `installs` tab, click the three dots relative to the Unity version box, click` Add Modules` from the drop-down menu, check `Vuforia Augmented Reality` and` Android Build Support`, finally click `Done`. Once the installation is finished, the relative icons of the installed modules will appear in the Unity version box;
3. download AirTestIDE from the [official website] (https://airtest.netease.com/), extract the contents of the zip and place it on the Desktop. It is necessary to place it on the Desktop in order to allow the test scripts and the Log Analysis .jar to work correctly;
4. download Poco-SDK from the [official website] (https://github.com/AirtestProject/Poco-SDK);
5. install Android Studio from the [official website] (https://developer.android.com/studio);
6. after installing Android studio, start it and create a virtual device with the following features:
   - Smartphone model: Pixel 2;
   - Operating system: Android 8.1 Oreo;
   - API level: 27;
   - RAM: 1536 MB;
   - Storage space: 2048 MB internal + 512 MB SD-CARD.
7. start the device and enable developer mode.

## Test execution
Below we will show how to use the aforementioned environments to conduct tests on each of the two AR applications.

### Safari Animal AR
The steps to follow to import the Safari Animal AR application locally will be defined below. Note that the executable application can be directly downloaded from [apk file] (https://github.com/PorfirioTramontana/MBT-AR-applications/blob/main/Safari%20Animal%20AR/application/safari.apk), in order to install it on the virtual device by drag and drop.

#### Import application
It is necessary to download, in zip format, the entire [Safari AR] repository (https://github.com/abdullahibneat/SafariAnimalsAR) and follow the instructions in the `How to use` section of the same repository. Subsequently it will be necessary to change the marker by following the following steps:
1. open the project with UnityHub;
2. select the GameObject `Image Target` from the object hierarchy;
3. from the Inspector section, in the Database item select `VuforiaMars_Images` and in the Image Target item select` Astronaut`;

At this point, after extracting the Poco-SDK from the zip, you need to drag and drop the `Unity3D` folder into the project, preferably in the` _Script` folder and then delete the folders inside it. `ngui` and` fairygui`. After that we need to add the `PocoManager` script to the` ARCamera`. In case of errors make sure that in the `Player Settings` section, in the` Other Settings` tab under the heading `Scripting Runtime Version`,` .Net 4.x Equivalent` is selected. As for the scripts, in the `_Script` folder of the Unity project, the file [SondaManager] (https://github.com/PorfirioTramontana/MBT-AR-applications/blob/main/Safari%20Animal%20AR/) must be added by drag and drop 'script con sonde/SondaManager.cs') and invoke its function in the other scripts to insert the probes. Alternatively, you can replace the files present with those in the [Script with probes] folder (https://github.com/PorfirioTramontana/MBT-AR-applications/tree/main/Safari%20Animal%20AR/script%20con%20sonde). Finally it will be necessary to create the apk that will have to be deployed on the virtual device and to do so the following steps are necessary:
1. open Android Studio and start the previously created emulated device;
2. after it has started, in Unity click on the `File` tab and then on` Buil Settings`;
3. click on `Android` and then on` Switch Platform`;
4. under Run Device select the emulated device;
5. Click on `Build And Run`.

If everything went well, the application should start on the emulated device. At this point it will be necessary to place the [marker] (https://github.com/PorfirioTramontana/MBT-AR-applications/blob/main/Safari%20Animal%20AR/marker.jpg) on the table or on the wall of the virtual room. To do this, simply click on the three dots of the bar associated with the device. In the new window that will open select the `Camera` tab and place the marker, preferably on the table, and close this window. Move to the room where the marker is present, frame it in order to make the augmented reality scene appear. Note that the developer has expected this application to fix the orientation of the smartphone horizontally.

#### Test
To perform the tests you will need to open the `AirTestIDE` folder (previously located on the Desktop) and start` AirTestIDE.exe`. At startup you will need to click on the `skip` button of the window that will open in addition to the command prompt. Once the IDE is open, click on the `File` tab and then` Open` to open the test script related to the desired coverage criterion. Before starting it:
* make sure your phone is connected to the IDE. To do this, just click on the `connect` button next to the device name in the Devices window. If the device does not appear click on 'refresh ADB`. If, after connecting the device with AirTestIDE, the RAM memory becomes saturated, the problem is due to the way in which the resources are allocated to emulate the graphics of the device. To solve this problem it is necessary to change the emulated device, creating it with the following characteristics:
  - Smartphone model: click on the `New Hardware profile` button, leave all the default settings and finally click` Finish`;
  - Operating system: Android 11.0 with ABI x86_64;
  - API level: 30;
  - Graphics: Software (to be selected in the `Emulated Performance` section after selecting the Operating System);
  - RAM: 1536;
  - Storage space: 800 MB internal.
* make sure that the application just started points the marker creating the augmented reality scene;
* be sure to delete any previous Log file from the smartphone memory. To do this, you need to:
  - click on `Settings`;
  - click on `Storage`;
  - click on `Internal shared Storage`;
  - click on `Files`;
  - click on `Android`;
  - click on `Data`;
  - click on `com.abdu.SafariAR`;
  - click on `files`;
  - delete `LogFiles.txt`.

After carrying out the above checks, start the test script and wait for it to finish. To view the report click on the `Run` tab and then on` View Report`. The interactions file will be created in the same folder as the script, which will define the interactions performed for each path executed. At this point it is essential to extract the log file from the smartphone. To do this, it is necessary to use the [Analysis Log] program (https://github.com/PorfirioTramontana/MBT-AR-applications/blob/main/analysis%20log/Analisi%20Log.jar), taking care not to close the emulated device, following steps:
1. start `Log Analysis`;
2. click on the `Import` button;
3. enter `com.abdu.SafariAR` as the package name;
4. enter any name that does not contain spaces and \ or symbols as the name of the log file;
5. Click on the `Import` button.

If everything is successful, there will be a message of successful loading, the log file will have been deleted from the emulated device and will be present on the Desktop with the chosen name. At this point it will be possible to load the scripts in order to evaluate their coverage. To do this, click on the `Load Script` button and insert the files, containing the probes, to be evaluated (` Autofocus`, `AnimalSpawn`,` AnimalsController`). After uploading them you will need to click on `Analyze`. Once this is done, a window will open showing which branches have been executed and how many times and the percentage of coverage of the script (branches executed / total branches). In case the coverage percentage is less than 100% for each script it will be possible to click the `Unexecuted branches` button, which will show which branches of the code have not been executed. The above can be done for each of the test scripts (`testAllTransionsCoverageNew.air`,` testAllTransionsCoverageEstesoNew.air`, `testAllStateCoverageNew.air`,` testAllOneLoopPathsCoverageNew.air`). Note that you can bypass the test run by downloading the interaction logs and files from [here] (https://github.com/PorfirioTramontana/MBT-AR-applications/tree/main/Safari%20Animal%20AR/application). It will be possible to analyze the log file using the `Upload` button of the` Log Analysis` program which allows you to load the file not from the emulated device but from the PC.

#### Mutant tests
Mutants are versions of the application that have been injected with errors. In this case of the application in question, two have been created.

##### Mutant 1
Mutant 1 predicts the injection of an error related to the movement of the animal. In other words, by moving the pad to the right, the animal moves to the left and vice versa. This error was obtained by editing the AnimalsController script. What will be said can be bypassed if you download the [apk] (https://github.com/PorfirioTramontana/MBT-AR-applications/blob/main/Safari%20Animal%20AR/mutante%201/safariErroreMovimentoMutante1.apk) of the mutant and install, by drag and drop, on the emulated device. To create mutant 1 you need:
* start UnityHub by opening the Safari Animal AR project;
* within Unity, open the `_Script` folder of the project;
* open the `AnimalsController.cs` file;
* modify the instruction on line 41, putting the minus symbol (-) immediately after the equal symbol;
* save the script;
* generate the apk as shown above.

Alternatively, instead of modifying the file, it can be replaced with the one already modified, downloadable from [here] (https://github.com/PorfirioTramontana/MBT-AR-applications/blob/main/Safari%20Animal%20AR/mutante%201/AnimalsController.cs ). Once the mutant has been obtained, it will be necessary to start AirTestIDE, connect the emulated device and start the test file of the desired coverage criterion (respecting what has been said in the previous section). If the test script is able to detect the error, AirTestIDE will show which assertion failed. In particular, by generating the script report, you will clearly see which assertions were satisfied and which one caused the error. As proof of what has been said, even the interaction file (present in the same folder as the script started) will not have the final string "Test completed without errors". More precisely, within this file there will be all the paths, with the relative interactions, carried out up to before the malfunction. The sequence of interactions causing the error will be related exclusively to the last path executed.


##### Mutant 2
Mutant 2 predicts the injection of an error related to the appearance of more animals on the scene. In particular, the only animal to be alone on the scene will be the zebra. In fact, by clicking one of the buttons relating to any other animal it will be co-present with the zebra in the AR scene. What will be said can be bypassed if you download the [apk] (https://github.com/PorfirioTramontana/MBT-AR-applications/blob/main/Safari%20Animal%20AR/mutante%202/safariErroreAnimaliMutante2.apk) of the mutant and install, by drag and drop, on the emulated device. To create mutant 2 you need:
* start UnityHub by opening the Safari Animal AR project;
* within Unity, open the `_Script` folder of the project;
* open the file `AnimalSpawn.cs`;
* modify the statement on line 77, inserting the statement `models [0] .SetActive (true)`;
* save the script;
* generate the apk as shown above.

Alternatively, instead of modifying the file, it can be replaced with the one already modified, downloadable from [here] (https://github.com/PorfirioTramontana/MBT-AR-applications/blob/main/Safari%20Animal%20AR/mutante%202/AnimalSpawn.cs ). To run the test scripts on the mutant, just follow the instructions in the section on mutant 1.


### Point AR
The steps to follow to import the Point AR application locally will be defined below. Note that what will be explained in the Import Application section can be bypassed by directly downloading the [apk file] (hhttps://github.com/PorfirioTramontana/MBT-AR-applications/blob/main/Point%20AR/application/pointAR.apk), in order to to install it on the virtual device by drag and drop.

#### Import Application
It is necessary to download, in zip format, the entire [Point AR] repository (https://github.com/abdullahibneat/PointAR) and follow the instructions in the `How to use` section of the same repository. Unlike the previous application, two markers are needed here, which will be identified as [marker 1] (https://github.com/PorfirioTramontana/MBT-AR-applications/blob/main/Point%20AR/marker1.png) and [marker 2] ( https://github.com/PorfirioTramontana/MBT-AR-applications/blob/main/Point%20AR/marker2.png). The Poco-SDK must be added to the project, in the same way as in the previous case, and the `SondaManager` file must be added in order to insert the probes into the scripts present in the project. Alternatively, the scripts can be replaced with those already containing the probes, downloadable from [here] (https://github.com/PorfirioTramontana/MBT-AR-applications/tree/main/Point%20AR/script%20con%20sonde).

#### Test
To carry out the tests, the same steps shown above will be carried out. However, unlike the previous case, for each coverage criterion there are two \ three scripts, each relating to the case in which marker 1, marker 2 or neither is framed. So before starting the test script check that the correct marker is present in the virtual room (preferably place it on the wall); The log file must be imported from the virtual device, using the `Log Analysis` program, only when all the scripts related to the chosen coverage criterion have been executed. The only difference compared to the previous case is the different name of the package to be inserted (`com.abdu.PointAR`). As for the interaction files, even if related to the same criterion, they will be found in the respective test script folders. Note that the test scripts [testAllTransitionsCoverageMarker1] (https://github.com/PorfirioTramontana/MBT-AR-applications/blob/main/Point%20AR/testAllTransitionsCoverageMarker1.air/testAllTransitionsCoverageMarker1.ttpy (https://github.com/PorfirioTramontana/MBT-AR-applications/blob/main/Point%20AR/testAllOneLoopPathsCoverageAttesa.air/testAllOneLoopPathsCoverageAttesa.py) have commented instructions. If these instructions were uncomment, the extended version (running the other scripts related to the same criterion) of the selected criterion would be obtained. As in the previous case, it is possible to bypass the execution of the tests by downloading the logs and the interaction files from [here] (https://github.com/PorfirioTramontana/MBT-AR-applications/tree/main/Point%20AR/application).

#### Mutant tests
As in the previous case, two mutants have also been created for this application.

##### Mutant 1
Mutant 1 foresees the injection of an error relating to the opening of the drop-down menu. In other words, by clicking on the drop-down menu to select the language, it will not be able to open to show all the languages available for translation. What will be said can be bypassed if you download the [apk] (https://github.com/PorfirioTramontana/MBT-AR-applications/blob/main/Point%20AR/mutante%201/pointARErroreDropdown.apk) of the mutant and install it, by drag and drop, on the emulated device. To create mutant 1 you need:
* start UnityHub by opening the Point AR project;
* within Unity, navigate the GameObject hierarchy by clicking on `Canvas`, then on` LanguageSelectionGroup` and finally on `Dropdown`;
* uncheck the item `Dropdown (Script)` as shown in [figure] (https://github.com/PorfirioTramontana/MBT-AR-applications/blob/main/Point%20AR/mutante%201/spunta%20dropdown.PNG);
* generate the apk as shown above.

To run the test scripts on the mutant, just follow what was previously described.

##### Mutant 2
Mutant 2 predicts the injection of an error related to the translation of marker 1 into Lithuanian. In other words, by selecting the Lithuanian language, marker 1 will not be translated into the selected language but into Italian. What will be said can be bypassed if you download the [apk] (https://github.com/PorfirioTramontana/MBT-AR-applications/blob/main/Point%20AR/mutante%202/pointARErroreLituanoItaliano.apk) of the mutant and install it, by drag and drop, on the emulated device. To create mutant 2 you need:
* start UnityHub by opening the Point AR project;
* within Unity, open the `_Script` folder of the project;
* open the `translate.cs` file;
* modify the instructions on lines 71 and 72, inverting the values ​​of `true` and` false`;
* save the script;
* generate the apk as shown above.

Alternatively, instead of modifying the file, it can be replaced with the one already modified, downloadable from [here] (https://github.com/PorfirioTramontana/MBT-AR-applications/blob/main/Point%20AR/mutante%202/translate.cs). To run the test scripts on the mutant, just follow what was previously described.
