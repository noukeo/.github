## 🦉 Noukeo

<p align="center">
  <img width=400px src="/ressources/noukeo_no_bg.png" />
</p>

[**Noukeo**][website] is an open-source project aimed at simplifying the bootstrapping of microservice projects. The project is currently implemented in Java 11 and uses the Vert.x 4.0.0 library. The primary goal of [**Noukeo**][website] is to provide a streamlined, efficient development process for microservices, allowing developers to quickly create and deploy new services with minimal overhead.

[**Noukeo**][website] relies on Hazelcast for communication between different services, leveraging its powerful distributed computing capabilities to enable efficient, reliable communication between different components of the microservice architecture. Hazelcast also provides high-performance data storage and retrieval, making it an ideal choice for use in a microservice environment.

Overall, [**Noukeo**][website] represents a powerful tool for developers looking to create and deploy microservices quickly and efficiently. With its intuitive, streamlined interface and powerful underlying technology, [**Noukeo**][website] is an ideal choice for any organization looking to take advantage of the benefits of microservice architecture.

[**Noukeo**][website] can be used with the [crustil][] tool.

```mermaid
flowchart LR
    * ---> Traefik
    Traefik -- Health check ---> health-service
    Traefik -- Health check ---> api-gateway
    Traefik -- HTTP ---> api-gateway
    subgraph HTTP
    api-gateway -- HTTP ---> token-service
    api-gateway -- HTTP ---> path-service
    api-gateway -- HTTP ---> login-service
    api-gateway -- HTTP ---> group-service
    api-gateway -- HTTP ---> law-service
    api-gateway -- HTTP ---> account-service
    end
    subgraph SQL
    token-service -- SQL ---> id1[(Sql Cluster)]
    path-service -- SQL ---> id1[(Sql Cluster)]
    group-service -- SQL ---> id1[(Sql Cluster)]
    law-service -- SQL ---> id1[(Sql Cluster)]
    account-service -- SQL ---> id1[(Sql Cluster)]
    end
    subgraph EventBus
    health-service -- EventBus ---> Hazelcast
    api-gateway -- EventBus ---> Hazelcast
    token-service -- EventBus ---> Hazelcast
    path-service -- EventBus ---> Hazelcast
    login-service -- EventBus ---> Hazelcast
    group-service -- EventBus ---> Hazelcast
    law-service -- EventBus ---> Hazelcast
    account-service -- EventBus ---> Hazelcast
    end
```

[crustil]: https://github.com/crustil/crustil

[website]: https://noukeo.provider.ooo

[api-gateway]: https://github.com/noukeo/nk-api-gateway