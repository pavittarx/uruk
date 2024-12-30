I'll streamline these notes on Flutter and Dart for you, focusing on the key concepts and providing a more structured overview.

# Flutter and Dart: Streamlined Notes

## 1. Flutter Basics

Flutter is a cross-platform UI framework built on Dart.

- Entry point: `lib/main.dart`
- Main function:


```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(home: Text("Hello World")));
}
```

Key Concept: Everything in Flutter is a `Widget`.

## 2. Widget Types

1. Stateless Widgets: Immutable, rebuild when inputs change
2. Stateful Widgets: Mutable, can rebuild themselves


## 3. Common Widgets

### Text Widget

```dart
Text(
  'Hello, World!',
  textAlign: TextAlign.center,
  overflow: TextOverflow.ellipsis,
  style: TextStyle(fontWeight: FontWeight.bold),
)
```

### Container Widget

```dart
Container(
  margin: EdgeInsets.all(10.0),
  padding: EdgeInsets.all(8.0),
  color: Colors.amber[600],
  width: 48.0,
  height: 48.0,
  alignment: Alignment.center,
  child: Text("Hello World"),
)
```

### Row Widget

```dart
Row(
  mainAxisAlignment: MainAxisAlignment.center,
  crossAxisAlignment: CrossAxisAlignment.center,
  children: [
    Text("Hello!"),
    Text("This is John Doe."),
    Text("Thanks!")
  ],
)
```

## 4. Important Enums and Classes

### Enums

- `Colors`: e.g., `Colors.red`, `Colors.red[400]`
- `Axis`: `horizontal`, `vertical`
- `CrossAxisAlignment`: `start`, `end`, `center`, `stretch`, `baseline`
- `MainAxisAlignment`: `start`, `end`, `center`, `spaceAround`, `spaceBetween`, `spaceEvenly`


### Classes

- `Color`: `Color(0xFF42A5F5)`, `Color.fromARGB(255, 66, 165, 245)`
- `EdgeInsets`: `EdgeInsets.all(8.0)`, `EdgeInsets.symmetric(vertical: 8.0)`
- `BoxConstraints`: `BoxConstraints(minWidth: 100, maxWidth: 200)`


## 5. Dart Language Features

### Null Safety

```dart
int? nullableInt = null;
int nonNullableInt = 42;
```

### Async Programming

```dart
Future<String> fetchData() async {
  await Future.delayed(Duration(seconds: 2));
  return "Data fetched";
}

void main() async {
  String result = await fetchData();
  print(result);
}
```

### Collections

```dart
// List
var fruits = ['apple', 'banana', 'orange'];

// Set
var uniqueNumbers = {1, 2, 3, 4, 5};

// Map
var person = {
  'name': 'John',
  'age': 30,
  'city': 'New York'
};
```

----
# Common CLI Commands

# 1. Gradle Build Tool

Gradle is the build tool for devlopment on android platform

	~/android/gradle/
# Commands

```shell
# Cleans up gradle build
  ./gradlew clean

# Build from Cache
 ./gradlew build

# Make a clean build
  ./gradlew clean build

# Stop running Daemons
  ./gradlew --stop
```

## Using `pub.dev` package Manager

- The list of packages is store in `pubspec.yaml`file
- The `pubspec.lock` file contains the list of  stores the list of installed versions, to counter versioning conflicts between packages. 

```shell
# Install packages present in pubspec.yaml
  - flutter pub get (or)
  - dart pub get

# Upgrade all dependencies
  - flutter pub upgrade (or)
  - dart pub upgrade

# Upgrade specific package
  - flutter pub upgrade <package-name>

# Add a package
  - flutter pub add <package-name>
```

#### Managing Package Conflicts
Package conflicts may arise if two packages are using a different versions of the same package. This can be easily be resolved using ranged versioning. 

```yaml
  name: flutter_app
  dependencies: 
    url_launcher: '5.4.0' #  only version 5.4.0 is acceptable   
    collection: '^5.4.0'  # anything >= 5.4.0 but < 6.0.0 
    url_launcher: '>=5.4.0 <6.0.0' # specifies, a minimum and maximum version
```