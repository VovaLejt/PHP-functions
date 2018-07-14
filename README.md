# camelCase-
Convert string to camel case

<?php

function toCamelCase($str)
{
  $result = '';
  for ($i = 0; $i < strlen($str); $i++)
  {
    $curr = substr($str, $i, 1);

    if ($curr === "-" || $curr === "_")
    {
      $next = substr($str, $i + 1, 1);
      $up = strtoupper($next);
      $result = "{$result}{$up}";
      $i = $i + 1;
    }
    else
    {
      $result = "{$result}{$curr}";
    }

  }

  return $result;
}

?>
