---
tags:
  - unicap
  - graduação
  - 6-periodo
---

**Professor:** Jheymesson Apolinário
**Período:** Ago 2025 - Dez 2025
**Nota final:** TBA

#### Projeto 1GQ: 
- Tema: Data Streaming
	- [[Arquitetura de Sistemas - Projeto Data Streaming em Tempo Real com Apache Kafka.pdf| Slides Data Streaming com Apache Kafka]]
- Nota: 10
#### Prova 1GQ:
- [[Arquitetura de Sistemas - Resumo 1GQ (Ana Bia).pdf| Resumo de Ana Bia]]
- [[Arquitetura de Sistemas - Resumo 1GQ (Bela).pdf| Resumo de Bela]]
- Nota: 6.5
#### Nota 1GQ: 
- (10 * 2 + 6.5 * 8) / 10 =

#### Projeto 2GQ: 
- Tema: Micros serviço: **Laboratório & Diagnósticos**
	- **Responsabilidades:** requisições e resultados de exames (estrutura HL7/FHI Obs), laudos, workflows e validação.
	- **Banco:** MongoDB (variabilidade de resultados) + S3 (PDFs).
	- **API:** /lab-orders, /lab-results.
	- **Eventos:** LabOrderCreated, LabResultAvailable.
- Nota: XX
#### Prova 2º GQ:
- [[Arquitetura de Sistemas - Resumo 2GQ.pdf]]
- Nota: XX
#### Nota 2º GQ: 
- (nota_proj * peso_proj + nota_prova * peso_prova) / 10 = 

#### Média final:
- (nota_1GQ * 2 + nota_2GQ * 3) / 5 =

---
### Prova 2GQ: Microsserviços
#### 1. Segurança e Controle de Acesso: A Fortaleza Digital
Começamos discutindo como proteger nosso castelo. Não adianta ter paredes altas se o porteiro deixa qualquer um entrar, certo? Falamos sobre **Controle de Acesso**, diferenciando modelos clássicos. Vimos o **RBAC** (Role-Based Access Control), onde as permissões são atreladas ao cargo do sujeito, e o **ABAC** (Attribute-Based Access Control), que é mais sofisticado e olha para atributos como horário, local e departamento. Discutimos também a **Criptografia**. Lembra da história da Enigma e dos nazistas? Pois é, a base teórica aqui é entender a diferença entre a criptografia **Simétrica** (rápida, chave única, mas com o problema da distribuição da chave) e a **Assimétrica** (chaves pública/privada, resolve a distribuição, mas é lenta). O segredo do sucesso na web hoje é a **Híbrida**, que junta o melhor dos dois mundos.
#### 2. Webservices e a Comunicação Distribuída
Depois, entramos no mundo da comunicação entre sistemas. Como fazer componentes diferentes conversarem sem virar uma Torre de Babel? Estudamos os **Webservices**. Analisamos o **SOAP**, aquele "velho guerreiro" burocrático baseado em XML e contratos rígidos, ótimo para bancos. Comparamos com o **REST**, que é o "jovem descolado" da web, usando verbos HTTP e JSON, focado em recursos. E não esquecemos do **gRPC**, o "ligeirinho" da Google, que usa binário e Protobuf, perfeito para conversas internas rápidas. A grande lição aqui é entender os _trade-offs_ de cada um: complexidade vs. simplicidade, verbosidade vs. performance.
#### 3. SOA vs. Microsserviços: A Evolução da Espécie
Aqui a coisa ficou séria! Falamos da **SOA** (Service-Oriented Architecture). A SOA trouxe a ideia de serviços autônomos e reutilizáveis, muitas vezes orquestrados por um barramento (ESB). Mas a evolução nos levou aos **Microsserviços**. A diferença crucial teórica é o acoplamento e a governança. Nos microsserviços, focamos em "Smart endpoints and dumb pipes" (pontas inteligentes e canos burros), evitando a lógica centralizada do ESB. Também batemos forte no **DDD** (Domain-Driven Design), usando conceitos como _Bounded Contexts_ para definir onde termina um serviço e começa outro, garantindo que a divisão seja pelo negócio e não pela tecnologia.
#### 4. O Mundo dos Containers
Saindo da abstração total para a virtualização, explicamos o que _realmente_ é um container. Esqueça o comando `docker run` por um minuto. Teoricamente, um container é uma mentira bem contada pelo Sistema Operacional, usando **Namespaces** para isolar o que o processo _vê_ (rede, processos, sistema de arquivos) e **Cgroups** para limitar o que o processo _usa_ (CPU, memória). Entendemos que uma imagem não é mágica, é apenas um sistema de arquivos em camadas (UnionFS) imutáveis. Essa base teórica é o que permite a portabilidade e a eficiência que tanto amamos, sem o peso de uma máquina virtual completa.
#### 5. Arquitetura em Nuvem e Escalabilidade
Por fim, olhamos para as nuvens. Discutimos os modelos de serviço (**IaaS, PaaS, SaaS**) e como a responsabilidade de gerenciamento muda em cada um. Aprofundamos em **Estratégias de Deploy**, porque subir código não é só "dar play". Vimos o **Blue-Green** (troca instantânea, risco baixo, custo alto de infra) , o **Canary** (testar com um pouquinho de gente antes de liberar pra geral) e o **Rolling Update** (troca gradual, sem downtime, mas lento para rollback). Fechamos com a trindade da **Observabilidade**: Logs (o que aconteceu?), Métricas (quanto está acontecendo?) e Tracing (onde diabos está o problema?).

