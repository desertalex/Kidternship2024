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

# In the code there are several sections:
## Import
```
import ...
```
This includes a bunch of things that the file imports to make the code work. For the most part we will just forget about this. Click the three dots to expand it to see what the specific imports are.
## Main Activity Class
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
This is the starting point of all the code. We will skip over most of this except for the function call ```Greeting```. Here we call the function ```Greeting``` and input the paramaters ```name = "Android"``` and ```modifier = Modifier.padding(innerPadding)```.  
## Composable Function
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
The word ```fun``` stands for how fun this is going to be. Just kidding, it means "function" which is the name for this type of code block. A function is a piece of code we can use somewhere else. The word ```Greeting``` is the name for this function. We can change it to any name we want later. The line ```(name: String, modifier: Modifier = Modifier)``` shows the inputs of our function, so a name and a modifier. Remember the function call ```Greeting``` from the ```Main Activity Class```? That is where this Composable function gets called and where the parameters are inserted. Inside our function is some ```Text```
### Text

```
Text(
    text = "Hello $name!",
    modifier = modifier
)
```
This shows us that on the screen we will have some text. The text will be ```"Hello, $name!"```. Its weird that we have the ```$``` sign in front of name but what that means is we will be using the vale given from the parameter. 
## Preview
```
@Preview(showBackground = true)
@Composable
fun GreetingPreview() {
    KidternshipAppTheme {
        Greeting("Android")
    }
}
```
This will display what our page on the app looks like. It is useful in large apps where it takes a long time to build and run the app. Since our app is small and basic, just delete it since it is more trouble than it is worth.

## Press Play
Press the green play button on the top and see the app that we create as a default. An emulator appears to the right with our app on it. There is a white screen that says "Hello Android". How can we get it to say "Hello your name"? The secret is to replace the word ```Android``` in the ```Greeting``` function call with your name
# Steps to make cookie clicker
First of all, we need a cookie to click. Where should we put it. How about we put the cookie in the ```@Composable``` function. Underneath the text put ```Image()```. You will notice that the word Image turns red. In programming red is bad, it means there is an error. If we hover over the red Image, it says ```Unresolved reference: Image```. This means that the computer doesn't know what Image means. Luckily by hovering over the error we get a suggested fix. ```Import```. Click import and then the option that starts with ```@Composable Image``` Press that and Android Studio will automatically Import the code to make Image work. The word Image is still red. In this case it is because we are not done adding the Image, we have to choose what image we want to specifically use for it.

## Choose an Image
Download one of the images below. Right click one of the below images and select ```Save image as``` and save it to your computer. Its fine to keep it in the downlaods folder for convenience.

