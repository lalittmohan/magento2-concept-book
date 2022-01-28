>Plugins are used to extend (change) the behavior of any native public method within a Magento class. Native methods refer to those Magento class
methods included with a native installation. The behavior of native methods can be changed by creating an extension. Extensions use Plugin classes to
change the behavior of the target methods. Plugins change the behavior of the original class, but not the class itself.

## when it should use?
- [] when use multiple extension for same feature it decrease the probability of  conflicts between extensions

## when can not use it?
- final methods 
- final classes 
- private methods
- classes created without dependency injection.

>Note: Plugins allow you to modify a single method, while a preference allows you to change a whole class.
> interception is known as AOP (Aspect Oriented Programming).