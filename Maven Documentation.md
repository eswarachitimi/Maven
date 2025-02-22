#### 1. What is Maven?

Maven is a project management build automation tool. 
Building a project means 
- compiling the source code
- running the tests which could be unit tests as well as integration tests
- packaging the compiled code into jar files bundling these jar files into a web archive or a war file

Maven uses convention over configuration.

that is if we follow a certain project structure when we create our projects such as here is the base project directory under it source main Java source folder has a
child folder called main under it we have Java this is where all our source code should go source main SRC main resources is where any resources such as property files or XML configuration that
we use in our Java classes should go SRC test Java is where all our unit
and integration tests should be placed and finally SRC test resources is where all the property files or XML


configuration that we use on our tests should be placed once we use this folder structure we can simply execute a maven command such as maven install and maven
will compile the source code under the SRC main Java run the unit tests under SRC test Java and if the tests pass it will bundle or package the compiled

classes into a jar file if it is a standalone java application if it is a web application it will bundle it into a
war file and it can also deploy the war file onto a web application. This folder structure will be slightly different for a standalone Java project
for a web application and for different

types of projects but the beauty is that we need not create these folders manually for each type of project maven
provides several archetypes think about these archetypes as templates we can

execute a command with an archetype and it will create the folder structure thestandard folder structure required by maven for us there are different types
of archetypes like standalone, webapp, EAR etc another additional advantage is that all the popular ides such as Eclipse Intelli J come with inbuilt support 
these archetypes we can create the project's the different types of maven projects from within an IDE and also run and execute our build from within
eclipse from within intelliJ.

#### 2. Why is Maven ?

The million-dollar question why use maven in addition to its convention over configuration maven offers several other
advantages such as a common interface for the developers before maven if we as developers had to work on an open source project or even another project within our company or enterprise we had first understand how to build that project because each team might have
their own way of configuring the build

when they use other tools other than maven which is both time consuming and hectic that is where maven simplifies
things by simply grabbing the project from the source control we can execute maven clean install and the project will be built for us because all the
developers now will follow one standard project structure which is specified by maven secondly maven is not just a build management tool it can also manage
dependencies that is if our project

depends on other projects from within the organization or even in the open source world maven can grab those
projects download those dependencies and it will use them to compile our source code run the test and even bundle these
dependencies into war files and EAR files.

Maven is this a concept called repository where it puts all the artifacts and its plugins and it will download them on the fly so if a project needs a particular dependency in the
open source world or even within our firm those dependencies will be pulled from this repository and when we build
our projects our projects can also be pushed into these repositories these repositories can be on the Internet there is a public maven repository where all the open-source projects are available as jars many companies
maintain their own internal repository

which runs on their servers that way they can have control on what jar files or what projects who open source projects the teams within
that company can use and also they can share their artifacts within the company by pushing them to this repository here

I have a Bharath.jar which is my own jar file once it is pushed to this repository any other team which wants to
use it can simply pull it or added as a dependency and start using it more on repositories later on reuse maven is very lightweight when we download and
install it it grabs whatever it needs as plugins it uses a plug-in model for example a compiler plugin surefire plugin that can run unit tests as well
as the ws import plugin which can be used to generate stubs from a web services WSDL file and many other
plugins are there so maven when uses a

plug-in model through which these can be reused across projects and even if a upgrade happens to where the compiler or the Surefire plugin or any other plug-in
maven will automatically download the latest plug-in for example this surefire plug-in will be downloaded by maven only when we run our very first unit test
after that it will not download it until this plugin changes that is the beauty of using a plug-in model reuse as well as if i upgrade happens it can pull it
on the fly with all these advantages maven of course is one of the best build management dependency management and completely a project management tool
that should be used.

#### 3. what is pom.xml file?

When we execute a maven command to build a project the maven command looks for the pom dot XML under the project for information open this pom dot XML and it has a lot of information such as what type of project it is in this case it is
a jar project it could be war or several other types that are available the name of the project the artifact ID as well

as a user friendly name and a URL if there is one associated with this project this is optional this tells which company owns this product or
project www.bharaththippireddy.com HTTP colon two forward slashes similarly the group ID the artifact ID the packaging and version these four fields are call maven coordinates more on this in
lecture later on last but not the leastthe dependency section is where we add

all the libraries that our project needs in order to function whatever third-party libraries or libraries from
within other teams or projects with our enterprise can be included here as dependencies the archetype that we have used to generate this project has
included the J unit dependency because we need to write unit tests any Java project should have unit tests that is
the reason it included J unit library in here we can add any number of libraries within the dependencies element multiple

dependencies can be added and you willbe doing that in lectures later on this is the simplest of maven files that you
can see you are going to modify this mail file later on and create much more complex maven files.

#### 4. Maven Life Cycle Phases

when you ran the maven install command we have asked me when to execute a life cycle phase maven has multiple lifecycle phases starting from process resources compile test package and many more for brevity reasons I have skipped some
phases in between as well as after package when you execute a maven package maven will run all the phases prior to
it and then that particular phase if you run the test it will run process

resources first then compile then the test phase we as developers can execute maven package and we need not specify maven process resources space compile
space test 10 space package each phase life cycle phase is associated with one or more goals for example the process resources is associated with a resources plugins resources goal this is the one which does the actual work the phases
are something maven internally knows but they don't do any work on their own they are simply a part of the life cycle

actual work is done by the plugin goals associated with those phases we can have multiple goals associated with a face but usually there is only one goal the
compile phase is associated with a compiler plugins compiler goal test with surefire test goal surefire is the plugin which can run the test package
jar colon jar and so on when you execute a particular goal instead of giving Maven install you can also say maven

