# keycloak-theme-dissco

This is a custom theme for the DISSCO keycloak installations

## Building instructions:

This project does not contain the actual code, just the project-specific configuration/overrides

Building is handled by the github action "releases". 

A build is triggered whenever a tag is added. 

Please find all built releases in the project's github [releases page](https://github.com/grnet/keycloak-theme-dissco/releases) 

## How to install the theme into Keycloak:

Create the following folders:
```
$KEYCLOAK_BASE/modules/system/layers/keycloak/org/keycloak/keycloak-theme-vanilla
$KEYCLOAK_BASE/modules/system/layers/keycloak/org/keycloak/keycloak-theme-vanilla/main
```

and add into the folder "main" 
* the built jar keycloak-theme-vanilla/target/keycloak-theme-vanilla.jar
* the keycloak-theme-vanilla/module.xml from the source (this one) base folder

so you should end up with the following structure in
$KEYCLOAK_BASE/modules/system/layers/keycloak/org/keycloak/keycloak-theme-vanilla

```
keycloak-theme-vanilla
└── main
    ├── keycloak-theme-vanilla.jar
    └── module.xml
```

Following the above, we should also let wildfly server and keycloak to load this module as well. 
So, open file $KEYCLOAK_BASE/standalone/configuration/standalone.xml

Find the ```<subsystem xmlns="urn:jboss:domain:keycloak-server:1.1">``` node.

* Add the 
```<provider>module:org.keycloak.keycloak-theme-vanilla</provider>```
into the ```<providers>``` list
* Add the 
    ```
    <modules>
        <module>org.keycloak.keycloak-theme-vanilla</module>
    </modules>
    ```
    into the ```<theme>``` block