---
### Projeto 2GQ: Laboratório & Diagnósticos 
#### 👩‍💻 Integrante 1: Isabela (A "Especialista em Cloud")

* **Responsabilidade:** Endpoint `LabReports` (`POST /lab-results/<string:result_id>/report`).
* **O que pode falar:**
    * Explicar que essa rota é responsável por receber o **laudo (um arquivo PDF)** e conectá-lo a um resultado de exame que já existe no banco.
    * Mostrar no código a validação para garantir que um arquivo foi realmente enviado (`if 'file' not in request.files:`).
    * Mencionar o uso da biblioteca `werkzeug` com `secure_filename` para tratar o nome do arquivo, uma prática importante de segurança para evitar ataques de *directory traversal*.
    * Explicar como a conexão com a AWS é feita usando a biblioteca `boto3`.
    * Destacar que as credenciais e o nome do *bucket* S3 não estão no código, mas sim em **variáveis de ambiente** (`os.getenv`), como definido no `docker-compose.yml`, o que é uma boa prática.
    * Mostrar a linha `s3.upload_fileobj(...)`, que é o comando que efetivamente envia o arquivo para o *bucket* S3.
    * Explicar a parte final e crucial: `lab_results.update_one(...)`. Após o upload, o código **atualiza o documento no MongoDB** para adicionar a `report_url`, ligando o dado estruturado (resultado) ao dado não estruturado (o PDF no S3).
* **Ponto de Orgulho (O que "mais se orgulha"):**
    > "O que mais me orgulho foi de implementar exatamente o que a arquitetura do projeto pedia para o nosso módulo: o uso de **MongoDB para os metadados** dos exames e **S3 para os laudos em PDF**. Consegui fazer a API receber um arquivo de forma segura, enviá-lo para o S3 e, o mais importante, atualizar o documento no Mongo com a URL do laudo, fechando o ciclo de dados do paciente."

---

#### 👨‍💻 Integrante 2: (Sugestão: Júlia) - Os Endpoints de Consulta (`GET`s)

* **Responsabilidade:** `GET /lab-orders` e `GET /lab-results`.
* **O que pode falar:**
    * Explicar que esses dois *endpoints* são as "portas de leitura" do microserviço.
    * O ponto principal aqui é a **aderência ao padrão FHIR**. A proposta do projeto exige o uso de HL7/FHIR.
    * Mostrar que o código não retorna o dado "cru" do MongoDB. Em vez disso, ele **transforma os dados** para o formato FHIR.
    * No `GET /lab-orders`, mostrar como os campos do Mongo (`patient_id`, `exam_type`, `status`) são mapeados para um recurso FHIR `ServiceRequest`.
    * No `GET /lab-results`, mostrar o mapeamento similar para um recurso FHIR `Observation`.
    * Mencionar a função auxiliar `serialize_id` como um detalhe técnico necessário para converter o `ObjectId` do Mongo em uma *string* JSON legível.
