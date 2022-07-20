## Dependency Injection

> It's another object class needs to functions. 

```mermaid

  flowchart LR
  subgraph B[other class]
  end
  subgraph A[class]
  end
  subgraph C[dependency]
  end
  A--->|use|B
  A x--x C
  C x--x B
```

## Example 

- Model  class depends upon database 

```mermaid

  flowchart LR
  subgraph model[model]
  end
  subgraph database[Database]
  end
  subgraph C[Dependency]
  end
  model--->|Fetch|database
  model x--x C
  C x--x database
```

## Injecting Dependencies

Inject Dependencies means just push dependencies into class from outside(magento2 use di.xml). 

> you shouldn't instaniate depencies using new operation inside the class

Take dependency as constructor parameter or be a settter. As model class take database object as constructor parameter as depedency push(**inject**) .

you don't need fancy container (DIC, services container,pimple) 

```mermaid

  flowchart RL
  subgraph model[model]
  end
  subgraph database[Database as Dependency]
  end
  database--->|push|model
```
```public function __construct (Database $db)```

## why

Instead of create object everytime needed 

## Dependency Inversion Principal

```mermaid

  flowchart LR
  subgraph A[class]
  end
  subgraph B[dependency]
  end
  subgraph C[Interface]
  end
  style B fill:#bbf,stroke:#f66,stroke-width:2px,color:#fff,stroke-dasharray: 5 5
  A x--x|shouldn't depend upon dependency|B
  A --->|should depend upon | C
```
it should depend upon abstract so that it decouple implementation from dependency. It should depend upon interface.
we subtitute dependency as long as it satisfy required inteface . 

- It decouple code low-level implementation
- Easier to modify and reuse

## Problem !

As Adopted DI, class need dependencies **we need to figure out what depedencies they need?** and **how to instantiate the dependencies?**

## Solution

**Dependency Injection Container**  (Service Locator)

```mermaid

  flowchart LR
  subgraph A[class A]
  end
  subgraph B[class B]
  end
  subgraph C[dependencies 1]
  end
  subgraph D[dependencies 2]
  end
  subgraph E[dependencies 3]
  end
  subgraph F[dependencies 4]
  end
  subgraph Dependency Injection Container
  A ---> C
  A ---> D
  B ---> E
  B ---> F
  end
```

```
class A => array("dependencies 1","dependencies 2")
class B => array("dependencies 3","dependencies 4")
```
> It's map of dependencies class needs with logic to create those dependencies if they haven't been created yet. 
```mermaid
flowchart TD
    A[request for dependency getDependency] --> B[find dependency in container] --> C{do we have it loaded?}
    C -- yes --> D[return object]
    C -- No --> E[load dependency]
    E --> D
    B -- No ----> E[create dependency instance->store in DIC ]
```
so everytime asked for dependency array map figure out which dependency to use then container check if those dependency create already if it have return object/dependency otherwise cretate dep & store and return instead of construction of all class yourself you aske container for new instance or  resolve dependency construction, object container resolve dependency transparently you need & update container(DIC). 
## Benefit

- Abstraction
- More Modular
- More Flexible










