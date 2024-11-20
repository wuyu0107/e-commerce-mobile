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

### Assignment 9

<details>
  <summary>Explain why we need to create a model to retrieve or send JSON data. Will an error occur if we don't create a model first?</summary>

  ##### Creating a model to retrieve or send JSON data provides structure and consistency when handling complex data. An error may not occur if you handle the JSON directly using Map<String, dynamic> types, but it makes the code error-prone and harder to maintain.
</details>

<details>
  <summary>Explain the function of the http library that you implemented for this task.</summary>

  ##### The http library facilitates network requests to interact with APIs. It provides tools to send request, handles responses, and handle errors. It is crucial for sending GET requests to the Django backend to fetch product data as JSON.
</details>

<details>
  <summary>Explain the function of CookieRequest and why it’s necessary to share the CookieRequest instance with all components in the Flutter app.</summary>

  ##### The CookieRequest class manages sessions and cookies for authentication in Flutter apps. It allows session persistence, state management, and cross-component usage. 
</details>

<details>
  <summary>Explain the mechanism of data transmission, from input to display in Flutter.</summary>

  ##### The user inputs data via TextFormField, and Flutter validates the input using Form and GlobalKey<FormState>. The data is then packages into a request, and set to the backend using http or CookieRequest. The Django receieves the request, processes the data, and sends a JSON response. The response is received in Flutter, deserialized into models, and passed to widgets for rendering.Flutter’s UI is updated using widgets like FutureBuilder or ListView.builder to present the processed data to the user.
</details>

<details>
  <summary>Explain the authentication mechanism from login, register, to logout. Start from inputting account data in Flutter to Django’s completion of the authentication process and display of the menu in Flutter.</summary>

  ##### For login:
  User enters credentials (username and password). Data is sent to Django's /login/ endpoint via POST.Django checks the credentials against the database. If the credentials are valid, a session cookie is created and returned. CookieRequest stores the session cookie, and enabling subsequent authenticated requests. Then if the login is successful, the app navigates to the homepage. 

  ##### For registration
  User fills in registration details, then the data is sent to Django's /register/ endpoint. Django validates that data and creates a new user.

  ##### For logout
  User clicks on the logout button, which sends a POST request to Django's /logout/ endpoint. Django clears the session and invalidates the session cookie. The CookieRequest removes the session cookie, and the app navigates back to the login screen
</details>

<details>
  <summary>Step By Step Implementation</summary>

  #### Integrate Authentication System in Flutter
1. Change the root widget to provide the CookieRequest library like this:
```
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return Provider(
      create: (_) {
        CookieRequest request = CookieRequest();
        return request;
      },
      child: MaterialApp(
        title: 'Study Together with Notes',
        theme: ThemeData(
          colorScheme: ColorScheme.fromSwatch(
            primarySwatch: Colors.teal,
          ).copyWith(secondary: Colors.teal[200]),
        ),
        home: LoginPage(),
      ),
    );
  }
}
```
2. Create a new view method for login in authentication/views.py
```
@csrf_exempt
def login(request):
    username = request.POST['username']
    password = request.POST['password']
    user = authenticate(username=username, password=password)
    if user is not None:
        if user.is_active:
            auth_login(request, user)
            # Successful login status.
            return JsonResponse({
                "username": user.username,
                "status": True,
                "message": "Login successful!"
                # Add other data if you want to send data to Flutter.
            }, status=200)
        else:
            return JsonResponse({
                "status": False,
                "message": "Login failed, account disabled."
            }, status=401)

    else:
        return JsonResponse({
            "status": False,
            "message": "Login failed, check email or password again."
        }, status=401)
```

