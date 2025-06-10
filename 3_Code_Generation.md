# Prompt to generate code 

We will execute these steps in Cursor

1. Add cursor rules - Create a file `.cursor/rules/general.mdc` with following contents. Make sure `Rule Type` is `Always`

    ```
    - We are building a slack clone
    - Find the steps in @project-steps.md
    - Work on whatever step(s) I tell you to work on and only work on those steps at once
    - Once those steps are done, mark as completed
    - Then stop, I will give you further instructions

    ## UI Components
    - Use shadcn/ui components as needed for any UI code
    - When suggesting UI components, use Shadcn UI, Radix, or Tailwind components.

    ## Style
    - Use Tailwind CSS for styling.

    ## General
    - Set up proper logging
    - Follow clean code principles
    - Prefer async/await over callbacks
    - Write comprehensive error handling
    - Follow best practices
    - Use PascalCase for React component file names (e.g., UserCard.tsx, not user-card.tsx).
    - Prefer named exports for components.

    ## Tech Stack
    - Frontend: Next.js, Tailwind, Shadcn
    - Backend: Postgres, Supabase, Drizzle ORM

    ## Server Components
    - Use `"use server"` at the top of the file.
    - params in server pages should be awaited such as `const { courseId } = await params` where the type is `params: Promise<{ courseId: string }>`

    ## Nextjs
    - When fetching data, always use Next.js 15's data fetching methods (getServerSideProps, getStaticProps, etc.).
    - When using TypeScript, always use interfaces over types for components and props.
    - When handling errors, prefer custom error types and error factories for consistent handling.
    - Use the App Router instead of the Pages Router.
    - Leverage React Server Components (RSC) for improved performance.
    - Correctly determine when to use server vs. client components in Next.js.
    ```
2. Generate code. Please note that journey differs from this point onwards depending on the code cursor is generating. Refer to steps mentioned in `project-steps.md` & go step by step. Keep reviewing the code generated. Keep commiting at regular intervals.
    ```
    1. Work on steps 1-2 and do the database setup
    2. Complete steps 3 for core UI components
    3. Complete step 4 and 5
    4. Complete steps 6 for front end pages and routing
    5. Complete step 7 and 8
    6. Complete step 9 to final UI
    .....
    ```
3. In case of errors, keep using Cursor creatively to get error fixed. Good luck.