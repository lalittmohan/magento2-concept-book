## Builder Design Pattern {Creational Pattern}
> Separates object construction from  representation.

## Intent
- Same contruction process can create different type of object and  representation.
![builder](https://refactoring.guru/images/patterns/content/builder/builder-en.png)


#### A typical Builder consists of:

- Concrete class
- A builder interface
- The different builder implementations
- A director class that calls the appropriate builder and return object.


```mermaid
graph TD
  concrete --> method1
  concrete --> method2
  concrete --> method3
  subgraph concrete[concrete class]
  end
  subgraph method1[method1]
  end
  subgraph method2[method2]
  end
  subgraph method3[method3]
  end
  subgraph builder[builder class]
  end
  subgraph build[build & return object]
  end
  method1 --> builder
  method2 --> builder
  method3 --> builder
  builder --> build
  subgraph build[con]
  end
```

## structure

![structure](https://refactoring.guru/images/patterns/diagrams/builder/structure.png) 

<!-- slide:break -->

# 

I have added:

<!-- slide:break -->



<!-- panels:start -->
1.The Builder interface declares product construction steps that are common to all types of builders.
2.
<!-- panels:end -->
## References
[Recfactoring](https://refactoring.guru/design-patterns/builder)

[sourcemaking](https://sourcemaking.com/design_patterns/builder)
