> **What is Maven?**

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
