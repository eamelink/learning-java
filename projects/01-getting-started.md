# Getting Started

This project is to get familiar with some of the tools we use as Java developer, and setting up your environment.

## Install Java

There are only two version of Java that matter currently. Java 8 and Java 11. Both are LTS (Long Term Support) releases. Java 9 and 10 are not. Java 11 is pretty recent, and as of this writing (1-2-2019), most companies do not run Java 11 yet. Java 8 is what most companies run, and while not great, it's decent. Anything older than Java 8 should be scoffed at.

You should install both Java 8 and Java 11 on your machine.

It's good to know that Java comes in several flavours: A JDK (Java Development Kit), that you use to *develop* Java applications, and a JRE (Java Runtime Environment) that is used to *run* Java applications. When you compile a Java application, you don't end up with a native binary - like you would get when compiling a C or rust application. Instead, you get a bunch of `.class` files, which are an intermediate representation. These class files contain instructions called _byte code_, and byte code is portable. A JRE contains a JVM (Java Virtual Machine), which is an application that executes `.class` files. A JVM is platform-specific and will optimize the execution of `.class` files for the platform it runs on.

So you can compile your code once to `.class` files and run it on multiple platforms. This is convenient, although certainly not a game-changer.

Java was created by Sun, which was acquired by Oracle several years ago. More recently, Oracle stopped providing a free (well, it's still free but you're not allowed to use it commercially) JDK, but donated most of the JDK code to the OpenJDK project, which now provides free JDKs.

So for Java 8, you can still get a fine JDK from Oracle, and for Java 11, you should get it from OpenJDK.

Besides Oracle and OpenJDK, there are other vendors of JVMs. For example, Amazon created Corretto. For our purposes, The Oracle JDK for Java 8, and the OpenJDK one for Java 11 will work fine.

For Java 8, download the JDK from Oracle: https://www.oracle.com/technetwork/java/javase/downloads/index.html

For Java 11, the easiest way is to use

    brew cask install java

## Install jenv

Now that you have multiple Java versions on your machine, you need a convenient way to switch between them. Because some software you'll write with Java 11, and some other with Java 8.

`jenv` is a tool that helps you with that. It switches the symlink of your `java` and `javac` binaries to the version that you choose, and can also set the `JAVA_HOME` environment variable, which some processes use.

Install with:
    brew install jenv

Afterwards, you can run:

    jenv versions

This will list the Java versions available on your machine. (Maybe you need to run `jenv rehash` after you installed a new Java version).

Now you can either set your version globally by using

    jenv global 1.8

or set it locally, meaning only for the current directory. This is especially convenient in case you have one project that needs a different java version. Setting a local version with `jenv local` will create a `.java-version` file in the directory, and jenv will automatically configure your Java version every time you enter that directory in your shell.

Fun fact: Until Java 8, the official version was 1.8. So , As of 9, they realized that major versions were more appropriate, so when you list your versions with `jenv versions`, you should see at least `1.8` and `11`.

### Trying it out

You should be able to do something like the following in some directory, to verify that you have two working Java versions

    ➜  tmp jenv local 11
    ➜  tmp java -version
    openjdk version "11" 2018-09-25
    OpenJDK Runtime Environment 18.9 (build 11+28)
    OpenJDK 64-Bit Server VM 18.9 (build 11+28, mixed mode)
    ➜  tmp jenv local 1.8
    ➜  tmp java -version
    java version "1.8.0_144"
    Java(TM) SE Runtime Environment (build 1.8.0_144-b01)
    Java HotSpot(TM) 64-Bit Server VM (build 25.144-b01, mixed mode)

Note, the `➜` comes from my ZSH shell, but any other shell will be fine as well.

## Install Intellij

You can program Java without an IDE, and if you choose to use an IDE, you can pick from several good ones.

But for this set of exercises, use Intellij. The community edition will work just fine.

## Install Maven

Maven is the most widely used build tool for Java projects. It does - among other things - the following things for you:

 * Dependency management. It downloads Java libraries that you want to use from library repositories.
 * Invoking the Java compiler with the right set of arguments and source file locations.
 * Running the tests of your application.
 * Generating the project documentation
 * Packaging your application
 * Publishing your library to a repository

Maven has a plug-in architecture, and with plugins it can do a ton more. We'll run into several of them later.

To use Maven, you write a POM (Project Object Model) file, which describes your project. The POM file is an XML file. Many Java IDE's (including Intellij) understand POM files as well, and can use it to also understand how your project is setup.

This is extremely convenient: Maven can use the POM file in headless environments (such as a Jenkins machine) to build your project, and your IDE can also use the POM file to learn how your project is supposed to work, which dependencies it needs, and also run your application.

Your Maven POM file should be checked into Git, so that your colleagues can use the same POM file. Any IDE specific configuration, like Intellij's `.iml` files should be excluded from repositories! Each team member should generate his own IDE config from the Maven POM file. This gives the best project portability.

So install maven! Using brew:

    brew install maven

## Putting it all together

TODO
