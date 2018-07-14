<?php

function humanReadable($seconds)
{
  if ($seconds < 60 || $seconds % 60 === 0)
  {
    $minutes = "00";
  }

  if ($seconds >= 3600)
  {
    $ost = $seconds / 3600;
    $hours = intval($ost);
    $newSeconds = $seconds;
    $minutes = intval(($seconds - $hours * 3600) / 60);
    $seconds = ($seconds - $hours * 3600) % 60;

    if ($hours < 10)
    {
      $hours = "0".$hours;
    }
    elseif ($hours >= 100)
    {
      return "over the limit";
    }

    if ($minutes < 10)
    {
      $minutes = "0".$minutes;
    }   
  }
  else 
  {
    $hours = "00";

    if ($seconds >= 60)
    {
      $ost = $seconds / 60;
      $minutes = intval($ost);
      $seconds = $seconds - $minutes * 60;

      if ($minutes < 10)
      {
        $minutes = "0".$minutes;
      }

      if ($minutes >= 60)
      {
        $minutes = 59;
        $seconds = $minutes - 59;
      }
      elseif ($minutes === 0)
      {
        $minutes = "00";
      }  
    } 
  }

  if ($seconds < 10)
  {
    $seconds = "0".$seconds;
  }

  return $hours.":".$minutes.":".$seconds;
}

?>
