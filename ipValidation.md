<?php

function isValidIP($str)
{
  $str1 = '';
  $str2 = '';
  $str3 = '';
  $str4 = '';
  $length = strlen($str);
  $dot = substr_count($str, '.');
  $space = substr_count($str, ' ');

  if (preg_match('/^[a-z\D]+$/', $str) === 1)
  {
    return false;
  }

  if ($space !== 0 || $dot !== 3)
    {
      return false;
    }
    
  for ($i1 = 0; $i1 < $length; $i1++)
  {
    $curr = $str[$i1];
      
    if ($curr === ".")
    {
      break;
    }
    $str1 = "{$str1}{$curr}";
  }

  if ($str1 < 0 || $str1 > 255)
  {
    return false;
  }

  for ($i2 = $i1 + 1; $i2 < $length; $i2++)
  {
    $curr = $str[$i2];
      
    if ($curr === ".")
    {
      break;
    }
    $str2 = "{$str2}{$curr}";
  }

  if ($str2 < 0 || $str2 > 255)
  {
    return false;
  }

  for ($i3 = $i2 + 1; $i3 < $length; $i3++)
  {
    $curr = $str[$i3];
      
    if ($curr === ".")
    {
      break;
    }
    $str3 = "{$str3}{$curr}";
  }

  if ($str3 < 0 || $str3 > 255)
  {
    return false;
  }

  for ($i4 = $i3 + 1; $i4 < $length; $i4++)
  {
    $curr = $str[$i4];
    $str4 = "{$str4}{$curr}";
  }

  if ($str4 < 0 || $str4 > 255)
  {
    return false;
  }

  return true;
}

?>
