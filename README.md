<div id="top"></div>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]


<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/troopek/TropX">
    <img src="images/logo.png" alt="logo" width="80" height="80">
  </a>

<h3 align="center">TropX</h3>

  <p align="center">
    The best penetration testing and tech tools unified into one beatiful command line interface!
    <br />
    ·
    <a href="https://github.com/troopek/TropX/issues/new">Report Bug</a>
    ·
    <a href="https://github.com/troopek/TropX/issues/new">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
# About The Project

<img src="images/image.png" alt="image">

The best penetration testing and tech tools unified into one beatiful command line interface! Support for custom scripts, allows simple scripting with premade functions and variables. Customizable theme and settings page, along with decent support.

<p align="right">(<a href="#top">back to top</a>)</p>




<!-- GETTING STARTED -->
# Getting Started

Guide on how to obtain a local copy of TropX
**
## Installation
A local copy of TropX can be obtained using the `git clone` command

* Navigate to your terminal (I use Terminator)
* Navigate to the directory you want TropX saved
* Clone the repository using the git command
  ```sh
  git clone https://github.com/troopek/TropX 
  ```
* Navigate to the TropX folder
  ```sh
  cd TropX
  ```


## Setup
The setup can be automatically done by running the `setup.sh` file

* Run the `setup.sh` file with bash and follow along with the setup tutorial
  ```sh
  bash setup.sh
  ```

## Updates

You can update TropX to the newest version without losing any custom scripts and while also preserving your settings and other modified things. You can do this automatically by running the update.sh file.

* Firstly, navigate to your terminal (I use Terminator)
* Navigate to the directory where you cloned TropX
* Run the `update.sh` file with bash and wait until the proccess has finished
  ```sh
  bash update.sh
  ```
  
<p align="right">(<a href="#top">back to top</a>)</p>



<!-- USAGE -->
# Usage

Guide on how to use TropX efficiently and to it's fullest
* Firstly, run the `main.sh` file from the `TropX` directory.
  ```sh
  bash main.sh
  ```
* Afterwards you will be prompted to select out of a number of scripts and tools
* To select any script or option, you will have to input its corresponding number like `4` and then press `Enter`
* All tools and scripts will send you back to the main menu after executing

<p align="right">(<a href="#top">back to top</a>)</p>


<!-- Custom Scripts -->
## Custom Scripts

You can very easily add **Custom Scripts** to TropX to further personalize TropX, it supports multiple languages including **bash**, **python**, **javascript**, and even **C#**


### **Bash**

TropX has some default functions and variables to simplify the programming faction of custom scripts

---
* #### selectOptions 

* With `selectOptions` you can ask the user to select an option, the CLI equvalent of radio buttons 


  ```sh
  selectOptions "" "$current" "Select an Option" "Enter selection Here" "Try another selection" "Option1" "Option2" "Option3"
  ```
  
  *  `"" "$current"` Leave the first two arguments as shown
  *  `"Select an Option"` The next argument is the title for the option choices
  *  `"Enter selection Here" "Try another selection"` The next two are the `type here` text before the `>`, the second will be shown in case of an error
  *  `"Option1" "Option2" "Option3"` The rest are options which will be shown to the user, they can be passed singularly or in an Array
  * The ouput can be saved into a variable like so, where choice is the number corresponding to the option, so if you choose `Option2`, then `$SO` and also `choice` will be set to `2`. This extra step is recommended as sometimes the variable gets overwritten by this function getting run somewhere else and then its value will change to something completely diffrent and irrelevant.
    ```sh
    choice=$SO
    ```
  * The function has a built-in check for the selected option to confirm it is valid

---

* #### getInput
* With `getInput` you can get user input to save into a variable and use within your custom script

  ```sh
  getInput "" "$current" "Select an Option" "Type something useful" "file.txt"
  ```
  *  `"" "$current"` Leave the first two arguments as shown
  *  `"Select an Option"` The next argument is the title for the option choices
  *  `"Type something useful"` The following argument is going to be the details for what the user is supposed to type
  *  `"file.txt"` Next is an example of what their input should look like
  *  To ensure that your user returns a *proper* and *useful* string, you can run it trough an until loop
  * The ouput can be saved into a variable like so, where choice is the number corresponding to the option, so if you typed in `foo`, then `$SI` and also `input` will be set to `foo`. This extra step is recommended as sometimes the variable gets overwritten by this function getting run somewhere else and then its value will change to something completely diffrent and irrelevant.
    ```sh
    input=$SI
    ```
  * In the below example im using getInput to obtain a valid path to a file
    ```sh
        getInput "" "$current" "File Path" "Please type in the relative or full path of the script" "Do not incldue a file extension" "file.txt"
    path=$SI

      until [ -f $path ] #this is a bash built-in way to check if a file exists
      do
        getInput error "$current" "File Path" "Please type in the relative or full path of the script" "Do not incldue a file extension" "file.txt"
        path=$SI
      done
    ```
  *  Within the loop, the first argument i passed to the function was error to indicate, do this also, as it indicates to the function, and the function to the user, that the input was not valid.
    
