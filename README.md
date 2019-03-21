# Log4j2-HtmlPatternLayout

Extends log4j2 HTMLLayout with the possibility to format strings using the syntax used in the pattern layout. 


log4j2.xml

```XML
<?xml version="1.0" encoding="UTF-8"?>
<Configuration packages="com.github.kilianB.log4j"
	status="WARN">
	<Appenders>
		<File name="LOGFILE" fileName="logfile.html" append="false">
			<PatternHtmlLayout
				pattern="%p %td %d{HH:mm:ss} %td %c{1} %td %m"
				header="Priority,Time,Sender,Message" omitStyle="true"
				justTable = "true"
				theadCSSClass= "thead-dark"
				tableCSSClass="table table-striped" />
		</File>
	</Appenders>
	<Loggers>
		<Root level="info">
			<AppenderRef ref="LOGFILE" />
		</Root>
	</Loggers>
</Configuration>
```


log4j2.properties example

```
packages = com.github.kilianB.log4j

appender.fileAppender.type = File
appender.fileAppender.name = LOGFILE
appender.fileAppender.append = FALSE
appender.fileAppender.layout.type = PatternHtmlLayout
appender.fileAppender.layout.header = Priority,Time,Sender,Message
appender.fileAppender.layout.pattern = %p %td %d{HH:mm:ss} %td %c{1} %td %m
appender.fileAppender.layout.omitStyle = TRUE
appender.fileAppender.layout.tableCSSClass = striped highlight responsive-table
```

<table>

## Configuration parameters.
<tr>
  <th>Tags</th> <th>Description</th> <th>Default</th>
</tr>
<tr>
  <td>header</td>
  <td>Comma seperated list of table headers. The table will have as many columns as headers supplied</td>
  <td>REQUIRED</td>
</tr>
<tr>
<td>pattern</td> <td>The pattern usage as defined by the <a href="https://logging.apache.org/log4j/2.x/manual/layouts.html#Patterns">pattern layout</a>.
The new introduced <code>%td%</code> keyword symbolizes the start of a new table cell. </td>
<td>REQUIRED - %m%n</td>
</tr>

<tr>
  <td>omitStyle</td>
  <td>TRUE | FALSE. Ignore the default styling of the original htmlLayout</td>
  <td>FALSE</td>
</tr>

<tr>
  <td>justTable</td>
  <td>TRUE | FALSE. Only print the table content to the file without html head/body markup. if true omitStyle is implied to be true</td>
  <td>FALSE</td>
</tr>

<tr>
  <td>tableCSSClass</td>
  <td>CSS class attached to the table tag. Useful if embedded into page with external styles </td>
  <td></td>
</tr>

<tr>
  <td>theadCSSClass</td>
  <td>CSS class attached to the thead tag. Useful if embedded into page with external styles </td>
  <td></td>
</tr>


<tr>
  <td>title</td>
  <td>title of the html page</td>
  <td>Log4j Log Messages</td>
</tr>
<tr>
  <td>contentType</td>
  <td>html head tag. default</td>
  <td>text/html</td>
</tr>
<tr>
  <td>charset</td>
  <td>charset of the html page</td>
  <td>UTF-8</td>
</tr>
<tr>
  <td>fontSize</td>
  <td>fontSize used in the table. Ignored if omitStyle = TRUE</td>
  <td>small</td>
</tr>
<tr>
  <td>fontName</td>
  <td>Font used in the table. Ignored if omitStyle = TRUE</td>
  <td>arial,sans-serif</td>
</tr>
<tr>
  <td>fontName</td>
  <td>Font used in the table. Ignored if omitStyle = TRUE</td>
  <td>arial,sans-serif</td>
</tr>
<tr>
  <td>alwaysWriteExceptions</td>
  <td>Outputs exceptions even if no exception is included in the pattern</td>
  <td>TRUE</td>
</tr>
<tr>
  <td>noConsoleNoAnsi</td>
  <td>If true and System.console() is null, do not output ANSI escape codes.</td>
  <td>FALSE</td>
</tr>
</table>
