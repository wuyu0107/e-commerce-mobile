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
<br/>

Preparation:
---
- Create a new Flutter project with the name e_commerce, then enter the project directory
  ```
  flutter create e_commerce
  cd e_commerce
  ```
- To run the project:
  ```
  flutter run
  ```
---
1. Create a new file name ```menu.dart``` in the ```e_commerce/lib``` directory. On the first line of the file, add the follwing code:
```
import 'package:flutter/material.dart';
```

2. From the ```main.dart``` file, cut the lines from line 39 to the end that contains the two classes below, and paste it to the file ```menu.dart``` created just prior to. 
```
class MyHomePage ... {
    ...
}

class _MyHomePageState ... {
    ...
}
```

3. Add the following code at the beginning of the file in ```main.dart```
```
import 'package:e_commerce/menu.dart';
```

#### Create a Card with NPM, Name, and Class
4. To create a card with NPM, Name, and Class in Flutter, it is essential to declare three variables of type strings containing the NPM, name and class in the ```class MyHomePage``` in the ```menu.dart``` file as shown below:
```
class MyHomePage extends StatelessWidget {
    final String npm = '2306199743'; // NPM
    final String name = 'Min Kim'; // Name
    final String className = 'KKI'; // Class
    ...
}
```

5. After declaring the three variables, create a new class name ```InfoCard``` in the ```menu.dart``` file to create a simple card that displays the NPM, name, and class information.
```
...
class InfoCard extends StatelessWidget {
  // Card information that displays the title and content.

  final String title;  // Card title.
  final String content;  // Card content.

  const InfoCard({super.key, required this.title, required this.content});

  @override
  Widget build(BuildContext context) {
    return Card(
      // Create a card box with a shadow.
      elevation: 2.0,
      child: Container(
        // Set the size and spacing within the card.
        width: MediaQuery.of(context).size.width / 3.5, // Adjust with the width of the device used.
        padding: const EdgeInsets.all(16.0),
        // Place the title and content vertically.
        child: Column(
          children: [
            Text(
              title,
              style: const TextStyle(fontWeight: FontWeight.bold),
            ),
            const SizedBox(height: 8.0),
            Text(content),
          ],
        ),
      ),
    );
  }
}
```

#### Create a Button Card with Icon
6. Create a new class named ```ItemHomepage``` that contains the attributes of the card. On the ```menu.dart``` file, put the code snippet given below outside of the ```MyHomePage``` and ```InfoCard``` class. Then create a list of ```ItemHomepage``` that contains the buttons you want to add to the ```MyHomePage``` class.
```
...
 class ItemHomepage {
     final String name;
     final IconData icon;

     ItemHomepage(this.name, this.icon);
 }
 ...
```
```
class MyHomePage extends StatelessWidget {  
     ...
     final List<ItemHomepage> items = [
         ItemHomepage("View Product List", Icons.mood),
         ItemHomepage("Add Product", Icons.add),
         ItemHomepage("Logout", Icons.logout),
     ];
     ...
 }
```

7. After adding the buttons, create a ```ItemCard``` class to display the button on the home page of the application. When The button is pressed, it will display a snackbar message "You have pressed the [button name] button.".
```
...
class ItemCard extends StatelessWidget {
  // Display the card with an icon and name.

  final ItemHomepage item; 
  
  const ItemCard(this.item, {super.key}); 

  @override
  Widget build(BuildContext context) {
    return Material(
      // Specify the background color of the application theme.
      color: Theme.of(context).colorScheme.secondary,
      // Round the card border.
      borderRadius: BorderRadius.circular(12),
      
      child: InkWell(
        // Action when the card is pressed.
        onTap: () {
          // Display the SnackBar message when the card is pressed.
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(
              SnackBar(content: Text("You have pressed the ${item.name} button!"))
            );
        },
        // Container to store the Icon and Text
        child: Container(
          padding: const EdgeInsets.all(8),
          child: Center(
            child: Column(
              // Place the Icon and Text in the center of the card.
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Icon(
                  item.icon,
                  color: Colors.white,
                  size: 30.0,
                ),
                const Padding(padding: EdgeInsets.all(3)),
                Text(
                  item.name,
                  textAlign: TextAlign.center,
                  style: const TextStyle(color: Colors.white),
                ),
              ],
            ),
          ),
        ),
      ),
    );
  }
}
...
```

8. Next, to integrate and display all the cards on the ```HomePage```, change the ```Widget build()``` section in ```MyHomePage``` class.
```
...
class MyHomePage extends StatelessWidget {
  ...  
  @override
  Widget build(BuildContext context) {
    // Scaffold provides the basic structure of the page with the AppBar and body.
    return Scaffold(
      // AppBar is the top part of the page that displays the title.
      appBar: AppBar(
        // The title of the application with white text and bold font.
        title: const Text(
          'Study Together With Notes',
          style: TextStyle(
            color: Colors.white,
            fontWeight: FontWeight.bold,
          ),
        ),
        // The background color of the AppBar is obtained from the application theme color scheme.
        backgroundColor: Theme.of(context).colorScheme.primary,
      ),
      // Body of the page with paddings around it.
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        // Place the widget vertically in a column.
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.center,
          children: [
            // Row to display 3 InfoCard horizontally.
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceEvenly,
              children: [
                InfoCard(title: 'NPM', content: npm),
                InfoCard(title: 'Name', content: name),
                InfoCard(title: 'Class', content: className),
              ],
            ),

            // Give a vertical space of 16 units.
            const SizedBox(height: 16.0),

            // Place the following widget in the center of the page.
            Center(
              child: Column(
                // Place the text and grid item vertically.

                children: [
                  // Display the welcome message with bold font and size 18.
                  const Padding(
                    padding: EdgeInsets.only(top: 16.0),
                    child: Text(
                      'Welcome to Study Together with Notes',
                      style: TextStyle(
                        fontWeight: FontWeight.bold,
                        fontSize: 18.0,
                      ),
                    ),
                  ),

                  // Grid to display ItemCard in a 3 column grid.
                  GridView.count(
                    primary: true,
                    padding: const EdgeInsets.all(20),
                    crossAxisSpacing: 10,
                    mainAxisSpacing: 10,
                    crossAxisCount: 3,
                    // To ensure that the grid fits its height.
                    shrinkWrap: true,

                    // Display ItemCard for each item in the items list.
                    children: items.map((ItemHomepage item) {
                      return ItemCard(item);
                    }).toList(),
                  ),
                ],
              ),
            ),
          ],
        ),
      ),
    );
  }
}
...
```