3. Then create a new file in ```screens``` folder named ```login.dart```. And fill the file with the following code
```
import 'package:e_commerce/screens/menu.dart';
import 'package:flutter/material.dart';
import 'package:pbp_django_auth/pbp_django_auth.dart';
import 'package:provider/provider.dart';
import 'package:e_commerce/screens/register.dart';

void main() {
  runApp(const LoginApp());
}

class LoginApp extends StatelessWidget {
  const LoginApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Login',
      theme: ThemeData(
        useMaterial3: true,
        colorScheme: ColorScheme.fromSwatch(
          primarySwatch: Colors.teal,
        ).copyWith(secondary: Colors.teal[200]),
      ),
      home: const LoginPage(),
    );
  }
}

class LoginPage extends StatefulWidget {
  const LoginPage({super.key});

  @override
  State<LoginPage> createState() => _LoginPageState();
}

class _LoginPageState extends State<LoginPage> {
  final TextEditingController _usernameController = TextEditingController();
  final TextEditingController _passwordController = TextEditingController();

  @override
  Widget build(BuildContext context) {
    final request = context.watch<CookieRequest>();

    return Scaffold(
      appBar: AppBar(
        title: const Text('Login'),
      ),
      body: Center(
        child: SingleChildScrollView(
          padding: const EdgeInsets.all(16.0),
          child: Card(
            elevation: 8,
            shape: RoundedRectangleBorder(
              borderRadius: BorderRadius.circular(12.0),
            ),
            child: Padding(
              padding: const EdgeInsets.all(20.0),
              child: Column(
                mainAxisSize: MainAxisSize.min,
                children: [
                  const Text(
                    'Login',
                    style: TextStyle(
                      fontSize: 24.0,
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                  const SizedBox(height: 30.0),
                  TextField(
                    controller: _usernameController,
                    decoration: const InputDecoration(
                      labelText: 'Username',
                      hintText: 'Enter your username',
                      border: OutlineInputBorder(
                        borderRadius: BorderRadius.all(Radius.circular(12.0)),
                      ),
                      contentPadding:
                          EdgeInsets.symmetric(horizontal: 12.0, vertical: 8.0),
                    ),
                  ),
                  const SizedBox(height: 12.0),
                  TextField(
                    controller: _passwordController,
                    decoration: const InputDecoration(
                      labelText: 'Password',
                      hintText: 'Enter your password',
                      border: OutlineInputBorder(
                        borderRadius: BorderRadius.all(Radius.circular(12.0)),
                      ),
                      contentPadding:
                          EdgeInsets.symmetric(horizontal: 12.0, vertical: 8.0),
                    ),
                    obscureText: true,
                  ),
                  const SizedBox(height: 24.0),
                  ElevatedButton(
                    onPressed: () async {
                      String username = _usernameController.text;
                      String password = _passwordController.text;

		  // Check credentials
		  // TODO: Change the URL and don't forget to add a trailing slash (/) at the end of the URL!
		  // To connect the Android emulator to Django on localhost,
		  // use the URL http://10.0.2.2/
                      final response = await request
                          .login("http://localhost:8000/auth/login/", {
                        'username': username,
                        'password': password,
                      });

                      if (request.loggedIn) {
                        String message = response['message'];
                        String uname = response['username'];
                        if (context.mounted) {
                          Navigator.pushReplacement(
                            context,
                            MaterialPageRoute(
                                builder: (context) => MyHomePage()),
                          );
                          ScaffoldMessenger.of(context)
                            ..hideCurrentSnackBar()
                            ..showSnackBar(
                              SnackBar(
                                  content:
                                      Text("$message Welcome, $uname.")),
                            );
                        }
                      } else {
                        if (context.mounted) {
                          showDialog(
                            context: context,
                            builder: (context) => AlertDialog(
                              title: const Text('Login Failed'),
                              content: Text(response['message']),
                              actions: [
                                TextButton(
                                  child: const Text('OK'),
                                  onPressed: () {
                                    Navigator.pop(context);
                                  },
                                ),
                              ],
                            ),
                          );
                        }
                      }
                    },
                    style: ElevatedButton.styleFrom(
                      foregroundColor: Colors.white,
                      minimumSize: Size(double.infinity, 50),
                      backgroundColor: Theme.of(context).colorScheme.primary,
                      padding: const EdgeInsets.symmetric(vertical: 16.0),
                    ),
                    child: const Text('Login'),
                  ),
                  const SizedBox(height: 36.0),
                  GestureDetector(
                    onTap: () {
                      Navigator.push(
                        context,
                        MaterialPageRoute(
                            builder: (context) => const RegisterPage()),
                      );
                    },
                    child: Text(
                      'Don\'t have an account? Register',
                      style: TextStyle(
                        color: Theme.of(context).colorScheme.primary,
                        fontSize: 16.0,
                      ),
                    ),
                  ),
                ],
              ),
            ),
          ),
        ),
      ),
    );
  }
}
```

