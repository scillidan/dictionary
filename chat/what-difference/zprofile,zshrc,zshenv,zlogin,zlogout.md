What is the difference between .zprofile, .zshrc, .zshenv, .zlogin, .zlogout?

```md
These files are configuration scripts for the Z shell (`zsh`), used to customize the shell behavior at different stages of the shell startup and exit process. Each file serves a distinct purpose and is sourced at different times, depending on the type of shell being started (login, interactive, or non-interactive).

Here’s a breakdown of the differences between `.zprofile`, `.zshrc`, `.zshenv`, `.zlogin`, and `.zlogout`:

### 1. **.zshenv**

- **Purpose:**  
  This file is always sourced on **every** invocation of the `zsh` shell—whether login, interactive, or non-interactive.
- **Typical use case:**  
  Setting environment variables that need to be available to all zsh instances, such as `PATH`, `EDITOR`, `LC_ALL`, or any variables required regardless of shell type.
- **Note:**  
  Because this file is sourced in *every* shell startup, it should be minimal and fast-loading, and it should avoid commands that produce output or rely on interactive features.

### 2. **.zprofile**

- **Purpose:**  
  This file is sourced **only by login shells** (similar to `.profile` or `.bash_profile` in `bash`).
- **Typical use case:**  
  Commands or environment setup that only need to run once at login, such as setting environment variables, starting agents or daemons, initializing user environment, etc.
- **Execution order:**  
  Sourced after `.zshenv` and before `.zlogin`.
- **Note:**  
  If you are using `zsh` as a login shell, `.zprofile` is a good place to set path variables or run commands you want executed once per login.

### 3. **.zshrc**

- **Purpose:**  
  This file is sourced by **interactive shells** (both login and non-login).
- **Typical use case:**  
  Setting shell options, aliases, functions, key bindings, and prompt configuration—basically, anything that configures interactive behavior.
- **Note:**  
  Not sourced by non-interactive shells (scripts), so placing important environment variables here might cause problems.

### 4. **.zlogin**

- **Purpose:**  
  This file is sourced **after `.zprofile` and `.zshrc`** for **login shells**.
- **Typical use case:**  
  Commands you want to run once *after* all initialization is done; for example, starting up programs or printing messages after environment setup.
- **Execution order:**  
  `.zshenv` → `.zprofile` → `.zshrc` → `.zlogin`

### 5. **.zlogout**

- **Purpose:**  
  This file is sourced when a **login shell exits**.
- **Typical use case:**  
  Cleanup commands, such as terminating background jobs, clearing temporary files, or logging logout events.

### Summary in Tabular Form

| File         | Sourced When                        | Typical Use                             | Notes                               |
|--------------|-----------------------------------|---------------------------------------|-----------------------------------|
| `.zshenv`    | **All zsh shells** (login, interactive, non-interactive) | Set environment variables needed everywhere | Keep minimal, fast, no output     |
| `.zprofile`  | Login shells only                  | Environment setup at login             | Runs before `.zlogin`              |
| `.zshrc`     | Interactive shells only (login or not) | Interactive settings: aliases, prompts, keys | Not sourced in scripts            |
| `.zlogin`    | Login shells only, after `.zshrc` | Commands to run at login after setup  |                                   |
| `.zlogout`   | When a login shell exits           | Cleanup on logout                      |                                   |

### Typical Execution Order for Login Interactive Shell

1. `.zshenv`
2. `.zprofile`
3. `.zshrc`
4. `.zlogin`

### Typical Execution for Non-login Interactive Shells

1. `.zshenv`
2. `.zshrc`

### Typical Execution for Non-interactive Shells (e.g., scripts)

1. `.zshenv` only

### Summary

- Put **environment variables used everywhere** in `.zshenv`.
- Put **login-only initializations** in `.zprofile`.
- Put **interactive configurations** like aliases and prompts in `.zshrc`.
- Put **commands to run after login initialization** in `.zlogin`.
- Put **logout scripts** in `.zlogout`.

If you want, I can provide example contents for each file!
```

