# Kidternship2024
Files for a Kidternship class

**Kotlin** - Programming language we will use for our app  
**Android** - Operating system our app will run on  
**Android Studio** - The "Integrated development environment" (IDE) we will use to write and build our app  
Step 1: Open Android Studio  
Step 2: Click on "New Project"  
Step 3: Make sure "Empty Activity" is selected and press "next"  
Step 4: Name your App whatever you want, and click "Finish"  
A gradle sync will start. That is Android Studio downloading and configuring things in the background that are neccessary for your app. This may take a few minutes in the meantime we can learn about what is part of Android Studio  
On the Left side of the screen is your project structure. Press the arrow to expand the file structure where it says "app" then "kotlin+java" then "com.example.myapplication" or whatever you called your project. Now we can see the file "MainActivity.kt" The ".kt" shows us that the file is a Kotlin file  
To the middle/right is the actual code. Near the top we can see that the code is from the file MainActivity.kt. This is generated for us when we create the project.  
In the code there are several sections  
```
import ...
```
This includes a bunch of things that the file imports to make the code work. For the most part we will just forget about this. Click the three dots to expand it to see what the specific imports are.  
```
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContent {
            MyApplicationSampleTheme {
                Scaffold(modifier = Modifier.fillMaxSize()) { innerPadding ->
                    Greeting(
                        name = "Android",
                        modifier = Modifier.padding(innerPadding)
                    )
                }
            }
        }
    }
}
```
This is the starting point of all the code. We will skip over what is going on here and get to what is important.  
Below That is the following code:  
```
@Composable
fun Greeting(name: String, modifier: Modifier = Modifier) {
    Text(
        text = "Hello $name!",
        modifier = modifier
    )
}
```
This is called a function. The ```@Composable``` means the function is one that will be visually shown on the app.  
The word ```fun``` stands for how fun this is going to be. Just kidding, it means "function" which is the name for this type of code block. A function is a piece of code we can use somewhere else. The word ```Greeting``` is the name for this function. We can change it to any name we want later. The line ```(name: String, modifier: Modifier = Modifier)``` shows the inputs of our function, so a name and a modifier. Finally we get to the inside of our function:  
```
Text(
    text = "Hello $name!",
    modifier = modifier
)
```
This shows us that on the screen we will have some text. The text will be ```"Hello, $name!"```. Its weird that we have the ```$``` sign in front of name but what that means is we will be using the value from the input on top. 