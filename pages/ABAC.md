- [[Attribute-based access control]]
- 在基于属性的访问控制（ABAC）中，不是根据认证后与用户相关的主体的权利，而是根据用户的属性来授予访问权。用户必须向访问控制引擎证明关于他或她的属性的所谓主张。基于属性的访问控制策略规定了哪些要求需要得到满足，以便授予对一个对象的访问权。例如，该要求可能是 "18岁以上"。任何能够证明这一要求的用户都被授予访问权。当认证和识别不是严格要求时，用户可以是匿名的。然而，人们确实需要以匿名的方式来证明要求。例如，这可以通过匿名证书来实现。XACML（可扩展访问控制标记语言）是一个基于属性的访问控制标准。XACML 3.0在2013年1月实现了标准化。