##sCSVSign
Separator for Im/Export in Enterprise Edition

##sGiCsvFieldEncloser
Encloser for Im/Export

##blCheckForUpdates
Shop will be checked for version in admin home page only if this option is checked


##sAltImageDir / sSSLAltImageUrl
In case if pictures for articles should be loaded from separate server and are available only through http - it's enough to include sAltImageDir option in config.inc.php. Then to load picture for article only define the rest http path to the image file. Attention: If this option is set in the configuration file config.inc.php, uploading of product pictures in admin area is not possible!
If you are using https, you also have to set the sSSLAltImageUrl option.
<pre>$this->sAltImageDir = "[http://[path_to_images_dir_on_server]/";
$this->sSSLAltImageUrl = "[https://[path_to_images_dir_on_server]/";</pre>

##sCookieDomain
In case you setup different subdomain for SSL/non-SSL pages cookies may not be shared between them. Defines the domain that the cookie is available.

##sAuthOpenIdRandSource
define 'Auth_OpenID_RAND_SOURCE' (filename for a source of   random bytes)
<pre>$this->sAuthOpenIdRandSource  = '/dev/urandom';</pre>

##sCookiePath
possibility to define path on the server in which the cookie will be available on.
<pre>$this->sCookiePath = '/dev/urandom';</pre>

##blForceSessionStart
Force session start on first page view and for users whose browsers do not accept cookies, append sid parameter to URLs.
<pre>$this->blForceSessionStart = "1";</pre>

##aTrustedIPs
Defines IP addresses, for which session + cookie id match and user agent change checks are off.

##blUseTimeCheck
Additionally checks if "oxactivefrom > current date < oxactiveto"

##blUseStock
If value is TRUE checks stock state "( oxstock > 0 or ( oxstock <= 0 and ( oxstockflag = 1 or oxstockflag = 4 ) )"

##sCustomTheme
Is a global config parameter which activates a template override system for an easier design customization and defines 
custom theme directory name in ‘views’ folder. The structure of this custom theme has to be the same as main theme. The 
shop will look up if there is an adapted file in your custom folder; if not it will return to the main folder.

##blLogChangesInAdmin
Log all modifications performed in Admin (in oxadminlog table)
<pre>$this->blLogChangesInAdmin = 0;</pre>

##blMallSharedBasket
Common cart for subshops use together with option in main shop configurations (Mall tab): "Allow users from other shops"

##blSeoMode
Switch off SEO URLs
<pre>$this->blSeoMode = false;</pre>

##iPicCount
Change number of item pictures

##aModules
Some classes can be overloaded, but only by setting up this information in config.inc.php directly
<pre>$this->aModules = array(
‘oxutilsobject’ => ‘my_oxutilsobject’
);
</pre>

##aRequireSessionWithParams
This configuration array specifies additional request parameters, which, if received, forces a new session being started.

This is the default array with the request parameters and their values, which forces a new session: 
<pre>
array(
    'cl' => array(
        'register' => true,
        'account'  => true,
    ),
    'fnc' => array( 
        'tobasket' => true, 
        'login_noredirect' => true, 
        'tocomparelist'    => true,
    ),    
    '_artperpage' => true,
    'ldtype'      => true,
    'listorderby' => true,
);
</pre>

If you want to extend this array include in config.inc.php file this option:
<pre>
$this->aRequireSessionWithParams = array(
    'parameter_name' => array(
        'parameter_value' => true,
    )
);
</pre>
The keys of the array are the names of parameters and the values of the arrays are the parameter values that lead to the 
session being started, e.g:
<pre>
$this->aRequireSessionWithParams = array(
    'fnc' => array(
        'login_noredirect' => true,
    ),
    'new_sid' => true
);
</pre>

##blUseCron
Enables or disables the use of cron jobs in config.inc.php

Implemented with OXID eShop version 4.6.0
<pre>$this->blUseCron = true;</pre>

##iCreditRating
Sets the default value of credit rating

Implemented with OXID eShop version 4.7.3
<pre>$this->iCreditRating = 1000;</pre>

##blEnterNetPrice
Prices will be entered without tax

##blSkipViewUsage
If you can't log in to the admin panel, try setting the parameter blSkipViewUsage temproarily to "true".

Implemented with OXID eShop version 4.7
<pre>$this->blSkipViewUsage = true;</pre>

##sShopLogo
Add your own logo image file, upload it to /out/az ure/img/.

Implemented with OXID eShop version 4.8
<pre>$this->sShopLogo = 'your_own_image.jpg'</pre>

##blDemoShop
Enables shop demo mode
<pre>$this->blDemoShop= true;</pre>

##blDoNotDisableModuleOnError
Disable module auto deactivation

Implemented with OXID eShop versions 5.1.2/4.8.2 and 5.0.11/4.7.11
<pre>$this->blDoNotDisableModuleOnError = false;</pre>
