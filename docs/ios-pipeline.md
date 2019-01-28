# Setting up the iOS Build Pipeline
In order to set up the automated iOS builds you need to have [installed the build extension and set up a macOS agent](https://dinomite-studios.github.io/unity-azure-pipelines-tasks/). After this is completed, head over to the [Azure Dev Ops](dev.azure.com) and create a new project if you haven't done so yet.

## 1. Create a pipeline
 - On the left hand side click on *Pipelines*
 - Create a new pipeline
 - _Do not_ pick your repository location directly, but click on *Use the visual designer* just below
 - Give Dev Ops access to your repository and pick your branch
 - Select "_Start with an empty job_" right at the top
 - Click on Pipeline, set up a name and pick your build agent ( e.g. Default in Self-Hosted )
 
Great now that we have everything in place, we will need to define the tasks.

## 2. Setting up the Unity Build task
 - Click the "+" on the Agent Job 1 and search for "Unity build" and click *Add*
 - Select the new task and let's configure it 
 - Give the task a name or leave it as is
 - Set your Build target to iOS
 - If your Asset folder is not at the toplevel of your Repository, set the foldername in Unity Project Path
 - Expand the Output variables tab and name set the Reference name e.g. to _unityBuildTask_
 
 ## 3. Setting up the Xcode build task
  - Click the "+" on the Agent Job 1 again and this time search for "Xcode" and click *Add*
  - Select the Xcode task on the left and configure it as follows
  - Set the _"Workspace or project path"_ to *$(unityBuildTask.buildOutputPath)/Unity-iPhone.xcodeproj* (Replace unityBuildTask with whatever you set at the step 2.
  - Set the _"Scheme"_ to *Unity-iPhone*
  
  

 