* **Ponto de Orgulho (O que "mais se orgulha"):**
    > "Minha responsabilidade foi garantir que, apesar de usarmos MongoDB internamente, nossa API 'fala' a língua universal da saúde, o **FHIR**. O que mais me orgulho é a **camada de transformação** que criei nos métodos `GET`. Não estamos apenas 'cuspindo' dados do banco; estamos formatando-os como recursos `ServiceRequest` e `Observation`. Isso torna nosso microserviço interoperável e pronto para se conectar com qualquer outro sistema hospitalar que siga o mesmo padrão."

---

#### 👨‍💻 Integrante 3: (Sugestão: Eduardo) - Criação de Pedidos e Eventos (`POST /lab-orders`)

* **Responsabilidade:** `POST /lab-orders`.
* **O que pode falar:**
    * Explicar que este *endpoint* é o **ponto de partida** de todo o fluxo de trabalho do laboratório.
    * Mostrar a validação de *payload* (verificando se `patient_id` e `exam_type` foram enviados).
    * Explicar a criação do documento no MongoDB com o `status` inicial `"requested"`.
    * **Ponto-chave:** Focar na parte de **Arquitetura Orientada a Eventos (EDA)**.
    * Mostrar a linha `events.insert_one(...)` e explicar que, além de salvar o pedido, o serviço **publica um evento** (`LabOrderCreated`).
    * Explicar *por que* isso é importante: outros microserviços (como o de Faturamento ou Notificações) podem "ouvir" esse evento e iniciar seus próprios processos, sem que o nosso serviço de laboratório precise saber que eles existem. Isso se chama **baixo acoplamento**.
* **Ponto de Orgulho (O que "mais se orgulha"):**
    > "Fiquei com o início do nosso fluxo, a criação do pedido de exame. O ponto principal do meu código, e do que mais me orgulho, não é apenas salvar o pedido no banco. É a implementação da **arquitetura orientada a eventos**. Ao criar o pedido, eu também disparo um evento `LabOrderCreated` na coleção de eventos. Isso é a base da arquitetura de microserviços: nosso serviço avisa o que fez, e outros podem reagir a isso sem que a gente precise se acoplar a eles."

---

#### 👩‍💻 Integrante 4: (Sugestão: Henrique) - Registro de Resultados e Lógica de Negócio (`POST /lab-results`)

* **Responsabilidade:** `POST /lab-results`.
* **O que pode falar:**
    * Explicar que este é o *endpoint* mais complexo, pois ele **fecha o ciclo** do exame e coordena dados entre diferentes coleções.
    * **Validação Robusta:** Mostrar que o código valida não apenas o *payload* (os campos obrigatórios), mas também o `order_id`. Ele verifica se o ID é um `ObjectId` válido e, em seguida, se **o pedido realmente existe** (`lab_orders.find_one`). Isso evita que "resultados órfãos" sejam criados.
    * **Enriquecimento de Dados:** Apontar que o `patient_id` é copiado do pedido original para o documento de resultado, garantindo a integridade referencial.
    * **Conclusão do Workflow:** Explicar as três ações que acontecem em sequência:
        1.  Salva o resultado (`lab_results.insert_one`).
        2.  Dispara o evento `LabResultAvailable` (assim como o Integrante 3, mostrando a consistência da arquitetura).
        3.  **Atualiza o pedido original:** Usa `lab_orders.update_one` para mudar o `status` do pedido de `"requested"` para `"completed"`.
* **Ponto de Orgulho (O que "mais se orgulha"):**
    > "Minha função foi registrar o resultado do exame, o que completa o fluxo iniciado pelo pedido. O que mais me orgulho é a **lógica de coordenação e consistência de dados**. O código não apenas salva o resultado; ele primeiro **valida se o pedido original existe** para evitar dados órfãos. Em seguida, ele dispara o evento `LabResultAvailable` e, o mais importante, ele **'volta' na coleção de pedidos e atualiza o status** daquele pedido para `completed`. Isso garante que o estado do nosso sistema permaneça consistente."

---
