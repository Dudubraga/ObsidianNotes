---
tags:
  - queenpitch
---

#### Anotações durante o desenvolvimento
##### (apagar ao longo do tempo pra não encher dms)
###### 1. Update the Fetch Logic in `page.tsx`
```tsx
// page.tsx

// You'll need a simpler interface for the new API response
interface OrganizationUser {
  id: number;
  name: string;
  email: string;
  // Add other properties like 'lastName' if they exist
}

// ... inside your EquipePage component ...

useEffect(() => {
  const fetchTeamMembers = async () => {
    // We need the user's organization ID to build the new URL
    if (!user?.organizationId || !token) {
      setIsLoading(false);
      return;
    }
    
    try {
      setIsLoading(true);
      // --- START: KEY CHANGES ---
      const response = await fetch(
        // 1. Use the new organization users endpoint
        `${process.env.NEXT_PUBLIC_BASE_URL}/organizations/${user.organizationId}/users`,
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

      const data: OrganizationUser[] = await response.json();

      // Temporarily disable role checking or set a default, as this data is not available yet
      setCurrentUserRole("ADMIN"); // Or null, depending on desired default behavior

      // 2. Map the simpler user data to the complex TeamMember interface
      const mappedData = data.map((orgUser) => {
        return {
          id: orgUser.id,
          userId: orgUser.id,
          name: orgUser.name, // This data is available
          email: orgUser.email, // This data is available
          // --- Add placeholders for missing data ---
          permissionLevel: "Desconhecido", // Placeholder for role
          creations: 0,
          addedBy: "N/A", // Placeholder for inviter
          projects: [], // Placeholder for projects array
          status: "ACTIVE", // Default status
        };
      });
      // --- END: KEY CHANGES ---

      setTeamData(mappedData);
    } catch (error) {
      console.error("Erro ao buscar a lista de membros da organização:", error);
      setTeamData([]);
    } finally {
      setIsLoading(false);
    }
  };

  fetchTeamMembers();
}, [token, user?.organizationId]); // The dependencies are simpler now
```
###### 1. Filtering Data Based on User Role
```tsx
// page.tsx

// ... inside the EquipePage component ...

const filteredTeamData = useMemo(() => {
  // First, find the logged-in user's data from the list
  const currentUser = teamData.find(member => member.userId === user?.id);

  let visibleUsers = teamData;

  // If the user is an Editor or Viewer, apply visibility rules
  if (currentUserRole && (currentUserRole === 'EDITOR' || currentUserRole === 'VIEWER')) {
    if (currentUser) {
      const currentUserProjects = new Set(currentUser.projects);

      // 1. Filter the list to only include users who share at least one project
      visibleUsers = teamData.filter(member =>
        member.projects.some(project => currentUserProjects.has(project))
      );

      // 2. For the visible users, filter their project lists to only show shared projects
      visibleUsers = visibleUsers.map(member => ({
        ...member,
        projects: member.projects.filter(project => currentUserProjects.has(project)),
      }));
    } else {
      // If the current user can't be found, show an empty list for safety
      visibleUsers = [];
    }
  }
  // Admins and Managers will skip the 'if' block and see everyone by default

  // Finally, apply the search filter to the result
  const searchedUsers = searchQuery
    ? visibleUsers.filter((member: TeamMember) =>
        member.name.toLowerCase().includes(searchQuery.toLowerCase()) ||
        member.email.toLowerCase().includes(searchQuery.toLowerCase())
      )
    : visibleUsers;

  // Sort the final list by role
  return searchedUsers.sort((a: TeamMember, b: TeamMember) => {
    const orderA = roleOrder[a.permissionLevel as keyof typeof roleOrder] || 99;
    const orderB = roleOrder[b.permissionLevel as keyof typeof roleOrder] || 99;
    return orderA - bOrder;
  });
}, [teamData, searchQuery, currentUserRole, user?.id]);
```
###### 2. Auto-Refreshing the Table After an Action
```tsx
// page.tsx

const handleConfirmDelete = async () => {
  if (!userToDelete || !selectedProject || !token) return;

  try {
    const response = await fetch(/* ... */);

    if (response.ok) {
      // Instead of filtering the local state, just re-fetch the latest data from the server
      fetchTeamMembers(); 

      // Show the success view in the dialog
      setDeleteStatus('success');

      // Set a timer to close the dialog
      setTimeout(() => {
        setConfirmOpen(false);
        setUserToDelete(null);
      }, 2000);

    } else {
      // ... handle error
    }
  } catch (error) {
    // ... handle error
  }
};
```
###### The Fix in Your Dialogs (for Editing and Inviting)
```tsx
<InviteEditDialog
  // ... other props
  onSuccess={fetchTeamMembers} // <-- Pass the function
/>
<InviteDialog
  // ... other props
  onSuccess={fetchTeamMembers} // <-- Pass the function
/>
```

```tsx
// In both TeamEditDialog.tsx and InviteDialog.tsx

interface DialogProps {
  // ... other props
  onSuccess: () => void; // <-- Add the new prop to the interface
}

export default function YourDialog({ open, onClose, onSuccess }: DialogProps) {
  // ...

  const handleSubmit = async () => {
    // ...
    if (response.ok) {
      setAlertMessage({ text: "Success!", severity: "success" });
      onSuccess(); // <-- Call the function here to refresh the table
      handleClose();
    }
    // ...
  };

  // ...
}
```
###### ...
---
#### Dúvidas:

- [x] Não existe usuário **pendente** no projeto

- [x] Usuário é convidado como o mesmo cargo para vários projetos de uma vez, mas pode ser editado para cargos diferentes em projetos diferentes.  

- [x] **Reunião Sexta**
	- [x] O que é o status ATIVO / INATIVO
	- [x] Usuário sem projeto mostrando ?
		- [x] Tabela de equipe por organização x tabela de equipe por projeto
	- [x] Usuário não pode ter cargos diferentes


---
#### Ajustes:

- [x] ADMIN e GERENTE veem a **equipe inteira**.
- [x] REDATOR e VISUALIZADOR veem **apenas os projetos que estão participando**.

- [x] Usuário deletado pra sempre de vez.

- [x] **Adicionado por** - Desconhecido -> nome do próprio usuário.

- [x] usuário **inativo** é o usuário sem projeto nenhum.
- [x] apagar o switch de **ativar o usuário**.

- [x] Usuário nunca vai ter mais de um cargo diferente.

- [x] ~~Gerente~~ -> Gestor.

- [x] Botão de convidar do header.

- [x] Tela atualizar depois de editar.
