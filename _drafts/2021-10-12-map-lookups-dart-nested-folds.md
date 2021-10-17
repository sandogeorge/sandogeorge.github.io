---
layout: post
title: Map Lookup in Dart using Nested Folds
date: 2021-10-12 18:30
comments: true
categories: Computing
---
> This post explores a way of searching maps using the `iterable.fold()`{:.language-dart .highlight} method available in the Dart programming language. In addition to presenting code, the post discusses the implementation constraints, along with an example use case.

#### Table of Contents
* [Introduction](#introduction){: .toc}
* [Example Use Case](#example-use-case){: .toc}
* [Contraints](#constraints){: .toc}
* [Implementation](#implementation){: .toc}
* [Conclusion](#conclusion){: .toc}

#### Introduction

A map is a data type that stores a collection of key-value pairs, where each key is unique. The map enables us to store and retrieve data and perform complex operations intuitively. One such operation involves recursively analyzing the data using folding and producing a single output based on that analysis. Folding, as a concept, has its origins in functional programming and tends to result in concise, elegant code compared to performing the same operations using a procedural style.

#### Example Use Case

It’s not hard to think of a situation where we need to maintain configuration files for an application. It’s a common requirement, after all. We will, therefore, explore a use case in line with this. Imagine that we have an API-backed application, and we need to store, among other things, the base URL of the API server and the paths of the various endpoints. The configuration values, in a map, would look similar to the following:

```dart
Map<String, dynamic> configuration = <String, dynamic>{
    'api_base_url': 'https://example.com/api',
    'api_endpoints': <String, String> {
        'login': 'users/login',
        'logout': 'users/logout',
    },
    .
    .
    .
};
```

With the data in a map, we can import the configuration variable and immediately reference key-value pairs without any conversion, as we would have to do in the case of data formats such as JSON.

```dart
import 'path/to/config/file.dart';

print(configuration['api_endpoints']['login']);

===
Output: users/login
===
```

Note of use of the `[]`{:.language-dart .highlight} operator twice to access the desired value. What if we could simplify this by using a utility function to access arbitrary values using a single string as the key?! Then we could do something like the following:

```dart
print(getProperty(configuration, 'api_endpoints.login'));
```

We can implement this utility function concisely using nested folding, and we will see how shortly. But first, let us look at some constraints.

#### Constraints

To keep our implementation simple, we will adhere to the following constraints:

* The map must be of type `Map<String, dynamic>`{:.language-dart .highlight}.
* Keys should not contain characters we use as accessors: `.`{:.language-dart .highlight} and `#`{:.language-dart .highlight}.
* We will only perform deep searches on the following types: `Map<String, dynamic>`{:.language-dart .highlight} and `List<dynamic>`{:.language-dart .highlight}.

#### Implementation

Let's implement the utility function `getProperty()`{:.language-dart .highlight}. Here we define a function in just about twenty lines of code that will allow us to access nested values using a single string as the key.

```dart
dynamic getProperty(Map<String, dynamic> lookupMap, String key) {
    List<String> keys = key.split('.');
    try {
        return keys.fold(lookupMap, (previousValue, element) {
            Map m = previousValue as Map;
            if (element.contains('#')) {
                List listKeys = element.split('#');
                List indices = listKeys.getRange(1, listKeys.length).toList();
                return indices.fold(m[listKeys[0]], (previousValue, element) {
                    List l = previousValue as List;
                    return l[int.parse(element)];
                });
            }
            else {
                return m[element];
            }
        });
    }
    catch (_) {}
}
```

And again with documentation and comments.

```dart
/// Search [lookupMap] for [key] using nested folding.
///
/// Returns [null] if [key] is not found or if an error is thrown.
/// Use [.] as the map accessor and [#] as the list accessor.
dynamic getProperty(Map<String, dynamic> lookupMap, String key) {
    // 1. Split key by the map accessor to get overall map nesting.
    List<String> keys = key.split('.');

    try {
        // 2. Recursively process map using nesting structure given by keys.
        return keys.fold(lookupMap, (previousValue, element) {
            // 3. We can assume previous values in the outer fold are maps.
            Map m = previousValue as Map;

            // 4(a). If the key at this level contains the list accessor
            // Process this level as a list.
            if (element.contains('#')) {
                // 4(a)(i) Split key by list accessor to get list nesting
                // at this map level.
                List listKeys = element.split('#');

                // 4(a)(ii) Get list indices. Cater for consecutive list nesting.
                List indices = listKeys.getRange(1, listKeys.length).toList();

                // 4(a)(iii) Recursively process list using nesting structure
                //given by indices.
                return indices.fold(m[listKeys[0]], (previousValue, element) {
                    // 4(a)(iv) We can assume that previos values in the inner fold
                    //are lists.
                    List l = previousValue as List;

                    // 4(a)(v) Return list[element].
                    return l[int.parse(element)];
                });
            }
            // 4(b) Else the key at this level is just a map accessor.
            else {
                // 4(b)(i) Return map[element].
                return m[element];
            }
        });
    }
    // Catch errors and do nothing. Function will return null.
    // Meaning the lookup value was not found.
    catch (_) {}
}
```

Now let's look at some examples.

```dart
void main() {
  Map<String, dynamic> config = <String,dynamic>{
    "api_base_url": "https://example.com/api",
    "api_endpoints": {
        "login": "users/login",
        "logout": "users/logout"
    },
    "list": [
      12,
      15,
      <String, String>{
        "test": "pass!",
        "code": "meh",
      },
      [1, 2, 3, "The end!"],
    ],
    "map": <String,dynamic>{
      "nestedmap": <String, String>{
        "getme": "Got ya!"
      },
      "list2": [2, 3, 5, 7, 11],
    },
  };
  
  // Map accessor.
  print(getProperty(config, 'api_endpoints.login'));
  
  // List accessor.
  print(getProperty(config, 'list#0'));
  
  // Map within list.
  print(getProperty(config, 'list#2.test'));
  
  // List within map.
  print(getProperty(config, 'map.list2#2'));
  
  // Nested map.
  print(getProperty(config, 'map.nestedmap.getme'));
  
  // Nested list.
  print(getProperty(config, 'list#3#3'));
}

===
Output:

users/login
12
pass!
5
Got ya!
The end!
===
```

#### Conclusion

We have seen, with examples, how we can perform lookups on maps using folding. The implementation is concise and applicable wherever there is a need to intuitively retrieve nested values from a map that matches our constraints. The method may work beyond these constraints, but I have yet to do comprehensive testing to determine its actual bounds of utility. I hope that someone other than me finds this helpful!