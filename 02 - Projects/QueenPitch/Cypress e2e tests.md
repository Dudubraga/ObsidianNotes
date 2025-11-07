---
tags:
  - queenpitch
---

### Conta

##### Funcionalidade: Cadastro de Usuário
- **CT-001: Cadastro de um novo usuário**
	- **Pré-condição:** 
		- O usuário não deve estar logado e deve possuir um e-mail ainda não cadastrado.
	- **Passos para execução:**
		1. Acessar a página de cadastro.
		2. Preencher os dados pessoais com um endereço de e-mail válido e não existente na base.
		3. Clicar em “Próximo”.
		4. Preencher os dados da empresa.
		5. Clicar em “Próximo”.
		6. Clicar em “Acessar conta”.
	- **Resultado esperado:**
		- O sistema deve exibir a mensagem de sucesso.
		- O usuário deve ser redirecionado para a tela de login.
- **CT-002: Tentativa de cadastro de um usuário já existente**
	- **Pré-condição:** 
		- Deve existir um usuário na base de dados com um e-mail específico.
	- **Passos para execução:**
		1. Acessar a página de cadastro.
		2. Preencher os campos com dados válidos e, no campo e-mail, inserir o endereço que já existe na base. 
		3. Clicar em “Próximo”.
		4. Preencher os dados da empresa.
		5. Clicar em “Próximo”.
		6. Clicar em “Acessar conta”.
	- **Resultado esperado:**
		- O sistema não deve criar a conta e deve exibir uma mensagem de erro.
		- O usuário deve ser redirecionado para a tela inicial de cadastro.
- **CT-031: Cadastro de um novo usuário por convite**
	- 
##### Funcionalidade: Login de Usuário
- **CT-003: Login do Usuário**
	- **Pré-condição:** 
		- O usuário não deve estar logado e deve possuir um cadastrado.
	- **Passos para execução:**
		1. Preencher o login com um endereço de e-mail e senha válidos.
		2. Clicar em “Entrar”.
	- **Resultado esperado:**
		- O usuário deve ser redirecionado para a tela inicial do site.
- **CT-004: Login do Usuário inexistente**
	- **Pré-condição:**  
		- O usuário não deve estar logado e deve ter um e-mail não cadastrado.
	- **Passos para execução:**
		1. Preencher o login com um endereço de e-mail não válido.
		2. Clicar em “Entrar”.
	- **Resultado esperado:**
		- O sistema deve exibir uma mensagem de erro.
##### Funcionalidade: Editar informações de Usuário
- **CT-005: Editar dados do Usuário**
	- **Pré-condição:** 
		- O usuário precisa estar logado no sistema com uma conta válida.
	- **Passos para execução:**
		1. Realizar o login no sistema.
		2. Navegar até a página de “Dados pessoais”.
		3. Alterar o valor do campo "Nome" para um novo nome.
		4. Alterar o valor do campo "Sobrenome" para um novo sobrenome.
		5. Alterar o valor do campo "Telefone ou WhatsApp" para um novo número de telefone.
		6. Alterar o valor do campo "Cargo" para um novo cargo.
		7. Alterar o valor do campo "Nome da Empresa" para um novo nome da empresa.
		8. Alterar o valor do campo "Site da Empresa" para um novo site da empresa.
		9. Clicar no botão "Salvar Alterações".
	- **Resultado esperado:**
		- O sistema deve exibir uma mensagem de sucesso.
		- A página deve exibir os campos com os novos valores.
- **CT-006: Editar dados chaves do Usuário**
	- **Pré-condição:** 
		- O usuário precisa estar logado no sistema com uma conta válida.
	- **Passos para execução:**
		1.  Realizar o login no sistema.
		2. Navegar até a página de “Dados pessoais”.
		3. Alterar o valor do campo "E-mail" para um novo e-mail.
		4. Alterar o valor do campo "Senha" para uma nova senha.
		5. Inserir a nova senha no campo "Confirmar Senha".
		6. Clicar no botão "Salvar Alterações".
	- **Resultado esperado:**
		- O sistema deve exibir uma mensagem de sucesso.
		- A página deve exibir os campos com os novos valores.
