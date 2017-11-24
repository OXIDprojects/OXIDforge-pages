# Exception log seems to be cut off somehow

```
OxidEsales\EshopCommunity\Core\Exception\SystemComponentException-OxidEsales\EshopCommunity\Core\Exception\StandardException (time: 2017-11-20 21:16:50): [0]: EXCEPTION_SYSTEMCOMPONENT_CLASSNOTFOUND Utils 
 Stack Trace: #0 [internal function]: OxidEsales\EshopCommunity\Core\UtilsObject->oxNew('OxidEsales\\Esho...')
#1 C:\xampp\htdocs\oxid6\my_oxid_eshop_project\source\oxfunctions.php(103): call_user_func_array(Array, Array)
#2 C:\xampp\htdocs\oxid6\my_oxid_eshop_project\vendor\oxid-esales\oxideshop-ce\source\Core\Registry.php(377): oxNew('OxidEsales\\Esho...')
#3 C:\xampp\htdocs\oxid6\my_oxid_eshop_project\vendor\oxid-esales\oxideshop-ce\source\Core\Registry.php(393): OxidEsales\EshopCommunity\Core\Registry::createObject('OxidEsales\\Esho...')
#4 C:\xampp\htdocs\oxid6\my_oxid_eshop_project\vendor\oxid-esales\oxideshop-ce\source\Core\Registry.php(119): OxidEsales\EshopCommunity\Core\Registry::getObject('OxidEsales\\Esho...')
#5 C:\xampp\htdocs\oxid6\my_oxid_eshop_project\vendor\oxid-esales\oxideshop-ce\source\Core\Session.php(811): OxidEsales\EshopCommunity\Core\Registry::getUtils()
#6 C:\xampp\htdocs\oxid6\my_oxid_eshop_project\vendor\oxid-esales\oxideshop-ce\source\Core\Session.php(212): OxidEsales\EshopCommunity\Core\Session->_allowSessionStart()
#7 C:\xampp\htdocs\oxid6\my_oxid_eshop_project\vendor\oxid-esales\oxideshop-ce\source\Core\UtilsView.php(146): OxidEsales\EshopCommunity\Core\Session->start()
#8 C:\xampp\htdocs\oxid6\my_oxid_eshop_project\vendor\oxid-esales\oxideshop-ce\source\Core\ShopControl.php(714): OxidEsales\EshopCommunity\Core\UtilsView->addErrorToDisplay(Object(OxidEsales\Eshop\Core\Exception\SystemComponentException))
#9 C:\xampp\htdocs\oxid6\my_oxid_eshop_project\vendor\oxid-esales\oxideshop-ce\source\Core\ShopControl.php(139): OxidEsales\EshopCommunity\Core\ShopControl->_handleSystemException(Object(OxidEsales\Eshop\Core\Exception\SystemComponentException))
#10 C:\xampp\htdocs\oxid6\my_oxid_eshop_project\vendor\oxid-esales\oxideshop-ce\source\Core\Oxid.php(26): OxidEsales\EshopCommunity\Core\ShopControl->start()
#11 C:\xampp\htdocs\oxid6\my_oxid_eshop_project\source\index.php(15): OxidEsales\EshopCommunity\Core\Oxid::run()
#12 {main}

 Faulty component --> 

``` 
1. Try setting `xdebug.var_display_max_data`. To disable any limitation, use -1 as value.
2. `oxexception` uses getTraceAsString, which automatically strips StackTrace to limited amount of chars
das in die core/exception/oxexception.php und statt dem call von “getTraceAsString” (bei mir in line 159) rufst du die methode “getExceptionTraceAsString” auf:

```
protected function getExceptionTraceAsString() {
    $rtn = "";
    $count = 0;
    foreach ($this->getTrace() as $frame) {
        $args = "";
        if (isset($frame['args'])) {
            $args = array();
            foreach ($frame['args'] as $arg) {
 				if (is_string($arg)) {
 					$args[] = "'" . $arg . "'";
 				} elseif (is_array($arg)) {
 					$args[] = "Array";
 				} elseif (is_null($arg)) {
 					$args[] = 'NULL';
 				} elseif (is_bool($arg)) {
 					$args[] = ($arg) ? "true" : "false";
 				} elseif (is_object($arg)) {
 					$args[] = get_class($arg);
 				} elseif (is_resource($arg)) {
 					$args[] = get_resource_type($arg);
 				} else {
 					$args[] = $arg;
 				}
 			}
 			$args = join(", ", $args);
 		}
 		$rtn .= sprintf( "#%s %s(%s): %s(%s)\n",
 			$count,
 			$frame['file'],
 			$frame['line'],
 			$frame['function'],
 			$args );
 		$count++;
 	}
 	return $rtn;
}
```
