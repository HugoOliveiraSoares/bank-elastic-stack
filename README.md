# nubank-stack

Nubank Stack

### Front
* Web - Cliente responsivo 

1. Wallet

    ![](doc/wallet.png)

2. Income

    ![](doc/income-cdi.png)

### Infra
* Load Balance - Redirecionador de requisições 
* MongoDB      - Persistência

```mermaid
graph TD
    A[fa:fa-mobile Client] -->|:3000/*| B[fa:fa-server FrontEnd]
    B -->|:3005/*| C[fa:fa-balance-scale Load Balancer]
    C -->|:8081/account| D[fa:fa-server Account]
    C -->|:8082/income| E[fa:fa-server Income]
    C -->|:8083/wallet| F[fa:fa-server Wallet]
    D -->|:27017| G[fa:fa-database NoSQL]
    E -->|:27017| G
    F -->|:27017| G
```

### Backend
- [x] [Income](backend/income)  - Microsserviço responsável pela parte de rendimentos
- [x] [Wallet](backend/wallet)   - Microsserviço responsável pela parte de carteiras
- [ ] [Account](backend/account)  - Contains methods to access the user account details and the checking account transactions and bills
- [ ] [Auth](backend/auth)     - Authentication operations
- [ ] [Card](backend/card)     - Contains methods to retrieve the feed of transactions from the credit card
- [ ] [Payment](backend/payment)  - Contains methods to create payment requests




### How to run

```
docker-compose up
```

Then access 

http://localhost:3000

SwaggerUI

http://localhost:9090

All Services 

| Service      | Network |  Port |
|--------------|:-------:|------:|
| Web          |  Front  |  3000 |
| Load balance |  Front  |  3005 |
| SwaggerUI    |  Front  |  9090 |
| Income       |  Back   |  8081 |
| Wallet       |  Back   |  8082 |
| Account      |  Back   |  8083 |
| MongoDB      |  Back   | 27017 |



### Ref

* [mermaid-editor](https://mermaidjs.github.io/mermaid-live-editor)