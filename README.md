# Pierre's Sweet and Savory Treats

#### _Advanced Databases and Authentication Independent Project for Epicodus_, _Mar. 27 2020_

#### By _**Michelle Morin**_

## Description

This is an ASP.NET Core MVC application for Pierre's Bakery, to market his sweet and savory treats. The application includes user authentication and a many-to-many relationship between ``Treat``s and ``Flavor``s. A treat can have many flavors (e.g., sweet, savory, spicy) and a flavor can have many different treats (e.g., a sweet flavor could include chocolate croissants, cheesecake, etc.). A user is able to navigate to the splash page that lists all treats and flavors, and may click on an individual treat or flavor to see all the treats/flavors that belong to it.

## Specifications:

| Specification | Example Input | Example Output |
| ------------- |:-------------:| -------------------:|
| If user visits '/' root route, the application displays a splash page with links to '/treats' and '/flavors', as well as links to login/register | user visits '/' route | application displays homepage |
| Application allows a user to register for an account with Identity | user clicks "create account" option on splash page | application redirects to form for creating a user account |
| Application allows a registered user to login | registered user clicks "login" option on splash page | application redirects to login screen |
| Application allows a registered user to logout | registered user clicks "logout" option | application logs out of user account |
| Only logged-in users are able to create, update, and delete flavors/treats | user is not logged in | user unable to create, update, delete |
| If user visits '/treats' route, applications displays all treats in database, each clickable to view available flavors for that treat | user visits '/treats' route | application displays list of treats |
| If a registered user clicks "add new treat" link at '/treats', the application redirects to a form ('/treats/create') for adding a new treat | registered user clicks "add new treat" | the application redirects to new treat form |
| If user visits '/flavors' route, applications displays all flavors in database, each clickable to view available treats of that flavor | user visits '/flavors' route | application displays list of flavors |
| If a registered user clicks "add new flavor" link at '/flavors', the application redirects to a form ('/flavors/create') for adding a new flavor | registered user clicks "add new flavor" | the application redirects to new flavor form |
| When a registered user submits the new flavor form, the application adds the new flavor to the flavors table of the michelle_morin database and redirects to '/flavors' | registered user submits new flavor form | the application adds new flavor to correct database table and redirects to page displaying all flavors |
| When a registered user submits the new treat form, the application adds the new treat to the treats table of the michelle_morin database and redirects to '/treats' | registered user submits new treat form | the application adds new treat to correct database table and redirects to page displaying all treats |
| If user visits '/treats/{id}', the application displays a list of flavors for that treat | user clicks on specific treat in list at '/treats' | the application redirects to '/treats/{id}' to display available flavors of that treat |
| If user visits '/flavors/{id}', the application displays a list of treats of that flavor | user clicks on specific flavor in list at '/flavors' | the application redirects to '/flavors/{id}' to display available treats of that flavor |
| A registered user can add flavors to a specific treat | registered user clicks "add new flavor" on '/treats/{id}' page | the application redirects to a form for adding a new flavor |
| A registered user can add treats to a specific flavor | registered user clicks "add new treat" on '/flavors/{id}' page | the application redirects to a form for adding a new treat |
| A registered user can delete a treat from the list of all treats | registered user selects "delete treat" option on '/treats/{id}' | application deletes treat from database |
| A registered user can delete a flavor from the list of all flavors | registered user selects "delete flavor" option on '/flavor/{id}' | application deletes flavor from database |

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
* ``git clone https://github.com/michelle-morin/PierreBakery.Solution``
* ``cd PierreBakery.Solution``

_Confirm that you have navigated to the PierreBakery.Solution directory (e.g., by entering the command_ ``pwd`` _in Terminal)._

_Recreate the ``michelle_morin`` database using the following commands (in Terminal on macOS or PowerShell on Windows):_
* ``cd Bakery``
* ``dotnet restore``
* ``dotnet build``
* ``dotnet ef migrations add Initial``
* ``dotnet ef database update``

_Run this application by entering the following command in Terminal (macOS) or PowerShell (Windows) at the root of the Bakery directory:_
* ``dotnet run`` or ``dotnet watch run``

_To view/edit the source code of this application, open the contents of the PierreBakery.Solution directory in a text editor or IDE of your choice (e.g., to open all contents of the directory in Visual Studio Code on macOS, enter the command_ ``code .`` _in Terminal)._

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