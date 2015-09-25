### Step 1 ###

Download the latest release of Zamf using the link provided on the project home page or alternatively check-out the latest source using a subversion client such as Tortoise SVN.

### Step 2 ###

Download the latest release of [CakePHP](http://www.cakephp.org) from their website. Be sure to support the project by making a donation!

### Step 3 ###

Download the latest release of [Zend](http://framework.zend.com/download/latest) from their website.

### Step 4 ###

If you are working locally using [WAMP](http://www.wampserver.com) or [MAMP](http://www.mamp.info) you should place the [CakePHP](http://www.cakephp.org) Framework in your _www_ installation folder, or a location you think is suitable. Otherwise just upload the files to your server.

**Example:** _C:\wamp\www\cake\_

### Step 5 ###

Extract the [Zend](http://framework.zend.com/download/latest) Framework and place the entire _Zend_ folder in your projects _vendors_ directory.

**Example:** _C:\wamp\www\cake\app\vendors\_

If for some reason you don't want to include the entire Framework you can simply add the folders and files listed below. However I cannot guarantee this will always work with future versions of [Zend](http://framework.zend.com/download/latest).

  * _C:\wamp\www\cake\app\vendors\Zend\Amf\..._
  * _C:\wamp\www\cake\app\vendors\Zend\Date\..._
  * _C:\wamp\www\cake\app\vendors\Zend\Loader\..._
  * _C:\wamp\www\cake\app\vendors\Zend\Server\..._
  * _C:\wamp\www\cake\app\vendors\Zend\Date.php_
  * _C:\wamp\www\cake\app\vendors\Zend\Exception.php_
  * _C:\wamp\www\cake\app\vendors\Zend\Loader.php_
  * _C:\wamp\www\cake\app\vendors\Zend\Version.php_

### Step 6 ###

With Zamf downloaded and extracted, place the _zend_ folder and all of its contents into your projects _plugins_ directory.

**Example:** _C:\wamp\www\cake\app\plugins\zend\_

### Step 7 ###

Open and edit the file: _C:\wamp\www\cake\app\webroot\index.php_

**Original**
```
if (isset($_GET['url']) && $_GET['url'] === 'favicon.ico') {
    return;
} else {
    $Dispatcher = new Dispatcher();
    $Dispatcher->dispatch($url);
}
```
**Edited**
```
if (isset($_GET['url']) && $_GET['url'] === 'favicon.ico') {
    return;
} else {
    App::import('Vendor', 'Zend.AmfDispatcher');
    $Dispatcher = new Dispatcher();
    $Dispatcher->dispatch($url);
}
```

### Step 8 ###

Open and edit the file: _C:\wamp\www\cake\app\app\_controller.php_ making sure the Zamf plugin is added to the list of components being utilized.

```
<?php
class AppController extends Controller
{
    public $components = array('Zend.Amf');
}
?>
```

### Step 9 ###

Point your gateway to: http://localhost/cake/