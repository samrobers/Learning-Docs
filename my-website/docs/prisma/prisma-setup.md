
:::tip Start Here
First, make sure that prisma has been installed. Run the following in your terminal to add prisma to your project.

```
npm i prisma
```

Click **[here](https://www.prisma.io/docs/getting-started/setup-prisma/start-from-scratch/relational-databases/next-steps-typescript-postgres)** for Prisma Docs
:::



:::info 1. Initialize the prisma project by running the following:

```
    npx prisma init

```
:::

:::info 2. Setup DB Connections

 - **` You will have a .env file that will look like this: ` **

```
DATABASE_URL="postgresql://johndoe:randompassword@localhost:5432/mydb?schema=public"

```

 - **` Change the Url to the url of your DB`**

 - **` In the schema file the following code will look like this: `**

```
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

```

- **` Depending on what Database you are using, you need to change the provider to the correct DB. An example is below:`**

```
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "mysql" 
  url      = env("DATABASE_URL")
}

```

::: 

:::info 3. [Introspection](https://www.prisma.io/docs/concepts/components/introspection)/Model Setup must occur

 - **`if you already have a database with data already inside it, you can pull the models by using introspection. This copies all of the models without having to figure out what they are.`**
    ```
    npx db pull

    ```

  - **`  This command performs introspection on the db and pulls the models into the schema.`**

- **` if it is a new project, you will have to set up these models.`**

:::

:::info 4. Generating Artifacts

- **`This is a fancy way of installing the tools to establish a connection and it also double checks that the connection has been established and is valid`**
:::

:::info 5. Create an `index.js` file to be able to work with the data

:::

:::info 6. Add the correct imports that are below: 

```
const { PrismaClient } = require("@prisma/client");

const prisma = new PrismaClient();
```


:::