### Jornadas

##### Funcionalidade: Projeto
- **CT-007: Criar um Projeto**
	- **Pré-condição:** 
		- O usuário precisa estar logado no sistema.
	- **Passos para execução:**
		1. Navegar para a seção "Meus Projetos".
		2. Clicar em "Novo projeto".
		3. Preencher todas as etapas do formulário para alimentar a base de conhecimento.
		4. Clicar em "Enviar Respostas".
	- **Resultado esperado:**
		- O sistema deve exibir uma mensagem de sucesso. 
		- O sistema deve levar o usuário para a tela de “Meus Projetos”. 
- **CT-009: Editar um Projeto**
	- **Pré-condição:**
		- O usuário precisa ter um projeto existente.
	- **Passos para execução:**
		1. Navegar para a seção "Meus Projetos".
		2. Clicar em "Acessar" ao lado do projeto desejado.
		3. Editar informações da base de conhecimento.
		4. Clicar em "Salvar alterações".
	- **Resultado esperado:**
		- O sistema deve mostrar uma mensagem de sucesso.
- **CT-010: Excluir um Projeto**
	- **Pré-condição:** 
		- O usuário precisa ter um projeto existente.
	- **Passos para execução:**
		1. Navegar para a seção "Meus Projetos".
		2. Clicar em "Excluir projeto" ao lado do projeto desejado.
		3. Clicar em "Sim, excluir" na confirmação.
	- **Resultado esperado:**
		- O sistema deve mostrar uma mensagem de sucesso.
##### Funcionalidade: Posicionamento
- **CT-023: Criar um Posicionamento**
    - **Pré-condição:**
        - O usuário precisa estar logado e dentro de um projeto existente.
    - **Passos para execução:**
        1. Entrar na Jornada através do dashboard. _(Marketing de Conteúdo)_
        2. Clicar em "Criar" na seção do Posicionamento.
        3. Clicar em "Salvar".
    - **Resultado esperado:**
        - O posicionamento é salvo com sucesso e fica disponível para consulta dentro da “base de criações” do projeto.
- **CT-024: Gerar novo Posicionamento**
    - **Pré-condição:**
        - O usuário precisa ter um posicionamento já criado.
    - **Passos para execução:**
        1. Entrar na Jornada através do dashboard. _(Marketing de Conteúdo)_
        2. Clicar em "Acessar" na seção do Posicionamento.
        3. Clicar em "Novo posicionamento".
        4. Clicar em "Salvar".
    - **Resultado esperado:**
        - O sistema deve mostrar uma mensagem de sucesso.
- **CT-025: Editar um Posicionamento**
    - **Pré-condição:**
        - O usuário precisa ter um posicionamento já criado.
    - **Passos para execução:**
        1. Entrar na Jornada através do dashboard. _(Marketing de Conteúdo)_
        2. Clicar em "Acessar" na seção do Posicionamento.
        3. Clicar no posicionamento que deseja editar.
        4. Alterar o texto escrito.
        5. Clicar em "Salvar".
    - **Resultado esperado:**
        - O sistema deve mostrar uma mensagem de sucesso.
- **CT-026: Compartilhar um Posicionamento**
    - **Pré-condição:**
        - O usuário precisa ter um posicionamento já criado.
    - **Passos para execução:**
        1. Entrar na Jornada através do dashboard. _(Marketing de Conteúdo)_
        2. Clicar em "Acessar" na seção do Posicionamento.
        3. Clicar em "Compartilhar".
    - **Resultado esperado:**
        - A página de compartilhamento deve abrir com o nome do projeto e conteúdo.
##### Funcionalidade: Pitch
- **CT-011: Criar um Pitch**
	- **Pré-condição:** 
		- O usuário precisa estar logado e dentro de um projeto existente.
	- **Passos para execução:**
		1. Entrar na Jornada através do dashboard. *(Marketing de Conteúdo)*
		2. Clicar em "Criar" na seção do Pitch.
		3. Clicar em "Salvar".
	- **Resultado esperado:**
		- O pitch é salvo com sucesso e fica disponível para consulta dentro da “base de criações” do projeto.
