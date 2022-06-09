# Dart Basics

Contents:

- [Declaring variables](#declaring-variables)
- [Type inference with `var`](#type-inference-with-var)
- [`final` and `const` keyword](#final-and-const-keyword)
- [`late` keyword](#late-keyword)
- [`dynamic` keyword](#dynamic-keyword)
- [Type conversion](#type-conversion)
- [Checking type of a dynamic variable](#checking-type-of-a-dynamic-variable)
- [List](#list)
- [Set](#set)
- [Map](#map)
- [Null](#null)
- [Null safety](#null-safety)
- [References](#references)

## Declaring variables

```dart
void main() {
  int variable1 = 42;
  double variable2 = 42.42;
  String variable3 = 'fourty-two';
  bool variable4 = false;
  List variable5 = [42, 42.42, 'fourty-two', false];
  Map variable6 = {
    'key1': 42,
    'key2': 42.42,
    'key3': 'fourty-two',
    'key4': false
  };

  print('variable1: $variable1');
  print('variable2: $variable2');
  print('variable3: $variable3');
  print('variable4: $variable4');
  print('variable5: $variable5');
  print('variable5[0]: ${variable5[0]}');
  print('variable6: $variable6');
  print('variable6[\'key1\']: ${variable6['key1']}');
}
```

## Type inference with `var`

```dart
void main() {
  var variable1 = 42;
  var variable2 = 42.42;
  var variable3 = 'fourty-two';
  var variable4 = false;
  var variable5 = [42, 42.42, 'fourty-two', false];
  var variable6 = {
    'key1': 42,
    'key2': 42.42,
    'key3': 'fourty-two',
    'key4': false
  };

  print('variable1: $variable1');
  print('variable2: $variable2');
  print('variable3: $variable3');
  print('variable4: $variable4');
  print('variable5: $variable5');
  print('variable5[0]: ${variable5[0]}');
  print('variable6: $variable6');
  print('variable6[\'key1\']: ${variable6['key1']}');
}
```

## `final` and `const` keyword

Using `final` keyword means that a variable cannot be reassigned.

```dart
void main() {
  var variable = 'hello';
  final finalVariable = 'world';
  print('variable: $variable');
  print('finalVariable: $finalVariable');

  variable = 'halo';
  finalVariable = 'dunia';
  // Error: Can't assign to the final variable 'finalVariable'.
  print('variable: $variable');
  print('finalVariable: $finalVariable');
}
```

Using `const` keyword means that a variable is completely immutable.

```dart
void main() {
  final finalList = [1, 2, 3];
  print('list: $finalList');
  finalList[0] = 42;
  print('finalList: $finalList');

  const constList = [1, 2, 3];
  print('constList: $constList');
  constList[0] = 42;
  // Unsupported operation: Cannot modify an unmodifiable list
  print('constList: $constList');
}
```

## `late` keyword

`late` keyword can be used to defer an initialization of a variable until it is needed.

```dart
void main() {
  var variable = getGreeting();
  print('variable value is:');
  print(variable);
  // getGreeting called
  // variable value is:
  // hello

  late var lateVariable = getGreeting();
  print('lateVariable value is:');
  print(lateVariable);
  // lateVariable value is:
  // getGreeting called
  // hello
}

String getGreeting() {
  print('getGreeting called');
  return 'hello';
}
```

## `dynamic` keyword

A dynamic variable can holds value with any kind of data type.

```dart
void main() {
  dynamic variable1 = 42;
  print('variable1: $variable1');
  variable1 = 'fourty-two';
  print('variable1 $variable1');

  // Or

  var variable2;
  variable2 = 42;
  print('variable2: $variable2');
  variable2 = 'fourty-two';
  print('variable2: $variable2');
}
```

## Type conversion

```dart
void main() {
  // String to Number
  var variable1 = '42';
  var intVariable1 = int.parse(variable1);
  var doubleVariable1 = double.parse(variable1);
  print('Result: $variable1 $intVariable1 $doubleVariable1');
  // Result: 42 42 42.0

  // Number to another Number
  var variable2 = 42;
  var doubleVariable2 = variable2.toDouble();
  print('Result: $variable2 $doubleVariable2');
  // Result: 42 42.0
  var variable3 = 42.42;
  var intVariable3 = variable3.toInt();
  print('Result: $variable3 $intVariable3');
  // Result: 42.42 42

  // Number to String
  var variable4 = 42;
  var variable5 = 42.42;
  print('Result: ${variable4.toString()} ${variable5.toString()}');
  // Result: 42 42.42

  // Boolean to String
  var variable6 = false;
  print('Result: ${variable6.toString()}');
  // Result: false
}
```

## Checking type of a dynamic variable

```dart
void main() {
  dynamic variable1 = 42;
  print('variable1 is int: ${variable1 is int}');
  print('variable1 is not String: ${variable1 is! String}');

  dynamic variable2 = 42.42;
  print('variable2 is double: ${variable2 is double}');
  print('variable1 is not int: ${variable1 is! int}');

  dynamic variable3 = 'fourty-two';
  print('variable3 is String: ${variable3 is String}');
  print('variable1 is not double: ${variable1 is! double}');
}
```

## List

```dart
void main() {
  List<int> variable1 = [42, 43, 44];
  var variable2 = <String>['hello', 'world'];
  print('variable1 (List of integers): $variable1');
  print('variable2 (List of Strings): $variable2');
  // variable1 [42, 43, 44]
  // variable2 [hello, world]

  var variable3 = [42, 42.42, 'fourty-two', false];
  print('variable3 (List of dynamics): $variable3');
  // variable3 (List of dynamics) [42, 42.42, fourty-two, false]

  var variable4 = <int>[];
  variable4.add(42);
  variable4.add(43);
  variable4.add(44);
  print('variable4: $variable4');
  // variable4: [42, 43, 44]
  print('variable4.length: ${variable4.length}');
  // variable4.length: 3
  variable4.removeAt(1);
  print('variable4: $variable4');
  // variable4: [42, 44]
}
```

## Set

Like `List`, `Set` can holds more than one value. The difference is `Set` can only hold unique values.

```dart
void main() {
  Set<int> variable1 = {};
  variable1.add(43);
  variable1.add(45);
  variable1.add(45); // Duplicate
  variable1.add(42);
  variable1.add(44);
  variable1.add(45); // Duplicate
  print('variable1: $variable1');
  print('variable1 element at 0: ${variable1.elementAt(0)}');
  print('variable1 contains 40: ${variable1.contains(40)}');
  // variable1: {43, 45, 42, 44}
  // variable1 element at 0: 43
  // variable1 contains 40: false
  variable1.remove(43);
  print('variable1: $variable1');
  // variable1: {45, 42, 44}

  var variable2 = <int>{10, 11, 12};
  print('variable2: $variable2');
  // variable2: {10, 11, 12}
}
```

## Map

`Map` can holds more than one **key-value pair**. With `List`, the key type is `int` starting from 0, and will be incremented each time we insert a new value. In `Map` we have to define the type for both key and value. If we do not define the type, then it is assumed that the type is `dynamic`.

```dart
void main() {
  Map<String, int> variable1 = {'key1': 42, 'key2': 43, 'key3': 44};
  print('variable1: $variable1');
  print('variable1 key "key2": ${variable1['key2']}');
  // variable1: {key1: 42, key2: 43, key3: 44}
  // variable1 key "key2": 43

  var variable2 = <int, int>{0: 42, 1: 43, 2: 44};
  print('variable2: $variable2');
  print('variable2 key "2": ${variable2[2]}');
  // variable2: {0: 42, 1: 43, 2: 44}
  // variable2 key 2: 44

  variable2[3] = 45;
  print('variable2: $variable2');
  // variable2: {0: 42, 1: 43, 2: 44, 3: 45}
  variable2.remove(3);
  print('variable2: $variable2');
  // variable2: {0: 42, 1: 43, 2: 44}
}
```

## Null

In Dart `null` represents an empty value. A variable has to hold a value before it can be used. If we want to create a variable which can be `null`, we can add `?` when declaring it.

```dart
void main() {
  int variable1;
  int? variable2;
  print(variable1);
  // Error: Non-nullable variable 'variable1' must be assigned before it can be used.
  print(variable2);
  // null

  var? variable3 = 10;
  // We cannot use "?" with var
}
```

## Null safety

### Checking null

```dart
void main() {
  List<int>? variable;

  print('variable 1 element 0: ${variable[0]}');
  // Will not compile
  // The method '[]' can't be unconditionally invoked because the receiver can be 'null'

  if (variable != null) {
    print('variable 1 element 0: ${variable[0]}');
    // Will compile
    // We already make sure that variable will not be null
  }
}
```

### Converting nullables

```dart
void main() {
  // Non-nullable to nullable
  String variable1 = 'fourty-two';
  String? nullableVariable1 = variable1;

  // Nullable to non-nullable
  String? variable2;

  // Checking using if
  String nonNullableVariable21;
  if (variable2 != null) {
    nonNullableVariable21 = variable1;
  }

  // Checking using ternary operator
  String nonNullableVariable22 =
      variable2 != null ? variable2 : 'get null value';

  // Checking using null-aware operator
  String nonNullableVariable23 = variable2 ?? 'get null value';

  // Converting nullable to non-nullable without null checking
  String nonNullableVariable24 = variable2!;
  // Becareful, this means that we are telling the compiler that we
  // are sure that variable2 will not be null, even though it is a
  // nullable variable
}
```

### Accessing nullable variable members

```dart
void main() {
  String? variable;

  int length1 = variable.length;
  // Will not compile
  // Since variable can be null, we have to do checking

  int length2 = variable?.length;
  // Will not compile
  // Since variable?.length can results in null, but length2 is not nullable

  int? length3 = variable?.length;
  // Will compile
}
```

## References

- [dart:core library](https://api.dart.dev/stable/2.16.2/dart-core/dart-core-library.html)