```md
这些文件是 Z shell（`zsh`）的配置脚本，用于在 shell 启动和退出的不同阶段自定义 shell 行为。每个文件都有其独特功能，并在不同时间被加载，具体取决于启动的 shell 类型（登录 shell、交互式 shell 或非交互式 shell）。

下面是 `.zprofile`、`.zshrc`、`.zshenv`、`.zlogin` 和 `.zlogout` 之间区别的详细说明：

### 1. **.zshenv**

- **用途：**  
  该文件在 **每次调用 zsh** 时都会被加载 —— 无论是登录、交互还是非交互式 shell。
- **典型用例：**  
  设置需要在所有 zsh 实例中可用的环境变量，比如 `PATH`、`EDITOR`、`LC_ALL`，或其他无论 shell 类型都必须存在的变量。
- **注意事项：**  
  因为此文件会在每次 shell 启动时加载，内容应该尽量简洁并且快速加载，应避免包含会产生输出或依赖交互功能的命令。

### 2. **.zprofile**

- **用途：**  
  该文件仅由 **登录 shell** 加载（类似于 `bash` 中的 `.profile` 或 `.bash_profile`）。
- **典型用例：**  
  只需在登录时运行一次的命令或环境配置，例如设置环境变量、启动代理或守护进程、初始化用户环境等。
- **执行顺序：**  
  在 `.zshenv` 之后、`.zlogin` 之前被加载。
- **注意事项：**  
  如果你将 `zsh` 作为登录 shell 使用，`.zprofile` 是设置路径变量或执行每次登录时只需运行一次命令的好地方。

### 3. **.zshrc**

- **用途：**  
  该文件由 **交互式 shell** 加载（无论是否登录）。
- **典型用例：**  
  设置 shell 选项、别名、函数、键绑定和提示符配置——基本上包含所有调整交互行为的内容。
- **注意事项：**  
  非交互式 shell（脚本）不会加载此文件，所以将重要环境变量放在这里可能会出现问题。

### 4. **.zlogin**

- **用途：**  
  该文件在 **登录 shell** 中，在 `.zprofile` 和 `.zshrc` 之后被加载。
- **典型用例：**  
  你想在所有初始化完成后只运行一次的命令；例如启动程序或打印信息。
- **执行顺序：**  
  `.zshenv` → `.zprofile` → `.zshrc` → `.zlogin`

### 5. **.zlogout**

- **用途：**  
  该文件在 **登录 shell 退出时** 被加载。
- **典型用例：**  
  清理命令，比如终止后台任务、清理临时文件或记录退出日志。

### 表格总结

| 文件         | 何时加载                          | 典型用途                             | 备注                               |
|--------------|---------------------------------|-----------------------------------|-----------------------------------|
| `.zshenv`    | **所有 zsh shell**（登录、交互、非交互） | 设置所有情况下需要的环境变量       | 简洁快速，避免输出                 |
| `.zprofile`  | 仅登录 shell                    | 登录时的环境配置                   | 在 `.zlogin` 之前加载             |
| `.zshrc`     | 仅交互式 shell（登录与否）       | 交互式设置：别名、提示符、键绑定   | 脚本不加载                         |
| `.zlogin`    | 仅登录 shell，且在 `.zshrc` 后加载 | 登录后执行的命令                   |                                   |
| `.zlogout`   | 登录 shell 退出时                 | 退出时清理任务                     |                                   |

### 登录交互式 Shell 的典型执行顺序

1. `.zshenv`
2. `.zprofile`
3. `.zshrc`
4. `.zlogin`

### 非登录交互式 Shell 的典型执行顺序

1. `.zshenv`
2. `.zshrc`

### 非交互式 Shell（例如脚本）的典型执行顺序

1. 仅 `.zshenv`

### 总结

- 将**所有 shell 都要用到的环境变量**放在 `.zshenv`。
- 将**仅登录时需要初始化的内容**放在 `.zprofile`。
- 将**交互式配置**（如别名和提示符）放在 `.zshrc`。
- 将**登录后需要执行的命令**放在 `.zlogin`。
- 将**退出时需要执行的脚本**放在 `.zlogout`。

如果你需要，我可以为每个文件提供示例内容！
```