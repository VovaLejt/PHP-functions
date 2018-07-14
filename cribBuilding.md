function myCrib($n)
{
  $goriz = "_";
  $space = " ";
  $wall = "|";
  $sl1 = "/";
  $sl2 = "\\";
  $next = "\n";
  $edge = str_repeat($space, $n * 2);
  $center = str_repeat($goriz, $n * 2 + 1);
  $upperRoof = $edge.$center.$edge.$next;
  $lowerRoof = '';
  $middleHouse = '';
  $overMiddleHouse = '';
  $topDoor = '';

  for ($i = 1; $i <= $n * 2; $i++)
  {
    $nextEdge = str_repeat($space, $n * 2 - $i);
    $currCenter = str_repeat($goriz, ($i + $n) * 2 - 1);
    $lowerRoof = 
    $lowerRoof.$nextEdge.$sl1.$currCenter.$sl2.$nextEdge.$next;
  }

  if ($n > 1)
  {
    for ($i = 1; $i < $n; $i++)
    {
      $betweenWalls = str_repeat($space, $n * 5 + $n - 1);
      $overMiddleHouse = $overMiddleHouse.$wall.$betweenWalls.$wall.$next;
    }
  }

  for ($i = 1; $i <= $n; $i++)
  {
    $edge = str_repeat($space, $n * 2);
    $upperDoor = str_repeat($goriz, $n * 2 - 1);
    $middleHouse = $wall.$edge.$upperDoor.$edge.$wall.$next;
  }

  if ($n > 1)
  {
    for ($i = 1; $i < $n; $i++)
    {
      $between4Walls = str_repeat($space, $n * 2 - 1);
      $topDoor = $topDoor.$wall.$between4Walls.$wall.$between4Walls.$wall.$between4Walls.$wall.$next;
    }
  }

  $floor = str_repeat($goriz, $n * 2 - 1);
  $bottomHouse = $wall.$floor.$wall.$floor.$wall.$floor.$wall.$next;

  $crib = $upperRoof.$lowerRoof.$overMiddleHouse.$middleHouse.$topDoor.$bottomHouse;

  return $crib;
}
