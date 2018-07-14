<?php

function orderWeight($str)
{
  $arr = array();

  $result = explode(" ", $str);

  for ($i = 0; $i < count($result); $i++)
  {
    $arr[$i] = array_sum(str_split($result[$i]));
  }

  array_multisort($arr, $result);
  $j = 0;

  for ($i = 0; $i < count($result); $i++)
  {
    if ($j < count($result) - 1)
    {
      $j = $i + 1;

      if (array_sum(str_split($result[$i])) === array_sum(str_split($result[$j])))
      {
        if (strlen($result[$i]) < strlen($result[$j]))
        {
          for ($t = 0; $t < count($result[$i]); $t++)
          {
            if ($result[$i][$t] > $result[$j][$t])
            {
              $curr = $result[$i];
              $result[$i] = $result[$j];
              $result[$j] = $curr;
              $i = 0;
            }
          }
        }
      }
    }
  }

  $result = implode(" ", $result);
  
  return $result;
}

?>
