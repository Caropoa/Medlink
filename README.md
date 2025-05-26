<?php
function findPoint($strArr)
{
    $arr1=explode(", ",$strArr[0]);
    $arr2=explode(", ",$strArr[1]);

    $comun=array_intersect($arr1,$arr2);
    if (!empty($comun)){
        return implode(",",$comun);
    }
    else{
        return "false";
    }
}
echo findPoint(['1, 3, 4, 7, 13', '1, 2, 4, 13, 15']);
?>
