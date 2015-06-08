# Introduction to Xcode
------

## Objectives
1. Understand the concept of an Integrated Development Environment.
2. Get oriented with the basic layout of Xcode.
3. Become familiar enough with Xcode to accomplish the first lab, *Your-First-NSLog*.

## What is Xcode?

Xcode is the **Integrated Development Environment** (**IDE**) provided by Apple to third-party programmers such as yourself for developing iOS and OS X applications written in Objective-C and Swift. An IDE is a program (or program suite) that incorporates tools for the various aspects of creating software. Xcode, specifically, brings together the code editor, compiler, debugger, interface builder, application bundler, and simulator (which is technically a separate program launched from within Xcode).

**Note:** *The first time you open Xcode, your machine will ask you if you want enable "Developer Mode". Go ahead and do this; don't be scared of it! What it does is allow you to debug your projects without OS X asking for your administrator password every time. If you previously selected "No" the first time you opened Xcode, don't worry! Just open your terminal and type* `$ DevToolsSecurity -enable`.

Let's unpack some of the terminology in that last sentence:

1. **Code Editor** - a text editor with specialized in handling code as text. Sublime Text is a prime example of a standalone code editor.
2. **Compiler** - this is a program that translates your code from Objective-C or Swift into machine language, the native language of the processor. When you hit "Run", your code is first compiled so it can then be handed to your computer's processor to execute. Xcode also contains a **Pre-Compiler** which scans your code *as you type it* for syntacical errors and other problems to reduce the likelihood that your build contains code that will cause a crash.
3. **Debugger** - all code has errors. "Good Practice" guidelines and pre-compilers help reduce the likelihood of errors being written, but they happen. Good debugging tools allow the programmer to scan the code as processes are running, watching the application's elements act upon and change themselves to see where they collide.
4. **Interface Builder** - specifically in Xcode this is the name of the suite that allows the use of Storyboards to create the visual layout of an user interface (UI) in a similar fashion to design and layout software.
5. **Application Bundler** - this assembles the program as an application package to be shipped to the consumer for deployment. You won't be using this for any of the labs, but you should know that Xcode contains the functionality to submit your application to the App Store for review. You might eventually do this on your own with side projects.
6. **Simulator** - Xcode contains a program for partially replicating the conditions of running your application on a mobile device. It's very useful for development to see how your code might behave once it's deployed, but for a variety of reasons it can't ever be quite the real thing so it can't replace testing your build on an actual mobile device.



## Xcode Anatomy 101

**Note:** *If this is your first time using Xcode and would like a sample project to explore, go ahead and fork, clone, and open the lab in next the lesson titled* Your-First-NSLog.

In addition to the typically-placed application Toolbar, Xcode has four main workspace windows. These are, in clockwise rotation from the left:

1. The Navigator area,
2. The Editor area,
3. The Utilities area, and
4. The Debug area.

<img src="https://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_overview.png" width=100%>


## 0. Workspace Toolbar
<img src="https://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_workspace_toolbar.png" width=100%>

The Toolbar is a small collection of project-wide buttons and labels. They are:

