This is version 1 of the upgraded Augmented Space Library (ASL). It is being built with Unity 2020.1.0b3 (Unity 2020 beta version 3) and Amazon Web Services - GameLift RealTime Servers (https://docs.aws.amazon.com/gamelift/latest/developerguide/realtime-howitworks.html).  

Documentation for this framework can be found here: https://uwb-arsandbox.github.io/ASL_Master/ASLDocumentation/Help/index.html The first page of website is shown below.

<html>
	<head></head>
	<body>
		<h1>Augmented Space Library Documentation</h1>
		<p>Welcome to the Augmented Space Library (ASL) Documentation System. Here you will find documentation on how ASL works so you can further improve its functionality, as well as find documentation on demos within ASL to better understand how they work and how you can use ASL for your own multiplayer projects. </p>
			<h2>Getting Started</h2>
			<p>The steps to install and setup ASL are as follows:
				<ul>				
					<li>
						<p><strong>Download ASL</strong> - Download this project and open it in Unity 2020.1.0b3 (older versions will most likely not work, but newer ones should). If you have packages errors, then make sure you are using Unity 2020.1.0b3 or higher. If that still does not resolve your package issues, then  continue into Unity and then go to Help->Reset Packages to defaults then install the needed packages manually.</p>
					</li>
					<li>
						<p><strong>Connect to other users</strong> - First and very importantly, you must always build these scenes: <legacyBold>ASL_LobbyScene</legacyBold> and <legacyBold>ASL_SceneLoader</legacyBold>. You will not be able to connect to others and will receive  errors if you do not have these scenes in your Unity build settings. Now, with that out of the way, there are two ways in which you can connect players to each other for either testing your application or using it. The first is through the use of the provided ASL_LobbyScene. If you use this method, you must ensure you always launch from this scene and include the name of the scene you want to launch to in its "AvailableScenes" dropdown UI object. The second method allows you to connect from whatever scene you want and is generally recommended as it involves less user steps. To use this method, you must attach the "QuickConnect" script to an empty GameObject and place that empty GameObject in the Unity Hierarchy window of your desired first scene at the very top so it execute first. You can see examples of this in all of the Simple Tutorials. You must also pick a unique room name and the starting scene for players to transition to after connecting and readying up with each other, the starting would ideally be the scene the QuickConnect script is located in, but does not have to be. If your room name is not unique, then you will join another ASL user's room. The starting scene can be the name of the scene you are currently working in. If you do use this method, you must still build the ASL_LobbyScene and ASL_SceneLoader scenes, though they no longer have to be built first.</p>
					</li>
					<li>
						<p><strong>Using ASL</strong> - You are now ready to begin programming a multi-user interactive experience! Refer to the documentation  if you are having trouble with any function, but in general, make sure to claim your object before doing anything with it and even then, the stuff you do with it should be ASL related only if you want others to see your changes. Note that any and all ASL tutorials should work without any setup.</p>
					</li>
				</ul>
			</p>				
			<h2>Adding documentation</h2>
			<p>Note, the steps to add to this documentation file are as follows, but note that SandCastle can be tricky at times.
				<ul>
					<li>
						<p><strong>Install Sandcastle</strong> -  Go here https://randynghiem.wordpress.com/2015/06/18/how-to-set-up-sandcastle-help-file-builder-with-visual-studio-2015/ and follow the steps provided. When you are actually installing SandCastle, install everything it desires.</p>
					</li>
					<li>
						<p><strong>Check the XML Documentation File Box</strong> - Right click in Visual Studios on "Assembly-CSharp" and go to properties. If nothing shows up then you need to allow Unity properties to be visible in Visual Studios. To do this, follow these directions: https://answers.unity.com/questions/1140063/cant-open-project-property-in-visual-studio-2015-w.html Once in the properties, go to build, and tick the "XML documentation file:" check box. An image of what it looks like can be found in the first link. WARNING: Rather annoying, every time you interact with, run, or even focus on Unity, this file gets rewritten and this checkbox becomes unchecked. If you build SandCastle when this box is unchecked, no errors will appear, instead your documentation file will be blank. </p>
					</li>
					<li>
						<p><strong>Add Sandcastle to Visual Studio</strong> - Now that you have SandCastle installed and Visual Studio project properties set up, you need to add SandCaslte to your project. If the current documentation file (where you got this information from) is no longer available, then you'll need to add a new SandCastle project. To do this, right click your Solution in Visual Studios and Add New Project. Then select Documentation, Sandcastle Help File Builder Project. After adding this, go to the "Documentation Sources" folder and add "Assembly-CSharp.dll" which should also automatically add "Assembly-CSharp.xml", but if it doesn't, add it yourself. These sources by default will be found in "Temp\bin\Debug\" if you were able to successfully build your "Assembly-CSharp" project from Visual Studio. After adding this documentation sources, right click and build your SandCastle Documentation Folder. After this, just go to where it was built and go into the "Help" folder to find your documentation. If this documentation still exists and just needs updating, then instead of creating a new SandCastle project, just add this one instead (ASLDocumentation.shfbproj) and then build.</p>
					</li>
				</ul>
			</p>
			<p>For any additional help in installing, using, or modifying ASL, please contact Kelvin Sung.</p>		
			<h2>Final Notes</h2>
			<p>ASL allows you to have in sync objects (ASLObjects) in your scene before you start your scene and to instantiate these objects at run time. However, in order to ensure ASLObjects starting in your scene are synced properly across users they must have a unique name. This allows ASL to find these objects later and assign them the correct ASL ID. Technically, the formula used to help generate object uniqueness is based upon a string that combines the following: The object's name + the square root of ((the object's position, rotation, scale) + (the Dot Product of the object's rotation and scale * Vector.one)). The following string ends up being the object's name plus a number that is most likely unique, but not guaranteed. To ensure proper ASL object synchronization, give your ASLObjects that start in your scene unique names. ASLObjects instantiated during runtime do not need to have a unique name as their ids are created in a different fashion that is guaranteed to be unique and synchronized. Lastly, the technology being used in ASL (specifically the VR and AR libraries) are constantly being updated. This is a double edged sword as there will be bugs that are no fault of your own, but there is also consistently new content and bug patches. This is even more noticable due to ASL being built on a beta version of Unity. It has often been found that simply closing Unity and restarting it can solve some of the more unique errors that appear while programming. If you find yourself stuff on an error or warning, make sure you try, as the saying goes, turning it off and back on again.</p>	
			<h3>AR Use</h3>
			<p>ASL currently (as of March 2020) supports ARFoudation and its functionalities. If ARFoundation is not being used in your project, feel free to remove its SDK from your project. To do this, remove all the ARFoundation related packages via Window->Package Manager from your project (including ARCore or ARKit packages). Doing so will prevent any ARCore demos from being able to execute. Currently, this includes all demos in "Assets/ASL_Tutorials/Complex/AR_CSS451_MP_Assignments" and "Assets/ASL_Tutorials/Simple/ARCloudAnchors". This will also cause some ASL errors to appear, the code that causes these errors can be safely commented out or delted. In general, ASL has the capability to synchronize all devices, however, ASL currently only has ARFoundation -> ARCore Extension Cloud Anchors integrated. This means only Android AR devices will have the ability to have the same world origin to work from when in. If the user wants iOS to work, then they must install ARKit themselves and add the Cloud Anchor API key themselves, found in Project Settings ->ARCore Extensions. Make sure you select iOS Support Enabled checkbox as well. Since WMTK is also installed in ASL, AR capable headsets can be used as well. However, currently, cloud anchors are not available in these headsets. Eventually, cloud anchors should be possible (normal anchors already are), it is unknown when this capability will be added to ARFoundation. https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/ https://docs.unity3d.com/2019.3/Documentation/Manual/AROverview.html (point cloud = cloud anchor). It should be noted that in the future it is entirely possible that cloud anchors should be moved from an ARCore base to a Azure (spatial anchors) base, or even a new base if Unity creates their own backend for cloud anchors. Lastly, it should be noted that ARFoundation does not have an instant preview mode like Google's ARCore does. Therefore, in order to test on an Android device, you must build on that device. This can take a lot of time depending on your project size and computer specs. It is therefore recommended that you debug as much as possible on the computer (whatever you can without an AR camera) and then switch to debugging on an actual Android device, and that you strip out any libraries you don't need (e.g., the Mixed Reality Toolkit if you aren't using VR in your project as well). It looks like this instant preview may be possible in future Unity releases https://unity.com/solutions/ar-and-vr-games.</p>			
			<h4>AR Requirements</h4>
			<p>The minimum Android API Level is 9.0 'Pie'. AR is setup using Unity's ARFoundation, the ARCore XR Plugin, and ARCore Extensions. Information on these things can be found here: https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.0/manual/index.html, https://docs.unity3d.com/Packages/com.unity.xr.arcore@4.0/manual/index.html, and https://github.com/google-ar/arcore-unity-extensions. To get started with AR, setup your scene similar to the Simple Tutorial - ARCloudAnchors_Example. Specifically, ensure you have ARCameraSpawner in your scene. This object will automatically create the necessary AR objects for you once an online connection is setup by spawning the ARHolder object. Once setup, ASL requires you perform the following actions to ensure all users will stay in-sync. These actions relate specifically to Cloud Anchors which are required to ensure proper real-world orientation between users. There are two methods you can use. The first is to set the world origin for all users. if you choose this method, then every user will have the same world origin - something that is needed to ensure all objects remain in the same spot across users. The world origin, which is created via ASLHelper.CreateARCoreCloudAnchor(), should only set once (e.g., the world origin should never change once set). And, as with cloud anchors in general, should only be able to be set by one person. Whether this is done in code (by using GameLiftManager.Instance().AmLowestPeer()) or by another rule that you chose, it doesn't matter. The second method is to use just a normal cloud anchor and then to have your game objects be children of this cloud anchor. Doing so this way essentially replicates the world origin method, but this means only SendAndSetLocal____ functions will be able viable, as SendAndSetWorld____ may place objects in different locations on different devices due to the devices having different world origins. It should be noted that both methods can be used in tandem, but if you plan on setting the world origin at all, it must be done first - even before any objects are placed in the scene as they may not move properly after the world origin is set. However, sometimes it is easier to already have your objects in the scene upon start, rather than instantiate them at runtime. If your app is set up this way, then it is suggested you ensure the objects will not show up on the screen by giving them an initial position of 100 or higher, and then, after setting world origin, to move these objects with a SendAndSetLocal___ or World___ function. Doing so will then place all objects for all users in the appropriate location. This is the method the AR_CSS451_Mp2 scene uses. As of March 31, 2020, setting the World Origin does not act like it should and therefore should not be used (set it's value to false).</p>
			<h3>VR Use</h3>
			<p>Due to the different types of VR equipment out there, Unity's XR Plugin Management is bein gutlized in ASL to help ensure any and all VR devices can be used in ASL. To add a different VR device than one covered under the Mixed Reality Toolkit (which are the Hololens and the MIxed Reality Headset), go here: https://docs.unity3d.com/2019.3/Documentation/Manual/VROverview.html and follow the instructions accordingly. Make sure you add the plugin in the XR Plugin Management setting which can be found in Project Settings. Lastly, to figure out how to use the Mixed Reality Toolkit in your application, see the Simple Tutorial: MixedRealityToolkitSetup_Example. This example shows how you can get the headset working in your scene. It should be noted that because of the different VR types out there, the Lobby Scene currently does not support VR. If you run from the Unity Editor (Play Mode) then you can type in the Lobby Scene via the keyboard - during this time the VR headset will show an empty scene. If you build and run, then you cannot use the keyboard. Therefore, it is up to the user if they are using VR to change how input works with the Lobby Manager to get their VR device working (e.g., implement a virtual keyboard and change the canvas and it's object's so that the VR headset and controllers can see and interact with them). </p>			
			<h4>VR Requirements</h4>
			<p>There is nothing specific in ASL for VR development. The only thing that ASL contains, because most users will use this platform if VR is being used, is the Mixed Reality Toolkit https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html. If you are using the MRTK, then know that ASL has already completed the setup process for you, and all you need to do is learn how to use it by importing the examples. If you are not using MKTK for VR, then look here for instructions on what to do: https://docs.unity3d.com/2019.3/Documentation/Manual/VROverview.html. Note that when building VR applications, you must have Universal Windows Platform builder installed (via the Unity Hub) and Windows SDK 18362 or higher. To see if you have this SDK, switch to the Universal Windows Platform in Build Settings and check under the Target SDK Version for 10.0.18362.0. You must also go into your computer Settings->Developer Settings and select "Developer mode". If you ever receive an error when attempting to run your VR app stating that it cannot be launched, run this command in Powershell with admin rights and without the containing quotes: "Get-AppxPackage | Where-Object {$_.IsDevelopmentMode -eq "True"} | Remove-AppxPackage" https://developercommunity.visualstudio.com/content/problem/298851/uwp-designer-doesn-load-systemruntimeinteropservic.html Last but not least, make sure the VR application is properly exited after running - this helps keep AWS happy, but more importantly, it'll allow you to rebuild. If you have trouble rebuilding your VR application, make sure the first build has fully exited. The maximum amount of connected monitors you can have when you have a VR device plugged in is 2, even if you have multiple GPUs. If you are using more than 2 monitors and attempting VR, then the VR device will just show a black screen.</p>
			<h3>Notes on Realtime Apps</h3>
			<p>If you check out "Assets/ASL_Tutorials/Complex/CSS385_MP_Assignments/Mp2/" you will notice that while all objects start in sync, due to the same random seed being used across all devices, the scene can quickly deteriorate as it is a realtime game with constantly moving parts that assume because they have the same code and same starting location will always be in sync. In order to synchronize this app completely, every object would need to move with a SendAndSet function and, more importantly, this would need to be handled by some "Host" like user, that processed collisions. Then other players would just send information specific about them. This model is the client-server model and is not the model ASL uses (we use the P2P model). Because of this, these types of applications are very hard for ASL to run efficiently. To help explain this better, ASL would be a very good library for a turn-based game, as each player could send its information and calculate what would happen on their own - still being in sync with other devices because they will calculate the same thing. Then they could release their turn and wait to receive  info. ASL would not be a good choice for a shooter game like the "Assets/ASL_Tutorials/Complex/CSS385_MP_Assignments/Mp2/" assignment because even though all objects start in the same position, due to internet speeds, it is possible that an instantiated object would miss a moving target on one device where it spawned in slow, but hit on another device because it spawned on time. Normally, for these types of games, there is a server to handle all of these interactions and then just pass on that information to its users - hit or miss, ensuring everyone stays in-sync. However, ASL does not do that, instead relying on the user themselves to calculate the game state. While ASL in theory could be used to make any application multiplayer, it favors certain types of applications over others and it is advised that you use it as intended - to create collaborative applications not based upon a physics movement system.</p>		
			<h3>Known Issues and Warnings</h3>
			<p>
				<ul>
					<li>
						<p><strong>All Builds</strong> -  *Warning: Script attached to 'Sphere' in scene '' is missing or no valid script is attached. *Cause: Unknown, no such object or scene (notice how scene name is empty) exist. *Solution: Ignore. </p>
						<p>*Warning: Script attached to '_PlaneThatCallsIntoPlugin' in scene '' is missing or no valid script is attached. *Cause: Unknown, no such object or scene (notice how scene name is empty) exist. *Solution: Ignore</p>
						<p>*Error: ArguementNullException: Value cannot be null. Parameter name: _unity_self. *Cause: Unknown. *Solution: Appears to only happen when exiting when using MRTK, solution for now is to ignore and wait for them to fix as it doesn't seem to cause any issues. </p>
						<p>*Warning: Depth Buffer Sharing is not enabled to improve hologram stabilization. See Mixed Reality Toolkit > Utilities > Optimize Window tool for more information to improve performance *Cause: Unknown as Optimize Window tool does not exist *Solution: Ignore. </p>
						<p>*Warning: Depth Buffer Sharing has 24-bit depth format selected. Consider using 16-bit for performance. See Mixed Reality Toolkit > Utilities > Optimize Window tool for more information to improve performance. *Cause: Unknown, 16-bit is being used and Optimize Window tool does not exist. *Solution: Ignore. </p>
						<p>*Warning: Virtual reality enabled cannot be set while the Editor is in Play mode. *Cause: Attempting to run a VR app with the Play Button. *Solution: Ignore - VR is already set and should work from the Play Mode. This is believed to be a remnant of the Unity's now deprecated VR system.</p>
					</li>
					<li>
						<p><strong>PC</strong> - None</p>
					</li>
					<li>
						<p><strong>Android</strong> - *Warning: System.Windows.Forms.dll assembly is referenced by user code, but is not supported on Android platform. Various failures might follow. *Cause: Using .Net4.0. *Solution: Ignore, ASL doesn't not use Window Forms.</p>
					</li>
					<li>
						<p><strong>Universal Windows Platform</strong> - *Error: DirectoryNotFoundException: Could not find a part of the path "filePathToBuild\ProjectName\Data\boot.config". *Cause: Package being updated, removing the fix for this error, which is looking for a file in the wrong location. When using Universal Windows Platform EXE build, open up the WindowsMRBuildProcessor.cs class (should see it in the Unity console window) and go to line 116 (bootConfigPath = Path.Combine(bootConfigPath, PlayerSettings.productName);) and comment it out. It adds an unnecessary folder to the file path when building the Executable Only version. *Note: This error will come back every time its package is rebuilt and there exists other versions of this error if you chose a different option than Build Executable for Universal Windows Platform. To solve those other versions, do the same thing here, but take out the appropriate line (might not be line 116).</p>
					</li>
				</ul>
			</p>
	</body>
</html>





