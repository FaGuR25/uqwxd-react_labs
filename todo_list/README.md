# **Coding-project-template (Documentación del código)**

## **TODO LIST CON REACT**
En esta actividad lo que se realizó fue un programa con react sobre una aplicación simple de una lista de tareas donde las funciones son de agregar, eliminar y editar.

Además, se reportará la practica anexando una conclusion sobre el desarrollo de la practica, el uso de la plataforma **Skills Network** etc.

## **Skills Network**

Skills Network es una comunidad de creadores de contenido de primer nivel, autores, educadores que están ayudando al mundo a aprender tecnologías de vanguardia, un proyecto a la vez.

Referencia: Red de Habilidades. (s/f). Recuperado el 19 de marzo de 2024, de Skills.network website: https://skills.network/

## **CREAR APLICACIÓN** 

**Tiempo estimado:** 1 hora 30 minutos

1. Primero clonamos el repositorio que nos comparten para ya tener un repositorio nuevo y empezar a codificar.(https://github.com/ibm-developer-skills-network/uqwxd-react_labs.git)

2. Para clonarlo, se abre un CMD y despues de haber creado un repositorio en nuestra cuenta copiamos el enlace que viene en **CODE** y en CMD se pone: 

     ```css
    git clone https://github.com/<your Github username>/uqwxd-react_labs.git
    ```
   (se tiene que estar dentro de la carpeta del proyecto para que funcione)
   
    Despues se cambia a la carpeta donde se codificará todo *todo_list* con el siguiente comando:
    

    ```css
    cd uqwxd-react_labs/todo_list/
    ```

3. Para correr la aplicacion primero se deben de instalar paquetes con el siguiente comando:
    ```css
    set NODE_OPTIONS=--openssl-legacy-provider
    ```
    (En mi caso fue esa linea ya que yo tengo mi equipo con SO Windows)
    
    Para correr solo tenemos que estar en la carpeta de **todo_list** en cmd y escribir la linea de codigo:
    ```css
    npm start
    ```

## **CÓDIGO**

lo que se hizo fue ir siguiendo paso por paso lo que el tutorial  iba dando o explicando, no me adentraré tanto en esta parte ya que solo explica como agregar las funciones que debe de tener la aplicacion, por ejemplo para agregar una tarea se tienen que seguir dos pasos:
1. En **App.js** se tiene que agregar una función:
   ```css
      function handleSubmit(e) {
    e.preventDefault();

    let todo = document.getElementById('todoAdd').value
    const newTodo = {
      id: new Date().getTime(),
      text: todo.trim(),
      completed: false,
    };
    if (newTodo.text.length > 0 ) {
        setTodos([...todos].concat(newTodo));
    } else {

        alert("Enter Valid Task");
    }
    document.getElementById('todoAdd').value = ""}
    



Define una funcion llamada **HABDLE SUBMIT** que maneja el envío del formulario para agregar una nueva tarea a la lista. Dentro de esta función, se crea un nuevo objeto de tarea con un ID único, el texto de la tarea ingresado por el usuario y el estado **completed** establecido en **false**. Luego, se agrega esta nueva tarea al estado **todos** utilizando la función **setTodos**.

2. Y la otra parte es la de crear el boton con un **return** y el código:
     ```css
    <div id="todo-list">
    <h1>Todo List</h1>
        <form onSubmit={handleSubmit}>
            <input
              type="text"
              id = 'todoAdd'
            />
            <button type="submit">Add Todo</button>
        </form>
        {todos.map((todo) =>
            <div className="todo" key={todo.id}>
                <div className="todo-text">{todo.text}</div>
            {/* insert delete button below this line */}
            </div>)}
    </div>
    ```
Estos pasos se recrean en todas las funciones de la tarea.

## **HOOK UseEffect**

Los Hooks son funciones que te permiten “enganchar” el estado de React y el ciclo de vida desde componentes de función.

El hook useEffect de React es una herramienta poderosa que nos permite controlar los efectos secundarios en nuestros componentes. Los efectos secundarios son cualquier cambio de estado que no sea el resultado directo de una actualización de estado.

Para importar este hook se necesita importar el paquete:

```css
import React, {useState,useEffect} from "react";
```
Para después agregar el código que permitirá almacenar las tareas en el almacenamiento local como un **JSON**.

```css
useEffect(() => {
    const json = localStorage.getItem("todos");
    const loadedTodos = JSON.parse(json);
    if (loadedTodos) {
      setTodos(loadedTodos);
    }
  }, []);

useEffect(() => {
    if(todos.length > 0) {
        const json = JSON.stringify(todos);
        localStorage.setItem("todos", json);
    }
  }, [todos]);
```
## **CONCLUSIÓN**

En lo personal desconocia la comunidad de **Skills Network** es la primera vez que la utilizo y me parecio de gran ayuda porque tiene tutoriales de paso a paso para crear pequeñas aplicaciones donde puedes ir a tu ritmo y saber para que funciona cada funcion, constante o linea de codigo que se presenta. 

En esta actividad que se basó en crear una lista de tareas lo hicimos para poder visualizar en un mayor detalle la funcionalidad que tienen los **Hook** y en este caso el **UseEffect** el cual permite almacenar las tareas en el almacenamiento como un **JSON** y que se puede observar llendo a inspeccionar el codigo abriendo la opción de *aplicación* y después *almacenamiento*.

De esta actividades me llevo los aprendizajes de para que funcionan los hooks en React y del uso al menos principiante de la comunidad de Skills Network.