- **CT-012: Gerar novo Pitch**
	- **Pré-condição:**
		- O usuário precisa ter um pitch de vendas já criado.
	- **Passos para execução:**
		1. Entrar na Jornada através do dashboard. *(Marketing de Conteúdo)*
		2. Clicar em "Acessar" na seção do Pitch.
		3. Clicar em "Novo pitch de vendas".
		4. Clicar em "Salvar".
	- **Resultado esperado:**
		- O sistema deve mostrar uma mensagem de sucesso.
- **CT-013: Editar um Pitch**
	- **Pré-condição:**
		- O usuário precisa ter um pitch de vendas já criado.
	- **Passos para execução:**
		1. Entrar na Jornada através do dashboard. *(Marketing de Conteúdo)*
		2. Clicar em "Acessar" na seção do Pitch.
		3. Clicar em "Novo pitch de vendas".
		4. Alterar o texto escrito.
		5. Clicar em "Salvar".
	- **Resultado esperado:**
		- O sistema deve mostrar uma mensagem de sucesso.
- **CT-014: Compartilhar um Pitch**
	- **Pré-condição:**
		- O usuário precisa ter um pitch de vendas já criado.
	- **Passos para execução:**
		1. Entrar na Jornada através do dashboard. *(Marketing de Conteúdo)*
		2. Clicar em "Acessar" na seção do Pitch.
		3. Clicar em "Compartilhar".
	- **Resultado esperado:**
		- A página de compartilhamento deve abrir com o nome do projeto e conteúdo.
##### Funcionalidade: Persona
- **CT-015: Criar uma Persona**
    - **Pré-condição:**
        - O usuário precisa estar logado e dentro de um projeto existente.
    - **Passos para execução:
        1. Entrar na Jornada através do dashboard. _(Marketing de Conteúdo)_
        2. Clicar em "Criar" na seção da Persona.
        3. Clicar em "Salvar".
    - **Resultado esperado:**
        - A persona é salva com sucesso e fica disponível para consulta dentro da “base de criações” do projeto.
- **CT-016: Gerar nova Persona**
    - **Pré-condição:**
        - O usuário precisa ter uma persona já criada.
    - **Passos para execução:**
        1. Entrar na Jornada através do dashboard. _(Marketing de Conteúdo)_
        2. Clicar em "Acessar" na seção da Persona.
        3. Clicar em "Nova persona".
        4. Clicar em "Salvar".
    - **Resultado esperado:**
        - O sistema deve mostrar uma mensagem de sucesso.
- **CT-017: Editar uma Persona**
    - **Pré-condição:**
        - O usuário precisa ter uma persona já criada.
    - **Passos para execução:**
        1. Entrar na Jornada através do dashboard. _(Marketing de Conteúdo)_
        2. Clicar em "Acessar" na seção da Persona.
        3. Clicar na persona que deseja editar.
        4. Alterar as informações.
        5. Clicar em "Salvar".
    - **Resultado esperado:**
        - O sistema deve mostrar uma mensagem de sucesso.
- **CT-018: Compartilhar uma Persona**
    - **Pré-condição:**
        - O usuário precisa ter uma persona já criada.
    - **Passos para execução:**
        1. Entrar na Jornada através do dashboard. _(Marketing de Conteúdo)_
        2. Clicar em "Acessar" na seção da Persona.
        3. Clicar em "Compartilhar".
    - **Resultado esperado:**
        - A página de compartilhamento deve abrir com o nome do projeto e conteúdo.
##### Funcionalidade: Planejamento de Conteúdo
- **CT-027: Criar um Planejamento de Conteúdo**
    - **Pré-condição:**
        - O usuário precisa estar logado e dentro de um projeto existente.
    - **Passos para execução:**
        1. Entrar na Jornada através do dashboard. _(Marketing de Conteúdo)_
        2. Clicar em "Criar" na seção do Planejamento de Conteúdo.
        3. Clicar em "Salvar".
    - **Resultado esperado:**
        - O plano de conteúdo é salvo com sucesso e fica disponível para consulta dentro da “base de criações” do projeto.
