# CARLA-ScenarioRunner-Docu
This is an in deepth descripton of the Carla Scenario Runner
ScenarioRunner is a module that allows traffic scenario definition and execution for the CARLA simulator. The scenarios can be defined through a Python interface.

To get a first impression on how the Scenario Runner works follow the get started Tutorial. To execute a scenario we need the scenario_runner.py script and hand over the scenario name. The scenariorunner function is used running (and repeating) a single scenario or a list of scenarios.

The name of the Scenario that is used for calling is defined in a xml file and is located in srunner/examples. 
In the xml file the scenario name references to a class, which is the actual scenario you want to run. The xml is used to create multiple spawn points (in different Maps) for a scenario. You could also set other attributes, like weather settings. 
The Python scenario Classes can be found under srunner/scenarios. Similar scenario classes are in one Python file and do not have to match the file name. For example, the scenarios VehicleTurningLeft and VehicleTurningRight are in the file object_crash_intersection.py.
To test the Scenario you run manual_control.py in the Root Folder. A new window opens and you can drive through the simulation yourselfNow we know what the scenario Runner is, how to run it and what components there is.
 Creating a new scenario 
To create our own scenario we need a new python File in the srunner/scenarios folder with our class in it. To understand how to write a scenario lets look at an existing scenario, the follow_leading_vehicle.py. First we need all our imports that we are going to use. Then we have our actual scenario class and hand over a BasicScenario Object. This class can be found in the same folder in basic_scenario.py. In our init function we setup all relevant parameters. We need a function named initialize_actors, where we spawn all required Actors for this scenario. The create_behavior function defines what the Actors do in the scenario. We need to build a behaviour tree that executes all our conditions sequential. 
For Feedback if the scenario was successful, we use the create_test_criteria function. Most of the time we want to check if there was a collision. But you can define every condition that is relevant to your scenario.
Lastly, we have the del function that destroys all actors left. Of course, other functions needed can be added as we can see in some scenarios. Read code of Scenarios that have a aspect your scenario should have to implement it. 
After you created a new scenario, you need a xml file with the spawn locations for the ego vehicle. You can use another xml file as template. Each Spawn point needs an individual name. Now you can run your scenario with scenario_runner.py.

Scenario_runner.py 
Lets look deeper into the scenario_runner.py script that we use to call the scenarios. We can run python scenario_runnner.py –help to see which parameters we can set. If we want to give our scenario more variables we have to extend the parser and the call function of the scenario.
