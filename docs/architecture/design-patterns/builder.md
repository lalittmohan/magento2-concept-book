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
<!-- slide:break -->

## structure

![structure](https://refactoring.guru/images/patterns/diagrams/builder/structure.png)

<!-- slide:break -->

1. The **Builder interface** declares product construction steps that are common to all types of builders

2. **Concrete Builders** provide different implementations of the construction steps. Concrete builders may produce products that don’t follow the common interface

3. **Products** are resulting objects. Products constructed by different builders don’t have to belong to the same class hierarchy or interface

4. The **Director** class defines the order in which to call construction steps, so you can create and reuse specific configurations of products.

5. The **Client** must associate one of the builder objects with the director. Usually, it’s done just once, via parameters of the director’s constructor. Then the director uses that builder object for all further construction. However, there’s an alternative approach for when the client passes the builder object to the production method of the director. In this case, you can use a different builder each time you produce something with the director.

## Example

![example](https://sourcemaking.com/files/v2/content/patterns/Builder_example1.png)

<!-- panels:end -->
## References
[Recfactoring](https://refactoring.guru/design-patterns/builder)

[sourcemaking](https://sourcemaking.com/design_patterns/builder)
