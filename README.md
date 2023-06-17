# Android Cheatsheet

This is a collection of visual guides that I find myself coming back to repeatedly while doing Android development. Open to contributions!

## Table of contents

[Activities and Fragments](#activities-and-fragments)

[User interface](#user-interface)

[Kotlin](#kotlin)

[Jetpack Compose](#jetpack-compose)

[Architecture](#architecture)

[Build process](#build-process)

[General software engineering](#general-software-engineering)

## Activities and Fragments

### Lifecycle flowchart

<img src="https://i2.wp.com/androhub.com/wp-content/uploads/2015/04/activity_lifecycle.png?resize=538%2C668">

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
### RecyclerView pieces
<img src="https://developer.android.com/codelabs/basic-android-kotlin-training-recyclerview-scrollable-list/img/4e9c18b463f00bf7.png" width="60%">

| Piece           | What it does                                                                                                                                                                                                                                                                               |
|-----------------|------------------------------------------------------------------------------------------------------------------------------|
| `RecyclerView`  | The `ViewGroup` that contains the views corresponding to your data.                                                                                                                                                                                                                        |
| item            | One data item of the list to display. Can be of any type; often a data class you define.                                                                                                                                                                                                   |
| `Adapter`       | Takes data and prepares it for `RecyclerView` to display.                                                                                                                                                                                                                                  |
| `ViewHolder`s   | A pool of views for `RecyclerView` to use and reuse to display items. Each individual `ViewHolder` is a wrapper around a `View`.                                                                                                                                                           |
| `View`          | A layout that can display one data item.                                                                                                                                                                                                                                                   |
| `LayoutManager` | Measures and positions individual item views within a `RecyclerView` and determines the policy for when to recycle item views that are no longer visible. The ones provided in the `RecyclerView` library are `LinearLayoutManager`, `GridLayoutManager`, and `StaggeredGridLayoutManager` |

[Source](https://developer.android.com/codelabs/basic-android-kotlin-training-recyclerview-scrollable-list)

### ImageView ScaleTypes
<img src="https://raw.githubusercontent.com/frostyshadows/android-cheatsheet/master/Screen%20Shot%202020-05-22%20at%208.13.07%20AM.png" width="60%">

[Source](https://thoughtbot.com/blog/android-imageview-scaletype-a-visual-guide)

### [PorterDuff modes](https://developer.android.com/reference/android/graphics/PorterDuff.Mode) for tinting

<img src="https://chiuki.github.io/images/android-shaders-filters/porter_duff.png">

[Source](https://chiuki.github.io/android-shaders-filters/#/)

## Kotlin

### Kotlin Standard Library functions
<img src="https://github.com/frostyshadows/android-cheatsheet/blob/master/Kotlin-library-functions.png" width="60%">

### Type system
<img src="https://raw.githubusercontent.com/frostyshadows/android-cheatsheet/master/kotlin-nothing-entire-hierarchy.png">

[Source](http://natpryce.com/articles/000818.html)

## Jetpack Compose

### Three phases of a frame

<img src="https://developer.android.com/static/images/jetpack/compose/phases-state-read-draw.svg" width="80%">

[Source](https://developer.android.com/jetpack/compose/phases)

### Choosing an API to implement an animation

<img src="https://developer.android.com/images/jetpack/compose/animation-flowchart.svg">

[Source](https://developer.android.com/jetpack/compose/animation)

### Arrangement

| Horizontal arrangements in Rows | Vertical arrangements in Columns |
|---------------------------------|----------------------------------|
| <img src="https://developer.android.com/images/reference/androidx/compose/foundation/layout/row_arrangement_visualization.gif"> | <img src="https://developer.android.com/images/reference/androidx/compose/foundation/layout/column_arrangement_visualization.gif"> |

[Source](https://developer.android.com/reference/kotlin/androidx/compose/foundation/layout/Arrangement)

## Architecture

### Uncle Bob's clean architecture

<img src="https://miro.medium.com/max/1200/0*JD606Sqx6RYZLKdu." width="60%">

[Source](https://android.jlelse.eu/thoughts-on-clean-architecture-b8449d9d02df)

## Build process
<img src="https://stuff.mit.edu/afs/sipb/project/android/docs/images/build.png">

[Source](https://stuff.mit.edu/afs/sipb/project/android/docs/tools/building/index.html)

## General software engineering

### Code review checklist
<img src="https://i0.wp.com/www.michaelagreiler.com/wp-content/uploads/2019/08/Code_Review_Checklist_Greiler.png?w=800&ssl=1">

[Source](https://www.michaelagreiler.com/code-review-checklist-2/)

<img src="https://github.com/frostyshadows/android-cheatsheet/blob/master/Android-code-review-checklist.png">

### Gang of Four design patterns
<img src="https://github.com/frostyshadows/android-cheatsheet/blob/master/GangOfFour-1.png" width="100%">
<img src="https://github.com/frostyshadows/android-cheatsheet/blob/master/GangOfFour-2.png" width="100%">

[Source](http://www.blackwasp.co.uk/GangOfFour.aspx)
