<?php

function xbonacci($signature, $n)
{
  $numOfElem = count($signature);
  $arr = array();
  $arrFirstElem = array();

  for ($i = 0; $i < $n; $i++)
  { 
    if ($i <= $numOfElem - 1)
      $arr[] = $signature[$i];
    elseif ($i === $numOfElem)
      $arr[] = array_sum($arr);
  }
  
  for ($i = $numOfElem; $i < $n - 1; $i++)
  {
    $firstElem = array_shift($arr);
    $arrFirstElem[] = $firstElem;
    $sum = array_sum($arr);
    $arr[] = $sum;
  }

  $result = array_merge($arrFirstElem, $arr);

  return $result;
}

?>
