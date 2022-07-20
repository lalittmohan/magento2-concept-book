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

Inject Dependencies means just push dependencies into class from outside. 

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

## dependency inversion principal

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
it should depend upon abstract so that it decouple implmentation from dependency. It should depend upon interface.
we subtitute dependency as long as it satisfy required inteface . 

- It decouple code low-level implmentation
- Easier to modify and reuse

## Problem !

As Adopted DI, class need dependencies **we need to figure out what depedencies they need?** and **how to instantiate the dependencies?**