4. Then in the ```main.dart``` file, in the ```MaterialApp(...)``` widget, change the ```home: MyHomePage()``` to ```home: LoginPage()```.
```
 home: LoginPage(),
```

5. Create a new function in authentication application for registration.
```
@csrf_exempt
def register(request):
    if request.method == 'POST':
        data = json.loads(request.body)
        username = data['username']
        password1 = data['password1']
        password2 = data['password2']

        # Check if the passwords match
        if password1 != password2:
            return JsonResponse({
                "status": False,
                "message": "Passwords do not match."
            }, status=400)

        # Check if the username is already taken
        if User.objects.filter(username=username).exists():
            return JsonResponse({
                "status": False,
                "message": "Username already exists."
            }, status=400)

        # Create the new user
        user = User.objects.create_user(username=username, password=password1)
        user.save()

        return JsonResponse({
            "username": user.username,
            "status": 'success',
            "message": "User created successfully!"
        }, status=200)

    else:
        return JsonResponse({
            "status": False,
            "message": "Invalid request method."
        }, status=400)
```

6. Then create a new file register.dart in the Flutter project.
```
import 'dart:convert';
import 'package:flutter/material.dart';
import 'package:e_commerce/screens/login.dart';
import 'package:pbp_django_auth/pbp_django_auth.dart';
import 'package:provider/provider.dart';

class RegisterPage extends StatefulWidget {
  const RegisterPage({super.key});

  @override
  State<RegisterPage> createState() => _RegisterPageState();
}

class _RegisterPageState extends State<RegisterPage> {
  final _usernameController = TextEditingController();
  final _passwordController = TextEditingController();
  final _confirmPasswordController = TextEditingController();

  @override
  Widget build(BuildContext context) {
    final request = context.watch<CookieRequest>();
    return Scaffold(
      appBar: AppBar(
        title: const Text('Register'),
        leading: IconButton(
          icon: const Icon(Icons.arrow_back),
          onPressed: () {
            Navigator.pop(context);
          },
        ),
      ),
      body: Center(
        child: SingleChildScrollView(
          padding: const EdgeInsets.all(16.0),
          child: Card(
            elevation: 8,
            shape: RoundedRectangleBorder(
              borderRadius: BorderRadius.circular(12.0),
            ),
            child: Padding(
              padding: const EdgeInsets.all(20.0),
              child: Column(
                mainAxisSize: MainAxisSize.min,
                children: <Widget>[
                  const Text(
                    'Register',
                    style: TextStyle(
                      fontSize: 24.0,
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                  const SizedBox(height: 30.0),
                  TextFormField(
                    controller: _usernameController,
                    decoration: const InputDecoration(
                      labelText: 'Username',
                      hintText: 'Enter your username',
                      border: OutlineInputBorder(
                        borderRadius: BorderRadius.all(Radius.circular(12.0)),
                      ),
                      contentPadding:
                          EdgeInsets.symmetric(horizontal: 12.0, vertical: 8.0),
                    ),
                    validator: (value) {
                      if (value == null || value.isEmpty) {
                        return 'Please enter your username';
                      }
                      return null;
                    },
                  ),
                  const SizedBox(height: 12.0),
                  TextFormField(
                    controller: _passwordController,
                    decoration: const InputDecoration(
                      labelText: 'Password',
                      hintText: 'Enter your password',
                      border: OutlineInputBorder(
                        borderRadius: BorderRadius.all(Radius.circular(12.0)),
                      ),
                      contentPadding:
                          EdgeInsets.symmetric(horizontal: 12.0, vertical: 8.0),
                    ),
                    obscureText: true,
                    validator: (value) {
                      if (value == null || value.isEmpty) {
                        return 'Please enter your password';
                      }
                      return null;
                    },
                  ),
                  const SizedBox(height: 12.0),
                  TextFormField(
                    controller: _confirmPasswordController,
                    decoration: const InputDecoration(
                      labelText: 'Confirm Password',
                      hintText: 'Confirm your password',
                      border: OutlineInputBorder(
                        borderRadius: BorderRadius.all(Radius.circular(12.0)),
                      ),
                      contentPadding:
                          EdgeInsets.symmetric(horizontal: 12.0, vertical: 8.0),
                    ),
                    obscureText: true,
                    validator: (value) {
                      if (value == null || value.isEmpty) {
                        return 'Please confirm your password';
                      }
                      return null;
                    },
                  ),
                  const SizedBox(height: 24.0),
                  ElevatedButton(
                    onPressed: () async {
                      String username = _usernameController.text;
                      String password1 = _passwordController.text;
                      String password2 = _confirmPasswordController.text;

                      // Check credentials
                      // TODO: Change the url, don't forget to add a slash (/) inthe end of the URL!
                      // To connect Android emulator with Django on localhost,
                      // use the URL http://10.0.2.2/
                      final response = await request.postJson(
                          "http://localhost:8000/auth/register/",
                          jsonEncode({
                            "username": username,
                            "password1": password1,
                            "password2": password2,
                          }));
                      if (context.mounted) {
                        if (response['status'] == 'success') {
                          ScaffoldMessenger.of(context).showSnackBar(
                            const SnackBar(
                              content: Text('Successfully registered!'),
                            ),
                          );
                          Navigator.pushReplacement(
                            context,
                            MaterialPageRoute(
                                builder: (context) => const LoginPage()),
                          );
                        } else {
                          ScaffoldMessenger.of(context).showSnackBar(
                            const SnackBar(
                              content: Text('Failed to register!'),
                            ),
                          );
                        }
                      }
                    },
                    style: ElevatedButton.styleFrom(
                      foregroundColor: Colors.white,
                      minimumSize: Size(double.infinity, 50),
                      backgroundColor: Theme.of(context).colorScheme.primary,
                      padding: const EdgeInsets.symmetric(vertical: 16.0),
                    ),
                    child: const Text('Register'),
                  ),
                ],
              ),
            ),
          ),
        ),
      ),
    );
  }
}
```

