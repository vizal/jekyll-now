---
layout: post
title: How To Install  .NET Core 1.1 on Ubuntu 16.04
---

### Introduction

Since it release .NET Core 1.0 on June 2016, it get a lot attention for software development. It runs on Windows, Mac, and several flavors of Linux including RedHat Enterprise Linux and Ubuntu. It supports C#, VB, and F# and modern constructs like generics, Language Integrated Query (LINQ), async support and more. The Core Runtime, libraries, compiler, languages and tools are all open source on GitHub where contributions are accepted, tested and fully supported.

Now we are going to install .NET Core on Ubuntu 16.04 machine

## Prerequisites

Before you begin this guide you'll need the following:

- A clean install Ubuntu 16.04 droplet
- A root access or sudo previledge

## Step 1 — Add the .Net apt-get feed
In order to install .NET Core on Ubuntu, you need to first set up the apt-get feed that hosts the package you need.

```command
sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893
```
```
[secondary_label Output]
Executing: /tmp/tmp.m1g2ZTmpqa/gpg.1.sh --keyserver
hkp://keyserver.ubuntu.com:80
--recv-keys
417A0893
gpg: requesting key 417A0893 from hkp server keyserver.ubuntu.com
gpg: key 417A0893: public key "MS Open Tech <interop@microsoft.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
```
You need to  update your repository
```command
 sudo apt-get update
```
## Step 2 — Install .NET Core SDK

.NET Core 1.1 is the latest version. To install .NET Core 1.1 on Ubuntu  simply use apt-get.

```command
sudo apt-get install dotnet-dev-1.0.0-preview2.1-003177
```

## Step 3 — Create our first app

Create our first app. We will create the simplest one: console app
```command
mkdir hello_world
cd hello_world
dotnet new
```
For first time creating, You will find output similar as follow
```
[secondary_label Output]
Welcome to .NET Core!
---------------------
Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to see available commands or go to https://aka.ms/dotnet-cli-docs.
Telemetry
--------------
The .NET Core tools collect usage data in order to improve your experience. The data is anonymous and does not include commandline arguments. The data is collected by Microsoft and shared with the community.
You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT environment variable to 1 using your favorite shell.
You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-telemetry.
Configuring...
-------------------
A command is running to initially populate your local package cache, to improve restore speed and enable offline access. This command will take up to a minute to complete and will only happen once.
Decompressing 100% 5805 ms
Expanding 100% 28544 ms
Created new C# project in /home/sammy/hello_world.
```
You will find 2 files inside your project
```
Program.cs  project.json
```
## Step 4 — Let we edit our first app
```command
vi Program.cs
```
```
[label Program.cs]
using System;

namespace ConsoleApplication
{
    public class Program
    {
        public static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```
## Step 5 — Restore
We need to restores the dependencies and tools of a project.
```command
dotnet restore
```
```
[secondary_label Output]
log  : Restoring packages for /home/sammy/hello_world/project.json...
log  : Writing lock file to disk. Path: /home/sammy/hello_world/project.lock.json
log  : /home/sammy/hello_world/project.json
log  : Restore completed in 1564ms.
```
## Step 6 — Run  the app
Now, time to fire up our first app.
```command
dotnet run
```

```
[secondary_label Output]
Project hello_world (.NETCoreApp,Version=v1.1) will be compiled because expected outputs are missing
Compiling hello_world for .NETCoreApp,Version=v1.1

Compilation succeeded.
    0 Warning(s)
    0 Error(s)

Time elapsed 00:00:01.9442921


Hello World!
```
## Conclusion
That's it! Now you have a .Net Core server ready
