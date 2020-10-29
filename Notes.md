You can install it from 

Get from https://sdkman.io

SDKMAN! is a tool for managing parallel 
versions of multiple Software Development Kits on most Unix based systems. 

Download with   

curl -s "https://get.sdkman.io" | bash  
sdk install gradle   

We define tasks in our gradle script , task such as    
- build
- clean etc  
We can also add plugins

Next we run the appropriate task 

task 'hello'{
    doLast{
        println "Hello Gradle"
    }
}

We can run this as   

gradle hello  

Using plugin
apply plugin: 'java'

gradle tasks --all
gradle -i build


To use the system Gradle
gradle -wrapper
./gradlew build
gradle build : now using gradlew   

Gradle mostly consists of  
- Projects 
- Tasks

Build has one or more projects 
- Project has one or more tasks

Build Phases
Initialization
Configuration
Execution {doFirst (at the start of the task execution) , doLast (at the end of the task executiion)}

Task dependencies

task hello{
    doFirst{
        println "Hello Gradle First"
    }

    doLast{
        println "Hello Gradle Last"
    }
}

task world {
    
    dependsOn hello
    
    doLast{
        println(" , welcome to my world")
    }
}

The hello task runs first then the world task runs.

PLUGINS
Extends project's capabilities
  - Well-known plugins
  - Community plugins

plugins {
    id 'java'
    id "org.flywaydb.flyway" version "6.3.2"
}

Then run   
gradle task --all  
This downloads all the flyway libraries and task into our project

Run mulitple task at once 
gradle clean build
gradle clean build -i (give information on the build)

To change the version number of the jar using gradle we just specify this in our gradle 
configuration


version = "1.1-SNAPSHOT"

SOURCE SET 
Gradle build depends on Java source code convention , if our project has a different
structure then we need to tell gradle where to find the source code then

sourceSets{
    main{
        java{
            srcDir ''
        }
    }
    test{
        java{
            srcDir ''
        }
    }
}