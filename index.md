## How to ETL data from MariaDB to SQL Server using SSIS

We all know about SSIS. Its a great tool to make a data integration from a database system to another one, or from a flat file to a database system, and also from/to HDFS. However, the only thing that is missing in SSIS is the real time data integration such as Kafka.

In this quick steps, we will send data from MariaDB to SQL server using SSIS tool, we will first make a full data integration, then the daily data integration and finally we will upload the work to SQL server in order to run them automatically in every time unite.

## Create the SSIS project
Make sure that you have installed Visual studio 2019.
In order to start a SSIS project, you have your Visual Studio 2019 installation. follow the instructions in this link.
https://docs.microsoft.com/en-us/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15

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
