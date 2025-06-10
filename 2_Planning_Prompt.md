# Prompt to finalize Planning for Cursor implementation 

We will execute these steps in Claude/ChatGPT

1. Copy contents of `prompts/output/Project_Description.md` or the requirements you finalized.
2. Open `prompts/input/Planner.md`
3. Paste copied content between tags `<project_request>` and `</project_request>`
4. Copy the modified `prompts/input/Planner.md` 
5. Open Claude/ChatGPT
6. Open Repo Prompt and copy the existing content of project that we created during initial setup and paste it in claude as well. `For reference i had 13 files copied via Repo Prompt`
7. Run the following prompt
    ```
    Create the plan as mentioned. Don't include already done steps. Start from what we have. Steps must go in order that we have to complete them in. Already done steps and its code is attached with prompt. Return as a single markdown block like the original prompt asked in the todo format.
    ```
8. Iterate on the plan.
9. Once you are happy with project steps output, copy the output (Output of my iterations can be seen under `prompts/output/Project_Steps.md`)
10. Move to cursor/windsurf and create a file `project-steps.md` under `project root`
11. Paste the output in `project-steps.md`


