## How to ETL data from SQL Server to MariaDB using SSIS

We all know about SSIS. Its a great tool to make a data integration from a database system to another one, or from a flat file to a database system, and also from/to HDFS. However, the only thing that is missing in SSIS is the real time data integration such as Kafka.

In this quick steps, we will send data from SQL Server to MariaDB using SSIS tool, we will first make a full data integration, then the daily data integration and finally we will upload the work to SQL server in order to run them automatically in every time unite.

## Create the SSIS project
- Make sure that you have installed Visual studio 2019.
- In order to start a SSIS project, you have your Visual Studio 2019 installation. Follow the instructions in this link
[SSIS Setup](https://docs.microsoft.com/en-us/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15)
- Make sure to download and install the [Integration Service](https://marketplace.visualstudio.com/items?itemName=SSIS.SqlServerIntegrationServicesProjects).
- Right click on visual studio 2019 and run it as an admin.
- Create a new project.
- In the search text above write "Integration Services Project", then finish the Wizard.

## Download the MariaDB connector
<p>We can contact MariaDB via serveral methods, the free one is by ODBC engine.</p>
<p>Click on this link to download MariaDB connector [MariaDB Connector](https://mariadb.com/kb/en/mariadb-connector-odbc/).</p>
<p>In the link above, follow these steps to setup the MariaDB Connector in the right way.</p>
- After the click on the link, navigate to the connectors tab.
- From product select ODBC connector.
- In the OS select the operating system thats match your needs. (In my case, ive selected MS windows 32-bit)
- Last thing you need to do is just download it.

## Setup the MariaDB connector
- Open the downloaded file and install it.
- In the search bar write ODBC data Sources (32-bi, and select it from the menu.
- In the "User DSN" click Add to create a new connection profile.
- Select the driver, in our case is MariaDB ODBC 3.1 Driver, then click finish.
- Give it a name "NewMariaDB" or any name else you want.
- Give the MariaDB server name or IP Address, the port, the username and password, then click on "Test DSN".
- The connection must setup seccussfully.
- Select the Database you want to connect with from the drop down list, then finish the system till the end.
- Now the Connector is ready to be used in SSIS.

## Table information between the two DB systems
<p>In order to copy the data between the databases, you need to create a table in the destionation database in order to get all the upcoming records inside it. You have to be aware about the columns number, name and data type. For example if the is a column name "ID" and datatype is "int" as a primary key, the same column with the same specifications must be locatedc in the destination database table.</p>

## SSIS ODBC connector, SQL Server OLE DB Provider
- In the Visual studio, open the SSIS project you created back in the first step.
- In the left menu, drag and drop "Data Flow Task" to the working space.
- Double click on the "Data flow task", after rename it if required.
- We will make a data integration from SQL Server to MariaDB, so our source is "Source Assistant".
- A pop-up window ill open to you to select the database engine you want to connect with, from the list select SQL server, then press on "New..." on the right.
- In the "Server or file name" field, write down the SQL server IP Address.
- In the "Log on to the server" section, select the login type you want.
- From the "Initial catalog" drop down list, select the database name you want to connect with.
- Click "test connection" to validate the connection, the click on "OK".
- Right click on the same "Source Assistant" and select edit.
- Select the table name you want to get the data from. you can write an SQL statement instead.
- Click on "Preview" button to see the data saple inside the selected table.
- Click on "OK"
<p>Now the SQL Server connection is ready to fetch the records, now lets setup the destination of these records, is Maria DB ODBC.<

- From the SSIS Toolbox, select ODBC Destination, right click on it and select "Edit".
- Click on "New" button to setup a new connection.
- Since we dont have a "Data connections" profile yet, we have to create a new on by click on "New" button.
- From the "Data source specification, select the profile name you created back in "Setup the MariaDB connector" step.
- Write the username and the password, test your connection then click "OK", and also "OK".
- Choose the "Data access mode" to be "Table Name-Batch".
- Select the Table Name.
- Since we didnt match the arrow between the Source database and the destination one, click "OK", go to the "OLE DB Source", get the blue arrow to hit the "ODBC Destination", then open the "ODBC Destination agaon, go to the "Mapping" to map each column from source table to the destionation one.
-  Now everything looks good, right click in the working field and select "Execute task".

You can use the [editor on GitHub](https://github.com/mbmasadeh/MariaDBToSQLServer-DataIntegration/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/mbmasadeh/MariaDBToSQLServer-DataIntegration/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
