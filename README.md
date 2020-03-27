# Pierre's Sweet & Savory Treats

#### _Advanced databases and authentication independent project for Epicodus_

#### By: **Michelle Morin**, March 27 2020

## Description

This is a web application for Pierre's Bakery, to market his sweet and savory treats. This application includes user authentication via Identity and a many-to-many relationship between ``Treat``s and ``Flavor``s. A treat can have many flavors (e.g., sweet, savory, spicy) and a flavor can have many different treats (e.g., a sweet flavor could include chocolate croissants, donuts, cheesecake, etc.). Registered users that are logged into the web application are able to create, read, update, and delete treats and flavors, whereas anonymous users are only able to view lists of all treats and flavors and corresponding detail pages for each treat and flavor.

## Specifications:

| Specification | Example Input | Example Output |
| ------------- |:-------------:| -------------------:|
| If user visits '/' root route, the application displays a splash page with links to '/Treats' and '/Flavors', and '/Account' | user visits '/' route | application displays homepage |
| Application allows a user to register for an account with Identity | user clicks "login/register" option on splash page, then completes form at '/Account/Register' | application creates new user account and redirects to '/Login' |
| Application allows a registered user to login | registered user clicks "log in" option at '/Account' | application redirects to '/Account/Login' |
| Application allows a registered user to logout | registered user clicks "logout" option at '/Account' | application logs out of user account |
| Only registered, logged-in users are able to create, update, and delete flavors | user is not logged in and/or not registered and clicks "add flavor", "edit flavor", or "delete flavor" | user redirected to 'Account/Login' |
| Only registered, logged-in users are able to create, update, and delete treats | user is not logged in and/or not registered and clicks "add treat", "edit treat", or "delete treat" | user redirected to 'Account/Login' |
| If user visits '/Treats' route, the application displays all treats in the database, each clickable to view available flavors for that treat | user visits '/Treats' | application displays list of all treats in alphabetical order |
| If a registered user clicks "add new treat" link at '/Treats', the application redirects to a form ('/Treats/Create') for adding a new treat | registered user clicks "add new treat" | the application redirects to form at 'Treats/Create' |
| If user visits '/Flavors' route, the application displays all flavors in the database, each clickable to view available treats of that flavor | user visits '/Flavors' | application displays list of flavors in alphabetical order |
| If a registered user clicks "add new flavor" link at '/Flavors', the application redirects to a form ('/Flavors/Create') for adding a new flavor | registered user clicks "add new flavor" | the application redirects to form at 'Flavors/Create' |
| When a registered user submits the new flavor form, the application adds the new flavor to the flavors table of the michelle_morin database and redirects to '/Flavors' | registered user submits new flavor form | the application adds new flavor to flavors table and redirects to '/Flavors' |
| When a registered user submits the new treat form, the application adds the new treat to the treats table of the michelle_morin database and redirects to '/Treats' | registered user submits new treat form | the application adds new treat to treats table and redirects to '/Treats' |
| If user visits '/Treats/{id}', the application displays a list of flavors for that treat | user clicks on specific treat in list at '/Treats' | the application redirects to '/Treats/{id}' to display description and available flavors of that treat |
| If user visits '/Flavors/{id}', the application displays a list of treats corresponding to that flavor | user clicks on specific flavor in list at '/Flavors' | the application redirects to '/Flavors/{id}' to display available treats corresponding to that flavor |
| A registered user can add a flavor(s) to a treat | registered user clicks "add new flavor" at '/Treats/{id}' | the application redirects to a form (at '/Treats/AddFlavor/{id}') that, when submitted, adds a new flavor to that treat |
| A registered user can delete a treat from the list of all treats | registered user selects "delete treat" option on '/Treats/{id}' | application deletes treat from database |
| A registered user can delete a flavor from the list of all flavors | registered user selects "delete flavor" option on '/Flavors/{id}' | application deletes flavor from database |

## Setup/Installation Requirements

### Install .NET Core

#### on macOS:
* _[Click here](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-2.2.106-macos-x64-installer) to download a .NET Core SDK from Microsoft Corp._
* _Open the file (this will launch an installer which will walk you through installation steps. Use the default settings the installer suggests.)_

