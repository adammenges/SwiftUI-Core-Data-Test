# SwiftUI-Core-Data-Test

## CloudKit notes/changes

In order to use this with CloudKit yourself you will need to change the name of the data model from `com.jknlsn.CoreDataCloudKitDemo` to reference your own CloudKit container. CloudKit containers are currently not deletable, so I would recommend using one for different CloudKit testing you are doing, and just delete the contents when using for a new test. You will also need to change the CloudKit initialisation to reference this container instead of `com.jknlsn.CoreDataCloudKitDemo.`

See this commit to see the complete changes made to use CloudKit instead of CoreData: 
https://github.com/jknlsn/SwiftUI-Core-Data-Test/commit/84e82111e2f08f2f288a8868e7379764ed64a3e8

## Original README

Extended sample program to demonstrate how CoreData can be used with SwiftUI.
This sample has been sort of a play ground to try to duplicate or reinvent some familiar 
UIKit patterns using SwiftUI that are common with some Core Data based Apps.

This project currently compiles and runs on Xcode 11.0 Beta 7 
Current development testing has mostly been on iPhone devices.
It does run on iPad and macOS with a few size class issues.

The key component of this sample is the class CoreDataDataSource which encapsulates
much of the functionality of an NSFetchedResultsController for use with SwiftUI.
This version of CoreDataDataSource has several custom initializers for extended capabilities.

=======================

The App uses a Tab View that displays and edits the same CoreData database several ways.

Tab 1: Typical "drill-down" view with Lists and Detail view editing

Tab 2: Two side-by-side instances of the same view as in Tab 1. This is helpful to see that
the Core-data changes are observed by all views properly.

Tab 3: Has a Data Source set up to support a nested SwiftUI Grouped List 
with correct implementations of move and delete within a group.

Tab 4: Demonstrates Selecting rows within a List
It uses a generic ListSelectionManager to allow specific actions (e.g. updating database) 
at the time on the selection or deselection, in addition to inserting and deleting from the selection Set.
It also demonstrates how to create a custom ToggleStyle to use instead of the Default Switch ToggleStyle.
Selecting Items is only allowed in Edit mode, which also exposes several commands when active.

Tab 5: Demonstrates how to use a SearchBar with the CoreDataDataSource
Added a new method to load the data source using an NSPredicate to supply data to a ForEach List.
Created a UIViewRepresentable SearchBar that accepts the search text and returns a new
NSPredicate back to the SwiftUI view after each keystroke.

=======================

CREDITS:
1.  Thanks to @kontiki for insight on how to correctly use the editMode environment var.
https://stackoverflow.com/questions/57496453/swiftui-how-do-i-make-edit-rows-in-a-list

=======================

KNOWN ISSUES:

1.  Start the App and then Select the Side by Side tab, tap Edit in either of the two views. 
Selecting any other tab view causes a crash somewhere in the SwiftUI framework. 
(No longer an issue in Beta 7). 

This project is still a work in progress.  Several more changes will be made in the near future.

