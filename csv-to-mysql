<?php 

$con = mysqli_connect("DATABASE_HOST", "DATABASE_USER", "DATABASE_PASS", "DATABASE_NAME") or die(mysql_error());
$filePath = "/path/to/csv_file.csv";
$tableName = "tableName";
$fieldDelimiter = ",";
$lineDelimiter = "\n";

// If your csv file has not a header row, remove the line "IGNORE 1 LINES".
mysqli_query($con, '
    LOAD DATA LOCAL INFILE "'.$filePath.'"
    INTO TABLE '.$tableName.'
    FIELDS TERMINATED by \'' . $fieldDelimiter . '\'
    LINES TERMINATED BY \'' . $lineDelimiter . '\'
    IGNORE 1 LINES
') or die(mysql_error());

$query = mysqli_query($con, "SELECT COUNT(*) AS total_rows FROM " . $tableName);
$result = mysqli_fetch_array($query);
$total_rows = $result['total_rows'];

echo $total_rows . " rows have been added to the table " . $tableName;

?>
