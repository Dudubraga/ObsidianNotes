Valores permitidos: ["ADMIN", "MANAGER", "EDITOR", "VIEWER"]
Lembrando que os nomes em português são:

- Administrador 
- ⁠Gestor
- ⁠Redator
- ⁠Visualizador

- [!] A rota de update que temos hoje em dia para Project-User só altera o role do usuário no projeto, ficou faltando os parâmetros para editar o status e a lista de projetos 
```tsx
	const payload = {
	    role: validatedData.role,
	    projectIds: validatedData.projects,
	    status: validatedData.active ? "ACTIVE" : "INACTIVE",
	};
```
```json
	{
	  "role": "EDITOR",
	  "projectIds": [15, 20, 22],
	  "status": "INACTIVE",
	}
```

- [!] Não existe usuário **pendente** no projeto
![[Bug - Usuário Pendente.mp4]]

- [?] Usuário é convidado como o mesmo cargo para vários projetos de uma vez, mas pode ser editado para cargos diferentes em projetos diferentes.  

- [!] Bug visual quando tem muitos projetos
![[Bug visual muitos projetos edit.png]]

![[Bug visual muitos projetos convite.png]]