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
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Screenshot%202023-03-03%20094318.png?raw=true">  

Once downloaded, the installer will look like below. Simply launched the installer and follow the instruction.   
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/jdk%20installer.png?raw=true">  

### 1.2 Installing Node.js 
For this installation, select the `Windows Installer (.msi)` and the respective window operating system. In this video, we will be going with 64-bit installer.  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/node.js%20web.png?raw=true"> 

Now that you have downloaded it, launch the installer, and follow the instruction.  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/node.js%20installer.png?raw=true">   

### 1.3 Installing Yarn
Yarn itself is not a program. Yarn is a programming package manager, that is already included in `Node.js` but is not active by default. With our current version of Node.js, simply launch a `Command Prompt` window as an admin. Then proceed to type/copy the code line below: 
``` 
corepack enable
```
This will enable Yarn for us to install `NeoDash`. 
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Enabling%20corepack%20and%20checking%20yarn.png?raw=true"> 

### 1.4 Installing `Git`
For windows, you will have to navigate to `Git` download page linked above. Once there, from the section `Standalone Installer`, select the appropriate version for your computer. In this case, we will be going with the `64-bit Git for Windows Setup`.  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Git%20web.png?raw=true">  
After launching the installer, follow the instruction. 
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Git%20installer.png?raw=true">  

