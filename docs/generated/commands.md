# OpenCode 命令清单

更新时间：2026/5/15 10:49:41
命令总数：14

## 内置命令
共 2 条

| 命令 | 描述 |
| --- | --- |
| `/init` | guided AGENTS.md setup |
| `/review` | review changes [commit\|branch\|pr], defaults to uncommitted |

## 技能命令
共 12 条

| 命令 | 描述 |
| --- | --- |
| `/claw-chat` | Answer a user question normally, then wrap the final response in a fixed marker format. |
| `/agent-artifact-portability` | Places skills, knowledge-base markdown, and durable rules in this repo so other Cursor agents and teammates can discover and reuse them after git clone. Use when adding or moving skills, KB files, rules, AGENTS.md, or when the user asks about sharing agent context, multi-agent reuse, portable memory, or team-wide AI docs. |
| `/memory-recall` | Manually retrieve and display relevant project knowledge from the local knowledge base at .claude/MemoryForge/. Use when you want to see what knowledge the system would inject for the current task, or to search the knowledge base with a specific query. Trigger when user says "recall memory", "what do you remember", "check knowledge base", or "/memory-recall". |
| `/sql-knowledge-import` | 扫描项目内的 SQL 文件，反向抽取表元数据（主表、字段、JOIN 键、WHERE 高频过滤、口径注释），生成 .claude/MemoryForge/tables/<table>.md 知识库初稿。 Trigger when 用户说："初始化知识库"、"导入数据字典"、"反向抽取表结构"、"sql-knowledge-import"、"扫一遍 SQL 建知识库"。 Use as 一次性冷启动工具；后续维护用 memory-capture / memory-manage。 Do NOT use for 单表临时查询（用 Kyuubi tables desc）、运行时数据查询、新建表 DDL（用 iceberg-create-table）。<br> |
| `/memory-manage` | View, edit, promote, or delete entries in the project's knowledge base at .claude/MemoryForge/. Use when user wants to manage their project memory — list all entries, promote candidates to permanent knowledge, remove outdated entries, or edit existing knowledge. Trigger when user says "manage memory", "list knowledge", "promote candidate", "delete knowledge", or "/memory-manage". |
| `/memory-capture` | Manually trigger knowledge extraction from the current or a recent Claude Code session. Use when you want to explicitly capture project knowledge — conventions, pitfalls, workflows, or key decisions — from the current coding session into the project's local knowledge base at .claude/MemoryForge/. Trigger when user says "capture memory", "save knowledge", "remember this session", or "/memory-capture". |
| `/evolve` | This skill should be used when the user asks to "evolve a skill", "create a new skill", "improve a skill", "list my skills", "show skill details", "reflect on skills", "delete a skill", "export a skill", "manage skills", "skill lifecycle", or discusses evolving, versioning, creating, or maintaining Claude Code skills. Acts as a meta-skill lifecycle manager for ~/.claude/skills/.<br> |
| `/sql-knowledge-base-header` | Requires every new or materially updated SQL file to open with a Title, Description, and detailed comment block for knowledge-base and agent reuse. Use when writing SQL, creating or editing .sql files, or when the user asks for KB-ready documentation, reusable query metadata, or agent-oriented SQL comments. |
| `/table-dialog-knowledge-extraction` | Extracts structured table ontology from user–agent dialogue (names, grain, keys, partitions, metrics, lineage) and persists it as markdown KB files under the repo. Use when the user discusses Hive/Iceberg tables, DDL, SQL sources, column meanings, or asks to save, document, or build a knowledge base about datasets; also when chat reveals new table facts worth recording for future agent reuse. |
| `/kyuubi` | 使用 kyuubi-cli 执行 Kyuubi SQL 查询、更新和删除操作，以及表元数据管理和 workspace 验证。<br><br>Triggers when user mentions:<br>- "查一下"、"查询一下"、"帮我查"、"执行 SQL"<br>- "查数据"、"数据查询"、"跑查询"<br>- "kyuubi"、"kyuubi-cli"<br>- "查一下数据"、"跑个 SQL"<br>- "查看表"、"搜索表"、"表结构"、"看看表"、"表信息"<br>- "查询历史"、"查看历史"、"历史记录"、"查询记录"<br>- "workspace"、"工作空间"、"切换空间"、"切换区域"<br>- "配置"、"环境"、"查看配置"、"有哪些环境"、"配置了哪些"<br>- "安装 kyuubi"、"更新 kyuubi"、"卸载 kyuubi"<br> |
| `/find-skills` | Helps users discover and install agent skills when they ask questions like "how do I do X", "find a skill for X", "is there a skill that can...", or express interest in extending capabilities. This skill should be used when the user is looking for functionality that might exist as an installable skill. |
| `/iceberg-create-table` | This skill should be used when the user asks to "create iceberg table", "建 iceberg 表", "写建表 DDL", "生成建表语句", "建一张表 ddl", or otherwise needs Iceberg `CREATE TABLE` statements that follow the project's standard template (lifecycle, encryption, optimization priority, field security levels). Apply when the user mentions Iceberg tables in the `iceberg_zjyprc_hadoop` catalog or asks to add a new physical table. Do NOT use for ad-hoc Spark/Hive temp views, `CREATE TABLE AS SELECT` result tables, or tables outside the `iceberg_zjyprc_hadoop` catalog.<br> |
