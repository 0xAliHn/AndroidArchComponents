## AndroidArchComponents
Android Architecture Components – Room, LiveData and ViewModel with MVVM

It helps us developers address two pain points:
  1. Manage our UI components lifecycle
  2. Persist data over configuration changes
  
  There are 3 main architecture components:
  1. Room
  2. LiveData
  3. ViewModel

### Room
Remember the amount of boilerplate code you had to write to create and manipulate even a very small database? You had to define the database structure, create an SQLiteHelper class etc.

Room is a library that saves you all such trouble. Now you can query your data without having to deal with cursors or loaders. You can define your database by adding annotations in your Model class. Yes, it’s that simple.

If you’ve used third-party ORMs like Sugar, you’ll feel right at home here. In fact, from now on, I wouldn’t even want to use one. Room is that brilliant! Why would you want to use a third-party library, when the official Android libraries give you an equal, or if not, better solution.

First, Add Google’s maven repository to your project-level build.gradle file.

``java
allprojects {
    repositories {
        jcenter()
        maven {
            url "https://maven.google.com"
        }
    }
}
``

Next, add the following dependencies for Room in your app-level build.gradle file.

``java
compile "android.arch.lifecycle:extensions:1.0.0-alpha1"
compile "android.arch.persistence.room:runtime:1.0.0-alpha1"
annotationProcessor "android.arch.lifecycle:compiler:1.0.0-alpha1"
annotationProcessor "android.arch.persistence.room:compiler:1.0.0-alpha1"
``

### ViewModel
Earlier in the post, we mentioned ViewModel. ViewModels are entities that are free of the Activity/Fragment lifecycle. For example, they can retain their state/data even during an orientation change.

ViewModels do not contain code related to the UI. This helps in the decoupling of our app components.

In Room, the database instance should ideally be contained in a ViewModel rather than on the Activity/Fragment.

### LiveData:
LiveData is a wrapper that lets interested classes observe changes in the data inside the wrapper.
