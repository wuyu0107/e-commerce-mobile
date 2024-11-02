# e_commerce

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

### Assignment 7
<details>
  <summary>Explain what are stateless widgets and stateful widgets, and explain the difference between them</summary>
  
  ---> Stateless widgets are widgets that never changes. Examples of stateless widgets include Icon, IconButton, and Text. They are static and do not hold a mutable state (meaning they have no class properties that change over time). In the other hand, stateful widget can change when a user interacts with it. They are said to be dynamic, meaning they can change its appearance when an event is triggered by a user interaction or when it receives a data. Examples include InkWell, Form, and TextField.
</details>

<details>
  <summary>Mention the widgets that you have used for this project and its uses</summary>
---> We use Scaffold, which provides the basic strcuture of the page with the AppBar and body. It acts as a container for other widgets to create a consistent layout through out the app. Another widget we use is Appbar, which displays the header at the top of the screen and contains the title, styled with custom color and font. Some stateless widgets we use in this project are Text-used for displaying text on screen and Icon-displays a specific icon; can be customized for colors and size. One stateful widget we use in the project is InkWell, which provides a ripple effect when an button/icon is tapped. It triggers the SnackBar when tapped. SnackBar is also a widget that displays a temporary message at the bottom of the application. It is triggered when a button is pressed. ThemeData is a widget to define the theme of the app, controlling the colors and other visualizations of the application. 
</details>

<details>
  <summary>What is the use-case for setState()? Explain the variable that can be affected by setState()</summary>
  
---> ```setState()``` is used to update the UI to reflect changes in variables or modify the state variables based on user interaction. It is used to update the user interface in response to changes in state variables. Variables that can be affected by ```setState()``` are only the ones that are within the  ```state``` class of ```Stateful``` widgets. 
  
</details>

<details>
  <summary>Explain the difference between const and final keyword</summary>
---> Const and final keywords behaves the same way, but const makes the variable constant from compile-time only while final keyword is used to hardcode the values of the variable and cannot be altered in future. Final is useed when a variable doesn't need to be reassigned but can be calculated at runtime. Const are used for variables which have known values. 
</details>

<details>
  <summary>Step-by-Step on Implementations</summary>
  
1.
</details>

