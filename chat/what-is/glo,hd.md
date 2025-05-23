What is .glo, .hd files in building .pdf from .tex?

```md
In the context of using LaTeX to generate PDF documents from `.tex` files, `.glo` and `.hd` files are auxiliary files that some bibliography management tools and LaTeX packages generate as part of the document compilation process, particularly when using glossaries or bibliographies.

### .glo files
- **Glo** stands for "glossary." 
- A `.glo` file is generated when you use the `glossaries` package or similar packages that handle glossaries in your LaTeX document.
- This file acts as an input for creating a glossary to be used in the final document.
- It contains entries for the terms that have been defined in the document, along with their associated definitions.

### .hd files
- **Hd** stands for "header." 
- A `.hd` file is used to store information about the glossary and its entries that are defined in the `.glo` file.
- It is typically generated during the processing of glossary entries and is necessary for programs that compile the glossary (like `makeindex` or `xindy`) to produce the final glossary output.

### Workflow
When you compile your `.tex` document that uses glossaries or acronyms:
1. The LaTeX compiler generates a `.glo` file (if using glossary terms).
2. You then run a glossary tool (like `makeindex` or `xindy`) on the `.glo` file to create a `.gls` file (the final glossary file).
3. The glossary tool may use the `.hd` file during this process.
4. Finally, you compile your LaTeX document again to integrate the generated glossary into the final PDF.

In summary, `.glo` and `.hd` files play critical roles in managing glossary entries when building a PDF document from LaTeX source files.
```

```md
在使用 LaTeX 从 `.tex` 文件生成 PDF 文档的过程中，`.glo` 和 `.hd` 文件是一些文献管理工具和 LaTeX 包在文档编译过程中生成的辅助文件，特别是在使用术语表或参考文献时。

### .glo 文件
- **Glo** 代表“术语表”。
- 当您在 LaTeX 文档中使用 `glossaries` 包或类似处理术语表的包时，会生成一个 `.glo` 文件。
- 该文件作为创建最终文档中使用的术语表的输入。
- 它包含在文档中定义的条目的词条及其相关定义。

### .hd 文件
- **Hd** 代表“头部”。
- `.hd` 文件用于存储与 `.glo` 文件中定义的术语表及其条目相关的信息。
- 它通常在处理术语表条目时生成，并且对于编译术语表的程序（如 `makeindex` 或 `xindy`）生成最终的术语表输出是必要的。

### 工作流程
当您编译使用术语表或首字母缩略词的 `.tex` 文档时：
1. LaTeX 编译器会生成一个 `.glo` 文件（如果使用了术语表词条）。
2. 然后您在 `.glo` 文件上运行术语表工具（如 `makeindex` 或 `xindy`）以创建一个 `.gls` 文件（最终的术语表文件）。
3. 在此过程中，术语表工具可能会使用 `.hd` 文件。
4. 最后，您再次编译 LaTeX 文档，以将生成的术语表整合到最终的 PDF 中。

总之，`.glo` 和 `.hd` 文件在从 LaTeX 源文件构建 PDF 文档时管理术语表条目中发挥着关键作用。
```

After building, should I clear them?

```md
Whether to clear auxiliary files like `.glo`, `.hd`, and others after building a PDF from a `.tex` file depends on several factors, including your workflow, the frequency of changes in your document, and your personal preferences. Here are some considerations:

### When to Keep Auxiliary Files
1. **Frequent Changes**: If you are actively working on your document, it’s often beneficial to keep the auxiliary files. They allow you to quickly recompile your document without having to regenerate everything from scratch each time.
2. **Glossaries and Citations**: If you frequently use glossaries, citations, or bibliographies, keeping these files can save time since they can be large files that take a while to regenerate.

### When to Clear Auxiliary Files
1. **Final Submission or Publication**: If you are preparing your document for final submission, it’s often a good practice to clear auxiliary files first and then rebuild your document. This can help ensure that you have a clean slate and that there are no outdated entries or metadata.
2. **Clutter Management**: Over time, especially in large projects, auxiliary files can accumulate and clutter your project directory. If you are maintaining a clean project directory is essential for you, consider removing unneeded files, especially after you’ve confirmed the final document is correct.
3. **Troubleshooting**: If you encounter problems during compilation (e.g., missing entries or formatting issues), clearing auxiliary files and recompiling from scratch can sometimes resolve these issues.

### Recommended Practice
- **Backup**: If you are concerned about losing work or important references, make sure to back up your project or use version control (like Git) before clearing files.
- **Automated Tools**: Some LaTeX editors or build tools (like `latexmk`) can handle the cleanup of auxiliary files automatically when you want to clean the project. They often have options that allow you to clean specific types of files without deleting everything.

In summary, if you're in an active development phase, it’s usually best to keep the files. If you're preparing for final output or want to clean up your workspace, feel free to clear them out.
```

```md
是否在从 `.tex` 文件生成 PDF 后清理辅助文件（如 `.glo`、`.hd` 等）取决于多个因素，包括你的工作流程、文档的修改频率以及个人偏好。以下是一些考虑事项：

### 何时保留辅助文件
1. **频繁修改**：如果你正在积极修改文档，通常保留辅助文件是有益的。它们可以让你快速重新编译文档，而无需每次都从头开始生成所有内容。
2. **词汇表和引用**：如果你经常使用词汇表、引用或参考文献，保留这些文件可以节省时间，因为它们可能是需要一段时间才能重新生成的大文件。

### 何时清理辅助文件
1. **最终提交或出版**：如果你正在准备文档以进行最终提交，通常建议先清理辅助文件，然后再重新构建文档。这可以帮助确保你拥有一个干净的起点，避免出现过时的条目或元数据。
2. **杂乱管理**：随着时间的推移，尤其是在大型项目中，辅助文件可能会积累并使项目目录变得混乱。如果保持项目目录的整洁对你很重要，考虑删除不需要的文件，尤其是在你确认最终文档是正确的之后。
3. **故障排除**：如果在编译过程中遇到问题（例如缺失条目或格式问题），清理辅助文件并从头重新编译有时可以解决这些问题。

### 推荐做法
- **备份**：如果你担心丢失工作或重要参考资料，请确保在清理文件之前备份你的项目或使用版本控制（如 Git）。
- **自动化工具**：一些 LaTeX 编辑器或构建工具（如 `latexmk`）可以在你想清理项目时自动处理辅助文件的清理。它们通常有选项，可以让你清理特定类型的文件，而无需删除所有文件。

总之，如果你处于积极开发阶段，通常最好保留文件。如果你正在准备最终输出或想整理工作区，可以考虑清理它们。
```