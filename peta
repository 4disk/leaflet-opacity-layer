<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	
	<link rel="shortcut icon" type="image/x-icon" href="docs/images/favicon.ico" />

    <link rel="stylesheet" href="src/leaflet.css" integrity="sha512-xodZBNTC5n17Xt2atTPuE1HxjVMSvLVW9ocqUKLsCC5CXdbqCmblAshOMAS6/keqq/sMZMZ19scR4PsZChSR7A==" crossorigin=""/>
    <link href='src/leaflet.fullscreen.css' rel='stylesheet' />
    <script src="src/leaflet.js" integrity="sha512-XQoYMqMTK8LvdxXYG3nZ448hOEQiglfqkJs1NOQV44cWnUrBc8PkAOcXy20w0vlaXaVUearIOBhiXZ5V3ynxwA==" crossorigin=""></script>
    <script src='src/Leaflet.fullscreen.min.js'></script>
    <script src='src/leaflet.ajax.js'></script>
    <script src='src/leaflet.ajax.min.js'></script>
    
<style>
    #btntool{
        width:40px;
        height:40px;
        border:2px solid blue;
        background-image:linear-gradient(45deg, blue, grey);
        color:white;
        font-weight:bold;
        font-size:20px;
        position:fixed;
        z-index:401;
        top:0px;
        right:5px;
        border-radius:5px;
        padding:0px 0px 3px 0px;
        text-align:center;
        transform: rotate(90deg);
        /*transition: 1s;
  }
    #divtools{
        display:none;
        position:fixed;
        background-image:linear-gradient(0deg, grey, white, grey);
        padding: 5px;
        opacity:80%;
        top:45px;
        right:5px;
        border-radius:20px;
        z-index:402;
    }
</style>
	<title>SIPILOK - peta sebaran</title>
    <div style="border:1px solid red; width:100%; color:red; text-align:center; font-weight:bold; font-family:arial;">PETA SEBARAN IZIN PRINSIP DAN IZIN LOKASI DI KABUPATEN SLEMAN</div>
    <div id="divbuttontool"><input type="button" id="btntool" value="|||" onclick="viewtool()"></div>
    <div id="divtools">
            <form action='' method='post'>cari koordinat : <input name="inputxy" id="inputxy" type="text" value='-7.712903, 110.357785' placeholder='isikan dalam format koordinat desimal'>
                <button id="buttoncarixy">cari</button>
            </form><br>
                *isikan koordinat dalam format desimal, contoh: -7.748127, 110.281989<hr></hr>
                tampilan peta :<br>
                
            <form action=''>
                <input type="radio" name="radioviewpeta" id="viewpeta0" value='src/blankmap.png' onclick="tampilpedas(this.value)" checked><label for="viewpeta0">blank</label>
                <input type="radio" name="radioviewpeta" id="viewpeta1" value="https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token=pk.eyJ1IjoibWFwYm94IiwiYSI6ImNpejY4NXVycTA2emYycXBndHRqcmZ3N3gifQ.rJcFIG214AriISLbB6B5aw" onclick="tampilpedas(this.value)"><label for="viewpeta1">mapbox</label>
                <input type="radio" name="radioviewpeta" id="viewpeta2" value="https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}'" onclick="tampilpedas(this.value)"><label for="viewpeta2">ArcGIS</label>
            </form>
            <hr></hr>
            transparansi : 
            <span id="sliderVal"></span><br>
            <input type="range" id="slider" min="0" max="100" step="0" value="50" style="width:100%;"> 
            <!--<input type="range" min="0" max="100" value="50" class="slider" id="rentangopacity"> -->
<script>
    
</script>
    </div>
    <script>
        function viewtool(){
        var kliktool = document.getElementById('divbuttontool');
        var tampiltool = document.getElementById('divtools');
        var klikcarixy = document.getElementById('buttoncarixy');
            if(tampiltool.style.display != 'block'){
                tampiltool.style.display='block';
            } else {
                tampiltool.style.display='none';
            }
            
        }
    </script>

</head>
<style>
    #divpetadasar{
        width: 100%; 
        height: 96vh;
    }
</style>
<body>
<script src='src/L.LatLng.UTM.js'></script>
<center><div id="teks"></div></center>
	<div id='divpetadasar'></div>
<?php
if(!isset($_POST['inputxy'])){
    $xy = '-7.716342, 110.354811';
}else{
    $xy = $_POST['inputxy'];
}
$dataxy = preg_replace('/[^0-9 .\-,]/', '', $xy);
?>  
<script>
//  menambahkan peta dasar
	var peta = L.map('divpetadasar', {
    fullscreenControl: {//menambahkan fungsi fullscreen
        pseudoFullscreen: false}
    }).setView([<?= $dataxy ?>], 20); //default 15

//ambil nilai radio PEta DASar
</script>

<?php 
if(isset($_POST['radioviewpeta'])){
    echo $_POST['radioviewpeta'];
} else { ?>

<script>
window.onload = L.tileLayer('src/blankmap.png', {
		maxZoom: 30,
		attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, ' +
			'Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
		id: 'mapbox/streets-v11',
		tileSize: 512,
		zoomOffset: -1
	}).addTo(peta);

function tampilpedas(basemapname){
	L.tileLayer(basemapname, {
		maxZoom: 30,
		attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, ' +
			'Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
		id: 'mapbox/streets-v11',
		tileSize: 512,
		zoomOffset: -1
	}).addTo(peta);
}
</script>
<?php } ?>

 </script>
 <?php 
    if(isset($_POST['inputxy'])) { ?>

<script>
    var titikpeta = L.marker([<?= $dataxy ?>]).addTo(peta);
    </script> 

 <?php
    }
?>

<script>    
 //menambahkan data dari file geojson
 //default format 
 /*
 L.geoJSON(data, {
    style: function (feature) {
        return {color: feature.properties.color};
    }
}).bindPopup(function (layer) {
    return layer.feature.properties.description;
}).addTo(map);
*/
    var style = {
        weight: "3",
        color: "red",
        opacity: "1",
        fillColor: "purple",
        fillOpacity: "0.5"
    };

    function popUp(f,l){
    var out = [];
    if (f.properties){
        //for(key in f.properties){
            //out.push(key+": "+f.properties[key]);
        //}
            out.push("<font style='color:blue'>Map Title</font>");
            out.push("Name : " + "<b>XYZ Ltd.");
            out.push("Function : " + "small office");
            out.push("Area : " + "<?= number_format(1.100,0, ',', '.') ?> m<sup>2</sup>");
            out.push("No. Permit : " + "<b>001/20/Gov</b>");
            out.push("Date Permit : " + "Mar 01, 1981");
            out.push("Status : " + "<b>valid</b>");
    <?php } ?>
        l.bindPopup(out.join("<br />"));
    }}

