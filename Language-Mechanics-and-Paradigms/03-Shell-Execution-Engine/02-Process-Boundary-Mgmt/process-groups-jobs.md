# 👥 Process Groups, Job Control, and Backgrounding

## 1. Process Groups (PGID)
The shell groups related pipeline processes into a distinct Process Group (`setpgid()`), allowing signals to be targeted to entire execution pipelines simultaneously.

## 2. Job Control Infrastructure
- **Foreground Execution:** The shell surrenders terminal control (`tcsetpgrp()`) to the active process group and waits for completion.
- **Background Execution (`&`):** The shell retains terminal control and runs the process asynchronously, exposing `fg` and `bg` commands to swap job states.