1. Close/Minimize/Maximize Window buttons (these are the red, yellow, and green dots standard to all OS X windows),
2. The ▶︎ "**Run**" button (`⌘`+`R`) which builds and then runs the current scheme,
3. The ◼︎ "**Stop**" button (`⌘`+`.`) which stops the running scheme or application,
4. The "**Scheme Menu**",
	* The left half selects the current target,
	* The right half selects the destination—the device or simulator you wish to run on, (**Note:** *If you connect an iOS device to your computer, Xcode will typically assume you want to run the build on that device and automatically select it as your destination. If you encounter an authorization error, this may be the cause of it. Selecting the simulator instead will not trigger the authorization check.*

5. The "**Activity viewer**" displays information relevant to the current operation, as well as symbols for the number of warning and errors generated by the compiler,
6. The **Editor configuration buttons**,
	* "**Standard Editor**" - shows the primary code editor window
	* "**Assistant Editor**" - shows a secondary code editor window alongside the primary window (this gets crowded without a larger screen),
	* "**Version Editor**" - shows the Xcode's built-in version control UI, since we utilize git and GitHub for version control, you will not use for the labs,
	
7. The **Workspace configuration buttons** which show or hide their respective areas:
</ol>

|Icon|Workspace Configuration Button|
|:--------:|--------|
|<img src="https://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_workspace_nav_left.png" >| Show or hide the **Navigator area**.|
|<img src="https://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_workspace_nav_middle.png" >| Show or hide the **Debug area**.|
|<img src="https://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_workspace_nav_right.png" >| Show or hide the **Utilities area**.|

###Choosing a Destination

The **Scheme Menu** allows you to select your target and destination with drop-down menus:

<img src="https://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_run_destination.png" width=100%>


## 1. The Navigator Area

The appropriately-named **Navigator area** is actually a stack of eight different navigators which help you get around your project based on different elements. You'll likely spend the most time with the Project Navigator which is the default drop-down file list.

<img src="https://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_navigator.png" >

**Top Tip:** *An easy well to tell if you are in either an* `*.xcodeproj` *file or an* `*.xcworkspace` *file is by looking for multiple "blueprint" icons in the Project Navigator. If you see only one then you are currently inside a* `*.xcodeproj` *file and running a scheme that incorporates outside frameworks like CocoaPods such as Specta & Expecta will fail to build. If you are using CocoaPods and don't see a second "blueprint" icon labeled "Pods", then you need to close your project and open the* `*.xcworkspace` *file instead.*

The folder icons indicate a "group". They are named "groups" instead of "folders" because this is a file structure internal to Xcode and separate from the operating system's file structure which uses directories, a.k.a. folders. You can create a group by going to the Status bar and selecting File —> New —> Group OR Group From Selection. Adding a file to a group does NOT move it around in your directory. You will not be making your own groups until later labs, but get used to calling them groups.

|Icon|Navigator Pane|Description|
|-----------|:--------------------:|:----------|
|<img src="http://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_project_navigator_table.png" >| Project |Add, delete, group, and otherwise manage files in your project, or choose a file to view or edit its contents in the editor area.|
|<img src="http://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_symbol_navigator_table.png" >| Symbol |Browse the symbols in your project as a list or hierarchy. Buttons on the left of the filter bar let you limit the shown symbols to a combination of only classes and protocols, only symbols in your project, or only containers.|
|<img src="http://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_find_navigator_table.png" >| Find |Use search options and filters to quickly find any string within your project.|
|<img src="http://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_issue_navigator_table.png" >| Issue |View issues such as diagnostics, warnings, and errors found when opening, analyzing, and building your project.|
|<img src="http://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_test_navigator_table.png" >| Test |Create, manage, run, and review unit tests.|
|<img src="http://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_debug_navigator_table.png" >| Debug |Examine the running threads and associated stack information at a specified point or time during program execution.|
|<img src="http://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_breakpoint_navigator_table.png" >| Breakpoint |Fine-tune breakpoints by specifying characteristics such as triggering conditions.|
|<img src="http://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_report_navigator_table.png" >| Report | View the history of your build, run, debug, continuous integration, and source control tasks.|

### The Test Navigator

After running a build utilizing your unit tests (`⌘U`), the Test navigator will populate itself with your test results. A green light means the test passed, a red light means it failed! Selecting a test by name in this navigator will load that test's file in the Code Editor at the relevant line for the selected test.

<img src="https://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_test_overview.png" width="100%">

**Note:** *The testing frameworks within Xcode periodically become unstable. If your tests fail when you're reasonably confident that they should be passing, before tearing your code apart try the first step of closing Xcode completely and restarting the application.*

## 2. The Code Editor

This is the window which contains Xcode's text editor for writing code. The font coloring is based upon the syntax of the currently relevant programming language. You can customize these colors and the font type & size of your text in Xcode's preferences under the "**Fonts & Colors**" tab. 

**Top Tip:** *You can also create a presentation preset for easily switching to larger display fonts without affecting your personal font customizations.*

### The Gutter

The left-most column in the Code Editor which contains the line numbers is known as the **Gutter**. Blue arrow-tabs present in the gutter are "**breakpoint indicators**". Breakpoints are a signal to the application to pause the processes for inspection. This allows you to freeze a moment in time of your application so you can look at exactly what's happening. This helps immensely with the debugging process.

<img src="https://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_debug_breakpoint_gutter.png" width=100%>
**Above:** *Xcode when encountering a breakpoint.*
 
The vertical line between the line numbers and your code allows you to fold or unfold your code. **Code folding** is an action that collapses a block or segment of code in the editor to make it easier to read. This feature won't be relevant to you until you get to the more advanced labs, but you should be aware of it in case you invoke it accidentally. Double-clicking on this folding bar will cause the selected block of code to collapse into a pair of curly braces containing an ellipsis `{ ... }`. Don't panic when you do this accidentally! Just click on the ellipsis and your code will expand back out.

## 3. The Utilities Area

The Utilies Area really shines in Interface Builder which we're not introducing to you just yet. In the Code Editor, however, it displays only either the File Inspector or the Quick Help guide.

* The **File Inspector** displays a set of information relevant to the current file such as directory path and target.
* The **Quick Help** guide is immensely helpful. It provides a summary description of the cursor-selected class and several relevant hot links, specifically the link to Apple's Reference Guide on that class. This is often quicker than a google search and works offline, being stored locally as part of Xcode. You can access this database directly in Xcode's status bar by selecting Help —> Documentation and API Reference.

## 4. The Debug Area

The debugger is usually tucked away while writing code, yet comes out to play almost every time the build is run. An automatic breakpoint will get triggered if your build succeeds but your program crashes. The information printed out can be a valuable source of insight toward finding the problem. In time, you'll learn how to interpret much of the information that gets dumped out by a crash!

<img src="https://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_debug_overview.png" width=100%>


Don't fret, though. Understanding the debugger is a skill in itself. It's OK to feel intimidated by all the computery information it throws out! Right now we're just going to explain the different interface elements. Let's a closer look.

<img src="https://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_debug_area_detail.png" width=100%>

The left window is the **Variable Viewer** which shows a drop-down list of all of your program's objects and instance variables held in memory at the current scope. We'll teach you how to review the information in this window.

The right window is the **Console Output Viewer**. This is where your `NSLog`s will print out, and where your crash details will print out when an exception breakpoint is thrown. You can also enter the `po <#objectName#>` command into this window to get a ***p***rint***o***ut of that object's description property, or you can also print out the result of a method with `po [<#objectName#> <#methodCall#>]`.

**// Flat-fact:** *If you've noticed the* `(lldb)` *ticker that trails the printouts in the Console Output Viewer, good eyes! [LLDB](http://lldb.llvm.org/) is the name of debugging program that's integrated into Xcode. It's part of the LLVM package and inherits from GDB which was developed by Richard Stallman in 1986.*

|Icon|Program Execution Control Symbol|Description|
|:---------:|-------------|:--------------|
|.|Hide/show Debug area| Allows you to hide the Debug area without reaching all the way across the screen to the Toolbar. |
|.|Turn Breakpoints On/Off| If this icon is highlighted blue, your manual breakpoints will pause the build at run time. If the icon is empty, your manual breakpoints are turned off. This is a useful toggle if you have numerous breakpoints set so you can avoid de-activating them individually.|
|<img src="https://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_debug_play.png" >| Play| Play button continues execution of the app.|
|<img src="https://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_debug_pause.png" >| Pause| Pause button suspends execution of the app.|
|<img src="https://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_debug_step_over.png" >| Step Over| Step over will execute the current line of code, including any methods.|
|<img src="https://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_debug_step_into.png" >| Step Into| If the current line of code calls a method, step into starts execution at the current line, and then stops when it reaches the first line of the a called method.|
|<img src="https://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_debug_step_out.png" >| Step Out| Step out executes the rest of the current method or function.|
|.|Debug View Hierarchy| This loads a special viewer for observing the stack of view layers in a user interface. |
|.|Simulate a location| The tells the iOS simulator to feed to the application a set of pre-recorded GPS information for testing location services.|

We'll teach your more about how to use the debugger effectively in the coming weeks. For now, just understand the layout of the tools well enough to locate the Console Output viewer. If you can only see the Variable (or vice-versa), the Console Output Viewer is likely hidden. There's a pair of show/hide buttons in the bottom right corner of the Debug area which governs these two viewers.

|Icon|Debugger Configuration Button|
|:--------:|--------|
|<img src="https://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_workspace_nav_left.png" >| Show or hide the **Variable Viewer**.|
|<img src="https://ironboard-curriculum-content.s3.amazonaws.com/iOS/intro-to-xcode/xcode_workspace_nav_right.png" >| Show or hide the **Console Output Viewer**.|

## Practicum: *Your-First-NSLog*

The next lesson titled *Your-First-NSLog* contains your first hands-on Xcode project. Even though the task it expects is rather simple, acquainting yourself with Xcode is a task in itself. While it isn't perfect, Xcode is one of the most fully functional IDEs in the developer ecosystem, combining a vast variety of tools with their owns depths of function. The layout of options, constantly changing with every update, can easily feel overwhelming to a new programmer. Get yourself acquainted with the current version of Xcode so you can more efficiently navigate your own tools!