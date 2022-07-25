## proxy patttern
A proxy is a structural design pattern that lets you provide a substitute or placeholder for another object. A proxy controls access to the original object, allowing you to perform something either before or after the request gets through to the original object.

## why ?
To tackle this situation you can use lazy loading of that resource-intensive class.

## how ?
We need to create an interface that is a substitute for the original class object. If you need to execute something either before or after the primary logic of the class, the proxy lets you do this without changing that class. Since the proxy implements the same interface as the original class, it can be passed to any client that expects a real service object.

## how does it work in magento?

We are using dependency injection to manage all our dependencies in Magento 2,we have product view  class is also having few more dependencies, so Magento’s centralized object creation process (DI by object manager) try to create an instance of all the dependency and it creates a chain reaction of object instantiation process. If the object particularly resources intensive, this can lead to unnecessary performance impact when another class depends on it. If the resource-intensive object is not needed in our code then it will impact the site performance.

In this case, proxy patterns come in. Proxy classes are also known as lazy loading classes because the actual call will not be made until it requires.
 Proxies are generated code and therefore do not need to be manually written. Simply reference a class in the form \Original\Class\Name\Proxy, and the class is generated if it does not exist.
 
 Let’s take a looks at another Proxy class `Magento\Catalog\Model\Config\Proxy` extend the main class(Config) and implement `NoninterceptableInterface`
 
 ```
 /**
 * Proxy class for @see \Magento\Catalog\Model\ProductTypes\Config
 */
class Proxy extends \Magento\Catalog\Model\ProductTypes\Config implements \Magento\Framework\ObjectManager\NoninterceptableInterface
{
 ```
 
 The proxy class overrides all the methods present in the main class and calls the functions through the requested object
 
 ```mermaid
 flowchart TB 
  A[`Magento\Catalog\Model\Config`] --- |requested object by _getSubject| B[ `Magento\Catalog\Model\Config\proxy` ] --- C[ custom class ]
  ```
