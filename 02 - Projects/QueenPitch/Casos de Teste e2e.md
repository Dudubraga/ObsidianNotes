
### Conta

##### Funcionalidade: Cadastro de Usuário
- **CT-001: Cadastro de um novo Usuário**
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
- **CT-002: Tentativa de cadastro de um Usuário já existente**
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
