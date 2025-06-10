# Initial Setup

1. Install Cursor or Windsurf (Make sure its added to PATH so that you can access it from command line)
2. Install node (if not already)
3. Install git and set it up (if not already)
4. Install RepoPrompt from https://repoprompt.com/ 

# Create Project

1. Navigate to your workspace and run the init command to create a new Next.js project using shadcn ui components 

    ```npx shadcn@latest init```

2. You may get prompted to install shadcn package. Hit `y` to install it.

3. Use arrow keys to start a new Next.js project with following details
    ```
    Project Name : slack-clone 
    base color : Neutral
    Use --force (if you get prompted for React 19)
    ```

4. Navigate to slack-clone directory and open it in cursor/windsurf

5. Open Terminal within cursor/windsurf and run following command

    ```
    npm install 
    npm run dev
    ```
6. Hit `http://localhost:3000` and you should be able to see nextjs page. Stop the dev mode once validated.

7. Create a remote git repo and push initial code

    ```
    git remote add origin git@github.com:2mohitarora/slack-clone.git
    git add -A
    git commit -a -m "first commit"
    git push -u origin main
    ```
# Setup Supabase postgres

1. You can use your github account to sign up on https://supabase.com/
2. Create an organization
    ```
    Name: Knowledge Sharing Projects
    Type: Personal
    Plan Pricing: Free
    ```
3. Once the organization is created, you can create a project
    ```
    Project Name: Slack Clone
    Database Password: Use Strong password (copy it and save it somewhere so that we can use it later)
    Region: East US (North Virginia)
    ```
# Setup RepoPrompt

1. Open Repo Prompt
2. Open slack-clone project in Repo Prompt
3. Click Filter and Hit Save. This will create a `.repo_ignore` file
4. Add following files at the end of `.repo_ignore` file
    ```
    # Project specific
    /public/
    favicon.ico
    .env.local
    .gitignore
    .repo_ignore
    /.cursor/
    project-steps.md
    /.windsurf/
    ```
5. Add, Commit and Push changed to Github

# Setup Drizzle ORM

1. Create `actions` folder under `project root`
2. Create `db` folder under `project root`
3. Inside db folder create `db.ts` file with following contents

    ```
    import { config } from "dotenv"
    import { drizzle } from "drizzle-orm/postgres-js"
    import postgres from "postgres"

    config({ path: ".env.local" })

    const schema = {}

    const client = postgres(process.env.DATABASE_URL!)

    export const db = drizzle(client, { schema })
    ```
4. Create a file `drizzle.config.ts` under `project root` with following contents
    ```
    import { config } from "dotenv"
    import { defineConfig } from "drizzle-kit"

    config({ path: ".env.local" })

    export default defineConfig({
        schema: "./db/schema/index.ts",
        out: "./db/migrations",
        dialect: "postgresql",
        dbCredentials: {
            url: process.env.DATABASE_URL!
        }
    })
    ```
5. Create a file `.env.local` under `project root` with following contents
    ```
    DATABASE_URL= (COPY CONNECTION STRING FROM SUPBASE & REPLACE PASSWORD IN CONNECTION STRING)
    ```
    How to get Connection string from Supabse
    ```
    1. Click Connect on Project
    2. Switch to ORM tab
    3. Select Drizzle from dropdown
    4. Copy the connection string
    5. Replace [YOUR-PASSWORD] in Connection String with password we saved earlier while creating db on supabase
    ```
6. Let's try First cursor/windsurf magic by installing missing drizzle packages used in `db.ts` and `drizzle.config.ts` we just created
    ```
    1. Make sure "db.ts" and "drizzle.config.ts" are open in Cursor/Windsurf
    2. Hit / in Cursor Agent window and select "Add Open Files to Context" (or similar way in Windsurf)
    3. Once db.ts and "drizzle.config.ts" are added to context, enter following text in agent window and hit enter
    - Create npm install command for missing packages
    4. It will find missing packages and create command "npm install dotenv drizzle-kit drizzle-orm postgres" to install missing packages
    5. Once you click "Run command", Cursor/Windsurf will install the missing packages.
    6. In scripts section of package.json, add following 3 lines
    
    "db:push": "npx drizzle-kit push",
    "db:studio": "npx drizzle-kit studio",
    "db:seed": "npx drizzle-kit seed"
    ```
7. Let's make sure everything compiles and project still runs after drizzle setup
    ```
    Run `npm run dev` and hit `http://localhost:3000`
    Add, Commit and push everything to Github
    ```