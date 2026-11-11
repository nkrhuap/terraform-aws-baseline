#### Módulo 1: Infraestrutura declarativa e Modelo de Estado (Semanas 1 e 2)

* **Conceito & Arquitetura:**
  * Funcionamento interno de ferramentas IaC: Grafos de dependência, chamadas de API idempotentes e sincronização de estado local vs. remoto.
  * Gerenciamento de segredos, concorrência no arquivo de estado e prevenção de *drift* de infraestrutura.
Análise de Regressão e Validação Estática (Shift-Left Security):
  * Uso de linters de HCL (`tflint`) e análise de segurança de código de infraestrutura (`tfsec` ou `checkov`) antes mesmo do plano ser gerado.
  * Estruturação de variáveis estritas com validações nativas do Terraform (`validation` block com regex/condicionais) e distinção entre variáveis de ambiente, segredos e outputs exportáveis.

* **Desafio Prático (Proof-of-Work 1):**
  * Desenhe e implemente um módulo declarativo para subir uma VPC estruturada (subnets públicas/privadas, tabelas de roteamento, gateway e instâncias) na AWS ou LocalStack.
  * O estado deve ser sincronizado com backend remoto (S3 + DynamoDB para locking).
  * Incluir uma interface de comandos simples para padronizar as checagens (ex: `make lint`, `make plan`, `make validate`) garantindo reprodutibilidade no ambiente.
  * Além do S3 + DynamoDB para lock, configurar versionamento no bucket S3 e criptografia em repouso (at-rest) via SSE-S3 ou KMS nativo.
  * Diagrama visual da topologia de rede criada e da arquitetura do backend de estado.
  * Tabela explicativa de cada decisão de design (ex: motivo da escolha do bloco CIDR `/16`, estratégias de subnets e segurança).

* **Papel do Mentor:** Validar a topologia de rede proposta, questionar decisões de segurança (Security Groups e escopo de IPs) e forçar a identificação do impacto de cada mudança no grafo antes da aplicação. Questionar o comportamento do estado quando ocorrem edições manuais no painel da nuvem (out-of-band changes) e como detectar/corrigir o drift. Avaliar se o código é genérico, modularizado e limpo, recusando o uso de valores hardcoded (magic strings/IPs) ou segredos expostos nos arquivos `.tf`.

