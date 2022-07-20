## what is it ? 

- It represents the application context in which the action is executed. 

**For example** the registry or the request object.

``` \Magento\Framework\App\Action\Context ``` is ``` ActionContext``` It represents the application context in which the action is executed.
It gives you access to all objects with application state that a controller action needs,

## problem
when extension developer need to perform basic task getRequest() or getLayout() he/she needs to  pass lots of parameters to constructor as a  parameter. 

Main problem is to determine context of  ```$this``` in code 

In Magento 1 Abstract classes with a lot of "helper" behaviour were considered a convenient API for class extender. This caused huge numbers of methods and implicit dependencies in abstract classes (AbstractModel, AbstractBlock, AbstractAction)

> It abondon inheritance-based APIs with interface-based APIs.



## solution

Context object in to store all these functions. When you want to use it, just inject the Context object in the Constructor to be able to use it.


However, the Context object doesn't have its functionality, it just acts as a container. So you will see parent::__construct($context); used a lot in child class.

Usually Context Objects are used in Block, Helper and Model. 

##### list of commonly used Context object functions.

###### Block 
```
$context->getRequest(); // return \Magento\Framework\App\RequestInterface
$context->getUrlBuilder(); // return \Magento\Framework\UrlInterface
$context->getScopeConfig(); // return \Magento\Framework\App\Config\ScopeConfigInterface
$context->getLogger(); // return \Psr\Log\LoggerInterface
$context->getEventManager(); // return \Magento\Framework\Event\ManagerInterface
$context->getStoreManager(); // return \Magento\Store\Model\StoreManagerInterface
$context->getPageConfig(); // return \Magento\Framework\View\Page\Config
$context->getFilesystem(); // return \Magento\Framework\Filesystem
$context->getViewFileSystem(); // return \Magento\Framework\View\FileSystem
$context->getAppState(); // return \Magento\Framework\App\State
$context->getCache(); // return \Magento\Framework\App\CacheInterface
$context->getSession(); // return \Magento\Framework\Session\SessionManagerInterface
$context->getInlineTranslation(); // return \Magento\Framework\Translate\Inline\StateInterface
$context->getEscaper(); // return \Magento\Framework\Escaper
$context->getLocaleDate(); // return \Magento\Framework\Stdlib\DateTime\TimezoneInterface
$context->getDesignPackage(); // return \Magento\Framework\View\DesignInterface
$context->getLayout(); // return \Magento\Framework\View\LayoutInterface
$context->getSidResolver(); // return \Magento\Framework\Session\SidResolverInterface
$context->getAssetRepository(); // return \Magento\Framework\View\Asset\Repository
$context->getViewConfig(); // return \Magento\Framework\View\ConfigInterface
$context->getCacheState(); // return \Magento\Framework\App\Cache\StateInterface
$context->getFilterManager(); // return \Magento\Framework\Filter\FilterManager
```


###### Helper
```
$context->getRequest(); // return \Magento\Framework\App\RequestInterface
$context->getUrlBuilder(); // return \Magento\Framework\UrlInterface
$context->getScopeConfig(); // return \Magento\Framework\App\Config\ScopeConfigInterface
$context->getLogger(); // return \Psr\Log\LoggerInterface
$context->getEventManager(); // return \Magento\Framework\Event\ManagerInterface
$context->getModuleManager(); // return \Magento\Framework\Module\Manager
$context->getCacheConfig(); // return \Magento\Framework\Cache\ConfigInterface
$context->getHttpHeader(); // return \Magento\Framework\HTTP\Header
$context->getRemoteAddress(); // return \Magento\Framework\HTTP\PhpEnvironment\RemoteAddress
$context->getUrlEncoder(); // return \Magento\Framework\Url\EncoderInterface
$context->getUrlDecoder(); // return \Magento\Framework\Url\DecoderInterface
```

###### Model 
```
$context->getLogger(); // return \Psr\Log\LoggerInterface
$context->getCacheManager(); // return \Magento\Framework\App\CacheInterface
$context->getEventDispatcher(); // return \Magento\Framework\Event\ManagerInterface
$context->getAppState(); // return \Magento\Framework\App\State
$context->getLogger(); // return \Psr\Log\LoggerInterface
```

