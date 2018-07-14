<?php

function inArray($array1, $array2)
{
  $str1 = '';
  $str2 = '';
  $str3 = '';
  $arr1 = array();
  $arr2 = array();

  for ($i = 0; $i < count($array2); $i++)
  {
    $str2 = $str2.$array2[$i]." ";
  }

  for ($i = 0; $i < count($array1); $i++)
  { 
    $curr = $array1[$i];

    if (strpos($str2, $curr) === false)
      $str1 = $str1;
    else
      $str1 = $str1.$curr." ";
  }
  
  if ($str1 === "")
    {
      $arr[] = $str1; 
      return $arr;
    }
  else

  for ($i = 0; $i < strlen($str1); $i++)
  {
    $curr = $str1[$i];

    if ($curr === " ")
    {
      $arr2[] = $str3;
      $str3 = " ";
    }
    else
      $str3 = $str3.$curr;
  }

  for ($i = 0; $i < count($arr2); $i++)
  {
    if (strpos(($arr2[$i]), " ") === false)
    {
      $arr2[$i] = $arr2[$i];
    }
    else
    {
      $arr2[$i] = substr($arr2[$i], 1, strlen($arr2[$i]) - 1);
    }
  }

  sort($arr2);

  return $arr2;
}

?>
