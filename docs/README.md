**Concepts**

<!-- tabs:start -->
<!-- tab:Architecture -->
|[Indexing](/)| [Caching](/)|[EAV](/)|[Dependency Injection](/)|[Object Manager](/)|[Declarative schemas ](/)|[interceptor](/)|[plugins](/)|[proxies](/)|
| --- | --- | --- | --- | --- | --- | --- | --- | --- |

<!-- tab:Backend -->
<!-- tab:Frontend -->
<!-- tab:UI Component -->
<!-- tab:API -->
<!-- tab:GraphQL -->
<!-- tab:Javascript -->
<!-- tabs:end -->


**code flow**

<!-- tabs:start -->
<!-- tab:ACL -->
|[add role](/)|[edit role](/)|[save role](/)|[delete role](/)|
| --- | --- | --- | --- |
<!-- tab:PRODUCT -->
<!-- tab:ORDER -->
<!-- tab:CUSTOMER -->
<!-- tab:INVENTORY -->
<!-- tab:PRICING -->
<!-- tab:PAYMENT -->
<!-- tab:SHIPPING -->
<!-- tab:SYSTEM -->
<!-- tabs:end -->

**Trends**

<!-- tabs:start -->
<!-- tab:PWA -->
<!-- tab:Headless -->
<!-- tab:Grpc|Microservices -->
<!-- tabs:end -->

@startuml
actor Foo1
boundary Foo2
control Foo3
entity Foo4
database Foo5
collections Foo6
Foo1 -> Foo2 : To boundary
Foo1 -> Foo3 : To control
Foo1 -> Foo4 : To entity
Foo1 -> Foo5 : To database
Foo1 -> Foo6 : To collections
@enduml

