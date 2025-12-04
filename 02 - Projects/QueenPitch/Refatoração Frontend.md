- [!]  **Protótipo:**
- [FIGMA](https://www.figma.com/design/JdNNnPyrCD5YC6Csxt3MnD/Queen-Pitch?node-id=3272-54637&p=f&t=lyjgg8YN5bFSTdny-0)

### Épico
> Aplicar alterações de Layout, conforme o Figma do projeto, com objetivo de harmonização do frontend e melhor experiência para os usuários.

- Refatoração da HOME aplicando o novo design **Home 2.0 no Figma**
- Padronização de fontes e tamanhos de fontes
- Ajustar MENU para exibir de acordo com o permissionamento do usuário; diferentes perfis de usuário **Gestor, Redator, Visualizador**

#### Comportamento dinâmico esperado:

- Quando o usuário criar o projeto, o card da próxima ação **criar posicionamento** deve ser exibido
- Quando ambos **projeto** e **posicionamento** forem concluídos, **não terá mais o card para indicar a próxima jornada/ação.**
- **O mesmo para o chat criativo**. Quando o usuário clicar em **acessar** pela primeira vez, o card do chat também sumirá, e o papagaio flutuante ficará visível indicando um shortcut para o chat.
- [!] Lembrar de criar o tooltip **Continue criando para liberar esta jornada**
- [!] Para as jornadas e novas formas de conteúdo que ainda não foram desenvolvidas, inserir a Tag **em breve** conforme protótipo.

#### Primeiro acesso sem projeto:
- O comportamento dinâmico dos cards quando o usuário não tem projeto criado, deve continuar os mesmos.
- **Desenvolver novo layout da Tela primeiro acesso sem projeto**, que consiste basicamente em reorganização das Jornadas + Cards das Novas formas de conteúdo.
- Como as novas formas de conteúdo ainda não foram desenvolvidas, sinalizar como **em breve**.
- [!] Se atentar a cada componente da tela:
	1. padronizar ícones: tamanho, cores
	2. ajustar menu esquerdo conforme Figma (no protótipo está diferente do software)
	3. garantir espaçamento correto entre os cards/componentes
	4. o header mudará, e a frase **Você está no projeto** deixará de ser exibida
	5. a forma de exibir o nível do projeto também mudará
	6. incluir popups de gatilho quando usuário clica no Acessar chat criativo, para ficar igual ao protótipo
- **Popup de Gatilho** > quando usuário CLICAR em chat criativo ou em qualquer jornada, antes de criar projeto,
	- O correto é exibir o popup de Gatilho (hoje está exibindo uma mensagem de alerta, e isso está incorreto)

#### Primeiro acesso sem posicionamento:
- O comportamento dinâmico dos cards quando o usuário não tem posicionamento criado, deve continuar os mesmos.
- Desenvolver novo layout da Tela primeiro acesso **sem posicionamento**, que consiste basicamente em reorganização das Jornadas + Novas formas de conteúdo, e na alteração de cores.
- Como as novas formas de conteúdo ainda não foram desenvolvidas, sinalizar como **em breve**.
- A cor do card **usuário sem projeto** era preto, agora será branco **sem posicionamento**.
- A cor do texto também mudará.