var jsonpeta = new L.GeoJSON.AJAX (
    ["xyz.json"],
    { onEachFeature:popUp, 
    style:style }
    ).addTo(peta);
</script>

<?php } ?>
</body>
<style>
    a{
        text-decoration:none;
        color:white;
    }
</style>
<div style="position:fixed; background-image:linear-gradient(0deg, silver, blue, silver); height:30px; width:100vw; bottom:0px; left:0px; z-index:1030;">
    <div style="position:fixed; bottom:5px; left:-5px; font-face:italic; font-size:12; color:white; z-index:1031;"><?php require '../../func/get_ip-browser.php'; echo $_IP_ADDRESS.' '.get_client_browser().' '.$_bacaMAC; ?></div>
    <span style="position:fixed; bottom:5px; right: 5px; font-face:italic; font-size:12; color:white; z-index:1031; text-decoration:none;">
    <a href="https://leafletjs.com" title="A JS library for interactive maps">Leaflet</a>
    | Map data © 
    <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a>
    contributors, Imagery © 
    <a href="https://www.mapbox.com">Mapbox</a>
    &copy;<i> 2019-<?= date("Y");?> <a href="https://www.instagram.com/4di.sk"> Adi Susetyo Kurnianto, S.STP</a></i>&nbsp &nbsp &nbsp </span>
</div>
</html>
