#### Módulo 1: Infraestrutura declarativa e Modelo de Estado (Semanas 1 e 2)

* **Conceito & Arquitetura:**
  * Funcionamento interno de ferramentas IaC: Grafos de dependência, chamadas de API idempotentes e sincronização de estado local vs. remoto.
  * Gerenciamento de segredos, concorrência no arquivo de estado e prevenção de *drift* de infraestrutura.


* **Desafio Prático (Proof-of-Work 1):**
  * Desenhe e implemente um módulo declarativo para subir uma VPC estruturada (subnets públicas/privadas, tabelas de roteamento, gateway e instâncias) na AWS ou LocalStack.
  * O estado deve ser sincronizado com backend remoto (S3 + DynamoDB para locking).


* **Papel do Mentor:** Validar a topologia de rede proposta, questionar decisões de segurança (Security Groups e escopo de IPs) e forçar a identificação do impacto de cada mudança no grafo antes da aplicação.

