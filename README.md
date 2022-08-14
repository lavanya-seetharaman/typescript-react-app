# Getting Started with Create React Typescript TodoList App

To setup the typescript project use either npm or yarn commands:
### npm command
```
npx create-react-app . — template typescript
```
### yarn command
```
yarn create react-app . — template typescript
```

## Folder structure 
Once your created you will get the folder structure like this:


```.
└── typescript-react-app
    ├── node_modules		
    ├── public
    ├── package-lock.json	
    ├── src
    ├── README.md		
    ├── package.json		
    └── tsconfig.json
 ```   
 The <code>tsconfig.json </code> is responsible for compile of typescript code

## Create state variables 
```
const [task, setTask]= useState<string>("");

const [taskDeadline, setTaskDeadline]= useState<number>(0);
 
const [todoList, setTodoList] = useState<ITask[]>([]);
```
 
 using above states we can able to create task and maintain the task list. It is typescript so we have to mention the type of variable.
 
## Create event handlers
```
<input type="text" placeholder='Task...' name="task" value={task} onChange={handleChange}/> 
<input type="number" placeholder='Deadline ( in days )...' name="deadline" value={taskDeadline} onChange={handleChange}/>
```
The two lines contains the <code>onChange</code> event handler. When the user changing the input value this event will get triggered from UI and <code>handleChange</code> will get execute.

Like <code> onChange</code> we are have lot of overridden methods available in javascript that can be utilized depends on context
To Learn further check this out <link>https://www.w3schools.com/jsref/event_onchange.asp</link>

## Create Components

Create new folder called "components" under <code>src</code>. Inside the components folder, create file as "TodoTask.tsx" 

Code

```
import React from 'react'
import { ITask } from '../interface/Interface'
interface Props{
    task:ITask;
    completeTask(taskNameToDelete:string):void;
}
const TodoTask=({task, completeTask}:Props)=> {
  return (
    <div className='task'>
        <div className='content'>
            <span>{task.taskName}</span><br/>
            <span>{task.taskDeadline} days</span>
        </div>
        <button onClick={()=>{completeTask(task.taskName)}}>X</button>
    </div>
  )
}

export default TodoTask
```
Above code contains interface in which we can type cast the task object and function called "completeTask".
Inside the div we have two span tag to display task name and task deadline respectively
then , we have button to perform the remove the completed task from the list.

From the App.tsx , using attributes as props pass the task and completeTask props like this :
```
<TodoTask key={key} task={task} completeTask={completeTask}/>
```

## Run the app
```
npm start
```
You can now view typescript-react-app in the browser.

  Local:            http://localhost:3000

To create a production build, use 
```
npm run build
```

Credits & Thanks to  : <a href="https://www.youtube.com/watch?v=bjnW2NLAofI">PedroTech</a>
