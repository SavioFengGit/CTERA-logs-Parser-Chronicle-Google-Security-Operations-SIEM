# CTERA-logs-Parser-Chronicle-Google-Security-Operations-SIEM-
In this repository, you will find a custom Chronicle SIEM Parser that I have written to normalize raw logs into a Unified Data Model.

## Description 
I had to write a custom parser to normalize raw logs from the CTERA drive, and I want to share my code (not complete, but useful) with all of u. 

There are 5 types of logs in CTERA:
 - System – General CTERA Edge Filer events, including starting up, connecting to the network and the CTERA Portal, disconnecting from the network and the CTERA Portal.
 - Cloud Backup – Events related to cloud backup or restore operations.
 - Cloud Sync – Events related to cloud drive synchronization operations.
 - Access – Events related to user access to the CTERA Edge Filer.
 - Audit – Changes to the CTERA Edge Filer configuration.
   
<br>
In this code i managed Cloud Sync, Access and some System log type.

<br><br>

## Useful information :
There are 4 phase to create a parser.
1) Parse and extract data from the original log.
2) Manipulate the extracted data. This includes using conditional logic to selectively parse values, convert data types, replace substrings in a value, convert to uppercase or lowercase, etc.
3) Assign values to UDM fields.
4) Output the mapped UDM record to the @output key.

<br> <br>

Here’s a brief description of the functions in Logstash’s mutate filter:
 - replace: This function is used to replace a field with a new value. The new value can be a literal or another field. For example, if you want to replace the value of the ‘host’ field with ‘localhost’, you would use the replace function.
 - merge: The merge function combines the values of two or more fields into a single field. You can merge arrays, hashes, and other data types. For example, if you have two fields ‘first_name’ and ‘last_name’, you can merge them into a single ‘name’ field.
 - rename: As the name suggests, the rename function is used to rename one or more fields. For example, if you want to rename the field ‘src’ to ‘source’, you would use the rename function.
 - gsub: This function is a substitution operation. It replaces a specified pattern with a replacement string. For example, you can use gsub to replace all occurrences of ‘http’ in a field with ‘https’.

<br>
When mapping the raw field to the UDM field, be careful with the data type and whether it’s an array or not. If it’s not an array, you can use rename; otherwise, you will use merge. Remember to write the final merge only once, or Chronicle will duplicate your attributes.


<br><br>
## Useful link:
 - UDM fields list -> https://cloud.google.com/chronicle/docs/reference/udm-field-list
 - Overview UDM -> https://cloud.google.com/chronicle/docs/event-processing/udm-overview
 - Required field based on event_type -> https://cloud.google.com/chronicle/docs/unified-data-model/udm-usage
 - Documentation of parser -> https://cloud.google.com/chronicle/docs/event-processing/parsing-overview
 - Logstash documentation -> https://www.elastic.co/guide/en/logstash
 - Ctera type of logs -> https://kb.ctera.com/docs/viewing-logs-6

<br><br>
# Author
<b>Xiao Li Savio Feng</b>