![Cookie](https://captaincookiedc.com/wp-content/uploads/2023/04/home-icon-cookie.png)

![Cookie](https://cld.accentuate.io/5251058663586/1669752515028/CHOC-CHIP_DUEX_90426_RT_V1-copy.png)

![Cookie](https://i.pinimg.com/originals/26/7f/74/267f7433d70ed088adaa3f98b59ea051.png)

![Cookie](https://i.pinimg.com/originals/9f/3a/a5/9f3aa5fc60634251bf4cfa3085285d6b.png)

## Add image to Android Studio project
On the far left sidebar, there is an icon with a small circle, square, and triangle. Click it. This is the resource manager. We will add our image here by clicking the plus near the top of the panel. Click on ```Import Drawables```. Find it in the downloads folder or whatever other folder you downloaded it to. And click ```OK```. Then click ```Next```. Change the name of the image for convenience and click next. Finally click import. Now drag and drop the image you imported into the ```Image()``` part of the code. It should make a line of code that says ```R.drawable.....```. This is a reference to your image. The image is still red though because it wants a ```painterResource``` instead of a reference to an image. do this by adding in the `Image()` `painterResource(id=)` In the spot where it says id=, put the path to the image (the one that says R.id.). It is still red, that is because we need to add `contentDescription = ""`. The final line should look something like `Image(painterResource(id = R.drawable.cookie), contentDescription = "")`. Now press play and see what your app looks like. You should see the cookie on your screen. Will anything happen when you press it?

Now we want to make the cookie clickable and add a counter for every time you click it. Lets start by making the cookie clickable. In the Image we created add a modifier `modifier = Modifier.clickable { }` Inside the curly braces we can put the logic to add the numbers. Run the app again and press the image, notice a difference?

Lets reuse the `Text()` above the image to count the cookies since it is similar. We need to start by creating a variable that can count. In the `MainActivity` class right above the `Greeting` put `val counter = 0`. We are creating a value called counter and setting the value to 0. How do we get the counter to show up in the screen? Lets pass it as a parameter in our greeting function. Change the `name = 'Android'` to `name = counter`. Unfortunately we get a Type mismatch. It wants a `String` but we are giving it an `Int`. In east words, string means word or letter and int means number. We are giving it a number when it is expecting a word. We can change the `@Composable fun greeting` to take an Int instead of a String. In the Composable function find the parameter input where it says `String` and change it to say `Int`.

Rerun the app and see the number appear. Does it count when we press on the cookie? Nope, still work to do.

In our image where I said we could add logic, lets change the count there. Since the parameter where we put counter in is called `name` put `name = name + 1` or shortened version is `name += 1`. This takes the value name and adds one to itself. We get an error though `val cannot be reassigned`.

Looks like setting counter to an int was not the right idea, lets try again and set it as something that can be reassigned. Change the line where we set val counter to `val counter = mutableStateOf(0)`. So close, we get another error. This is saying we need to use something called `remember`. Mutable state of is able to change its value but it will not show on the screen. Instead we need the following code: `val counter = remember {mutableStateOf(0)}`. Dont forget to import `remember`.

Below we see another error. Counter is red. There is another type mismatch where it requires an `Int` but Finds a `MutableState<Int>`. Just like we did before lets change the expected type in Greeting from `Int` to `MutableState<Int>`. Essentually we are wrapping our Int in a box of MutableState so that it can be changed.

Our logic to add is now broken with an error message too long for me to want to read. That is because we are trying to add 1 to the MutableObject instead of the Int inside of it. Change the logic to say `name.value += 1` to do that.

Reload the app and see what it says..... oh no it says `Hello MutableState(value=0)@347248324789` or something like that. That is because we are displaying the MutableState object instead of the number inside of it. In our `Text` change it to say `${name.value}`

Click the app to run it. Finally it works!!!

The final code should look similar to this
```
package com.example.kidternshipapp

import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.activity.enableEdgeToEdge
import androidx.compose.foundation.Image
import androidx.compose.foundation.clickable
import androidx.compose.foundation.layout.fillMaxSize
import androidx.compose.foundation.layout.padding
import androidx.compose.material3.Scaffold
import androidx.compose.material3.Text
import androidx.compose.runtime.Composable
import androidx.compose.runtime.MutableState
import androidx.compose.runtime.mutableStateOf
import androidx.compose.runtime.remember
import androidx.compose.ui.Modifier
import androidx.compose.ui.res.painterResource
import com.example.kidternshipapp.ui.theme.KidternshipAppTheme

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContent {
            KidternshipAppTheme {
                Scaffold(modifier = Modifier.fillMaxSize()) { innerPadding ->
                    val counter = remember {mutableStateOf(0)}
                    Greeting(
                        name = counter,
                        modifier = Modifier.padding(innerPadding)
                    )
                }
            }
        }
    }
}

@Composable
fun Greeting(name: MutableState<Int>, modifier: Modifier = Modifier) {
    Text(
        text = "Hello ${name.value}!",
        modifier = modifier
    )
    Image(painter = painterResource(R.drawable.cookie), contentDescription = "", modifier = Modifier.clickable { name.value += 1 })
}
```
