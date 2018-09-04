# usefulePHPScripts
Some PHP Scripts that i use recursively

# PHP TO EXCEL

```
if(isset($_POST['export_excel'])){ 
  $queryx1  = "SELECT id,title,firstname,other_names,lastname,mobile,email,date_of_birth,gender,fg_code,designation,ministerial FROM `ministerial_records` WHERE church = $chid AND zone = $znid AND date_of_birth BETWEEN '$from' AND '$to' AND cat LIKE '%inister%' AND status LIKE 'Active'";
   $setRec = mysqli_query($link, $queryx1);
   $columnHeader = '';  
   $columnHeader = "Sr NO" . "\t" . "Name of ministers" . "\t" . "Phone number" . "\t" . "Email address" . "\t" . "Date of Birth" . "\t" . "Gender" . "\t" . "Fg Code" . "\t" . "Designation" . "\t" . "Ministerial" . "\t";  
                
    $setData = '';  

    while ($rec = mysqli_fetch_row($setRec)) {  
        $rowData = '';  
        foreach ($rec as $value) {  
            $value = '"' . $value . '"' . "\t";  
            $rowData .= $value;  
        }  
        $setData .= trim($rowData) . "\n";  
    }    

    header("Content-type: application/vnd.ms-excel");  
    header("Content-Disposition: attachment; filename=Ministers_list.xls");  
    header("Pragma: no-cache");  
    header("Expires: 0");  

    echo ucwords($columnHeader) . "\n" . $setData . "\n";
}

```