#### on Windows:
* _[Click here](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-2.2.203-windows-x64-installer) to download the 64-bit .NET Core SDK from Microsoft Corp._
* _Open the .exe file and follow the steps provided by the installer for your OS._

#### Install dotnet script
_Enter the command ``dotnet tool install -g dotnet-script`` in Terminal (macOS) or PowerShell (Windows)._

### Install MySQL and MySQL Workbench

#### on macOS:
_Download the MySQL Community Server DMG File [here](https://dev.mysql.com/downloads/file/?id=484914). Follow along with the installer until you reach the configuration page. Once you've reached Configuration, set the following options (or user default if not specified):_
* use legacy password encryption
* set password (and change the password field in appsettings.json file of this repository to match your password)
* click finish
* open Terminal and enter the command ``echo 'export PATH="/usr/local/mysql/bin:$PATH"' >> ~/.bash_profile`` if using Git Bash.
* Verify MySQL installation by opening Terminal and entering the command ``mysql -uroot -p{your password here, omitted brackets}``. If you gain access to the MySQL command line, installation is complete. An error (e.g., -bash: mysql: command not found) indicates something went wrong.

_Download MySQL Workbench DMG file [here](https://dev.mysql.com/downloads/file/?id=484391). Install MySQL Workbench to Applications folder. Open MySQL Workbench and select Local instance 3306 server, then enter the password you set. If it connects, you're all set._

#### on Windows:
_Download the MySQL Web Installer [here](https://dev.mysql.com/downloads/file/?id=484919) and follow along with the installer. Click "Yes" if prompted to update, and accept license terms._
* Choose Custom setup type
* When prompted to Select Products and Features, choose the following: MySQL Server (Will be under MySQL Servers) and MySQL Workbench (Will be under Applications)
* Select Next, then Execute. Wait for download and installation (can take a few minutes)
* Advance through Configuration as follows:
  - High Availability set to Standalone.
  - Defaults are OK under Type and Networking.
  - Authentication Method set to Use Legacy Authentication Method.
  - Set password to epicodus. You can use your own if you want but epicodus will be assumed in the lessons.
  - Unselect Configure MySQL Server as a Windows Service.
* Complete installation process

_Add the MySQL environment variable to the System PATH. Instructions for Windows 10:_
* Open the Control Panel and visit _System > Advanced System Settings > Environment Variables..._
* Select _PATH..._, click _Edit..._, then _Add_.
* Add the exact location of your MySQL installation and click _OK_. (This location is likely C:\Program Files\MySQL\MySQL Server 8.0\bin, but may differ depending on your specific installation.)
* Verify installation by opening Windows PowerShell and entering the command ``mysql -uroot -p{your password here, omitted brackets}``. It's working correctly if you gain access to the MySQL command line. Exit MySQL by entering the command ``exit``.
* Open MySQL Workbench and select Local instance 3306 server (may be named differently). Enter the password you set, and if it connects, you're all set.

### Clone this repository

_Enter the following commands in Terminal (macOS) or PowerShell (Windows):_
* ``cd desktop``
* ``git clone https://github.com/michelle-morin/PierreTreats.Solution``
* ``cd PierreTreats.Solution/Bakery``

_Confirm that you have navigated to the Bakery directory (e.g., by entering the command_ ``pwd`` _in Terminal)._

_Recreate the ``michelle_morin`` database using the following commands (in Terminal on macOS or PowerShell on Windows) at the root of the Bakery directory:_
* ``dotnet restore``
* ``dotnet build``
* ``dotnet ef database update``

_Run this application by entering the following command in Terminal (macOS) or PowerShell (Windows) at the root of the Bakery directory:_
* ``dotnet run`` or ``dotnet watch run``

_To view/edit the source code of this application, open the contents of the PierreTreats.Solution directory in a text editor or IDE of your choice (e.g., to open all contents of the directory in Visual Studio Code on macOS, enter the command_ ``code .`` _in Terminal at the root of the PierreTreats.Solution directory)._

## Technologies Used

* Git
* HTML
* CSS
* C#
* dotnet script
* ASP.NET Core MVC 2.2
* Entity Framework Core 2.2
* Identity
* Razor
* MySQL

## License

Licensed under the MIT license.

&copy; 2020 - Michelle Morin