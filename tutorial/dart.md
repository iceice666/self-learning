
## 0. Setup


> - OS: Arch Linux x86_64 
> - Kernel: 6.7.0-zen3-1-zen
> - Android device: RMX3370 (Realme GT Neo 2)
> - IDE: Neovim v0.9.5 with customization

### Flutter setup

1. Install flutter package and dependencies  
    (You can use paru or yay to install aur package)
    ```bash
    > paru -S flutter google-chrome android-studio android-sdk-cmdline-tools-latest \
       android-sdk-build-tools android-sdk-platform-tools android-platform
    ```

2. Set chrome executable path
    ```bash
    export CHROME_EXECUTABLE="/usr/bin/google-chrome-stable"
    ```
3. Accept android licenses
    ```bash
    > sudo flutter doctor --android-licenses
    ```

4. Check everything is okay

    ```bash
    > flutter doctor
    Doctor summary (to see all details, run flutter doctor -v):
    [✓] Flutter (Channel stable, 3.16.8, on Arch Linux 6.7.0-zen3-1-zen, locale en_US.UTF-8)
    [✓] Android toolchain - develop for Android devices (Android SDK version 34.0.0)
    [✓] Chrome - develop for the web
    [✓] Linux toolchain - develop for Linux desktop
    [✓] Android Studio (version 2023.1)
    [✓] IntelliJ IDEA Ultimate Edition (version 2023.3)
    [✓] Connected device (3 available)
    [✓] Network resources

    • No issues found!
    ```

### Editor setup
check this [commit](https://github.com/iceice666/nvim/commit/e9ed7748209b169eaf33f45bc6751845fd54ab1c)

## 1. First run

Create a project
```bash
> flutter create learning_flutter
> cd learning_flutter
```
Run
```bash
> flutter run
Connected devices:
Linux (desktop) • linux  • linux-x64      • Arch Linux 6.7.0-zen3-1-zen
Chrome (web)    • chrome • web-javascript • Google Chrome 120.0.6099.224
[1]: Linux (linux)
[2]: Chrome (chrome)
Please choose one (or "q" to quit): 
```
Choose a device to run  
It will run a counter app




## 2. Dart tutorial

### declare variables and functions

To declare a variable, use `var` statement
```dart
  var a = 1; //int 
  var b = "1"; // String 
  var c = 1.1; // double 

  a = "123"; // Error: A value of type 'String' can't be assigned to a variable of type 'int'.
```

Use `dynamic` to declare a variable with **Any** type
```dart
dynamic a = 1;
a = '123'; // no error
```


Type with a trailing `?` means this is a **nullable** variable  
In dart, use `null` to represent a empty value (like `None` in python)
```dart
int? foo = null;
```

Declare a `List` with `[]`  
Use `const` to declare a constant variable
```dart
List<dynamic> a = const [1, '123', true];
```

Declare a `Map` with `{}`  
```dart
var map = {
    'key1': 'value1',
    'key2': 'value2',
    'key3': 'value3'
  };
```


Define a function
```dart
[return type] <function name>([<argtype> <argname>],...) {
    // do something
}
```

e.g.
```dart
void main() {

}
```

`void` means no return value

One-line syntax sugar

```dart
[return type] <function name>([<argtype> <argname>],...) =>
    // do something
```

e.g.
```dart
int plus(int a, int b) =>
    a + b;
```

Define a function with default value

```dart
[return type] <function name>({[<argtype> <argname> = <default value>],...}) {
    // do something
}
```
e.g.
```dart
birthday({String name='Amy', int month, int day}) =>
    "${name}'s birthday is $month/$day.";
```
### flow control

- if-else
    ```dart
    if (condition){
        // do something
    } 
    else if (condition){
        // do something
    }
    else {
        // do something
    }
    ```

- Ternary
    ```dart
    (condition) ? expr : expr;
    ```

- for loop
    ```dart
    for (init; condition; update){
        // do something
    }
    ```

    ```dart
    for (var item in iterator){
        // do something
    }
    ```

    ```dart
    <iterable>.foreach( // a closure )
    ```

- while loop
    
    check condition first
    
    ```dart
    while (condition){
        // do something
    }
    ```


- do-while loop

    do \<expr> first
    ```dart
    do {
    // do something
    } while(condition);
    ```

- switch

    ```dart
    Switch (variable) {
        case cond1:
            // do something
            break;

        case cond2:
            // do something
            break;

        ...

        default:
            // do something

    }
    ```

### error handling

#### Throw 
```dart
throw <An error>
```

#### Catch

```dart
try {
    // do something that may raise an error
} on <error/exception> {
    // do something to deal the the error
} catch {
    // do something to deal with other errors
} finally {
    // do something
}

```

### class

#### Define a class

```dart
class <class name> {
    <field type> <field name>;
    String name; // Public by default
    // with leading `_` can make a variable private
    String _id; // this is a private field
    ...

    some functions
    ...

    // Dart class constructor
    <class name>([args]){
        // do something
    }

    // Use `this.<field name> directly in the constructor declaration, 
    // and omit the body.
    <class name>([args which same as class fields]);
    // Named constructor
    <class name>.<function name>([args which same as class fields]);

    // getter
    [return type] get <name> => <value>
    // setter
    set <name>([args]){
        // do something
    }
}
```


#### Extends

Just like Java

```dart

class Foo{...}

class Bar extends Foo {...}

```

#### Mixin

```dart

mixin Foo{...}
mixin Bar{...}

// We can call functions which defined in `Foo` and `Bar` through `Yee`
class Yee with Foo, Bar {...}
```

### async


#### Define a async function

Use `async` to mark a function is **asynchronous**

```dart
Future<return type> <function name>([args]) async {
    // do something
}
```

Use `await` to call a async function
```dart
await async_fun();
```



## 3. Follow the [tutorial](https://ithelp.ithome.com.tw/users/20119550/ironman/2221?page=1)
