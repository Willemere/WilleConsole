# A massive library for modifying the standard console.
- Key priorities:
  - Creating custom commands.
  - Creating tables.
  - Changing fonts and their size.
  - Changing the console window, as well as changing the console taskbar, the location of the appearance.
  - Specific console launch (From command line).
  - Writing your color text using tags.
 
## Custom commands.
Let me clarify that your command works within your program. It does not depend on the command console call. (An exception is if you call the above application using the command console, but this is still the limit of your program => does not change anything.) Preparations? Let's start with the fact that we need to declare a variable to use all the commands from our library:
```C#
var manager = new WCommand();
```
After that we use the command registration:
```C#
 manager.RegisterCommand("help", new MHelp(),
     registerValue: "Module 'help' - Loaded!");
```
In this registration we indicate:
- Our command, which needs to be registered;
- The class that belongs to this command;
- registerValue tells us that this command is definitely registered. After registration, we will be shown the text with the specified variable.
  
After registering the commands. We create an infinite loop for (;;), equivalent to while(true). We output the text Usage:, so that the person understands that it is already possible to start writing.
Waiting for user input:
- Console.ReadLine() - waits for user input and pressing Enter;
-.? - safe null handling (if ReadLine returns null);
- Trim() - trims leading and trailing spaces.

Command Processing:
- Passes the input string to the command manager's Usage method;
- Usage is expected to parse the command and perform the necessary actions.
```C#
for (; ; )
{
    Console.WriteLine("Usage: ");
    string input = Console.ReadLine()?.Trim();
    manager.Usage(input);
}
```
In the previously registered command (manager.RegisterCommand("help", new MHelp()), we create the MHelp class.
In this class we need to implement the WCommand.IModule interface, which specifies:
- MHelp - the name of your module;
- WCommand.IModule - indicates that the class implements the IModule interface from the WCommand namespace.

The implementation exists due to the Action method, where the logic of the team's work occurs.
```C#
using Wille;

namespace MyProgramLol
{
    class MHelp : WCommand.IModule
    {
         public void Action(string[] args)
         {

         }
    }
}
```



/ I'll leave this here for now and continue later.
