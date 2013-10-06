<?php
//script chafa para bajar el periódico LaJornada :D 
//Estudiar y Aprender para el pueblo Defender .:[www.RojosBar.com]:.
//El script solo funciona después de las 16:05 hora Centro México [hora que es publicado en ISSUU]


//Aquí esta  la dirección del día de la LaJornada en ISSU y la supuesta información del navegador :D
$ch =  curl_init();
//aquí generamos la fecha
date_default_timezone_set('America/Mexico_City');
$fecha = date("dmY");
//aquí se ingresa el día al link
curl_setopt($ch, CURLOPT_URL, "http://issuu.com/lajornadaonline/docs/diario$fecha.pdf-3");
//esto es la supuesta información  del navegador
curl_setopt($ch, CURLOPT_USERAGENT, 'Mozilla/4.0 (compatible;MSIE 5.01; Windows NT 5.0 )');
curl_setopt($ch, CURLOPT_HTTPHEADER, array ("Accept-Language: es-es,en"));
curl_setopt($ch, CURLOPT_TIMEOUT, 10);
curl_setopt($ch, CURLOPT_FOLLOWLOCATION,1);
curl_setopt($ch, CURLOPT_RETURNTRANSFER,1);

//Se guarda la pagina

$result = curl_exec($ch);
curl_close($ch);

//parsear : aquí el script encuentra la dirección de las imágenes y la guarda como el matches1 
// el script encuentra el numero de las paginas y la guarda en el matches2

preg_match_all("(<meta name=\"twitter:image\" content=\"(.*)1.jpg\">)siU" ,$result, $matches1);
preg_match_all("(\"pageCount\":(.*),)siU" ,$result, $matches2);


$tves = $matches1[1][0];
$pag = $matches2[1][0];

//bajando las paginas en JPG 

//este FOR es para generar una secuencia del numero de "Paginas" del 1,2,3.... hasta el numero de pagina que se encontró en el matches2 
for ($i = 1; ; $i++) {
    if ($i > $pag) {
        break;
    }
  system( "wget $tves$i.jpg ");
}

?>