#### Fetch Data from Django
7. Create a new file ```list_product.dart``` file. And fill the file with the code:
```
import 'package:e_commerce/models/product_entry.dart';
import 'package:flutter/material.dart';
import 'package:e_commerce/widgets/left_drawer.dart';
import 'package:pbp_django_auth/pbp_django_auth.dart';
import 'package:provider/provider.dart';

class ProductEntryPage extends StatefulWidget {
  const ProductEntryPage({super.key});

  @override
  State<ProductEntryPage> createState() => _ProductEntryPageState();
}

class _ProductEntryPageState extends State<ProductEntryPage> {
  Future<List<Product>> fetchProduct(CookieRequest request) async {
    // Fetch the response from the Django backend
    final response = await request.get('http://localhost:8000/json/');

    // Decoding the response into JSON
    var data = response;

    List<Product> listProduct = [];
    for (var d in data) {
      if (d != null) {
        listProduct.add(Product.fromJson(d));
      }
    }
    return listProduct;
  }
  
  @override
  Widget build(BuildContext context) {
    final request = context.watch<CookieRequest>();
    return Scaffold(
      appBar: AppBar(
        title: const Text('Product Entry List'),
      ),
      drawer: const LeftDrawer(),
      body: FutureBuilder(
        future: fetchProduct(request),
        builder: (context, AsyncSnapshot snapshot) {
          if (snapshot.data == null) {
            return const Center(child: CircularProgressIndicator());
          } else {
            if (!snapshot.hasData) {
              return const Column(
                children: [
                  Text(
                    'There is no product entry in Study with Together.',
                    style: TextStyle(fontSize: 20, color: Color(0xff59A5D8)),
                  ),
                  SizedBox(height: 8),
                ],
              );
            } else {
              return ListView.builder(
                itemCount: snapshot.data!.length,
                itemBuilder: (_, index) => Container(
                  margin:
                      const EdgeInsets.symmetric(horizontal: 16, vertical: 12),
                  padding: const EdgeInsets.all(20.0),
                  child: Column(
                    mainAxisAlignment: MainAxisAlignment.start,
                    crossAxisAlignment: CrossAxisAlignment.start,
                    children: [
                      Text(
                        "${snapshot.data![index].fields.name}",
                        style: const TextStyle(
                          fontSize: 18.0,
                          fontWeight: FontWeight.bold,
                        ),
                      ),
                      const SizedBox(height: 10),
                      Text("${snapshot.data![index].fields.subject}"),
                      const SizedBox(height: 10),
                      Text("${snapshot.data![index].fields.description}"),
                      const SizedBox(height: 10),
                      Text("${snapshot.data![index].fields.price}"),
                    ],
                  ),
                ),
              );
            }
          }
        },
      ),
    );
  }
}
```
8. Then add the page ```list_product.dart``` to ```left_drawer.dart``` in widgets folder.
```
ListTile(
            leading: const Icon(Icons.add_reaction_rounded),
            title: const Text('Product List'),
            onTap: () {
              // Route to the mood page
              Navigator.push(
                context,
                MaterialPageRoute(builder: (context) => const ProductEntryPage()),
              );
            },
          ),
```
9. Then change the function of view product list button in the main page to redirect to the product page.
```
else if (item.name == "View Product List") {
            Navigator.push(
              context,
              MaterialPageRoute(builder: (context) => const ProductEntryPage()),
            );
```
#### Integrate Flutter Form with the Django Service
10. Create a new function in ```main/views.py``` to create a product entry in flutter.
```
@csrf_exempt
def create_product_flutter(request):
    if request.method == 'POST':

        data = json.loads(request.body)
        new_mood = Product.objects.create(
            user=request.user,
            name=data["name"],
            subject=data["subject"],
            description=data["description"],
            price=int(data["price"]),
        )

        new_mood.save()

        return JsonResponse({"status": "success"}, status=200)
    else:
        return JsonResponse({"status": "error"}, status=401)
```

