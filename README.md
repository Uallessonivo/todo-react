## Desafio 01 Rocketseat - ignite / ToDo

Essa será uma aplicação onde o seu principal objetivo é uma pequena aplicação de atividades a fazer, para treinar um pouco mais sobre manipulação do estado no React.

- Adicionar uma nova tarefa
- Remover uma tarefa
- Marcar e desmarcar uma tarefa como concluída

## Solução


- Adicionar uma nova tarefa

function handleCreateNewTask() {
// Se o input estiver vazio, impedir o envio da nova tarefa.
    if (!newTaskTitle) return;

// Nova tarefa recebe uma ID random e inicia o isComplete como false
    const newTask = {
      id: Math.random(),
      title: newTaskTitle,
      isComplete: false,
    };

// Recebo o valor do input e insiro na lista
    setTasks((oldState) => [...oldState, newTask]);

// Reseto o valor inserido no input    
    setNewTaskTitle("");
}



- Remover uma tarefa

function handleRemoveTask(id: number) {

// Filtra todas as tasks e retorna as tasks diferente do id selecionado
// Manteve na lista os ID que são diferentes ao ID selecionado
    const filteredTasks = tasks.filter((task) => task.id !== id);

// Atualiza o estado da lista    
    setTasks(filteredTasks);
}



- Marcar e desmarcar uma tarefa como concluída

function handleToggleTaskCompletion(id: number) {

// Mapeia todas as tarefa
// Verifica se na tarefa clicada o isComplete está setado como false
// Então retorna o valor contrário do isComplete que no caso agora é true

// Se não for diferente, retorna o isComplete com o valor padrão que é false

    const newTasks = tasks.map((task) =>
      task.id === id
        ? {
            ...task,
            isComplete: !task.isComplete,
          }
        : task
    );

    setTasks(newTasks);
}
