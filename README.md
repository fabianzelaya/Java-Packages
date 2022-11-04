# Packages
A Java program consists of a collection of classes. So far, most of your programs have consisted of a small number of classes. As programs get larger, however, simply distributing the classes over multiple files isn’t enough. An additional structuring mechanism is needed.

In Java, packages provide this structuring mechanism. A Java package is a set of related classes. For example, the Java library consists of several hundred packages, some of which are listed in Table 9.19.1. (Definition of **`package`**: A collection of related classes. The `import` statement is used to access one or more classes in a package.)

## Table 9.19.1: Important Packages in the Java Library.
| Package | Purpose | Sample Class |
| --- | --- | --- |
| **java.lang** | Language support | **Math** |
| **java.util** | Utilities** | **Random** |
| **java.io** | Input and output | **PrintStream** |
| **java.awt** | Abstract Windowing Toolkit | **Color** |
| **java.applet** | Applets | **Applet** |
| **java.net** | Networking | **Socket** |
| **java.sql** | Database access through Structured Query Language | **ResultSet** |
| **javax.swing** | Swing user interface | **JButton** |
| **org.w3c.dom** | Document Object Model for XML documents	| **Document** |

## Organizing Related Classes into Packages
To put one of your classes in a package, you must place a line
```java
package packageName;
```
as the first instruction in the source file containing the class. A package name consists of one or more identifiers separated by periods. (See Section 9.19 for tips on constructing package names.)

For example, let’s put the `Financial` class introduced in this chapter into a package named `com.horstmann.bigjava.`

The `Financial.java` file must start as follows:
```java
package com.horstmann.bigjava;
public class Financial
{
   . . .
}
```
In addition to the named packages (such as `java.util` or `com.horstmann.bigjava`), there is a special package, called the default package, which has no name. If you did not include any `package` statement at the top of your source file, its classes are placed in the default package.

![](https://zytools.zybooks.com/zyAuthor/BigJavaLateObjects/3/IMAGES/embedded_image_1_b432dc99-b908-4a6a-bb3b-984f1707e451_JNVgKZGRsu2pYUjzCfDE.png)

_In Java, related classes are grouped into packages._

## Importing Packages
If you want to use a class from a package, you can refer to it by its full name (package name plus class name). For example, java.util.Scanner refers to the Scanner class in the `java.util` package:
```java
java.util.Scanner in = new java.util.Scanner(System.in);
```
Naturally, that is somewhat inconvenient. For that reason, you usually import a name with an `import` statement:
```java
import java.util.Scanner;
```
Then you can refer to the class as `Scanner` without the package prefix.

You can import all classes of a package with an `import` statement that ends in `.*`. For example, you can use the statement
```java
import java.util.*;
```
to import all classes from the `java.util` package. That statement lets you refer to classes like `Scanner` or `Random` without a `java.util` prefix.

However, you never need to import the classes in the `java.lang` package explicitly. That is the package containing the most basic Java classes, such as `Math` and `Object`. These classes are always available to you. In effect, an automatic `import java.lang.*`; statement has been placed into every source file.

Finally, you don’t need to import other classes in the same package. For example, when you implement the class homework1.Tester, you don’t need to import the class `homework1.Bank`. The compiler will find the `Bank` class without an `import` statement because it is located in the same package, `homework1`.

## Syntax 9.19.1: Package Specification.
![](https://zytools.zybooks.com/zyAuthor/BigJavaLateObjects/3/IMAGES/embedded_image_1_b0d65c89-7a5a-4668-9070-c944ef17dbe9_JNVgKZGRsu2pYUjzCfDE.png)

## Package Names
Placing related classes into a package is clearly a convenient mechanism to organize classes. However, there is a more important reason for packages: to avoid name clashes.In a large project, it is inevitable that two people will come up with the same name for the same concept. This even happens in the standard Java class library (which has now grown to thousands of classes). There is a class `Timer` in the `java.util` package and another class called `Timer` in the `javax.swing` package. You can still tell the Java compiler exactly which `Timer` class you need, simply by referring to them as `java.util.Timer` and `javax.swing.Timer`. (Definition of **`name clash`**: Accidentally using the same name to denote two program features in a way that cannot be resolved by the compiler.)

Of course, for the package-naming convention to work, there must be some way to ensure that package names are unique. It wouldn’t be good if the car maker BMW placed all its Java code into the package `bmw`, and some other programmer (perhaps Britney M. Walters) had the same bright idea. To avoid this problem, the inventors of Java recommend that you use a package-naming scheme that takes advantage of the uniqueness of Internet domain names.

For example, I have a domain name `horstmann.com`, and there is nobody else on the planet with the same domain name. (I was lucky that the domain name `horstmann.com` had not been taken by anyone else when I applied. If your name is Walters, you will sadly find that someone else beat you to `walters.com`.) To get a package name, turn the domain name around to produce a package name prefix, such as `com.horstmann`.

If you don’t have your own domain name, you can still create a package name that has a high probability of being unique by writing your e-mail address backwards. For example, if Fabian Zelaya has an e-mail address `fabianzelaya@website.com`, then he can use a package name com.website.fabianzelaya for his own classes.

Some instructors will want you to place each of your assignments into a separate package, such as `homework1`, `homework2`, and so on. The reason is again to avoid name collision. You can have two classes, `homework1.Bank` and `homework2.Bank`, with slightly different properties.

## Packages and Source Files
A source file must be located in a subdirectory that matches the package name. The parts of the name between periods represent successively nested directories. For example, the source files for classes in the package `com.horstmann.bigjava` would be placed in a subdirectory `com/horstmann/bigjava`. You place the subdirectory inside the base directory holding your program’s files. For example, if you do your homework assignment in a directory `/home/britney/hw8/problem1`, then you can place the class files for the com.horstmann.bigjava package into the directory `/home/fabian/hw8/problem1/com/horstmann/bigjava`, as shown in Figure 9.19.1. (Here, we are using UNIX-style file names. Under Windows, you might use `c:\Users\Fabian\hw8\problem1\com\horstmann\bigjava.)`

## Figure 9.19.1: Base Directories and Subdirectories for Packages.
![](https://zytools.zybooks.com/zyAuthor/BigJavaLateObjects/3/IMAGES/embedded_image_1_07c0fe00-2637-474a-b2ab-50453f815864_JNVgKZGRsu2pYUjzCfDE.png)



## Thanks for watching!

If you like my code then follow me on my social media. Thank you!

[![](https://img.shields.io/badge/github-39d353?style=for-the-badge)](https://github.com/fabianzelaya)
[![](https://img.shields.io/badge/twitter-1D9BF0?style=for-the-badge)](https://twitter.com/fabianzelayahn)
[![](https://img.shields.io/badge/linkedin-0033FF?style=for-the-badge)](https://www.linkedin.com/in/fabianzelaya/)
[![](https://img.shields.io/badge/instagram-blueviolet?style=for-the-badge)](https://www.instagram.com/fabianzelayahn/)
[![](https://img.shields.io/badge/tiktok-fe2c55?style=for-the-badge)](https://www.tiktok.com/@fabian.zelayahn)
[![](https://img.shields.io/badge/fabianzelaya.com-lightgrey?style=for-the-badge)](http://www.fabianzelaya.com/)
<!--[![](https://img.shields.io/badge/fabianzelaya.com-orange?style=for-the-badge)](https://www.fabianzelaya.com/)-->

<img src="https://ucarecdn.com/d1a85e63-35f9-41d7-b758-ff05742057d1/GitHub_Black_Signature.png" width="240" height="79.63" />
