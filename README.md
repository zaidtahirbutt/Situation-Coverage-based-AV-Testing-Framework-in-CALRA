[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

# Intersection focused Situation Coverage-based Verification and Validation Framework for Autonomous Vehicles Implemented in CARLA

<p align="center">
  <img src="https://user-images.githubusercontent.com/25262332/147320344-826c573b-4016-4d0a-b0fa-434f76c82040.png">
</p>	



As seen in the video below, the SitCov V&V framework has generated a sunny and clear situation to test the AV with the adversereal vehicle coming in form the top of the intersection and AV from the left. The Deeplearning vision-only-based collision avoidance-control of the AV stops it in time. The camera feed of the AV can be seen on the top right. 

https://user-images.githubusercontent.com/25262332/166877997-05aae717-a718-49b0-af80-220c87183a70.mp4



In the second video below, the SitCov V&V framework has generated a rainy and foggy situation to test the AV with the adversereal vehicle coming in form the top of the intersection and AV from the right. The Deeplearning vision-only-based collision-avoidance control of the AV doesn't detect the hazard in time due to its vision being occluded by the rain and the fog and collision happens. The camera feed of the AV can be seen on the top right. 

https://user-images.githubusercontent.com/25262332/166877051-95ba479d-0ae4-45f7-a9f9-2847be5fc1b1.mp4





The above mentioned framework will be referred to as Situation Coverage-based (SitCov) Autonomous Vehicle (AV)-Testing Framework in CALRA. This repository contains the files and the steps needed to run the SitCov AV-Testing Framework in Carla. Our SitCov AV-Testing Framework uses CARLA software and Scenario Runner API. 

### Cite my paper and this repo as well if you plan to use this. 
Here is the link to the paper

https://doi.org/10.48550/arXiv.2112.14706 (arxiv)

https://doi.org/10.1007/978-3-030-98260-7_12 (Journal)

'''
## Reference Citation for my paper:

Tahir, Z., Alexander, R. (2022). Intersection Focused Situation Coverage-Based Verification and Validation Framework for Autonomous Vehicles Implemented in CARLA. In: , et al. Modelling and Simulation for Autonomous Systems. MESAS 2021. Lecture Notes in Computer Science, vol 13207. Springer, Cham. https://doi.org/10.1007/978-3-030-98260-7_12

'''


'''

Follow me on Linkedin: https://www.linkedin.com/in/zaidtb/

Follow me on twitter: https://twitter.com/Zaid_TB

'''


--------------------------------------------------------------------------

## Instruction to run the Situation Covoverage-based AV-Testing Framework

The full steps of getting this framework to run are mentioned below. These instructions are for a windows 10 OS, please run equivalent Linux commands or anyother OS commands (depending upon the OS you have).


## 1) Install Anaconda and create a virtual environment in Anaconda software
--------------------------------------------------------------------------

- First creating virtual python env in anaconda and install python using the following command:
  
  **conda create -n carla_sitcov_avtesting pip python=3.7**
  
-	Activate the virtual env to install the subsequent packages inside the virtual env using following command:

     **activate carla_sitcov_avtesting**
     
- Set up two folders in your drive. One for Carla and one for Scenario Runner. 

## 2) Install CARLA 9.10 (This exact version)
--------------------------------------------------------------------------

- Then go to **Carla 9.10** website here https://carla.readthedocs.io/en/0.9.10/start_quickstart/ and download **Carla 9.10** and follow the guidance on how to run it. If DirectXRunTime error occurs, download Carla9.4 and run CarlaEU4.exe and get the option to fix this error and install EU4 prerequisites first.

- One of the requirements mentioned on the page is to run this command:

     **pip install --user pygame numpy**
     
- **Test Carla installation** by going to the examples folder in Python API folder inside Carla (using the cd command in the terminal). My examples folder is at the following address in my PC, "D:\Carla9.10\WindowsNoEditor\PythonAPI\examples". Run the spawn_npc.py python script while CarlaUE4.exe is running using this command:

     **python spawn_npc.py**

## 3) Install Scenario Runner 9.10 (This exact version)
--------------------------------------------------------------------------

- Set up **scenario runner 9.10** for **Carla 9.10** using these links https://github.com/carla-simulator/scenario_runner/tree/0.9.10  and  https://github.com/carla-simulator/scenario_runner/blob/0.9.10/Docs/getting_scenariorunner.md and follow all the instructions provided there to run scenario runner 9.10 with Carla 9.10.

- Go into scenario runner folder and run the following commands (helping tip in Scenario Runner 9.10 installation):

     **pip3 install --user -r requirements.txt**
     
- Then set the environment variables as shown in the **scenario runner** docs link provided above.
The environment variables will take the paths of the Carla installation and Scenario Runner installation.
     
     
- To check the **Scenario Runner** installation, run the **CarlaUE4.exe** (**in Carla folder**) and run the following two python scripts in order in the **Scenario Runner folder** using these commands:
		
     **python scenario_runner.py --scenario NoSignalJunctionCrossing --reloadWorld --output**
		
     **python manual_control.py --autopilot**
     
- **Make sure your Carla 9.10 installation and Scenario Runner 9.10 are working properly before moving to the next steps.**Need to run scenario and manual control in different terminal at the same time. 

## 4) Setting up the Situation Coverage-based AV-Testing Framework
--------------------------------------------------------------------------

### 4a) The first step here is to download the two folders in this repo named **"PythonAPI"** and **scenario_runner-0.9.10**
### 4b) The second step is to go to your Carla installation folder and replace its **"PythonAPI"** folder with this repo's **"PythonAPI"** folder.
### 4c) The third step is to go to your Scenario Runner API folder and replace the whole folder with "scenario_runner-0.9.10" folder from this repo. Make sure both folders are named the same (scenario_runner-0.9.1), as the environment variables were set according to this name.
--------------------------------------------------------------------------

### Now install the following packages using these commands below:

- **pip install xmlschema**
- **pip install six**
- **pip install py-trees==0.8.1**
- **pip install ephem**
- **pip install networkx**
- **conda install -c conda-forge shapely**
- **pip install tabulate**
- **pip install XlsxWriter==1.4.3**

### The SitCov AV-Testing Framework is using Google Object Detection API which uses DeepLearning Models for object detection using Tensorflow. Install following packages for it using these commands:

- **pip install scipy** 

- Tensorflow 2.4.1 is used for the object detections part. Install it in the virtual environment us this command below:

	**pip install --ignore-installed --upgrade tensorflow==2.4.1**
	
- Follow all the steps here https://www.tensorflow.org/install to install all the dependencies of tensorflow.

- Install the following packages as well using these commands:

- **pip install matplotlib**

- **pip install opencv-python**

- **pip install openpyxl==3.0.7**

- **pip install cython**

- **pip install git+https://github.com/philferriere/cocoapi.git#subdirectory=PythonAPI** (visual studio need to be installed before in the working pc)

- **pip install tf_slim**

- Use following command to set the environment variables path to Models and Object detection Models inside the scenario runner! (considering you have scenario_runner-0.9.10 folder at this location in D: \ )

	**set PYTHONPATH=D:\scenario_runner-0.9.10\models;D:\scenario_runner-0.9.10\models\research;D:\scenario_runner-0.9.10\models\research\slim**

## 5) Running the Situation Coverage-based AV-Testing Framework

- Run the following command inside the "scenario_runner-0.9.10" folder to run the SitCov AV-Testing Framework automatic testsuite generation:

	### **python situationcoverage_AV_VV_Framework.py --scenario IntersectionScenarioZ_11  --not_visualize --Activate_IntersectionScenario_Seed --IntersectionScenario_Seed 13212 --use_sit_cov --reloadWorld --output**
	
	 **-- Please change the random number generation integer after the argument "--IntersectionScenario_Seed" (it is 13212 in the command displayed above), 	for a different starting random seed so you get a different "set" of results.**
	
	**-- Please remove the argument "--use_sit_cov" if you want to generate situations RANDOMLY instead of SITUATION-COVERAGE-BASED GENERATION.**

- For running SitCov AV-Testing automatic test-suite generation for more than one time use the following command (Just type the number infront of repetitions argument for the number of test cases you want generated):

	### **python situationcoverage_AV_VV_Framework.py --scenario IntersectionScenarioZ_11  --not_visualize --Activate_IntersectionScenario_Seed --IntersectionScenario_Seed 13212 --use_sit_cov --reloadWorld --output --repetitions 3**
	
	 **-- Please change the random number generation integer after the argument "--IntersectionScenario_Seed" (it is 13212 in the command displayed above), 	for a different starting random seed so you get a different "set" of results.**
	
	 **-- Please remove the argument "--use_sit_cov" if you want to generate situations RANDOMLY instead of SITUATION-COVERAGE-BASED GENERATION.**
	
## 6) Additional Directives while using this Situation Coverage-based AV-Testing Framework:

- Zoom out from the map at the start of the simulation towards the North East (drag your mouse to make the view as if a camera was pointing from the sky downwards) and spot where the ego and other vehicle are being generated and then zoom into that place from the top for each simulation run. Ideally I should have set up a camera to automatically show this view upon every simulation run, just need some additional coding for that. 

- Excel Template and Python code for writing SitCov AV-testing framework testsuite results has also been provided 

### 6b) One improvement needs to be done:

- The simulation class objects (each time a sitcov object is generated) aren't being removed after each simulation so the max repitions you can use is 20 using "--repetitions 20" command (this number might be lower or higher depending upon your PC specs but eventually your PC memory will overflow) after which your PC memory will overflow.

-This problem can also be fixed with a simple class object delete command after each simulation. But for now you can keep doing simulation runs for 20 reps and then change the random number seed for the next 20 runs and so on.

## 8) A few screenshots of the testcases generated by the SitCov AV-Testing Framework (taken from my paper):

- Below are a few screenshots of the SitCov AV-Testing Framework automatic testsuit generation. 

<p align="center">
  <img src="https://user-images.githubusercontent.com/25262332/147320549-7879bf04-f834-4492-8383-4448e11de4bc.png">
</p>	


<p align="center">
  <img src="https://user-images.githubusercontent.com/25262332/147320561-9128d665-f8e3-4b25-b99f-bd57b12b20ec.png">
</p>	



License
-------

Situation-Coverage-based-AV-Testing-Framework-in-CARLA specific code is distributed under MIT License.




