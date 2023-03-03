# A detailed guide to installing `neo4j` server community edition on windows.
This is a guide to installing `neo4j` server on windows 10, how to launch and connect to your own `neo4j` server, and how to install and use plugins with them. Throughout this guide, we will be downloading many programs and tools too:  
    - [Node.js](https://nodejs.org/en/download/)  
        -     [Yarn](https://yarnpkg.com/getting-started/install)  
    - [Git](https://git-scm.com/download/win) for windows  
    - [Java SE developer kit 17](https://www.oracle.com/java/technologies/downloads/#jdk17-windows)   
    - `NeoDash` (complicated, will be instructed below)

## Step 1: Installing prerequisites for `neo4j` server and NeoDash:
Our order of installation will be:  
1. Java developer kit 17 (JDK)   
2. Node.js  
3. Yarn  
4. Git  

### 1.1 Installing Java developer kit 17 (JDK) 
To start with, begin downloading JDK from the link given. The one you want to download is the `x64 Installer`, where its file extension ends with `.exe`.   
(Show pic of page with circle marking)  
Once downloaded, launched the installer and follow the instruction.   
(Show pic of the installer)  

### 1.2 Installing Node.js 
For this installation, select the `Windows Installer (.msi)` and the respective window operating system. In this video, we will be going with 64-bit installer.  
(Show pic of the page)  
Now that you have downloaded it, launch the installer, and follow the instruction.  
(Show pic of installer)  

### 1.3 Installing Yarn
Yarn itself is not a program. Yarn is a programming package manager, that is already included in `Node.js` but is not active by default. With our current version of Node.js, simply launch a `Command Prompt` window. 
(Show window)  
Then proceed to type/copy the code line below: 
``` 
    corepack enable
```
This will enable Yarn for us to install `NeoDash`. 


### 1.4 Installing `Git`
For windows, you will have to navigate to `Git` download page linked above. Once there, from the section `Standalone Installer`, select the appropriate version for your computer. In this case, we will be going with the `64-bit Git for Windows Setup`.  
(Show window)  
After launching the installer, follow the instruction. 

## Step 2: Installing `neo4j` server community edition and APOC core 
### 2.1 Installing `neo4j` server community edition 
Go to the following link to download the appropriate [neo4j server community edition](https://neo4j.com/download-center/#community)  
(Show pic of the choice here - Windows Executable)  

After downloading the file, locate the location you want to deploy the server. In this case, we are choosing the D: drive. We will be calling this the `NEO4J_HOME` folder.   
(Show pic of zip file in D:)

Once selected, launch a window of `Command Prompt`, and navigate to your `NEO4J_HOME`. You will be using the console to activate, install additional plugins, and to stop the server once you are done.  

### 2.2 Installing APOC core 
Since our work will also be using APOC for functions and queries that would be more convenient, we will be installing APOC core. This file is already available in the `labs` folder in `NEO4J_HOME`.  
Simply copy it over to `plugins` folder, and it will be available the next time you launch `neo4j`. 

## Step 3: Installing `NeoDash`
Before we continue to launch `neo4j`, we will also be downloading a dashboard builder that's built for `neo4j`. `NeoDash`, however, is a bit more complicated to install, as it is not just a folder, but a GitHub repository. To install, follow the steps below:  
1. Launch GitXXX  
(show pic)  
2. Navigate to where you want to install `NeoDash`. In this guide, we will be using the parent folder of `NEO4J_HOME`.   
(show pic)  
3. Type/copy the code below:
```
    git clone https://github.com/neo4j-labs/neodash 
```  
(show pic)  
4. Once the progress is done, type/copy the following code:  
```
    yarn install
```
(show pic)  
Now `NeoDash` is fully installed and ready to be used.

## Step 4: Launching and navigating
At this step, you should have everything ready to launch and use.

### 4.1: Launching neo4j:
To launch `neo4j`, navigate to the `bin` folder inside the `NEO4J_HOME` folder in `Command Prompt`, then copy this code below:  
``` neo4j console```  
`Neo4j` can then be accessed in a browser at the following address: `localhost:7474`.  
(show pic)  

You can then choose how to access `neo4j` browser, here we chose the method `username/password`.  
(show pic)  

### 4.2: Importing data files:
Usually, you need to use data outside of what `neo4j` can offer. In order to do so, you will need to navigate to your `NEO4J_HOME` folder. Once there, navigate to `import` folder, and put the data file there.   
(Show pic)  
The data is now ready to be used.

### 4.3: Launching NeoDash:
Similar to launching `neo4j`, you need to use `Command Prompt` to navigate to the folder where you have `NeoDash` cloned.  
(Show pic)

Once there, copy the following code:  
``` yarn run dev```  
This will run `NeoDash`, and you can access it by going to `localhost:3000` on your browser.   
(Show pic)

Once there, you will be shown this screen:  
(Show pic)

Simply click `NEW DASHBOARD`  
(Show pic)

When shown this screen:  

You need to change the following:
- Connection: Bolt
- Port: 7867

Then, click `Connect`, and you will be connected and your dashboard is ready to use.

### 4.4 Load a pre-designed dashboard:

In order to load a pre-designed dashboard, go to `Load Dashboard` on the left.  
(Show pic)  
Copy and paste a dashboard content here, as such:   

Click `LOAD DASHBOARD`, and the dashboard is now available.

## Step 5: Closing `neo4j` and `NeoDash` after done.

### 5.1: Closing `neo4j`:
In the `Command Prompt` that is running `neo4j`, simply press `CTRL`, hold, and `C`, to close `neo4j`.  
You might be prompted with this message:  
(Show pic)  
Type `y` or `Y` to close, and `n` or `N` to cancel closing. Afterward, you should see this message:  
(Show pic)  
That means `neo4j` has successfully closed, and you can close the browser tab and the `Command Prompt` now.

### 5.2: Closing `NeoDash`:
Similar to above, in the `Command Prompt` that is running `NeoDash`, simply press `CTRL`, hold, and `C`, to close `NeoDash`.  
You might be prompted with this message:  
(Show pic)  
Type `y` or `Y` to close, and `n` or `N` to cancel closing. Afterward, you should see this message:  
(Show pic)   
That means `NeoDash` has successfully closed, and you can close the browser tab and the `Command Prompt` now.That means `neo4j` has successfully closed, and you can close the browser tab and the `Command Prompt` now.