11. Then connect the page ```productentry_form.dart``` to ```CookieRequest``` by adding:
```
Widget build(BuildContext context) {
    final request = context.watch<CookieRequest>();

    return Scaffold(
```

12. Then also change the ```onPressed: ()```
```
onPressed: () async {
                      if (_formKey.currentState!.validate()) {
                        // Send request to Django and wait for the response
                        // TODO: Replace [YOUR_APP_URL] with the actual URL of your Django app
                        final response = await request.postJson(
                          "http://localhost:8000/create-flutter/",
                          jsonEncode(<String, String>{
                            'name': _name,
                            'subject': _subject,
                            'description': _description,
                            'price': _price
                                .toString(), // Ensure price is converted to string
                          }),
                        );

                        if (context.mounted) {
                          if (response['status'] == 'success') {
                            ScaffoldMessenger.of(context).showSnackBar(
                              const SnackBar(
                                content: Text("Entry successfully saved!"),
                              ),
                            );
                            Navigator.pushReplacement(
                              context,
                              MaterialPageRoute(
                                  builder: (context) => MyHomePage()),
                            );
                          } else {
                            ScaffoldMessenger.of(context).showSnackBar(
                              const SnackBar(
                                content: Text(
                                    "Something went wrong, please try again."),
                              ),
                            );
                          }
                        }
                      }
                    },
```

#### Implement Logout Feature
13. Add a new function in ```authentication/views.py``` for logout function.
```
@csrf_exempt
def logout(request):
    username = request.user.username

    try:
        auth_logout(request)
        return JsonResponse({
            "username": username,
            "status": True,
            "message": "Logged out successfully!"
        }, status=200)
    except:
        return JsonResponse({
        "status": False,
        "message": "Logout failed."
        }, status=401)
```

14. Then add this code to ```entry_card.dart``` file and change the ```onTap: () {...}``` for widget ```Inkwell``` to ```onTap: () async {...}```. and add the second part of code into the ```async {...}```'s last part. 
```
@override
Widget build(BuildContext context) {
    final request = context.watch<CookieRequest>();
    return Material(
```
```
else if (item.name == "Logout") {
            final response = await request.logout(
                // TODO: Change the URL to your Django app's URL. Don't forget to add the trailing slash (/) if needed.
                "http://localhost:8000/auth/logout/");
            String message = response["message"];
            if (context.mounted) {
              if (response['status']) {
                String uname = response["username"];
                ScaffoldMessenger.of(context).showSnackBar(SnackBar(
                  content: Text("$message Goodbye, $uname."),
                ));
                Navigator.pushReplacement(
                  context,
                  MaterialPageRoute(builder: (context) => const LoginPage()),
                );
              } else {
                ScaffoldMessenger.of(context).showSnackBar(
                  SnackBar(
                    content: Text(message),
                  ),
                );
              }
            }
          }
```
</details>