9. To implement different colors for each buttons (```View Product List```, ```Add Product```, ```Logout```), add a ```color``` property to ```ItemHomepage``` class to represent each item's unique color. Then, in ```ItemCard``` widget, add a line of code to assign ```item.color``` for the background color. Next, in ```MyHomePage``` items list, add unique colors to each item so that each buttons have different colors.
```
class ItemHomepage {
...
final Color color; 
...

```
```
class ItemCard extends StatelessWidget {
...
  @override
    Widget build(BuildContext context) {
      return Material(
        color: item.color,
...
```
```
class MyHomePage extends StatelessWidget {
...
  final List<ItemHomepage> items = [
      ItemHomepage("View Product List", Icons.mood, Colors.teal),
      ItemHomepage("Add Product", Icons.add, Colors.green),
      ItemHomepage("Logout", Icons.logout, Colors.deepOrange),
    ];
...
```
</details>

### Assignment 8

<details>
  <summary>What is the purpose of const in Flutter? Explain the advantages of using const in Flutter code. When should we use const, and when should it not be used?</summary>

  ##### The use of ```const``` keyword is to serve as an indicator that tells the compiler that "for this variable, it will never change, so create one copy of it and wherever it's mentioned, reference back to the copy." Using ```const``` in Flutter can enhance the application's performance and efficiency - it results in faster, smoother, and more memory-efficient apps since it allows Flutter to reuse the existing object instead of creating a new one. Employing ```const``` shines in immutable data objects, pre-defined values, and optimizing widget trees. It is best to avoid const, if an object's data needs to be modified after creation or object's fetched data is from an external source.
</details>

<details>
  <summary>Explain and compare the usage of Column and Row in Flutter. Provide example implementations of each layout widget!</summary>

  ##### Column widget is used to arrange widgets vertically and Row widget is used to arrange widgets horizontally. Column widget arranges its children vertically, so is often used to stack widgets from top to bottom, such as text labels, buttons, or images in a single column. Row widget arranges its children horizontally and is used to display widgets side by side, such as text or buttons in a single row.
```
// Example of Column Implementation
... 
  child: Column(
    // Place the Icon and Text in the center of the card.
    mainAxisAlignment: MainAxisAlignment.center,
      children: [
        Icon(
        item.icon,
        color: Colors.white,
        size: 30.0,
        ),
        const Padding(padding: EdgeInsets.all(3)),
        Text(
          item.name,
          textAlign: TextAlign.center,
          style: const TextStyle(color: Colors.white),
        ),
      ],
    ),
...
```
```
// Example of Row Implementation
...
  children: [
    // Row to display 3 InfoCard horizontally.
    Row(
      mainAxisAlignment: MainAxisAlignment.spaceEvenly,
      children: [
        InfoCard(title: 'NPM', content: npm),
        InfoCard(title: 'Name', content: name),
        InfoCard(title: 'Class', content: className),
      ],
    ),
... 
```
</details>

<details>
  <summary>List the input elements you used on the form page in this assignment. Are there other Flutter input elements you didn’t use in this assignment? Explain!</summary>

  ##### Input elements that are used are ```TextFormField``` for text inputs in fields such as name, subject, description, and price, and ```ElevatedButton``` used as a submit button to save the form data. Some other Flutter input elements that aren't used in the form are: checkbox (used for binary choices), Switch (used for toggles) and Radio (allows users to select one optino from multiple choices).
</details>

<details>
  <summary>How do you set the theme within a Flutter application to ensure consistency? Did you implement a theme in your application?</summary>

  ##### It is possible to set the theme by defining the theme in ```MaterialApp``` by adding the ```theme``` property to ```MaterialApp```, or use theme in widgets to ensure consistency by referencing ```Theme.of(context)```. In my application, it uses both.
```
theme: ThemeData(
  colorScheme: ColorScheme.fromSwatch(
    primarySwatch: Colors.teal,
  ).copyWith(secondary: Colors.teal[200]),
),
```
```
decoration: BoxDecoration(
  color: Theme.of(context).colorScheme.primary,
),
```
</details>

<details>
  <summary>How do you manage navigation in a multi-page Flutter application?</summary>

  ##### Navigation is managed using Flutter's ```Navigation```, which allows you to push and pop routes (screens) onto and off of the navigation stack. Routes are often defined by ```MaterialPageRoute``` or by name routes. 
```
ListTile(
  leading: const Icon(Icons.home_outlined),
  title: const Text('Home Page'),
  // Redirection part to MyHomePage
  onTap: () {
    Navigator.pushReplacement(
      context,
      MaterialPageRoute(
        builder: (context) => MyHomePage(),
      ));
    },
),
```

</details>



