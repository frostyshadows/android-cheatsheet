# Android Cheatsheet

This is a collection of visual guides that I find myself coming back to repeatedly while doing Android development. Open to contributions!

## Table of contents

[Activities and Fragments](#activities-and-fragments)

[User interface](#user-interface)

[Kotlin](#kotlin)

[Architecture](#architecture)

[General software engineering](#general-software-engineering)

## Activities and Fragments

### Lifecycle flowchart

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/dabe9ea1-d26b-460a-92a1-39c4ed6eece4/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20200522%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200522T144016Z&X-Amz-Expires=86400&X-Amz-Signature=e3a76b7d9b80f87df5d2f62ed421fc8d558022c4d6117f2ebd325b4541fec16b&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22">

### Callback methods

|   Callback    |              When               |                         What                        |Is Activity visible|
| --------------|---------------------------------|-----------------------------------------------------|:-----------------:|
|onCreate()     | Activity is first created       | All the necessary UI elements should be initialized | no                |
| onStart()     | Activity becomes visible to user| Code that maintains the UI, start async tasks (get data from API or database), register listeners                                                                           | yes               |
| onResume()    | Activity becomes interactable to user| Starts animations                              | yes               |
| onPause()     | User is leaving the activity     | Stops animations                                   |partially visible  |
| onStop()      | Activity is no longer visible to user| Unregisters listeners and resources allocated in onStart()|no      |
| onRestart()   | Activity in the stopped state is about to start again (on back click) | Cursor objects should be re-queried                                                                                                         | no                |
| onDestroy()   | Activity is destroyed from memory|                                                    | no                |


### Launch modes
| Mode           | Default       | Instantiation      | New Task on Launch | Allow other activities within Task |
| ---------------| --------------|--------------------| -------------------| -----------------------------------|
| standard       | Yes           | Everytime an intent is created, a new instance is created. Also instances can be member of multiple tasks and more than one instance in a Task. | No. Open in the same Task that originated the intent | Yes    |
| singleTop      | No            | Exactly like standard but if the activity is at the top of the Task stack then it uses the existing instance.       | No. Open in the same Task that originated the intent      |    Yes      |
| singleTask     | No   | Single instance   |   Yes. Always a Root Task.      |       Yes          |
| singleInstance | No    | Single instance     |    Yes. Always a Root Task.   |    Never. Always the only activity in the task  |

[Source](https://guides.codepath.com/android/Navigation-and-Task-Stacks)

## User interface

### ImageView ScaleTypes
<img src="https://raw.githubusercontent.com/frostyshadows/android-cheatsheet/master/Screen%20Shot%202020-05-22%20at%208.13.07%20AM.png" width="60%">

[Source](https://thoughtbot.com/blog/android-imageview-scaletype-a-visual-guide)

### [PorterDuff modes](https://developer.android.com/reference/android/graphics/PorterDuff.Mode) for tinting

<img src="https://chiuki.github.io/images/android-shaders-filters/porter_duff.png">

[Source](https://chiuki.github.io/android-shaders-filters/#/)

## Kotlin

### Kotlin Standard Library functions
<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ecdd49b3-7045-42af-b9ed-afca0c8c8bf9/Screen_Shot_2020-05-23_at_10.14.54_AM.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20200523%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20200523T171706Z&X-Amz-Expires=86400&X-Amz-Signature=749233425b27cc54907d8a98005cb105b7208281bef3807c12663cc04605024c&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Screen_Shot_2020-05-23_at_10.14.54_AM.png%22" width="60%">

## Type system
<img src="https://www.kotlindevelopment.com/content/images/2018/09/typical_nothing.png">

[Source](https://www.kotlindevelopment.com/typical-kotlin/)

## Architecture

### Uncle Bob's clean architecture

<img src="https://miro.medium.com/max/1200/0*JD606Sqx6RYZLKdu." width="60%">

[Source](https://android.jlelse.eu/thoughts-on-clean-architecture-b8449d9d02df)


## General software engineering

### Code review checklist
<img src="https://i0.wp.com/www.michaelagreiler.com/wp-content/uploads/2019/08/Code_Review_Checklist_Greiler.png?w=800&ssl=1">

[Source](https://www.michaelagreiler.com/code-review-checklist-2/)
