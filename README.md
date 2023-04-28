# Creating a sample Todo application using React + Amplify.

## Pre-requisites

1. Amplify CLI

Install the Amplify CLI using the command: 

```bash
npm install -g @aws-amplify/cli
```

To set up the Amplify CLI on your local machine, you have to configure it to connect to your AWS account.
Run the command below to set up the CLI

```bash
amplify configure
```

2. Setting up React Project

Create a new React project to initialize Amplify in.

```bash
npx create-react-app todo-app
cd todo-app
```

Start the app using the command below.

```bash
npm start
```

## Initializing Amplify.

Create an Amplify backend to create backend services for the app.

```bash
amplify init
```

- Provide project information and create the backend
- Authentication Method: AWS Profile and Select New Profile.

Some commands to remember: 

```bash
Some next steps:
"amplify status" will show you what you've added already and if it's locally configured or deployed
"amplify add <category>" will allow you to add features like user login or a backend API
"amplify push" will build all your local backend resources and provision it in the cloud
"amplify console" to open the Amplify Console and view your project status
"amplify publish" will build all your local backend and frontend resources (if you have hosting category added) and provision it in the cloud
```

## Add Amplify Libraries

Install the amplify library to begin development 

```bash
npm install aws-amplify
```

## Set up frontend

Configure Amplify so it can interact with backend services.

Open `src/index.js` and add the following code below the last import:

```js
import { Amplify } from 'aws-amplify';
import awsExports from './aws-exports';
Amplify.configure(awsExports);
```

As you add or remove categories and make updates to your backend configuration using the Amplify CLI, the configuration in aws-exports.js will update automatically.

## Creating an API

Add an API using the command: 

```
amplify add api
```

1. Choose: GraphQL
2. Build a Single API
3. Deploy it using `amplify push`
4. Open it through the console `amplify console api`


Can test in Console.

```

mutation createTodo {
  createTodo(input: {
    name: "Build an API"
    description: "Build a serverless API with Amplify and GraphQL"
  }) {
    id
    name
    description
  }
}

mutation updateTodoById {
  updateTodo(input: {description: "", id: "", name: "", status: ""}) {
    createdAt
    description
    id
    name
    status
    updatedAt
  }
}


mutation deleteToDoById {
  deleteTodo(input: {id: ""})
}


query listTodos {
  listTodos {
    items {
      id
      description
      name
    }
  }
}

query GetTodoById {
  getTodo(id: "") {
    createdAt
    description
    id
    name
    status
    updatedAt
  }
}

```