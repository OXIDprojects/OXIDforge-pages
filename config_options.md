##sCSVSign
Separator for Im/Export in Enterprise Edition

##sGiCsvFieldEncloser
Encloser for Im/Export

##blCheckForUpdates
Shop will be checked for version in admin home page only if this option is checked


##sAltImageDir
In case if pictures for articles should be loaded from separate server and are available only through http - it's enough to include option in config.inc.php. Then to load picture for article only define the rest http path to the image file. Attention: If this option is set in the configuration file config.inc.php, uploading of product pictures in admin area is not possible!
<pre class="lang:php decode:true">$this-&gt;sAltImageDir = "[http://[path_to_images_dir_on_server]/ http://[path_to_images_dir_on_server]/]";</pre>