- **CT-028: Gerar novo Planejamento de Conteúdo**
    - **Pré-condição:**
        - O usuário precisa ter um plano de conteúdo já criado.
    - **Passos para execução:**
        1. Entrar na Jornada através do dashboard. _(Marketing de Conteúdo)_
        2. Clicar em "Acessar" na seção do Planejamento de Conteúdo.
        3. Clicar em "Novo plano de conteúdo".
        4. Clicar em "Salvar".
    - **Resultado esperado:**
        - O sistema deve mostrar uma mensagem de sucesso.
- **CT-029: Editar um Planejamento de Conteúdo**
    - **Pré-condição:**
        - O usuário precisa ter um planejamento de conteúdo já criado.
    - **Passos para execução:**
        1. Entrar na Jornada através do dashboard. _(Marketing de Conteúdo)_
        2. Clicar em "Acessar" na seção do Planejamento de Conteúdo.
        3. Clicar no plano de conteúdo que deseja editar.
        4. Alterar as informações.
        5. Clicar em "Salvar".
    - **Resultado esperado:**
        - O sistema deve mostrar uma mensagem de sucesso.
- **CT-030: Compartilhar um Planejamento de Conteúdo**
    - **Pré-condição:**
        - O usuário precisa ter um plano de conteúdo já criado.
    - **Passos para execução:**
        1. Entrar na Jornada através do dashboard. _(Marketing de Conteúdo)_
        2. Clicar em "Acessar" na seção do Planejamento de Conteúdo.
        3. Clicar em "Compartilhar".
    - **Resultado esperado:**
        - A página de compartilhamento deve abrir com o nome do projeto e conteúdo.
##### Funcionalidade: Landing Page
- **CT-019: Criar uma Landing Page**
    - **Pré-condição:**
        - O usuário precisa estar logado e dentro de um projeto existente.
    - **Passos para execução:**
        1. Entrar na Jornada através do dashboard. _(Marketing de Produto)_
        2. Clicar em "Criar" na seção da Landing Page.
        3. Clicar em "Salvar".
    - **Resultado esperado:**
        - A landing page é salva com sucesso e fica disponível para consulta dentro da “base de criações” do projeto.
- **CT-020: Gerar nova Landing Page**
    - **Pré-condição:**
        - O usuário precisa ter uma landing page já criada.
    - **Passos para execução:**
        1. Entrar na Jornada através do dashboard. _(Marketing de Produto)_
        2. Clicar em "Acessar" na seção da Landing Page.
        3. Clicar em "Nova landing page".
        4. Clicar em "Salvar".
    - **Resultado esperado:**
        - O sistema deve mostrar uma mensagem de sucesso.
- **CT-021: Editar uma Landing Page**
    - **Pré-condição:**
        - O usuário precisa ter uma landing page já criada.
    - **Passos para execução:**
        1. Entrar na Jornada através do dashboard. _(Marketing de Produto)_
        2. Clicar em "Acessar" na seção da Landing Page.
        3. Clicar na landing page que deseja editar.
        4. Alterar as informações.
        5. Clicar em "Salvar".
    - **Resultado esperado:**
        - O sistema deve mostrar uma mensagem de sucesso.
- **CT-022: Compartilhar uma Landing Page**
    - **Pré-condição:**
        - O usuário precisa ter uma landing page já criada.
    - **Passos para execução:**
        1. Entrar na Jornada através do dashboard. _(Marketing de Produto)_
        2. Clicar em "Acessar" na seção da Landing Page.
        3. Clicar em "Compartilhar".
    - **Resultado esperado:**
        - A página de compartilhamento deve abrir com o nome do projeto e conteúdo.
##### Funcionalidade: Apresentação da Solução
- **CT-023: Verificar bloqueio**
	- **Pré-condição:**
		- O usuário deve estar logado.
	- **Passos para execução:**
		- ...
	- **Resultado esperado:**
		- O usuário não deve ser capaz de acessar a página.
##### Funcionalidade: Marketing Estratégico
- **CT-024: Verificar bloqueio**
	- **Pré-condição:**
		- O usuário deve estar logado.
	- **Passos para execução:**
		- ...
	- **Resultado esperado:**
		- O usuário não deve ser capaz de acessar a página.