---

* #### message
* With the `message` function you can display a message to the user that remains until they press a key

  ```sh
  Message="Disclaimer: TropX is cool!"
  message "$current" "Message" "$Message"
  ```
  *  `"$current"` Leave the first argument as shown
  *  `"Message"` The next argument is the title for the message
  *  `"$Message"` The last argument is the variable in which the message is stored
    
---

* #### changeWImode
* With the `changeWImode` function, you can easily change the mode of your Wireless Interface
  ```sh
  changeWImode monitor
  # ...
  changeWImode managed
  ```
  * The only argument passed will be the mode you want to change the Wireless Interface to
  * The Wireless Interface used will be the one the user has saved in the settings
    
---

* #### changeMac
* With the `changeMac` function, you can easily change your Mac Address to either a random or specific one
  ```sh
  changeMac 
  # ...
  changeMac "00:d0:70:00:20:69"
  # ...
  changeMac reset
  ```
  * You can optionally pass an argument which will, if set to `reset`, set your Wireless Interface back to it's permanent default Mac Address, otherwise the argument will be the the Mac Address the Wireless Interface spoofs
  * If no argument is passed, a random Mac Address will be selected
  * The Wireless Interface used will be the one the user has saved in the settings
---

* #### $WI
* The `WI` variable holds the name of the Wireless Interface (e.g. `wlan0`)

---

* #### $PRIMARY & $SECONDARY
* The `PRIMARY` variable holds the color code for the primary (*no shit*) color
* The `SECONDARY` variable holds the color code for the secondary (*no shit again*) color
* Make sure to escape it like such
  ```sh
  echo -e "${PRIMARY}Hello ${SECONDARY}World!"
  ```
* Even though it is not neccesary to use these variables it is highly recommended so your script stays in sync with the user's settings

---
### **python, javascript, and C#**
Sadly these languages do not have any premade functions **yet**!

---


## Setup
The custom script creation process

* To create a new Custom Script, firstly start TropX **(*No Shit*)**
* Afterwards, select `M` short for Manage Scripts
* Choose the first option `1` to create a new script
* Type in the script name and continue
* Select the way in which you want to provide TropX with the script and confirm

## Share your script
TropX is still looking for more tools and scripts!
* If you believe that you made a decent tool or script that you would like featured as a default, make sure to share it with us
* Firstly, head on over to the TropX directory in your file manager
* Then, head on over to the `custom_scripts` folder
* When there, locate the folder of the custom script you wish to upload
* Copy the `main.sh` file
* Upload it to this [Google Form](https://forms.gle/VS78nDGNCdn6jE5S7 "Upload Your Script Within This Form")

<p align="right">(<a href="#top">back to top</a>)</p>


<!-- ROADMAP -->
# Roadmap

View our Trello Roadmap: [Trello TropX](https://trello.com/b/GItUPVEs/tropx "Trello Roadmap for TropX")


See the [open issues](https://github.com/troopek/TropX/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- CONTRIBUTING -->
# Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- LICENSE -->
# License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- CONTACT -->
# Contact

eugene.chicevic@gmail.com

Project Link: [https://github.com/troopek/TropX](https://github.com/troopek/TropX)

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
# Credits
Big shoutout to all these people as their scripts helped make TropX possible, make sure to check them out!

* Netattack2 by Chrizater
* WifiSpammer by 125k
* Ducky Flasher by Hak5

<p align="right">(<a href="#top">back to top</a>)</p>


<!-- Compatibility -->
# Compatibility

* Linux Machines (Prefferably Kali)
* Windows (using [Cygwin](https://www.cygwin.com/setup-x86_64.exe))
* MacOS (shebangs only partially supported)

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- DISCLAIMER -->
# DISCLAIMER

I am not held responsible for any misdeeds done with the help of this tool, i provide it to you for educational purposes only. By using this tool you accept that i am not held responsible for any consequences your usage of my tool might yield.

<p align="right">(<a href="#top">back to top</a>)</p>


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/troopek/TropX.svg?style=for-the-badge
[contributors-url]: https://github.com/troopek/TropX/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/troopek/TropX.svg?style=for-the-badge
[forks-url]: https://github.com/troopek/TropX/network/members
[stars-shield]: https://img.shields.io/github/stars/troopek/TropX.svg?style=for-the-badge
[stars-url]: https://github.com/troopek/TropX/stargazers
[issues-shield]: https://img.shields.io/github/issues/troopek/TropX.svg?style=for-the-badge
[issues-url]: https://github.com/troopek/TropX/issues
[license-shield]: https://img.shields.io/github/license/troopek/TropX.svg?style=for-the-badge
[license-url]: https://github.com/troopek/TropX/blob/master/LICENSE.txt