## Step 2: Installing `neo4j` server community edition and APOC core 
### 2.1 Installing `neo4j` server community edition 
Go to the following link to download the appropriate [neo4j server community edition](https://neo4j.com/download-center/#community)  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Neo4j%20community%20server%20web.png?raw=true">   

After downloading the file, locate the location you want to deploy the server, and extract the zip file there. In this case, we are choosing the D: drive. We will be calling this the `NEO4J_HOME` folder. The result will look like this:  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images\Post%20extraction.png?raw=true">     

### 2.2 Installing APOC core 
Since our work will also be using APOC for functions and queries that would be more convenient, we will be installing APOC core. This file is already available in the `labs` folder in `NEO4J_HOME`.  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Apoc%20in%20here.png?raw=true">  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Apoc%20file.png?raw=true">

Simply copy it over to `plugins` folder, and it will be available the next time you launch `neo4j`.  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Apoc%20now%20available.png?raw=true">

### 2.3 Configurating `neo4j` and `windows` for remote connection
#### 2.3.1 Configuring `neo4j` for remote connect
In order to connect to `neo4j` from outside, we must configure the program to listen to inbound connection request. First, you must access the `conf` folder in `NEO4J_HOME`:    
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Access%20conf.png?raw=true"> 

Then, open the neo4j conf with any program that can be used to edit it. In this example, we will be using `Visual Studio Code`:  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Open%20neo4j%20conf.png?raw=true"> 

Now locate these lines and delete the `#` before the line. Becareful not to accidentally pull the code into a different line.   
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Uncomment%20these%20for%20connection.png?raw=true"> 

#### 2.3.2 Configuring `Windows Defender Firewall`  
As of now, you have enable `neo4j` to respond to call for it from outside, but you still need to configure window's own firewall: `Windows Defender Firewall`.  
1. Open `Windows Defender Firewall`  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Opening%20windows%20defender%20firewall.png?raw=true"> 

2. Access `Advance settings`  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Advance%20settings.png?raw=true"> 

3. Go to `Inbound Rules`, then select `New rules` on the right side   
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Inbound%20rules,%20new%20rules.png?raw=true"> 

4. Here, you have to choose connecting through port    
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Port%20.png?raw=true"> 

5. Choose connection type `TCP` and type in port number `7474`. This is the default http port for neo4j. It is also the port noted in the section above when you delete the `#` above.  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/tcp%20port%207474.png?raw=true">

6. Now choose `Allow the connection`
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Allow%20connection.png?raw=true">

7. Select all options here
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Select%20all%20option.png?raw=true">

8. Lastly, name the port opening, so we can find it again in the future. For `neo4j`, we name it `neo4j http`. 
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Name%20port%20opening.png?raw=true">

9. Now we have to repeat step 3-8 again, but for another rule to enable `neo4j bolt`, and `NeoDash` to connect. Below are the two steps 5 and 8, where there is a difference in the process. In each respective rules, their ports are:
    - `neo4j bolt`: `7687`  
    - `NeoDash`: `3000`  

<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Neodash%20port.png?raw=true">  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/name%20neodash%20port.png?raw=true">  

## Step 3: Installing `NeoDash`
Before we continue to launch `neo4j`, we will also be downloading a dashboard builder that's built for `neo4j`. `NeoDash`, however, is a bit more complicated to install, as it is not just a folder, but a GitHub repository. To install, follow the steps below:  
1. Launch `Git CMD`  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Git%20CMD%20for%20install.png?raw=true">   

2. Navigate to where you want to install `NeoDash`. In this guide, we will be using the parent folder of `NEO4J_HOME`.   
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Navigate%20to%20parent%20folder%20of%20neo4jhome.png?raw=true">   

3. Type/copy the code below:
```
git clone https://github.com/neo4j-labs/neodash 
```  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Cloning%20neodash.png?raw=true">    

4. Once the progress is done, type/copy the following code:  
```
yarn install
```
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Yarn%20installed%20neodash.png?raw=true">  

You have now installed `NeoDash`, but you have not finished setting it up yet. 
Now navigate into the folder with this command  
```
cd neodash
```
And run the command again to set up `NeoDash` dependencies.  
```
yarn install
```
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Yarn%20installed%20neodash%20dependancies.png?raw=true">  

Now `NeoDash` is fully installed and ready to be used.

## Step 4: Launching and navigating
At this step, you should have everything ready to launch and use.

For any one to access neo4j from outside but on the same network, you will need to access through the computer's `IP address`. In order to do so, open a `Command Prompt` window, and copy the following code:  
``` 
ipconfig
```
Now, locate this line, and the entire corresponding number on the right hand side is you `IP address`
(ipconfig)

### 4.1: Launching neo4j:
To launch `neo4j`, navigate to the `bin` folder inside the `NEO4J_HOME` folder in `Command Prompt`, then copy this code below:  
``` 
neo4j console
```  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/neo4j%20server%20launched.png?raw=true"> 

`Neo4j` can then be accessed in a browser at the following address: `IP address:7474`.  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/neo4j%20browser%20launch.png?raw=true">  

You can then choose how to access `neo4j` browser, here we chose the method `username/password`. For the first time, we will be using the default username: `neo4j` and password: `neo4j` to access the first time.  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/neo4j%20usr%20and%20pass.png?raw=true"> 

You will be prompted to change your password. This username and password is what you will use everytime you access neo4j again.
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Provide%20new%20password%20for%20user%20neo4j.png?raw=true"> 

### 4.2: Importing data files:
Usually, you need to use data outside of what `neo4j` can offer. In order to do so, you will need to navigate to your `NEO4J_HOME` folder. Once there, navigate to `import` folder, and put the data file there.   
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Inserting%20files%20into%20import.png?raw=true"> 
The data is now ready to be used.

### 4.3: Launching NeoDash:
Similar to launching `neo4j`, you need to use `Command Prompt` to navigate to the folder where you have `NeoDash` cloned.  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Two%20command%20prompt.png?raw=true">

Once there, copy the following code:  
``` 
yarn run dev
```  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/neodash%20is%20now%20online!.png?raw=true">


This will run `NeoDash`, and you can access it by going to `IP address:3000` on your browser. Once there, you will be shown this screen:  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Neodash%20now%20available.png?raw=true">

Simply click `NEW DASHBOARD`, and you will be taken to this screen: 
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Neodash%20connect%20to%20neo4j.png?raw=true">

You need to change the following:
- Connection: bolt
- Port: 7687
- Username: neo4j
- Password: the password you created above
Then, click `CONNECT`, and you will be connected and your dashboard is ready to use.

### 4.4 Load a pre-designed dashboard:

In order to load a pre-designed dashboard, go to `Load Dashboard` on the left.  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Load%20dashboard.png?raw=true">    
Copy and paste a dashboard content here, as such:  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Copy%20dashboard.png?raw=true">  
Click `LOAD DASHBOARD`, and the dashboard is now available.  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Pre-designed%20dashboard.png?raw=true">  


## Step 5: Closing `neo4j` and `NeoDash` after done.

### 5.1: Closing `neo4j`:
In the `Command Prompt` that is running `neo4j`, simply press `CTRL`, hold, and `C`, to close `neo4j`.  
You might be prompted with this message:  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Closing%20neo4j.png?raw=true">    
Type `y` or `Y` to close, and `n` or `N` to cancel closing. Afterward, you should see this message:  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Terminated%20neo4j%20and%20close.png?raw=true">    
That means `neo4j` has successfully closed, and you can close the browser tab and the `Command Prompt` now.

### 5.2: Closing `NeoDash`:
Similar to above, in the `Command Prompt` that is running `NeoDash`, simply press `CTRL`, hold, and `C`, to close `NeoDash`.  
You might be prompted with this message:  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Closing%20neodash.png?raw=true">    
Type `y` or `Y` to close, and `n` or `N` to cancel closing. Afterward, you should see this message:  
<img width="640" alt="image" src="https://github.com/agiga-quanta/neo4j-server-installation-and-plugins-windows/blob/main/images/Terminated%20neodash%20and%20close.png?raw=true">     
That means `NeoDash` has successfully closed, and you can close the browser tab and the `Command Prompt` now.That means `neo4j` has successfully closed, and you can close the browser tab and the `Command Prompt` now.