##### Funcionalidade: Marketing de Performance
- **CT-025: Verificar bloqueio**
	- **Pré-condição:**
		- O usuário deve estar logado.
	- **Passos para execução:**
		- ...
	- **Resultado esperado:**
		- O usuário não deve ser capaz de acessar a página.
---
# Casos de Teste

### Usuário:

- **CT-001: Cadastrar um novo usuário** 
- **CT-002: Cadastrar um usuário já existente**
- **CT-003: Cadastrar um novo usuário por convite** 
- **CT-004: Login do usuário** 
- **CT-005: Login do usuário inexistente** 
- **CT-006: Editar dados do usuário** 
- **CT-007: Deletar usuário**
### Projeto:

- **CT-008: Criar um Projeto** 
- **CT-009: Editar um Projeto** 
- **CT-010: Excluir um Projeto** 
- **CT-011: Selecionar um Projeto no dashboard (alterar dashboard mostrado)**
### Jornadas:

- **Posicionamento da Marca**
    - **CT-012: Criar um Posicionamento** 
    - **CT-013: Gerar novo Posicionamento** 
    - **CT-014: Editar um Posicionamento** 
    - **CT-015: Compartilhar um Posicionamento** 
- **Pitch de Vendas**
    - **CT-016: Criar um Pitch** 
    - **CT-017: Gerar novo Pitch** 
    - **CT-018: Editar um Pitch** 
    - **CT-019: Compartilhar um Pitch** 
- **Persona**
    - **CT-020: Criar um Persona** 
    - **CT-021: Gerar novo Persona** 
    - **CT-022: Editar um Persona** 
    - **CT-023: Compartilhar um Persona** 
- **Planejamento de Conteúdo**
    - **CT-024: Criar um Planejamento** 
    - **CT-025: Gerar novo Planejamento** 
    - **CT-026: Editar um Planejamento** 
    - **CT-027: Compartilhar um Planejamento** 
- **Landing Page da Solução**
    - **CT-028: Criar um Landing Page** 
    - **CT-029: Gerar novo Landing Page** 
    - **CT-030: Editar um Landing Page** 
    - **CT-031: Compartilhar um Landing Page** 
- **Apresentação da Solução**
    - **CT-032: Mostrar “Em Breve”** 
- **Marketing Estratégico**
    - **CT-033: Mostrar “Em Breve”** 
- **Marketing de Performance**
    - **CT-034: Mostrar “Em Breve”** 
### Equipe:

- **Tabela de membros**
    - **CT-35: Verificar visão administrador proprietário** 
    - **CT-36: Verificar visão administrador**
    - **CT-37: Verificar visão gestor**
    - **CT-38: Verificar visão redator** 
    - **CT-39: Verificar visão visualizador** 
- **CT-040: Convidar membro** 
- **CT-041: Convidar membro de outra organização**
- **CT-042: Reenviar convite** 
- **CT-043: Editar membro**
- **CT-044: Remover membro** 
### Chat Criativo:

- **CT-045: Criar novo chat** 
- **CT-046: Editar nome do chat**
- **CT-047: Deletar chat**
- **CT-048: Enviar e receber mensagem no chat** 
- **Botões de atalho no chat**
    - **CT-049:** **Pedir Análise de Mercado** 
    - **CT-050:** **Pedir Conteúdo para Instagram** 
    - **CT-051:** **Pedir Conteúdo para Blog** 
    - **CT-052:** **Pedir Conteúdo para LinkedIn** 
- **CT-053: Anexar arquivo** 
- **Biblioteca de Prompts**
    - **CT-054: Criar Novo Prompt**
    - **CT-055: Usar Prompt**
    - **CT-056: Editar Prompt**
    - **CT-057: Deletar Prompt**
    - **CT-058: Criar nova Categoria**
    - **CT-059: Selecionar Categoria**
    - **CT-060: Editar Categoria**
    - **CT-061: Deletar Categoria**
    - **CT-062: Selecionar Categoria (alterar prompts mostrados)**
### Notificações:

- **CT-063: Ler notificação** 
- **CT-064: Ver conteúdo compartilhado** 
- **CT-065: Marcar todas as notificações como lidas** 

---