space surefire colon test maven will then execute all the phases before the phase with which this goal is associated surefire test is associated with the test phase so maven will execute process resources and its associated goals
compile its associated goal and then finally it will execute the surefire test code similarly if you execute jar all the phases prior to it will be executed and their
associated goals will be executed then the jar goal will be executed depending

on the type of the project the association might change if you are building a stand-alone java project the package phase can be associated with
jar colon  jar and if it is a web application project maven dynamically associates it with a war colon war goal
as a developer once you know that this is how the phases and goals work you can work on any java project developed by
any other team and easily build it.

#### 5. Maven Plugins

In this lecture, we will learn the two key concepts of maven namely the maven plugins and goals a maven plugin is a collection of one or more goals you have
already used a couple of goals when you created the project and built it the generate goal from the archetype plugin and the install goal from the install

plugin a goal can be a specific task which we usually run independently or it can be a part of a bigger build here the compile if we use it independently it
compiles our Java classes and tests it can also be a part of a bigger build wherein we compile the source code and the test and then the test goal will run
which will run our tests which is from the Surefire plugin and the package will


package our compiled classes if the tests pass into jar files or if it is a web application it will package it into a war file these goals can also take
parameters when you have used the archetype generate goal we have specified or mentioned several parameters such as group ID artifact ID etc and they can also have default
values for these parameters the generate

goal from archetype plugin if you do not pass the archetype artifact ID it will assume maven archetype quick start as a default value and create a project of
that type we refer to a goal using the plugin ID colon the goal ID party type is the plugin ID and generate is the goal ID by itself maven does not know
how to create a project compile it package it etc it uses the plugins like compiler jar to get the work done every
maven project gets a set of these

default plugins through the settings through the parent settings but we can override them by defining them in our
pom dot xml for example later on in later sections you will be overriding the compiler settings by defining it in your pom dot XML and
it will switch the version to 1.8

#### 6. Maven Profiles

Build portability means the deployment engineer or a devops engineer or even a developer should be able to build the application across different environments without changing any configuration or by changing
a little configuration maven allows  build portability through its profiles for example when

we built an application that connects to a database or that consumes a web service this application needs a database connection information and the user name and password or it might need a web service url
to connect . And talk to a web service.

And these details will be different across different environments. On the Devon environment where the developer do the testing the database server might be different or
the web service application might be running on dev server.

So similarly the testing environment will have its own server or a database where the testing team has
the entire database and data.

And finally of course the production which will be accessed by the client will have we'll be running on a different database server or we'll host a web service on a different server and our app needs all
this information and across environments as we build our application. We need to change these when we  deploy our application.

If we are deploying on production we need to change the database information and point it to production.
Or we should change the web service url so that our application points to the production Server instead of reducing

this work and automating everything we can use profiles in maven and we create different profiles and based on which profile is currently activated and our application is built Maven will pick that information
and make it a part of our application so that it can be deploid.

So when we are building our application on Dev we will activate the dev profile and maven will pick the
configuration for the dev profile only those files that has the database information on the web service connection
information for dev.

Similarly if we activate the test profile it will pick the appropriate configuration information and
put it into the app. And same for Prod..

So this is how it will look like we'll have a profiles folder under which we can have dev as subfolder which will
have application.properties test and then prod as well and depending on which our profile is activated

the build will pick up that particular application.properties which will have the connection information.
So you're going to see Maven profiles how to activate them and much more in action in the next few lectures.

#### 7. Maven Scopes

Maven allows us to specify the visibility of our project dependencies using a scope element which scope
we use will impact on when those dependencies are available in the maven lifecycle for our project

their are total of  six dependencies starting with compile run time provided test system an import.
If we use the compile time scope then that those dependencies will be available during the project build.

That is when our class are compiled when our tests are compiled and the test are run and then our application
is run and by default if we don't specify any scope compile is the scope that will be used by Maven next is provided.

These are the dependencies that are required during the build test and run but they are not required
to be exported meaning they need not be a part of our application when they are depliod For example if we

are building a web application then the servlet- API is required locally in our project when we compile
our classes when we run our test but it need not go into the war file or the web application when it is deploid to a server because. Servers or  application.
Containers or web containers.

Well how the servlet API jar that is the reason will mark a servlet API dependency has provided.
So any dependency that you don't want to export into a web application or into a enterprise application.
You mark it with scope called provided.

Next is runtime as the name itself says these dependencies maintain a runtime scope. These are available only for running the tests as well as our application.
They will not be available for compilation test scope as the name itself says.

Again these are available to compile our test and run the tests j-Unit is a very good example.
We don't need j-unit to compile our application source classes.
We need it or our application classes we need this for compiling our test as well as running the test system scope which is very less used.

It is not that popular but still system scope is similar to that offer a provided scope but instead of
an application container or a web container providing that dependency or that is not even pulled from a maven 

repositary we will copy this onto a subdirectory of our project and we will point when we use
the system scope will also provide a path to that particular dependency which is relative to our project usually.
So this is very rarely used.

But remember that if you want to point to a library which is not a part of a maven dependency and
not even provided by a web container then you will use the system scope and point to that external dependency.
Last but not the least import.

Again as the name itself says this is used on Pom based projects not Jar projects not war projects
put on Pom based projects.

I'll talk more about this dependency when I do a section on and I do a lecture on dependency management
later on.

To summarize the total six scopes in maven are compiled run time provided test  system an import
and depending on what scope you mark a dependency with it will affect the availability of their dependency
during the maven lifecycle for our projects.
