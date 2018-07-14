<?php

function validBraces($braces)
{
  $length = strlen($braces);
  $result = '';
  $arr = array();

  if ($length % 2 !== 0)
  {
    return false;
  }

  $counter = 0;

  for ($i = 0; $i < $length; $i++)
  { 
    $curr = $braces[$i];

    if ($braces[$i] === "(")
      $counter += 1;
    if ($braces[$i] === "[")
      $counter += 2;
    if ($braces[$i] === "{")
      $counter += 3;
    if ($braces[$i] === ")")
      $counter -= 1;
    if ($braces[$i] === "]")
      $counter -= 2;
    if ($braces[$i] === "}")
      $counter -= 3;
    if ($counter < 0)
      return false;

    $result = $result.$braces[$i];

    if ($counter === 0)
    {
      $arr[] = $result;
      $result = '';
    }
  }

  $numElem = count($arr);

  for ($i = 0; $i < $numElem; $i++)
  {
    $j = strlen($arr[$i]) - 1;

    for ($ind = 0; $ind < strlen($arr[$i]) / 2 - 1; $ind++)
    {        
      if (($arr[$i][$ind] === "(" && $arr[$i][$j] !== ")") || ($arr[$i][$ind] === "[" && $arr[$i][$j] !== "]") || ($arr[$i][$ind] === "{" && $arr[$i][$j] !== "}" || $arr[$i][$ind] !== "(" && $arr[$i][$j] == ")") || ($arr[$i][$ind] !== "[" && $arr[$i][$j] === "]") || ($arr[$i][$ind] !== "{" && $arr[$i][$j] === "}"))
      {
        return false;
      }

      $j--;
    }
  }

  return true;
}

?>
