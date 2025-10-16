---
tags:
  - unicap
  - graduação
  - 6-periodo
  - projeto-extensão
---

**Professor:** Pedro Henrique
**Período:** Ago 2025 - Dez 2025
**Nota final:** TBA

# Lojinha IA
- Business Case e Blueprint:
	- [[Projeto PDAE - Business Case & Blueprint.pdf | Apresentação de Business Case e Blueprint]]
	- [Base de Cálculo](https://universidadecatolica-my.sharepoint.com/:x:/r/personal/julia_00000849304_unicap_br/Documents/Base%20de%20calculo%20-%20Business%20case%20(Lojinha%20IA).xlsx?d=w340888e4504042388cd450e41d030fe2&csf=1&web=1&e=iAnZpi)
	- [Slides Apresentações](https://universidadecatolica-my.sharepoint.com/:p:/r/personal/julia_00000849304_unicap_br/_layouts/15/Doc.aspx?sourcedoc=%7BAF1CE746-E6AC-4A68-AFE3-44C9EF340343%7D&file=Lojinha%20IA%20-%20Business%20Case%20&%20Blueprint.pptx=&nav=eyJzSWQiOjI2NCwiY0lkIjo4MzI1ODA0NTB9&action=edit&mobileredirect=true)
	- Materiais de Apoio:
		- [[Modelo de Criação PDAE - Business Case.pdf]]
		- [[Modelo de Criação PDAE - Blueprint.pdf]]
		- [[Modelo de Criação PDAE - Base de Cálculo.png]]
- Design:
	- Casos de Uso
- Desenvolvimento:
	- [Drive com aulas n8n](https://drive.google.com/drive/folders/1aZcf7Hy9vcyIWfhep2jwZYOgLXN6D2_f?usp=drive_link)
	- [Repositório Git](https://github.com/c3-disciplina-ResidenciaSoftwareAVANADE/Lojinha_IA)
	- [Kanban Git](https://github.com/orgs/c3-disciplina-ResidenciaSoftwareAVANADE/projects/1)
### Equipe: 
- Eduardo Braga
- Henrique Franca
- Isabela Medeiros
- Júlia Galvão
- Rafael Angelim
### Resumo:
O projeto "Lojinha IA" visa desenvolver uma plataforma de vendas conversacional, utilizando um chatbot inteligente como o principal ponto de contato com o cliente. A solução tem como objetivo principal automatizar e humanizar a experiência de compra online, oferecendo aos clientes um assistente virtual capaz de responder a perguntas, fornecer detalhes sobre produtos e gerenciar pedidos, tudo através de uma interface de chat. Além disso, o sistema servirá como uma ferramenta de análise de dados para a equipe interna, com diferentes níveis de acesso para funcionários e proprietários.
### Contexto e Problema a Ser Resolvido:
A empresa já opera com uma loja virtual, mas a plataforma apresenta baixa adesão e um volume de vendas insatisfatório. A causa central para este baixo desempenho é a falta de uma comunicação interativa e humanizada, que permita aos clientes tirar dúvidas e receber o suporte que normalmente teriam com um vendedor em uma loja física.
Essa lacuna na comunicação resulta em uma experiência de compra impessoal e em baixas taxas de conversão. O objetivo estratégico do projeto é, portanto, fortalecer o canal de vendas digital para torná-lo mais eficiente, viabilizando a **redução da dependência das lojas físicas e a otimização da equipe de vendas**, que hoje em dia, a empresa conta com 50 lojas físicas no país, com 25 vendedores em cada.
### Objetivos do Projeto:
- **Centralizar Vendas no Chat:** Criar um chatbot que conduza todo o processo de venda, desde a descoberta do produto até o fechamento do pedido.
- **Melhorar a Experiência do Cliente:** Oferecer um "vendedor IA" que forneça descrições detalhadas de produtos, compare itens, informe preços e responda a perguntas em tempo real.
- **Automatizar Processos:** Implementar funcionalidades automáticas como cálculo de frete a partir do CEP e armazenamento de pedidos (concluídos e abandonados) e coleta de dados de interação.
- **Disponibilizar Análises Automatizadas:** Desenvolver uma interface onde a equipe interna possa consultar, de forma simples, os dados e as análises sobre vendas e comportamento do consumidor gerados pela IA.
### Funcionalidades Detalhadas:
O sistema será acessado por três tipos de usuários, cada um com permissões específicas:
**1) Para o Cliente (Chat de Vendas - Telegram):
- **Atendimento Interativo:** O cliente poderá fazer perguntas em linguagem natural, como "quais marcas de `produto` você tem?", "qual o mais barato?" ou "qual o preço por unidade?".
- **Cálculo de Frete:** O chatbot solicitará o CEP do cliente e consultará o banco de dados para informar o valor do frete automaticamente.
- **Gestão de Pedidos:** Todo o processo de seleção de produtos e fechamento do pedido será realizado dentro do chat, que armazenará tanto os pedidos concluídos quanto os carrinhos abandonados (com expiração em 1 ano).
**2) Para o Funcionário (Chat Interno - Acesso para Consulta):**
- **Acesso por Chat Seguro:** A interação será através de um chatbot interno (controlado via n8n), separado do chat público do cliente.
- **Consultas de Dados:** O funcionário poderá fazer perguntas ao bot para obter informações sigilosas em **modo de apenas visualização**.
- **Exemplos de Perguntas:** "Qual foi o faturamento de ontem?", "Liste os 5 produtos mais vendidos da semana" ou "Quantos carrinhos foram abandonados hoje?".
**3) Para o Dono/Administrador (Chat Interno - Acesso Total):**
- **Acesso Administrativo por Chat:** Utilizando a mesma interface de chat interna segura, o proprietário terá acesso administrativo completo.
- **Consultas e Comandos:** Além de poder fazer todas as consultas do funcionário, o dono poderá executar comandos para **visualizar e alterar dados** do sistema.
- **Exemplos de Comandos:** "Alterar o preço do 'Produto X' para R$ 99,90", "Gerar relatório financeiro de agosto" ou "Verificar logs de acesso do sistema".

### Atividades para Desenvolvimento:

#### Cores:
| Desenvolvimento | `#3B82F6` | Azul: Uma cor clássica para tecnologia e construção, representando o trabalho principal de codificação. |
| --------------- | --------- | ------------------------------------------------------------------------------------------------------- |
| Configuração    | `#F97316` | Laranja: Representa a energia da preparação e da montagem da fundação do projeto.                       |
| Testes          | `#8B5CF6` | Violeta: Uma cor que se destaca e é frequentemente associada à lógica e resolução de problemas.         |
| Documentação    | `#EAB308` | Amarelo/Dourado: Associado a informação, conhecimento e clareza.                                        |
| Processo        | `#22C55E` | Verde: Para atividades de coordenação, reuniões e validações (UAT), indicando progresso e alinhamento.  |

---
#### 01 - Infraestrutura e Configuração:
| Atividade                           | Descrição                                                                                   | Dificuldade | Membros | Tipo                           |
| :---------------------------------- | ------------------------------------------------------------------------------------------- | ----------- | ------- | ------------------------------ |
| **Configurar Instância MongoDB**    | Criar a conta e o cluster no MongoDB que hospedará o banco de dados.                        | XS          | 2       | Configuração                   |
| **Definir Coleções no MongoDB**     | Criar as coleções: `produtos`, `pessoas`, `carrinho`, `compra`, etc.                        | S           | 2       | Configuração                   |
| **Migrar Dados (Excel -> MongoDB)** | Criar um fluxo/script no n8n para popular o novo banco com os dados das planilhas iniciais. | M           | 2       | Desenvolvimento / Configuração |
| **Configurar Bot do Telegram**      | Criar o bot no Telegram para obter o token de acesso.                                       | XS          | 1       | Configuração                   |
| **Conectar n8n com MongoDB**        | Criar o nó de credencial no n8n e validar a conexão com o banco de dados.                   | S           | 1       | Configuração / Desenvolvimento |
| **Conectar n8n com OpenAI**         | Validar o uso da chave da API da OpenAI em um fluxo simples.                                | S           | 1       | Configuração / Desenvolvimento |

#### 02 - Chat de vendas:
| Atividade                              | Descrição                                                                                                                | Dificuldade | Membros | Tipo            |
|:-------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | ----------- | ------- | --------------- |
| **Fluxo de Atendimento**               | Criar o fluxo principal no n8n que recebe mensagens do Telegram, processa na OpenAI e responde ao cliente.               | L           | 2       | Desenvolvimento |
| **Fluxo de Consulta de Produtos**      | Implementar a lógica para o cliente perguntar sobre produtos (ex: "quais marcas você tem?") e o bot consultar o MongoDB. | L           | 2       | Desenvolvimento |
| **Fluxo de Gerenciamento de Carrinho** | Desenvolver a lógica para adicionar/remover itens do carrinho do cliente durante a conversa.                             | M           | 2       | Desenvolvimento |
| **Fluxo de Cálculo de Frete**          | Criar a etapa que solicita o CEP e retorna o valor do frete.                                                             | S           | 1       | Desenvolvimento |
| **Fluxo de Fechamento de Pedido**      | Desenvolver a lógica para finalizar a compra, salvando o pedido.                                                         | M           | 2       | Desenvolvimento |

#### 03 - Chat de consulta: 
| Atividade                                  | Descrição                                                                                      | Dificuldade | Membros | Tipo            |
| :----------------------------------------- | ---------------------------------------------------------------------------------------------- | ----------- | ------- | --------------- |
| **Configurar Bot Interno e Autenticação**  | Criar um bot separado e um fluxo no n8n para validar se o usuário é funcionário ou dono.       | M           | 3       | Desenvolvimento |
| **[Funcionário] Consulta de Faturamento**  | Permitir que funcionários perguntem "qual o faturamento de ontem?" e o bot consulte o MongoDB. | S           | 2       | Desenvolvimento |
| **[Funcionário] Consulta de Demanda**      | Implementar a consulta para "liste os 5 produtos mais vendidos".                               | S           | 2       | Desenvolvimento |
| **[Dono] Alteração de Dados**              | Desenvolver o comando administrativo para alterar preço de produtos e estoque.                 | M           | 3       | Desenvolvimento |
| **[Dono] Geração de Relatório Financeiro** | Criar um fluxo que agregue dados de um período e gere um relatório simples.                    | L           | 3       | Desenvolvimento |

#### 04 - Testes:
| Atividade                                  | Descrição                                                                                                            | Dificuldade | Membros | Tipo                     |
| :----------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | ----------- | ------- | ------------------------ |
| **Elaborar Casos de Teste**                | Documentar os testes a serem realizados para cada funcionalidade desenvolvida.                                       | M           | 3       | Documentação / Testes    |
| **Executar Testes Unitários e Integrados** | Realizar testes contínuos durante o desenvolvimento para garantir que os componentes (n8n, IA, DB) funcionem juntos. | L           | 3       | Desenvolvimento / Testes |

#### 05 - Homologação & Depoly:
| Atividade                                | Descrição                                                                                       | Dificuldade | Membros | Tipo                             |
| :--------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------- | ------- | -------------------------------- |
| **Preparar Ambiente e Roteiro para UAT** | Configurar um ambiente de homologação e criar um guia para os stakeholders validarem a solução. | S           | 2       | Documentação / Processo          |
| **Sessão de UAT com Stakeholders**       | Executar a sessão de testes com o cliente para coleta de feedback e aprovação final.            | M           | 5       | Documentação / Processo / Testes |
| **Aplicar Ajustes Finais pós-UAT**       | Implementar as correções e melhorias identificadas durante a homologação.                       | M           | 2       | Desenvolvimento                  |
| **Documentação Final do Código**         | Documentar todo o código e funcionalidades.                                                     | M           | 3       | Documentação                     |
| **[ENTREGA] Go-live da Solução**         | Executar o deploy e realizar a entrega final do projeto no dia 14/11.                           | S           | 5       | Processo                         |

eu = 41
henrique = 41
bela = 40
julia = 41
rafa = 41

### ...
