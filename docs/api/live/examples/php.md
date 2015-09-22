# My first contribution : get some data from our Pioupiou

<?php

$monPioupiouUrl = "http://api.pioupiou.fr/v1/live-with-meta/419";

$monCurl = curl_init();
curl_setopt_array($monCurl, array(
        CURLOPT_RETURNTRANSFER => 1,
        CURLOPT_URL => $monPioupiouUrl,
        CURLOPT_USERAGENT => 'Codular Sample cURL Request'
));

$resuPioupiouUrl = curl_exec($monCurl);
curl_close($monCurl);

$resuJsonPioupiou = json_decode ($resuPioupiouUrl, true);

// print_r ($resuJsonPioupiou); // Dump all data if needed

echo 'Preasure : ' . $resuJsonPioupiou ['data'] ['measurements'] ['pressure'] . "\n";
echo 'Avg Speed : ' . $resuJsonPioupiou ['data'] ['measurements'] ['wind_speed_avg'] . "\n";
echo 'Heading : ' . $resuJsonPioupiou ['data'] ['measurements'] ['wind_heading'] . "\n";

?>
