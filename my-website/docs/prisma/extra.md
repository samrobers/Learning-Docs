
Schema.prisma

```
  datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}
```

- specify the correct Db
- change the Db url to the correct URl

in the .env

```

DATABASE_URL="postgresql://johndoe:randompassword@localhost:5432/mydb?schema=public"

```

Here's a short explanation of each component:

USER: The name of your database user
PASSWORD: The password for your database user
HOST: The name of your host name (for the local environment, it is localhost)
PORT: The port where your database server is running (typically 5432 for PostgreSQL)
DATABASE: The name of the database
SCHEMA: The name of the schema inside the database

When running PostgreSQL locally on Mac OS, your user and password as well as the database name typically correspond to the current user of your OS, e.g. assuming the user is called janedoe:

npx prisma migrate

npm install @prisma/client

querying the DB

```

import { PrismaClient } from '@prisma/client'

const prisma = new PrismaClient()

async function main() {
  // ... you will write your Prisma Client queries here
}

main()
  .catch((e) => {
    throw e
  })
  .finally(async () => {
    await prisma.$disconnect()
  })

```

Here's a quick overview of the different parts of the code snippet:

Import the PrismaClient constructor from the @prisma/client node module
Instantiate PrismaClient
Define an async function named main to send queries to the database
Call the main function
Close the database connections when the script terminates

Inside the main function, add the following query to read all User records from the database and print the result:

```

async function main() {
  // ... you will write your Prisma Client queries here
  const allUsers = await prisma.user.findMany()
  console.log(allUsers)
}

```

This should print an empty array because there are no User records in the database yet:

```
npx ts-node index.ts

```

Writing Info To the DB

```

async function main() {
  await prisma.user.create({
    data: {
      name: 'Alice',
      email: 'alice@prisma.io',
      posts: {
        create: { title: 'Hello World' },
      },
      profile: {
        create: { bio: 'I like turtles' },
      },
    },
  })

  const allUsers = await prisma.user.findMany({
    include: {
      posts: true,
      profile: true,
    },
  })
  console.dir(allUsers, { depth: null })
}

```

Before moving on to the next section, you'll "publish" the Post record you just created using an update query. Adjust the main function as follows:

index.ts

```

async function main() {
  const post = await prisma.post.update({
    where: { id: 1 },
    data: { published: true },
  })
  console.log(post)
}

```

Explore the data in Prisma Studio

npx prisma studio

Examples
