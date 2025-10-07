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

- [?] Qual a diferença entre as rotas: 
	- `/project-users/project/{projectId}/user/{userId}/role` -> "Altera permissões do usuário no projeto"
	- `/projects/{id}/users/{userId}/role` -> "Atualizar a role e um usuário em um projeto"

- [!] Não existe usuário **pendente** no projeto
![[Bug - Usuário Pendente.mp4]]

- [?] Vários `fetchs()` pra pegar projetos
```tsx
// page.tsx

useEffect(() => {
  const fetchTeamMembers = async () => {
    if (!selectedProject || !token || projects.length === 0) {
      setIsLoading(false);
      if (projects.length === 0) setTeamData([]);
      return;
    }

    try {
      setIsLoading(true);
      // lista de usuários do projeto selecionado
      const response = await fetch(
        `${process.env.NEXT_PUBLIC_BASE_URL}/project-users/project/${selectedProject.id}/users`,
        {
          method: "GET",
          headers: {
            Authorization: `Bearer ${token}`,
            "Content-Type": "application/json",
          },
        }
      );
      if (!response.ok) {
        throw new Error(`Erro: ${response.status}`);
      }
      const data: ProjectUser[] = await response.json();
      const foundMember = initialUserData.find(projectUser => projectUser.user.id === user?.id);
      setCurrentUserRole(foundMember?.role || null);
      // pra cada usuário busca lista completa de projetos
      const mappedData = await Promise.all(
        initialUserData.map(async (projectUser) => {
          const inviterName = projectUser.inviter
            ? `${projectUser.inviter.name} ${projectUser.inviter.lastName || ""}`.trim()
            : "Desconhecido";
          let userProjectNames: string[] = [];
          try {
            const projectsAssociated = await fetch(
              `${process.env.NEXT_PUBLIC_BASE_URL}/project-users/user/${projectUser.user.id}/projects`,
              {
                headers: { Authorization: `Bearer ${token}` },
              }
            );
            if (projectsAssociated.ok) {
              const userProjectsData: ProjectUser[] = await projectsAssociated.json();
              userProjectNames = userProjectsData
                .map(up => projects.find(p => p.id === up.projectId)?.name)
                .filter((name): name is string => !!name);
            } else {
              throw new Error(`API failed with status ${projectsAssociated.status}`);
            }
          } catch (error) {
            console.error(`Não foi possível buscar projetos para o usuário ${projectUser.user.id}:`, error);
            userProjectNames = [];
          }
          return {
            id: projectUser.id, // id projectUser
            userId: projectUser.user.id, //id user
            name: `${projectUser.user.name} ${projectUser.user.lastName}`,
            email: projectUser.user.email,
            permissionLevel: projectUser.role,
            creations: 0,
            addedBy: inviterName,
            projects: userProjectNames,
            status: projectUser.status,
          };
        })
      );
      setTeamData(mappedData);
    } catch (error) {
      console.error("Erro ao buscar a lista inicial de membros:", error);
      setTeamData([]);
    } finally {
      setIsLoading(false);
    }
  };

  fetchTeamMembers();
}, [selectedProject, token, projects, user?.id]);
```

- [?] Usuário é convidado como o mesmo cargo para vários projetos de uma vez, mas pode ser editado para cargos diferentes em projetos diferentes.  

