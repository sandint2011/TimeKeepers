# TimeKeepers

### Contents

###### [Installation & Setup](https://github.com/sandint2011/TimeKeepers/blob/main/README.md#installation--setup)

###### [C# Coding Conventions](https://github.com/sandint2011/TimeKeepers/blob/main/README.md#c-coding-conventions-1)

# Installation & Setup

## GitHub

### Installation

1. Install [GitHub Desktop](https://desktop.github.com/?ref=winstall).

    - If you prefer, you can install [Git](https://gitforwindows.org/) instead, but most students are less familiar with the commandline and prefer a GUI.

### TimeKeepers Repository

1. Accept the GitHub/email invitation to become a collaberator on the TimeKeepers repository.

2. In GitHub Desktop, clone the repository:

    - _GitHub Desktop > File > CLone Repository... > `sandint2011/TimeKeepers`._

## Unity

### Installation

1. Install [Unity Hub](https://unity3d.com/get-unity/download).

    - Unity Hub might require an update, so open it and update/restart if it asks.

    - Unity Hub might also require you to activate a license, so be sure to follow the instructions (there is a free license).

2. In Unity Hub, install the Unity Editor version `2021.3.10f1 (LTS)`.

    - _Unity Hub > Installs > Install Editor > 2021.3.10f1 (LTS) > Install_

### Preferences & Settings

1. Set the Play Mode tint to red (optional but helpful).

    - _Unity > Edit > Preferences... > Colors > Play Mode tint > `#FFA0A0`._

2. Set objects to create at origin instead of camera pivot (optional but useful).

    - _Unity > Edit > Preferences... > Scene View > Create Objects at Origin > `CHECK`._

3. Reconfigure the editor layout as you see fit. You can drag panels around and use the Window tab to add more panels.

    - I've made a layout with most of the panels we'll use; feel free to use it.

        - _Unity > Window > Layouts > Load Layout from file... > `Layout.wlt`._

## VS Code

### Installation

1. Install [Visual Studio Code](https://code.visualstudio.com/Download).

2. Install the [.NET SDK](https://dotnet.microsoft.com/en-us/download).

### C# & Unity Extensions

1. Install the following VS Code extensions (press Ctrl+Shift+X to open the extensions tab).

    - _C#_

    - _C# Snippets_

    - _Debugger for Unity_

    - _Unity Code Snippets_

    - _Unity Snippets_

    - _Unity Tools_

### Unity Settings

1. Set Unity's default script editor to VS Code.

    - _Unity > Edit > Preferences... > External Tools > External Script Editor > `Visual Studio Code`._

# C# Coding Conventions

This is a shortened and slightly modified version of [Microsoft's .NET C# coding conventions](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions).

There is an auto-formatter set up for VS Code, so anything it automatically handles (like tabs, spacing, and newlines) is omitted from this list. Auto-formatters can only do so much, though, so some things (like naming conventions) need to be managed ourselves.

## Naming Conventions

### Pascal Case

Use pascal casing ("**P**ascal**C**asing") when naming a `class`, `record`, or `struct`.

```c#
public class Player
{
}
```

```c#
public record Rectangle(
    float X,
    float Y,
    float Width,
    float Height
);
```

```c#
public struct Action
{
}
```

When naming an `interface`, use pascal casing prefixed with an `I`.

```c#
public interface IEnemy
{
}
```

Use pascal casing for all `public` members such as fields, properties, events, methods, and local functions.

```c#
public class Events
{
    // Public field. Properties should be preferred to public fields.
    public vool isValid;
    
    // An init-only property.
    public IEventQueue EventQueue { get; init; }
    
    // An event.
    public event Action Event Processing;
    
    // Method.
    public void StartEventProcessing()
    {
        // Local function.
        static int CountQueueItems() => EventQueue.Count;
        // ...
    }
}
```

When writing positional records, use pscal casing for parameters, as they're the public properties of the record.

```c#
public record Rectangle(
    float X,
    float Y,
    float Width,
    float Height
);
```

### Camel Case

Use camel casing ("**c**amel**C**asing") when naming `private` or `internal` fields..

```c#
public class Player
{
    private int baseHealth;
}
```

Use camel casing for method parameters.

```c#
public void setHealth(int health)
{
    // ...
}
```

## Layout Conventions

Use the auto-formatter's layout changes whenever they're applied. If the auto-formatter has no preference, use the following conventions instead.

Write only one statement per line.

```c#
// Good.
player.resetHealth();
player.resetExperience();
```

```c#
// Bad.
player.ResetHealth(); player.ResetExperience();
```

Write only one declaration per line.

```c#
// Good.
int x;
int y;
```

```c#
// Bad.
int x; int y;
```

```c#
// Also bad.
int x, y;
```

Never use more than 1 blank line between code or comment lines.

```c#
// Good.
int a = 1;
int b = 2;

int c = 3;

string x = "Hello";
```

```c#
// Bad.
int a = 1;
int b = 2;

int c = 3;



string x = "Hello";
```

Separate block elements methods from each other and from fields and parameters with a blank line. Fields and properties can be grouped together, though.

```c#
// Good.
class Player
{
    public int Health { get; set; }
    public int Experience { get; set; }
    
    public void ResetHealth()
    {
        Health = 100;
    }
    
    public void ResetExperience()
    {
        Experience = 0;
    }
}
```

```c#
// Bad.
class Player
{
    public int Health { get; set; }
    public int Experience { get; set; }
    public void ResetHealth()
    {
        Health = 100;
    }
    public void ResetExperience()
    {
        Experience = 0;
    }
}
```

Do not place fields or properties between methods.

```c#
// Good.
class Player
{
    public int Health { get; set; }
    public int Experience { get; set; }
    
    public void ResetHealth()
    {
        Health = 100;
    }
    
    public void ResetExperience()
    {
        Experience = 0;
    }
}
```

```c#
// Bad.
class Player
{
    public int Health { get; set; }
    
    public void ResetHealth()
    {
        Health = 100;
    }
    
    public int Experience { get; set; }
    
    public void ResetExperience()
    {
        Experience = 0;
    }
}
```

Do not start or end blocks with blank lines.

```c#
// Good.
class Player
{
    void Ready()
    {
        health = 100;
        experience = 0;
    }
}
```

```c#
// Bad.
class Player
{
    
    void Ready()
    {
        
        health = 100;
        experience = 0;
    }
    
}
```

If continuation lines are not indented automatically, indent them one tab stop (4 spaces).

```c#
// Ideal, but too many parameters might make for a long line.
SetPosition(player.GetX(), player.GetY(), player.GetZ());
```

```c#
// Good.
SetPosition(
    player.GetX(),
    player.GetY(),
    player.GetZ()
);
```

```c#            
// Bad.
SetPosition(
            player.GetX(),
            player.GetY(),
            player.GetZ()
);
```

Continuous lines should end their parenthesis on their original indentation, with the first of multiple parameters (if there are any) getting its own line.

```c#
// Ideal, but long lines might need breaking up.
Vector3(x, y, z);
```

```c#
// Good.
Vector3(
    x,
    y,
    z
);
```

```c#
// Bad.
Vector3(x,
    y,
    z
);
```

```c#
// Bad.
Vector3(x,
    y, z);
```

## Commenting conventions.

Begin comments with a capital letter.

End comments with a period.

Place comments on their own line, not at the end of code lines.

```c#
// Good.
Foo();
```

```c#
Bar(); // Bad.
```

Don't create formatted blocks of asterisks around comments.

```c#
// Please
// do
// this.
```

```c#
// Or this.
```

```c#
/* Please
 * don't
 * do
 * this.
 */
```

```c#
/* Please don't do this either. */
```

## Strings

Concatinate strings with string interpolation, rather than concatination, unless there are no hardcoded strings being added.

```c#
// Good.
string fullName = $"{firstName}, {lastName}";
```

```c#
// Good, since there are only variables and no hardcoded strings.
string fullName = fullName + commaSeparator + lastName;
```

```c#
// Bad.
string fullName = firstName + ", " + lastName;
```

## Data types

### Implicitly typed local variables

Don't do them.

```c#
// Good.
string sentence = "This is a string.";
int number = 5;
```

```c#
// Bad.
var sentence = "This is a string.";
var number = 5;
```

### Numbers

Use `int` over `short` or `long` unless it's absolutely necessary.

Use `float` over `double` unless it's absolutely necessary, since Unity's classes and methods generally use them (most notably `Vector3`).

In general, use unsigned types (like `short`, `int`, or `long`) over unsigned types (like `byte`, `ushort`, `uint`, or `ulong`). This is because it makes refactoring to allow signed numbers in the future easier.

### Arrays

Use concise array initialization syntax in the declaration line.

```c#
// Good.
string[] letters = { "A", "B", "C" };
```

```c#
// Bad.
string[] letters = new string[] { "A", "B", "C" };
```

## `try`-`catch` and `using` statements

When using `try`-`catch` or `using` statements for exception handling, do not use them to hide the error. We want things to break as loudly as possible so they're easier to debug, as we can see exactly what went wrong and where.

```c#
// Good.
try
{
    return array[index];
}
catch (System.IndexOutOfRangeException e)
{
    Debug.Log("Index out of range: {0}", index);
}
```

```c#
// Bad.
try
{
    return array[index];
}
catch (System.IndexOutOfRangeException e)
{
    // Do nothing and/or fail silently.
    return defaultValue;
}
```
