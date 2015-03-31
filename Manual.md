# WWW SQL Designer #

Hello and welcome to WWW SQL Designer documentation. This page will hopefully help you with understanding how WWW SQL Desginer works and how can it be tailored to suit your needs.

## Browsers ##

WWW SQL Designer was tested in the following browsers:
  * Firefox 2.x+
  * Internet Explorer 6-10
  * Safari 3-5
  * Opera 9.x+
  * Konqueror 3.5.x
  * Chrome 3+

Konqueror is the only browser (from this list) which lacks support for Smooth connectors and XSLT transformations (creation of SQL scripts).

## Basics ##
The application allows you to:
  1. Draw E-R designs
  1. Edit tables and rows
  1. Manage keys
  1. Create relations (FK constraints)
  1. Save & Load designs
  1. Import DB schemas

## Layout Introduction ##

When you first copy the source code to a server or your local PC and open the index file, you will be presented with a screen that can be broken up into three sections.

**The Canvas**:
The canvas is the main working area and has a fine blue grid on it. This is where the actual ER Diagram will be created.

**The Toolbar**:
The top right corner of the screen has a toolbar where most command actions are visible. In the screenshot below, you will note that many are disabled. The toolbar will disable features that you cannot currently perform. These will be enabled as the correct items on the page are selected and the options become available.

**The Minimap**:
Lastly, in the bottom right corner of the screen you will see a minimap that you can use to quickly move your viewport on the canvas around. As many ERDs will be much larger than a screen, both the canvas and minimap will extend as needed.

![http://wwwsqldesigner.googlecode.com/hg/images/ScreenLayout.png](http://wwwsqldesigner.googlecode.com/hg/images/ScreenLayout.png)

## Getting Started ##

The easiest way to get familiar with a tool is to start using it, so the following will show you how to create a few tables, make keys and create constraints.

Click on Add Table on the toolbar and then click on the canvas where you want to place the table. When you click on the canvas you will have a popup open that asks you for the table name and allows an optional Table Comment to be added.

![http://wwwsqldesigner.googlecode.com/hg/images/editTable.png](http://wwwsqldesigner.googlecode.com/hg/images/editTable.png)

For this example, I am following a few tables in the test database that comes with certain builds of MySQL.

I have added the following information:
**Name**: authors
**Comment**: Listing of All Authors who currently have contracts

Pressing **OK** closes the pop-up and creates the table.

_Note: If you press Cancel, the table is still made with the default information in the pop-up._

Double-clicking on the label will bring up the table details again and you can change the name or comment of the table.

### Movement ###
To move the table around the canvas, drag it via the grey label.

### Adding Columns ###
<img src='http://wwwsqldesigner.googlecode.com/hg/images/columnDetail.png' align='left'>To add columns to your table, make sure that the table is selected (clicking anywhere on the table will do this) and on the menubad, click on <b>Add Field</b>. This creates a new column in the table and opens the details for it.<br>
<br>
You can enter the column name, specify the data type for it, specify the size of the column where appropriate (certain columns such as Date cannot have a size specified). If you want the column to have a default value, enter it into the Default text field. Lastly, there are two checkboxes: placing a check in <b>AutoIncrement</b> sets the column to automatically increment with each row that is inserted and the <b>Null</b> checkbox which allows the field to have a null value if it is checked.<br>
<br>
You will notice that different data types have a different color assigned to the row in the table. This is just a quick simple way to be able to look at the tables and know at a glance the type of data that will be inside.<br>
<br>
<b>Numeric</b>: Yellow<br>
<b>Text/Character</b>: Pink<br>
<b>Date/Time</b>: Green<br>
<b>Misc</b>: Violet<br>
<br>
Now, go and follow these steps again to create the second table Books.<br>
<br>
<h3>Adding Keys</h3>
<img src='http://wwwsqldesigner.googlecode.com/hg/images/selectedColumn.png' align='left'>The table Books has an extra index that is on the column authorId. This is not part of the primary key however.<br>
<br>
Select the column by left clicking on it. You will see two red arrows point to the column name.<br>
<br>
<br>

On the menubar, click on <b>Keys</b>. This will bring up a pop-up with all the key information.<br>
<br>
In this case, authorID will need a new key, so Press the Add Key button, which inserts a new key. In the list of available columns, select authorId and press the <b><<</b> button to add this column to the key. As keys can be named (aside from their automatically generated names, the Name Field can be edited to give the key a identifiable and meaningful name. Now press <b>OK</b> to save the changes.<br>
<br>
<img src='http://wwwsqldesigner.googlecode.com/hg/images/addingKeys.png' />

<br>

<h2>Creating Constraints</h2>
With the keys made, the authorId column can now be constrained by the authors table. Select the ID column in the Authors table and click on Connect Foreign Key. The cursor will change to a hand when you hover over any tables. Left Click the authorId column in the table Books. This now adds a constraint on that column.<br>
<br>
<img src='http://wwwsqldesigner.googlecode.com/hg/images/constrained.png' />

By repeating these steps, you can create pretty much anything using wwwSQLDesigner.<br>
<br>
If the canvas becomes too crowded, you can enlarge it by dragging a column over the edge of the canvas, thereby increasing the size.<br>
<br>
<img src='http://wwwsqldesigner.googlecode.com/hg/images/finalExample.png' />

<h2>Additional Tasks</h2>
Most commands are intuitively available from the right sidebar. Some additional tasks are described below:<br>
<br>
<ul><li>To <b>draw a connector (relation)</b>, first select a field which forms a Primary Key. You then have two options:<br>
<ol><li>Either click 'Create foreign key' button in sidebar and click target table's heading. New field and relation will be created;<br>
</li><li>or click 'Connect foreign key' button in sidebar and click target table's field. New relation will be created.</li></ol></li></ul>

<ul><li>To <b>perform any kind of save/load/export/import task</b>, press the 'Save/Load' button in sidebar. A dialog window will appear, allowing you to perform clientside or serverside tasks. If you wish to use a server-side backend (for instance, to save your design into a database table), make sure the backend is properly configured.<br>
<ul><li><b>Example:</b> The php-mysql backend stores designs in MySQL table. First, it is necessary to prepare the storage table (its definition is available in <code>backend/php-mysql/database.sql</code>); second, connection credentials must be entered into <code>backend/php-mysql/index.php</code>.</li></ul></li></ul>

<ul><li>To <b>automatically load a saved schema</b> (using default database backend), append "keyword=xyz" to URL, substituting "xyz" with the name of your saved schema.</li></ul>

<ul><li>To <b>start with toolbar minimized (hidden)</b>, append "toolbar=hidden" to the querystring.