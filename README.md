[![Build Status](https://travis-ci.org/Fabszn/scaffolding-plugin-lagom.svg?branch=master)](https://travis-ci.org/Fabszn/scaffolding-plugin-lagom)

# Scaffolding-plugin for [Lagom - The Reactive Microservices Framework](http://www.lagomframework.com/)

# Purpose
The plugin is to ease the creation of new Lagom service nested in one lagom project.

Today, there is two ways for create a Lagom project.

First, start from scratch and create project by hand (create folder, create classes, files configuration, etc) or start from Lagom-java's project template activator. Second way makes things easier.

Ok but when your project has been generated by activator, you need to refactor the HelloWorld lagom service to give it the right name and right package name. Cool! now your project is ready to work. However, now, you need to create one (or more) service(s) then you start a copy/paste/rename party to create all new services.

Conclusion, you lose productivity while Lagom's framework should rise your productivity.

To fix this issue, I propose one plugin to generate entirely a new service by only one command :

```
sbt "newService "
```
When this command is finished, you can apply runAll task to start your microservices system. Obviously, by default, your service will do nothing. But this plugin will bring you at the moment where you start design your API in Lagom interface.

Actually, service is generated with Java language.

# How to setup the plugin

Today the plugin is not deployed on one dependency repository. the unique way to use it, is to clone the repository and use the following command on sbt :

```
sbt publishLocal
```

Now the plugin is avalaible in your local repository.
Fill the plugins.sbt file (under project directory by convention) with the following statement :
```
addSbtPlugin("com.lightbend.lagom.sbt" % "scaffolding-plugin-lagom" % "[current version of plugin]")
```

then, enable the plugin at root project level, in your *build.sbt* file as follow :

```
lazy val root = (project in file("."))
    .enablePlugins(LagomScaffoldingPlugin)
```

Setting up is now finished. you should find new task named : *newService*

# How use the plugin

Using is very simple. at the sbt prompt use the following command :
```
> newService [ServiceName]
```

By default, the plugin will used the **organisation** setting  defined into the project. You can override it by used the parameter : *org:*
```
> newService [ServiceName] org:xx.xx.xx
```

That's all folks !
