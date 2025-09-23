**Professor:** Pedro Henrique
**Período:** Ago 2025 - Dez 2025
**Nota final:** TBA

## Lojinha IA
- Business Case e Blueprint:
	- [[Projeto PDAE - Business Case & Blueprint.pdf | Apresentação de Business Case e Blueprint]]
	- [Base de Cálculo](https://universidadecatolica-my.sharepoint.com/:x:/r/personal/julia_00000849304_unicap_br/Documents/Base%20de%20calculo%20-%20Business%20case%20(Lojinha%20IA).xlsx?d=w340888e4504042388cd450e41d030fe2&csf=1&web=1&e=iAnZpi)
	- Materiais de Apoio:
		- [[Modelo de Criação PDAE - Business Case.pdf]]
		- [[Modelo de Criação PDAE - Blueprint.pdf]]
		- [[Modelo de Criação PDAE - Base de Cálculo.png]]
- Design:
	- Casos de Uso
- Desenvolvimento:
	- [Drive com aulas n8n](https://drive.google.com/drive/folders/1aZcf7Hy9vcyIWfhep2jwZYOgLXN6D2_f?usp=drive_link)
	- Repositório Git
#### Equipe: 
- Eduardo Braga
- Henrique Franca
- Isabela Medeiros
- Júlia Galvão
- Rafael Angelim
#### Resumo:
O projeto "Lojinha IA" visa desenvolver uma plataforma de vendas conversacional, utilizando um chatbot inteligente como o principal ponto de contato com o cliente. A solução tem como objetivo principal automatizar e humanizar a experiência de compra online, oferecendo aos clientes um assistente virtual capaz de responder a perguntas, fornecer detalhes sobre produtos e gerenciar pedidos, tudo através de uma interface de chat. Além disso, o sistema servirá como uma ferramenta de análise de dados para a equipe interna, com diferentes níveis de acesso para funcionários e proprietários.
#### Contexto e Problema a Ser Resolvido:
A empresa já opera com uma loja virtual, mas a plataforma apresenta baixa adesão e um volume de vendas insatisfatório. A causa central para este baixo desempenho é a falta de uma comunicação interativa e humanizada, que permita aos clientes tirar dúvidas e receber o suporte que normalmente teriam com um vendedor em uma loja física.
Essa lacuna na comunicação resulta em uma experiência de compra impessoal e em baixas taxas de conversão. O objetivo estratégico do projeto é, portanto, fortalecer o canal de vendas digital para torná-lo mais eficiente, viabilizando a **redução da dependência das lojas físicas e a otimização da equipe de vendas**, que hoje em dia, a empresa conta com 50 lojas físicas no país, com 25 vendedores em cada.
#### Objetivos do Projeto:
- **Centralizar Vendas no Chat:** Criar um chatbot que conduza todo o processo de venda, desde a descoberta do produto até o fechamento do pedido.
- **Melhorar a Experiência do Cliente:** Oferecer um "vendedor IA" que forneça descrições detalhadas de produtos, compare itens, informe preços e responda a perguntas em tempo real.
- **Automatizar Processos:** Implementar funcionalidades automáticas como cálculo de frete a partir do CEP e armazenamento de pedidos (concluídos e abandonados) e coleta de dados de interação.
- **Disponibilizar Análises Automatizadas:** Desenvolver uma interface onde a equipe interna possa consultar, de forma simples, os dados e as análises sobre vendas e comportamento do consumidor gerados pela IA.
#### Funcionalidades Detalhadas:
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
