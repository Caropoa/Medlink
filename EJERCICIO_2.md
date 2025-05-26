<?php
function noIterate($strArr)
{
  $n = $strArr[0];
  $k = $strArr[1];
  
  $nLen = strlen($n);
  $kLen = strlen($k);
  
  $kCount = array_count_values(str_split($k));
  
  $start =0;
  $minLen =PHP_INT_MAX;
  $minStart =0;
  
  $windowCount =[];
  $have =0;
  $need = count($kCount);
  
for ($end = 0 ;$end < $nLen ; $end++) {
  $char =$n[$end];
  $windowCount[$char] = ($windowCount[$char] ?? 0) +1;
  if (isset($kCount[$char])&& $windowCount[$char] == $kCount[$char]){
    $have++;
  }
  while($have == $need){
    if (($end - $start + 1) < $minLen){
      $minLen = $end - $start + 1;
      $minStart = $start;
    }
    
    $leftChar =$n[$start];
    $windowCount[$leftChar]--;
    if(isset($kCount[$leftChar]) && $windowCount[$leftChar] < $kCount[$leftChar]){
      $have--;
    }
    $start++;
  }
}
return substr($n, $minStart,$minLen);
}
echo noIterate(["ahffaksfajeeubsne", "jefaa"]);
?>
