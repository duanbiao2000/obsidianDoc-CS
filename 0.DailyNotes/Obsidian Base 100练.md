好的，这里有100个关于Obsidian 1.9.0版本后加入的“Base”功能的应用练习，从入门到高手，并包括了使用LLM（大型语言模型）生成Base内容的示例。所有练习都采用`<details><summary>`的问答格式。

**核心概念**

在开始之前，请确保你已经：
1.  将Obsidian升级到1.9.0或更高版本。
2.  在“核心插件”中启用了“Bases”功能。

Base功能的核心是利用笔记的YAML Frontmatter（属性）来创建可筛选、排序和计算的数据库视图。所有数据仍然保存在你的Markdown笔记中。

---

### 第一部分：入门练习 (1-20)

这部分练习将帮助你熟悉Base的基本创建和操作。

<details>
<summary>1. 如何创建一个新的Base文件？</summary>
**答案:**
通过命令面板（`Ctrl/Cmd + P`），输入“Bases”，然后选择“Bases: Create new base”。这会创建一个新的`.base`文件，默认会显示你仓库中的所有笔记。
</details>

<details>
<summary>2. 如何将一个Base嵌入到笔记中？</summary>
**答案:**
与嵌入其他文件一样，使用`![[你的Base文件名.base]]`语法即可。
</details>

<details>
<summary>3. 如何只显示特定文件夹中的笔记？</summary>
**答案:**
在Base视图右侧的“Filters”面板中，点击“Add filter”，选择`file.folder`（或`Folder`），操作符选择`is`，然后选择你想要的文件夹。
</details>

<details>
<summary>4. 如何只显示包含特定标签的笔记？</summary>
**答案:**
在“Filters”面板中，添加一个过滤器，属性选择`tags`，操作符选择`contains`，然后输入或选择你的标签。
</details>

<details>
<summary>5. 如何在Base表格中添加/显示一个笔记的属性列？</summary>
**答案:**
在Base视图右侧的“Properties”面板中，点击“Add property”，然后从列表中选择或搜索你想要显示的属性（例如`author`, `status`等）。
</details>

<details>
<summary>6. 如何隐藏“File”这一默认列？</summary>
**答案:**
在“Properties”面板中，将鼠标悬停在`file.name`上，点击出现的眼睛图标即可隐藏它。
</details>

<details>
<summary>7. 如何根据某一列（如创建日期）对笔记进行排序？</summary>
**答案:**
首先确保“创建日期”属性列（如`file.ctime`）已显示。然后直接点击该列的标题即可进行升序或降序排序。
</details>

<details>
<summary>8. 我有一个读书笔记文件夹，如何创建一个只显示这些笔记的Base？</summary>
**答案:**
1.  创建一个新的Base。
2.  添加一个过滤器：`file.folder` is `读书笔记`。
3.  在“Properties”中添加你想看的属性，如`author`, `rating`, `status`。
</details>

<details>
<summary>9. 如何在Base表格视图中直接修改一个笔记的属性值？</summary>
**答案:**
直接点击表格中你想要修改的单元格，就可以像在Excel中一样进行编辑。例如，将一本书的`status`从“未读”改为“在读”。
</details>

<details>
<summary>10. 如何创建一个筛选出所有未完成任务的Base？（假设任务笔记有一个`status`属性）</summary>
**答案:**
添加一个过滤器，属性为`status`，操作符为`is not`，值为`completed`。
</details>

<details>
<summary>11. 如何重命名一个Base视图的名称？</summary>
**答案:**
在Base视图的左上角，点击当前的视图名称（默认为“Table”），在下拉菜单中选择“Rename view”。
</details>

<details>
<summary>12. 如何创建一个只显示过去7天内修改过的笔记的Base？</summary>
**答案:**
1.  添加一个过滤器，属性选择`file.mtime` (修改时间)。
2.  操作符选择`is after`。
3.  值输入`today() - "7d"`。
</details>

<details>
<summary>13. 如何显示所有图片附件（.png, .jpg）？</summary>
**答案:**
1.  创建一个Base。
2.  添加一个过滤器组（`or`逻辑）。
3.  在组内添加第一个过滤器：`file.ext` is `png`。
4.  在组内添加第二个过滤器：`file.ext` is `jpg`。
</details>

<details>
<summary>14. 如何创建一个显示所有没有设置`status`属性的笔记的Base？</summary>
**答案:**
添加一个过滤器，属性选择`status`，操作符选择`is empty`。
</details>

<details>
<summary>15. 如何导出Base视图为CSV文件？</summary>
**答案:**
点击左上角的视图名称，在下拉菜单中选择“Export to CSV”。
</details>

<details>
<summary>16. 我想建立一个电影清单，笔记中都有一个`rating`（1-5）属性，如何只显示评分大于等于4的电影？</summary>
**答案:**
添加一个过滤器，属性选择`rating`，操作符选择`is greater than or equal to`，值输入`4`。
</details>

<details>
<summary>17. 如何创建一个显示所有包含“会议”一词的笔记的Base？</summary>
**答案:**
添加一个过滤器，属性选择`file.name`，操作符选择`contains`，值输入`会议`。
</details>

<details>
<summary>18. 如何在同一个Base文件中创建第二个视图？</summary>
**答案:**
点击左上角视图名称旁边的“+”号，或者在视图下拉菜单中选择“New view”。
</details>

<details>
<summary>19. 如何将一个表格视图（Table）切换为卡片视图（Cards）？</summary>
**答案:**
1.  点击左上角的视图名称，选择“Configure view”。
2.  在“Layout”选项中，选择“Cards”。
</details>

<details>
<summary>20. 在卡片视图中，如何设置卡片的封面图片？</summary>
**答案:**
在卡片视图的配置中，“Image property”选项选择一个包含图片链接的属性（例如，一个名为`cover`的属性，其值为`[[cover.jpg]]`或一个URL）。
</details>

---

### 第二部分：进阶练习 (21-50)

这部分练习将引导你使用更复杂的过滤、公式和多视图管理。

<details>
<summary>21. 如何创建一个同时满足两个条件的过滤器（AND逻辑）？</summary>
**答案:**
默认情况下，添加多个过滤器就是AND逻辑。例如，同时添加`tags` contains `book`和`status` is `reading`，将只显示正在阅读的书籍。
</details>

<details>
<summary>22. 如何创建一个满足任一条件的过滤器（OR逻辑）？</summary>
**答案:**
在“Filters”面板中，点击“Add filter or group”，选择“New group (any)”。然后在这个组内添加你的多个条件。例如，显示`status` is `urgent` **或** `priority` is `high`的笔记。
</details>

<details>
<summary>23. 如何使用公式（Formula）创建一个新列？</summary>
**答案:**
在“Properties”面板中，点击“Add property”，然后选择“New formula”。例如，给它命名为`price_with_tax`。
</details>

<details>
<summary>24. 假设笔记有`price`属性，如何用公式计算含10%税的价格并显示在新列？</summary>
**答案:**
1.  创建一个名为`price_with_tax`的公式属性。
2.  在公式编辑框中输入`price * 1.1`。
</details>

<details>
<summary>25. 如何用公式将两个文本属性（如`firstName`和`lastName`）合并成一个完整的姓名列？</summary>
**答案:**
创建一个名为`fullName`的公式属性，公式为`firstName + " " + lastName`。
</details>

<details>
<summary>26. 如何创建一个“笔记年龄”的公式列，显示从创建到现在过去了多少天？</summary>
**答案:**
创建一个名为`noteAge`的公式列，输入公式 `(now() - file.ctime).days`。
</details>

<details>
<summary>27. 我有一个项目管理Base，笔记属性有`deadline`（日期格式），如何用公式计算距离截止日期还有几天？</summary>
**答案:**
创建一个名为`days_left`的公式属性，公式为`(deadline - now()).days`。
</details>

<details>
<summary>28. 如何使用`if`函数在公式中进行条件判断？</summary>
**答案:**
`if(condition, value_if_true, value_if_false)`。例如，创建一个名为`priority_label`的公式，内容为`if(priority > 3, "高", "普通")`。
</details>

<details>
<summary>29. 如何筛选出文件名以“2025-”开头的笔记？</summary>
**答案:**
添加一个过滤器，使用高级模式（点击过滤器输入框旁边的小代码图标），输入`file.name.startsWith("2025-")`。
</details>

<details>
<summary>30. 如何在卡片视图中，让没有封面的卡片显示特定的颜色？</summary>
**答案:**
在你的笔记中，如果`cover`属性为空，可以设置一个`color`属性，值为十六进制颜色码（如`#ff0000`）。然后在卡片视图配置中，将“Image property”设置为`cover`或`color`。Base会自动渲染颜色。
</details>

<details>
<summary>31. 如何创建一个Base，显示所有链接到当前笔记的笔记（模拟反向链接面板）？</summary>
**答案:**
将Base嵌入到你的笔记中。然后添加一个过滤器，使用高级模式输入 `file.hasLink(this.file)`。这里的`this.file`特指嵌入该Base的当前文件。
</details>

<details>
<summary>32. 如何显示所有`pages`属性大于200，并且`language`属性为“English”的读书笔记？</summary>
**答案:**
添加两个过滤器（AND逻辑）：
1.  `pages` is greater than `200`
2.  `language` is `English`
</details>

<details>
<summary>33. 如何用公式将一个数字格式化为货币字符串，例如将`123`变为`"$123.00"`？</summary>
**答案:**
创建一个公式属性，内容为`"$" + price.toFixed(2)`。
</details>

<details>
<summary>34. 如何创建一个视图，按文件夹分组显示我的所有笔记？</summary>
**答案:**
在视图的配置选项中，找到“Group by”选项，选择`file.folder`。
</details>

<details>
<summary>35. 我有一个会议记录文件夹，如何创建一个Base，显示所有“参与人”（`attendees`，一个列表属性）中包含“张三”的会议？</summary>
**答案:**
添加一个过滤器，属性选择`attendees`，操作符选择`contains`，值输入`张三`。
</details>

<details>
<summary>36. 如何创建一个Base，显示所有出链（outgoing links）数量超过5个的笔记？</summary>
**答案:**
添加一个过滤器，使用高级模式，输入`file.links.length > 5`。
</details>

<details>
<summary>37. 如何用公式检查一个任务是否逾期？（假设有`deadline`和`status`属性）</summary>
</details>

<details>
<summary>38. 如何创建一个“看板”视图的雏形？（按`status`属性分组的卡片视图）</summary>
**答案:**
1.  创建一个卡片视图。
2.  在视图配置中，设置“Group by”为`status`属性。
</details>

<details>
<summary>39. 如何筛选出属性`review_date`（审核日期）是今天的笔记？</summary>
**答案:**
添加一个过滤器，属性`review_date`，操作符`is`，值输入`today()`。
</details>

<details>
<summary>40. 如何在一个Base中创建一个“已归档”视图，显示所有`status`为`archived`或在`Archive`文件夹中的笔记？</summary>
**答案:**
1.  创建一个新视图，命名为“已归档”。
2.  添加一个OR逻辑的过滤器组。
3.  组内添加条件1: `status` is `archived`。
4.  组内添加条件2: `file.folder` is `Archive`。
</details>

<details>
<summary>41. 如何用公式从一个完整的日期时间属性`created_at`中只提取出日期部分？</summary>
**答案:**
创建一个公式属性，输入`created_at.date()`。
</details>

<details>
<summary>42. 如何显示所有YAML属性中`aliases`（别名）不为空的笔记？</summary>
**答案:**
添加一个过滤器，属性选择`aliases`，操作符选择`is not empty`。
</details>

<details>
<summary>43. 如何创建一个Base，显示所有与当前笔记有相同标签的笔记？</summary>
**答案:**
嵌入Base到笔记中，使用高级过滤器 `file.tags.some(tag => this.file.tags.contains(tag)) and file.path != this.file.path`。
</details>

<details>
<summary>44. 如何用公式将笔记的标签列表转换成一个用逗号分隔的字符串？</summary>
**答案:**
创建一个公式属性，输入`file.tags.join(", ")`。
</details>

<details>
<summary>45. 如何在Base中显示文件的相对路径？</summary>
**答案:**
在“Properties”中，添加`file.path`属性。
</details>

<details>
<summary>46. 如何筛选出YAML区域大于10行的笔记？（一个近似的指标）</summary>
**答案:**
这是一个高级用法，目前Base本身无法直接计算YAML行数。你可以通过外部脚本预处理，在YAML中加入一个`yaml_lines`属性，然后根据这个属性筛选。
</details>

<summary>48. 如何在Base中创建一个“复制Markdown链接”的按钮？</summary>
创建一个公式列，使用`link`函数。公式可以为`link(file.path, "复制")`。但这只会创建一个内部链接，更复杂的操作需要社区插件支持。
</details>

<details>
<summary>49. 如何创建一个显示所有孤立笔记（没有入链也没有出链）的Base？</summary>
**答案:**
添加一个AND过滤器组：
1. `file.inlinks.length == 0`
2. `file.outlinks.length == 0`
</details>

<details>
<summary>50. 如何在不同的Base视图之间快速切换？</summary>
**答案:**
点击Base视图左上角的视图名称，在下拉列表中选择你想要切换到的视图。
</details>

---

### 第三部分：高手练习 & LLM集成 (51-100)

这部分将深入探讨高级公式、复杂视图、自动化工作流，特别是如何利用LLM来生成和维护你的Base内容。你需要安装一个LLM插件，如 `Text Generator`。

<details>
<summary>51. [LLM] 我想创建一个书籍库，如何让LLM帮我生成10本关于“科幻小说”的书籍笔记，并包含标准化的YAML属性？</summary>
**答案:**
1.  安装并配置好`Text Generator`插件。
2.  创建一个新的笔记，打开`Text Generator`。
3.  使用类似以下的提示词 (Prompt):
    > “请为我生成10个独立的Markdown笔记内容，每个笔记代表一本经典的科幻小说。每个笔记都必须包含以下YAML frontmatter格式：
    > ```yaml
    > ---
    > title: "书籍标题"
    > author: "作者"
    > year: 出版年份
    > rating: 0
    > status: "toread"
    > tags: [book, scifi]
    > cover_url: "一个有效的封面图片URL"
    > ---
    > 
    > # [书籍标题]
    > 
    > [书籍的一段简短介绍]
    > ”
4.  执行生成，然后将返回的内容分割成10个独立的`.md`文件。你的书籍Base现在就会自动填充这些新笔记。
</details>

<details>
<summary>52. [LLM] 如何使用LLM为一个已存在的笔记（例如一篇粘贴的文章）自动生成摘要和关键词，并填充到YAML属性中？</summary>
**答案:**
1.  在`Text Generator`中创建一个模板。
2.  模板内容可以设置为：
    > ```yaml
    > ---
    > summary: "{{摘要}}"
    > keywords: [{{关键词列表}}]
    > ---
    > 
    > {{笔记原文}}
    > ```
3.  配置一个使用此模板的命令，其中包含两个LLM请求：一个用于生成`摘要`（“请为以下文章生成一个50字的摘要：{{笔记原文}}”），另一个用于生成`关键词列表`（“请为以下文章提取5个关键词，并用逗号分隔：{{笔记原文}}”）。
4.  对你的文章笔记执行此命令，它会自动更新YAML区域。
</details>

<details>
<summary>53. 如何创建一个“项目仪表盘”，其中包含三个视图：“进行中的项目”、“已完成的项目”和“所有项目的卡片视图”？</summary>
**答案:**
1.  在一个`.base`文件中创建三个视图。
2.  **视图1 “进行中”**: 表格布局。过滤器设置为 `type` is `project` AND `status` is `inprogress`。
3.  **视图2 “已完成”**: 表格布局。过滤器设置为 `type` is `project` AND `status` is `completed`。
4.  **视图3 “所有项目卡片”**: 卡片布局。过滤器设置为 `type` is `project`。设置封面图片和需要显示的属性。
</details>

<details>
<summary>54. 我有一个习惯打卡的Base，笔记属性有`habit`和`date`，如何用公式计算出每个习惯的“连续打卡天数”？</summary>
**答案:**
这是一个非常高级的挑战，因为Base的公式目前无法直接跨笔记进行连续性计算。实现这个功能的最佳方法是：
1.  **方法一（简化）**: 创建一个“最近打卡”视图，按`habit`分组，按`date`降序排序，让你能直观地看到每个习惯的最近打卡日期。
2.  **方法二（外部脚本）**: 使用Python或DataviewJS等工具定期扫描笔记，计算连续天数，并将结果写回每个习惯主笔记的YAML属性（如`streak_days`）中。然后Base就可以直接显示这个属性了。
</details>

<details>
<summary>55. [LLM] 我有很多会议录音的文字稿，如何利用LLM自动提取会议日期、参与者、以及行动项，并创建带有这些属性的会议记录笔记？</summary>
**答案:**
使用`Text Generator`插件，设计一个复杂的提示词：
> “你是一个会议纪要分析助手。请从以下会议文字稿中提取信息，并以YAML frontmatter的格式输出。你需要提取：
> - `meeting_date`: 会议日期 (格式 YYYY-MM-DD)
> - `participants`: 参与者列表 (YAML list格式)
> - `action_items`: 行动项列表，每个项目前要标记负责人 (YAML list格式)
> 
> 文字稿如下：
> ```
> {{selection}}
> ```
> ”
>
> 将这段提示词配置为命令，选中文字稿后执行，即可生成带有结构化数据的笔记。
</details>

<details>
<summary>56. 如何创建一个Base，用于管理CRM客户信息，并根据`last_contact_date`属性，将超过90天未联系的客户高亮显示？</summary>
**答案:**
1.  创建一个客户信息Base。
2.  添加一个名为`follow_up_status`的公式列。
3.  公式为：`if((now() - last_contact_date).days > 90, "🔴 需要跟进", "🟢 正常")`。
4.  你可以根据这个新列进行排序，优先处理需要跟进的客户。
</details>


<details>
<summary>59. [LLM] 如何使用LLM批量为一系列产品笔记生成统一格式的优缺点列表？</summary>
**答案:**
1.  创建一个`Text Generator`模板，用于调用LLM。
2.  提示词示例：
    > "根据以下产品描述，生成一个Markdown格式的优缺点列表。
    >
    > ### 优点
    > - [优点1]
    > - [优点2]
    >
    > ### 缺点
    > - [缺点1]
    >
    > 产品描述：
    > {{note_content}}
    > "
3.  可以使用`Text Generator`的批量处理功能，对一个文件夹下的所有产品笔记执行此模板。
</details>

<details>
<summary>60. 如何创建一个动态的“学习路线图”Base，根据前置课程（`prerequisites`属性）是否完成（`status: "completed"`）来决定当前课程的状态？</summary>
**答案:**
这同样超出了Base内置公式的能力范围，因为它需要查询其他笔记的状态。推荐的实现方式是：
1.  使用Dataview插件的行内查询（inline query）来动态显示每个课程的状态。
2.  或者，使用更强大的DataviewJS脚本来生成一个动态的Markdown表格，模拟Base的功能，但在其中加入跨笔记查询的逻辑。
</details>

<details>
<summary>61. 如何在Base中处理多对多关系？例如，管理作者和书籍，一个作者可以写多本书，一本书也可以有多个作者。</summary>
**答案:**
1.  创建两类笔记：“作者笔记”和“书籍笔记”。
2.  在“书籍笔记”的YAML中，使用列表属性`authors`链接到对应的作者笔记，如 `authors: ["[[作者A]]", "[[作者B]]"]`。
3.  在“作者笔记”的YAML中，也可以创建一个`books`列表。
4.  创建一个“书籍”Base，可以按`authors`属性进行筛选。
5.  创建一个“作者”Base，可以按`books`属性进行筛选。
</details>

<details>
<summary>62. [LLM] 如何让LLM扮演一个项目经理，为一个新的项目构想（一句话描述）生成一个包含任务拆解、预计工时和优先级的笔记，并自动添加`type: task`等属性？</summary>
**答案:**
配置一个`Text Generator`命令，提示词如下：
> “你是一个经验丰富的项目经理。请将以下项目构想拆解成一个详细的任务列表，并为每个任务估算工时（小时）和设置优先级（高/中/低）。请以一个完整的Markdown笔记形式输出，包含一个`tasks`属性，其值为一个对象列表的YAML。
>
> 项目构想: `{{selection}}`
>
> 输出格式示例:
> ```yaml
> ---
> project_name: "{{selection}}"
> status: "planning"
> tags: [project]
> tasks:
>   - task: "任务一"
>     hours: 8
>     priority: "高"
>   - task: "任务二"
>     hours: 16
>     priority: "中"
> ---
>
> # 项目：{{selection}}
>
> ## 任务分解
>
> ### 任务一
> ...
> ”
</details>

<details>
<summary>63. 如何创建一个Base视图，显示所有重复的笔记（文件名相同，但路径不同）？</summary>
**答案:**
这需要分组和计数的聚合功能，目前Base还不支持。但你可以通过DataviewJS查询实现：
```dataviewjs
const pages = dv.pages()
    .groupBy(p => p.file.name)
    .filter(g => g.rows.length > 1)
    .sort(g => g.key);
dv.table(["重复文件名", "文件路径"], pages.map(p => [p.key, p.rows.map(row => row.file.link).join(", ")]));
```
</details>

<details>
<summary>64. 我能否在Base的公式中使用正则表达式？</summary>
**答案:**
是的，可以使用`test()`函数。例如，要筛选出`email`属性符合标准邮箱格式的笔记，可以在高级过滤器中使用 `test(/^[^\s@]+@[^\s@]+\.[^\s@]+$/, email)`。
</details>

<details>
<summary>65. [LLM] 如何使用LLM将非结构化的文本（如剪藏的网页）转换为结构化的笔记，自动提取标题、作者、发布日期等信息填入YAML？</summary>
**答案:**
与问题55类似，创建一个`Text Generator`模板，让LLM从文本中提取关键信息。
> "从以下文章内容中提取`title`, `author`, `publication_date`，并以YAML格式返回。如果找不到某个信息，请将其值留空。
>
> 文章内容:
> {{clipboard}}
>"
</details>

<details>
<summary>66. 如何创建一个“每周回顾”的Base，自动筛选出上周创建的所有笔记，并按文件夹分组？</summary>
**答案:**
1.  创建一个新Base或新视图。
2.  添加一个AND过滤器组：
    -   `file.ctime` is after `today() - "7d" - (weekday(today()) - 1) + "d"` (上周一)
    -   `file.ctime` is before `today() - (weekday(today()) - 1) + "d"` (本周一)
3.  在视图配置中，设置“Group by”为`file.folder`。
</details>

<details>
<summary>67. 如何在Base中管理食谱，并添加一个“总热量”的公式列，该列的值是`ingredients`（一个对象列表）中每个成分热量的总和？</summary>
**答案:**
假设`ingredients`的YAML结构是：
```yaml
ingredients:
  - name: "鸡蛋"
    calories: 155
  - name: "面粉"
    calories: 364
```
可以使用`map`和`sum`函数来计算总和。创建一个公式列，输入：
`ingredients.map(i => i.calories).sum()`
</details>

<details>
<summary>68. [LLM] 如何使用LLM为我的旅行照片笔记批量生成描述性的文字和相关的`tags`？</summary>
**答案:**
这需要一个能够处理图片的多模态LLM插件。如果你的LLM插件支持（例如通过API连接到GPT-4V），你可以这样设计提示词：
> "这是一张旅行照片。请为其生成一段50字的生动描述，并提取5个相关的标签（如`#beach`, `#sunset`）。
>
> 图片: `{{image_path}}`"
>
> 然后批量处理你的照片笔记。
</details>

<details>
<summary>69. 我可以自定义Base视图的CSS样式吗？</summary>
**答案:**
可以。通过Obsidian的CSS片段（CSS Snippets）功能，你可以针对Base的特定CSS类（如`.base-table-view`, `.base-card-view`）编写自定义样式，来改变字体、颜色、间距等。
</details>

<details>
<summary>70. 如何创建一个“今日待办”的Base，显示所有`type: task`、`status: incomplete`且`due_date`为今天或之前的笔记？</summary>
**答案:**
创建一个AND过滤器组：
1. `type` is `task`
2. `status` is `incomplete`
3. `due_date` is on or before `today()`
</details>

<details>
<summary>71. [LLM] 我正在学习一门外语，如何用LLM为我的单词本笔记自动生成例句，并存入`examples`属性？</summary>
**答案:**
为`Text Generator`配置一个命令：
> “为单词`{{title}}`（在笔记标题中）生成三个英语例句，并以YAML列表的格式返回。
>
> 单词：`{{title}}`
>
> 格式:
> ```yaml
> examples:
>   - "例句1"
>   - "例句2"
>   - "例句3"
> ```
</details>

<details>
<summary>72. 如何在Base中创建一个“甘特图”的近似视图？</summary>
**答案:**
目前Base没有原生的甘特图视图。但你可以：
1.  创建一个任务Base，包含`start_date`和`end_date`属性。
2.  创建一个公式列，名为`timeline`，用文本字符（如`■`）来模拟时间条的长度和位置，但这非常复杂。
3.  更现实的方法是，使用Mermaid图表语法，并借助DataviewJS从Base查询的数据动态生成Mermaid代码。
</details>

<details>
<summary>73. 如何处理Base中的嵌套属性？例如`person.address.city`。</summary>
**答案:**
你可以在过滤器和公式中直接使用点符号来访问嵌套属性。例如，筛选城市为“北京”的笔记：`person.address.city` is `北京`。
</details>

<details>
<summary>74. [LLM] 我想写一部小说，如何用LLM帮我生成角色卡片笔记，包含姓名、年龄、背景故事和性格特点等YAML属性？</summary>
**答案:**
提示词示例：
> “为我的赛博朋克小说创建一个新的角色。请随机生成角色的姓名、年龄、职业，并撰写一段200字的背景故事和5个核心性格特点。请将这些信息以YAML frontmatter的格式输出。”
</details>

<details>
<summary>75. 如何在Base中实现一个简单的发票管理系统，自动计算每张发票的“总金额”（`items`列表中`price * quantity`的总和）？</summary>
**答案:**
类似于问题67，假设`items`结构为`{name, price, quantity}`。
创建一个名为`total_amount`的公式列，输入：
`items.map(i => i.price * i.quantity).sum()`
</details>

**剩余的25个练习将进一步挑战极限，并融合多种高级技巧。**

76.  **[LLM] 知识图谱扩展**：使用LLM分析一篇笔记，识别出其中的关键概念，并自动创建新的笔记链接到这些概念，同时在Base中跟踪这些新生成的“概念笔记”。
77.  **动态MOC**：创建一个Base，它能根据当前文件夹（`this.file.folder`）动态筛选和显示该文件夹下的所有笔记，作为一个可嵌入的、自动更新的目录。
78.  **财务追踪**：创建一个支出记录Base，用公式计算每个月的总支出，并通过视图分组功能按类别（`category`属性）查看支出分布。
79.  **A/B测试笔记**：创建两个版本的笔记模板（A和B），用一个`template_version`属性标记。然后用Base分析这两个版本的笔记在“完成率”（`status: "completed"`）上是否有差异。
80.  **[LLM] 自动链接建议**：使用LLM读取一个新笔记的内容，然后在你的知识库中找到3个最相关的旧笔记，并将它们的链接添加到一个名为`related_links`的YAML属性中。
81.  **高级时间计算**：在任务Base中，创建一个公式列`working_days_left`，只计算剩余的工作日（排除周末）。这需要更复杂的日期函数组合。
82.  **内容依赖过滤**：筛选出所有在笔记正文（`file.content`）中提到了`[[项目X]]`，但在YAML的`project`属性中却没有标记`项目X`的笔记，用于数据清洗。
83.  **[LLM] 风格转换器**：用LLM将一篇技术性的笔记改写成通俗易懂的语言，并将改写后的内容保存在一个新的笔记中，通过`original_note`属性链接回原文。
84.  **Base作为导航**：创建一个“仪表盘”笔记，嵌入多个Base视图，分别显示“今日待办”、“最近文档”、“高优项目”，作为你进入Obsidian的启动页面。
85.  **习惯养成可视化**：在习惯打卡Base中，使用公式列，根据连续打卡天数（假设已通过外部脚本计算）显示不同的emoji（如🔥, 👍, 😊），实现游戏化。
86.  **[LLM] 生成测试题**：让LLM根据你的学习笔记内容，生成选择题或填空题，并创建为带有`question`, `options`, `answer`属性的新笔记，方便后续用Base制作成复习卡片。
87.  **元数据健康检查**：创建一个Base，专门用来查找元数据不完整的笔记，例如`title`为空，或`review_date`格式不正确的笔记。
88.  **嵌套Base**：在一个描述项目的笔记中，嵌入一个只显示该项目相关任务的Base。这个Base的过滤器会引用父笔记的项目名称：`project` is `this.file.name`。
89.  **[LLM] 市场研究**：使用LLM插件和网页抓取功能，自动收集关于某个主题的最新新闻，并将每条新闻保存为一个带有来源、日期和摘要属性的笔记，在Base中进行跟踪。
90.  **复杂评分系统**：为书籍创建一个“综合评分”公式列，该评分由你的个人评分（`my_rating`）和社区评分（`goodreads_rating`）加权平均得出。
91.  **动态项目报告**：在一个项目周报模板中嵌入一个Base，该Base自动筛选出本周内所有状态变为“完成”的任务。
92.  **[LLM] 角色扮演对话**：创建一个`Text Generator`命令，让你能与你的一个“角色”笔记（问题74创建的）进行对话。LLM会基于角色的背景和性格特点来回答你的问题。
93.  **版本控制模拟**：管理文档时，为每次重大修改创建一个副本，并添加`version`和`change_log`属性。用Base来查看一个文档的所有历史版本和修改记录。
94.  **跨库查询（高级）**：虽然Base本身不支持，但可以通过将其他库的笔记数据导出为JSON，然后在一个库中使用DataviewJS读取这个JSON文件来模拟跨库Base。
95.  **[LLM] 情感分析**：对你的日记笔记（文件夹），使用LLM进行情感分析（正面/中性/负面），并将结果写入`sentiment`属性，然后在Base中可视化你一段时间内的情绪波动。
96.  **查找信息孤岛**：创建一个Base，筛选出那些只有一个入链（通常是来自某个MOC或索引），但没有任何出链的笔记，这些可能是知识网络中的“断头路”。
97.  **“下一步行动”生成器**：创建一个Base，显示所有`status`为`waiting_for`的任务。并创建一个公式按钮，点击后可以用LLM生成一封催办邮件的草稿。
98.  **[LLM] 思维链（CoT）提示**：创建一个复杂的`Text Generator`命令，让LLM在处理一个复杂问题时，先输出它的思考过程，再给出最终答案，并将整个过程记录在一个笔记中，用于知识溯源。
99.  **Base驱动的写作流程**：创建一个写作项目Base，管理你的章节。其中一个视图是“大纲”，只显示章节标题和简介。另一个是“写作中”，只显示`status: "writing"`的章节。还有一个是“字数统计”，用公式（`file.content.length`）来跟踪每章的进度。
100. **终极挑战：自我维护的知识库**：结合以上所有技巧，设计一个工作流。当你创建一个新笔记时，一个自动化工具（如Templater + Text Generator）会触发LLM进行分析，自动添加标签、摘要和相关链接。然后，一个“数据健康”Base会定期检查所有笔记的元数据完整性，并标记出需要你手动整理的条目，形成一个几乎全自动的知识管理闭环。

---

# Obsidian Bases YAML 应用练习题集 (Obsidian Bases YAML Practice Exercises)

**介绍 (Introduction):** Obsidian 1.9.0 及以上版本引入了 **Bases** 核心插件，可以将笔记集合变成强大的数据库，通过 YAML 配置定义视图、过滤器和公式[_[1]_](https://obsidian.md/changelog/2025-05-21-desktop-v1.9.0/#:~:text=Introducing%20Bases%2C%20a%20new%20core,plans%2C%20reading%20lists%2C%20and%20more)[_[2]_](https://help.obsidian.md/bases/syntax#:~:text=SQL%20or%20Dataview.%20The%20,a%20recursively%20defined%20filter%20object)。Bases 设计易用，不需要编程知识就能创建交互式列表、表格等视图[_[3]_](https://obsidian.rocks/getting-started-with-obsidian-bases/#:~:text=Bases%20are%20designed%20to%20be,notes%20from%20meh%20to%20amazing)。所有数据均存储在标准 Markdown 文件的 YAML Frontmatter 中，配置保存在 .base 文件内[_[4]_](https://obsidian.md/changelog/2025-05-21-desktop-v1.9.0/#:~:text=All%20the%20data%20in%20a,file%20format%20and%20syntax)[_[2]_](https://help.obsidian.md/bases/syntax#:~:text=SQL%20or%20Dataview.%20The%20,a%20recursively%20defined%20filter%20object)。以下练习题覆盖从入门到高级功能点，包括任务管理、项目追踪、日记系统、知识卡、学习记录、自动摘要、AI 问答和智能提示生成等实际应用场景。每题以 <details><summary> 展示，包含中英文题意和最新 Base YAML 配置示例，必要时调用 Gemini 模型，并提供标准答案 YAML 代码段。

## 基础功能 (Basic Features)

<details><summary>练习题1：创建一个基本的 Base 以列出所有带有标签 book 的笔记 - Create a basic Base listing all notes tagged with book</summary>

**练习题描述 (Chinese):** 编写 Base YAML 配置，只显示包含标签 book 的笔记。  
**Exercise Description (English):** Write a Base YAML configuration that shows only notes with the tag book.

**标准答案 (YAML):**

filters:  
  - file.hasTag("book")views:  
  - type: table    name: "Books"

</details>

<details><summary>练习题2：列出所有 Markdown 文件 - List all Markdown files</summary>

**练习题描述 (Chinese):** 编写 Base 配置，过滤出后缀名为 md 的文件（即只显示 Markdown 文件）。  
**Exercise Description (English):** Write a Base configuration to filter and show only files with the extension md (i.e. only Markdown files).

**标准答案 (YAML):**

filters:  
  - file.ext == "md"views:  
  - type: table    name: "Markdown Files"

</details>

<details><summary>练习题3：按照修改时间排序文件 - Sort files by modification time</summary>

**练习题描述 (Chinese):** 编写 Base 配置，在表格视图中按文件修改时间（file.mtime）降序排序显示文件。  
**Exercise Description (English):** Write a Base configuration to display files in a table view sorted by modification time (file.mtime) in descending order.

**标准答案 (YAML):**

views:  
  - type: table    name: "Recently Modified"    order:      - -file.mtime

</details>

<details><summary>练习题4：过滤特定文件夹中的文件 - Filter files in a specific folder</summary>

**练习题描述 (Chinese):** 编写 Base 配置，只显示位于文件夹 Projects 中的文件。  
**Exercise Description (English):** Write a Base configuration that shows only files located in the folder Projects.

**标准答案 (YAML):**

filters:  
  - file.inFolder("Projects")views:  
  - type: table    name: "Project Files"

</details>

<details><summary>练习题5：过滤指定前置属性的笔记 - Filter notes by a frontmatter property</summary>

**练习题描述 (Chinese):** 假设笔记 frontmatter 中有属性 status，请编写 Base 配置，只显示 status 属性值为 "in-progress" 的笔记。  
**Exercise Description (English):** Assuming notes have a frontmatter property status, write a Base configuration that shows only notes where status equals "in-progress".

**标准答案 (YAML):**

filters:  
  - status == "in-progress"views:  
  - type: table    name: "In-Progress Notes"

</details>

<details><summary>练习题6：定义属性显示名称 - Define a display name for a property</summary>

**练习题描述 (Chinese):** 在 Base 配置的 properties 部分，为属性 status 设置显示名称为 "Status"。  
**Exercise Description (English):** In the Base configuration under the properties section, set the display name of the property status to "Status".

**标准答案 (YAML):**

properties:  
  status:    displayName: "Status"

</details>

<details><summary>练习题7：多标签过滤 (AND) - Filter notes that have both of two tags</summary>

**练习题描述 (Chinese):** 编写 Base 配置，过滤出同时包含标签 book 和 reading 的笔记。  
**Exercise Description (English):** Write a Base configuration to filter notes that have **both** tags book and reading.

**标准答案 (YAML):**

filters:  
  and:    - file.hasTag("book")    - file.hasTag("reading")views:  
  - type: table    name: "Books in Reading List"

</details>

<details><summary>练习题8：多标签过滤 (OR) - Filter notes that have either of two tags</summary>

**练习题描述 (Chinese):** 编写 Base 配置，过滤出包含标签 book 或标签 article 中任一的笔记。  
**Exercise Description (English):** Write a Base configuration to filter notes that have **either** the tag book or article.

**标准答案 (YAML):**

filters:  
  or:    - file.hasTag("book")    - file.hasTag("article")views:  
  - type: table    name: "Books or Articles"

</details>

<details><summary>练习题9：创建一个基本表格视图 - Create a basic table view</summary>

**练习题描述 (Chinese):** 编写 Base 配置，创建一个名为 "My Base" 的表格视图（不需要过滤条件）。  
**Exercise Description (English):** Write a Base configuration to create a table view named "My Base" (no filters needed).

**标准答案 (YAML):**

views:  
  - type: table    name: "My Base"

</details>

<details><summary>练习题10：默认不使用过滤器 - Base with no filters (all files)</summary>

**练习题描述 (Chinese):** 编写 Base 配置，不使用任何 filters，使 Base 包含库中所有文件（默认视图）。  
**Exercise Description (English):** Write a Base configuration with no filters, so that the Base includes **all files** in the vault (default view).

**标准答案 (YAML):**

views:  
  - type: table    name: "All Files"

</details>

## 任务管理 (Task Management)

<details><summary>练习题11：显示未完成任务 - Show incomplete tasks</summary>

**练习题描述 (Chinese):** 假设任务笔记 frontmatter 中有属性 status 表示状态（例如 "done" 和 "todo"）。编写 Base 配置，只显示 status != "done" 的任务。  
**Exercise Description (English):** Assuming task notes have a frontmatter property status (e.g. "done" or "todo"), write a Base configuration to show only tasks where status != "done" (i.e., incomplete tasks).

**标准答案 (YAML):**

filters:  
  - status != "done"views:  
  - type: table    name: "Incomplete Tasks"

</details>

<details><summary>练习题12：按到期日期排序任务 - Sort tasks by due date</summary>

**练习题描述 (Chinese):** 假设每个任务有前置属性 dueDate 表示截止日期。编写 Base 配置，在表格中按 dueDate 升序显示任务（最早到期在前）。  
**Exercise Description (English):** Assuming each task has a frontmatter property dueDate for the deadline, write a Base configuration to display tasks in a table sorted by dueDate ascending (earliest due date first).

**标准答案 (YAML):**

views:  
  - type: table    name: "Tasks by Due Date"    order:      - note.dueDate

</details>

<details><summary>练习题13：按项目过滤任务 - Filter tasks by project</summary>

**练习题描述 (Chinese):** 假设任务前置属性 project 指定所属项目名称。编写 Base 配置，仅显示 project 属性值为 "Project A" 的任务。  
**Exercise Description (English):** Assuming tasks have a frontmatter property project indicating the project name, write a Base configuration to show only tasks where project equals "Project A".

**标准答案 (YAML):**

filters:  
  - project = "Project A"views:  
  - type: table    name: "Project A Tasks"

</details>

<details><summary>练习题14：项目完成率公式 - Project completion percentage</summary>

**练习题描述 (Chinese):** 假设项目笔记 frontmatter 中有 doneTasks 和 totalTasks 两个属性，表示完成任务数和总任务数。使用公式计算项目完成率（百分比）。  
**Exercise Description (English):** Assuming a project note has frontmatter properties doneTasks and totalTasks (number of tasks completed and total), use a formula to calculate the project’s completion percentage.

**标准答案 (YAML):**

formulas:  
  completionRate: '(doneTasks / totalTasks * 100).toFixed(1) + "%"'properties:  
  formula.completionRate:    displayName: "Completion %"

</details>

<details><summary>练习题15：计算剩余天数 - Calculate days remaining until due date</summary>

**练习题描述 (Chinese):** 假设任务前置属性 dueDate 是一个日期。使用公式计算从当前日期到截止日期的剩余天数。  
**Exercise Description (English):** Assuming tasks have a frontmatter property dueDate (a date), use a formula to calculate the number of days remaining from today to the due date.

**标准答案 (YAML):**

formulas:  
  daysLeft: '(date(dueDate) - date(now())) / (1000*60*60*24)'properties:  
  formula.daysLeft:    displayName: "Days Remaining"

</details>

<details><summary>练习题16：过滤逾期任务 - Filter overdue tasks</summary>

**练习题描述 (Chinese):** 编写 Base 配置，只显示截止日期早于当前日期（now()）的任务。  
**Exercise Description (English):** Write a Base configuration to show only tasks whose due date is **before** the current date (overdue tasks).

**标准答案 (YAML):**

filters:  
  - date(dueDate) < date(now())views:  
  - type: table    name: "Overdue Tasks"

</details>

<details><summary>练习题17：今天到期的任务 - Tasks due today</summary>

**练习题描述 (Chinese):** 编写 Base 配置，只显示截止日期在今天范围内的任务（从当天零点到明天零点之前）。  
**Exercise Description (English):** Write a Base configuration to show only tasks due **today** (between today’s start and tomorrow).

**标准答案 (YAML):**

filters:  
  and:    - date(dueDate) >= date(now())    - date(dueDate) < date(now()) + "1d"views:  
  - type: table    name: "Due Today"

</details>

<details><summary>练习题18：按标签过滤任务 - Filter tasks by tag</summary>

**练习题描述 (Chinese):** 编写 Base 配置，只显示带有标签 urgent 的任务。  
**Exercise Description (English):** Write a Base configuration to show only tasks that have the tag urgent.

**标准答案 (YAML):**

filters:  
  - file.hasTag("urgent")views:  
  - type: table    name: "Urgent Tasks"

</details>

<details><summary>练习题19：新建任务排序 - Sort newly created tasks first</summary>

**练习题描述 (Chinese):** 编写 Base 配置，在表格中按文件创建时间（file.ctime）降序排序显示任务（最新创建的任务最先显示）。  
**Exercise Description (English):** Write a Base configuration to display tasks sorted by creation time (file.ctime) in descending order (newest tasks first).

**标准答案 (YAML):**

views:  
  - type: table    name: "Newest Tasks"    order:      - -file.ctime

</details>

<details><summary>练习题20：任务状态列显示 - Show task status column</summary>

**练习题描述 (Chinese):** 在表格视图中加入前置属性 status 作为列，并设置显示名称为 "Status"。  
**Exercise Description (English):** Include the frontmatter property status as a column in the table view, and set its display name to "Status".

**标准答案 (YAML):**

properties:  
  status:    displayName: "Status"views:  
  - type: table    name: "Tasks with Status"

</details>

## 项目追踪 (Project Tracking)

<details><summary>练习题21：显示所有项目 - Show all projects</summary>

**练习题描述 (Chinese):** 假设项目笔记 frontmatter 有属性 project（如同任务中的项目引用）。编写 Base 配置，只显示具有 project 属性的笔记（即所有项目）。  
**Exercise Description (English):** Assuming project notes have a frontmatter property project (similar to task’s project reference), write a Base configuration to show only notes that have a project property (i.e., list all projects).

**标准答案 (YAML):**

filters:  
  - projectviews:  
  - type: table    name: "All Projects"

</details>

<details><summary>练习题22：活动项目过滤 - Filter active projects</summary>

**练习题描述 (Chinese):** 假设项目前置属性 status 表示项目状态（如 "active"）。编写 Base 配置，只显示 status = "active" 的项目笔记。  
**Exercise Description (English):** Assuming projects have a frontmatter property status (e.g. "active"), write a Base configuration to show only project notes where status = "active".

**标准答案 (YAML):**

filters:  
  - status = "active"views:  
  - type: table    name: "Active Projects"

</details>

<details><summary>练习题23：项目即将到期 - Upcoming projects (due within one month)</summary>

**练习题描述 (Chinese):** 假设项目前置属性 dueDate 为截止日期。编写 Base 配置，只显示截止日期在未来一个月（1M）内的项目。  
**Exercise Description (English):** Assuming projects have a frontmatter property dueDate, write a Base configuration to show only projects whose due date is within the next month.

**标准答案 (YAML):**

filters:  
  - date(dueDate) <= date(now()) + "1M"  - date(dueDate) > date(now())views:  
  - type: table    name: "Projects Due Soon"

</details>

<details><summary>练习题24：带归档标签的项目 - Filter archived projects</summary>

**练习题描述 (Chinese):** 编写 Base 配置，只显示带标签 archived 的项目笔记。  
**Exercise Description (English):** Write a Base configuration to show only project notes that have the tag archived.

**标准答案 (YAML):**

filters:  
  - file.hasTag("archived")views:  
  - type: table    name: "Archived Projects"

</details>

<details><summary>练习题25：定义项目优先级列 - Define a project priority column</summary>

**练习题描述 (Chinese):** 在 Base 配置的 properties 中，为属性 priority 设置显示名称为 "Priority"。  
**Exercise Description (English):** In the Base configuration under properties, set the display name of the property priority to "Priority".

**标准答案 (YAML):**

properties:  
  priority:    displayName: "Priority"views:  
  - type: table    name: "Project Priorities"

</details>



<details><summary>练习题27：剩余预算计算 - Calculate remaining budget</summary>**练习题描述 (Chinese):** 使用公式计算项目的剩余预算（budget - spent）。  
**Exercise Description (English):** Use a formula to calculate the remaining budget of a project (budget - spent).
**标准答案 (YAML):**
formulas:  
  remainingBudget: 'budget - spent'properties:  
  formula.remainingBudget:    displayName: "Remaining Budget"</details>

<details><summary>练习题28：排序最近更新的项目 - Sort projects by recent updates</summary>

**练习题描述 (Chinese):** 编写 Base 配置，在表格中按文件修改时间（file.mtime）降序排列显示项目，以查找最近更新的项目。  
**Exercise Description (English):** Write a Base configuration to display projects sorted by modification time (file.mtime) in descending order, to find the most recently updated projects.

**标准答案 (YAML):**

views:  
  - type: table    name: "Recent Projects"    order:      - -file.mtime

</details>

<details><summary>练习题29：计算项目进度天数 - Calculate days until project due</summary>

**练习题描述 (Chinese):** 使用公式计算项目从当前日期到截止日期的剩余天数（类似任务的天数计算）。  
**Exercise Description (English):** Use a formula to calculate the number of days remaining from today to the project’s due date (similar to task day count).

**标准答案 (YAML):**

formulas:  
  daysUntilDue: '(date(dueDate) - date(now())) / (1000*60*60*24)'properties:  
  formula.daysUntilDue:    displayName: "Days Until Due"

</details>

<details><summary>练习题30：截止未定的项目 - Projects with no due date</summary>

**练习题描述 (Chinese):** 编写 Base 配置，只显示没有设置 dueDate 的项目（即 dueDate 为空或不存在）。  
**Exercise Description (English):** Write a Base configuration to show only projects that **do not have** a dueDate set (i.e. dueDate is null or missing).

**标准答案 (YAML):**

filters:  
  - "not dueDate"views:  
  - type: table    name: "No Due Date Projects"

</details>

## 日记系统 (Journaling)

<details><summary>练习题31：显示所有日记 - Show all daily notes</summary>

**练习题描述 (Chinese):** 假设所有日记笔记存放在文件夹 Daily 中。编写 Base 配置，只显示文件夹 Daily 下的笔记。  
**Exercise Description (English):** Assuming all daily journal notes are stored in the folder Daily, write a Base configuration to show only notes in the Daily folder.

**标准答案 (YAML):**

filters:  
  - file.inFolder("Daily")views:  
  - type: table    name: "Daily Notes"

</details>

<details><summary>练习题32：过去7天日记 - Last 7 days of daily notes</summary>

**练习题描述 (Chinese):** 编写 Base 配置，只显示今天到 7 天前之间创建的日记笔记。  
**Exercise Description (English):** Write a Base configuration to show only daily notes created between 7 days ago and today.

**标准答案 (YAML):**

filters:  
  - file.ctime > date(now()) - "7d"views:  
  - type: table    name: "Last 7 Days Journals"

</details>

<details><summary>练习题33：按心情过滤日记 - Filter journals by mood</summary>

**练习题描述 (Chinese):** 假设日记笔记 frontmatter 中有属性 mood。编写 Base 配置，只显示 mood = "happy" 的日记。  
**Exercise Description (English):** Assuming journal notes have a frontmatter property mood, write a Base configuration to show only notes where mood = "happy".

**标准答案 (YAML):**

filters:  
  - mood = "happy"views:  
  - type: table    name: "Happy Journals"

</details>

<details><summary>练习题34：日记按日期排序 - Sort journals by date</summary>

**练习题描述 (Chinese):** 假设日记笔记 frontmatter 有属性 date。编写 Base 配置，在表格中按日期升序显示日记。  
**Exercise Description (English):** Assuming journal notes have a frontmatter property date, write a Base configuration to display the journals in a table sorted by date ascending.

**标准答案 (YAML):**

views:  
  - type: table    name: "Journals by Date"    order:      - note.date

</details>

<details><summary>练习题35：为日记生成自动摘要 - Auto-summarize journal entries</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型自动生成每篇日记的摘要，并将摘要存储在公式属性中。展示如何在 Base YAML 配置中集成提示词。  
**Exercise Description (English):** Use the Gemini model to auto-generate a summary for each journal entry, storing it in a formula property. Show how to integrate a prompt within the Base YAML configuration.

**标准答案 (YAML):**

formulas:  
  summary:    prompt: "请用一句话总结以下日记内容：{{note.content}}"  
    model: Geminiproperties:  
  formula.summary:    displayName: "Journal Summary"

</details>

<details><summary>练习题36：按标签过滤日记 - Filter journals by tag</summary>

**练习题描述 (Chinese):** 编写 Base 配置，只显示带有标签 journal 的笔记。  
**Exercise Description (English):** Write a Base configuration to show only notes tagged with journal.

**标准答案 (YAML):**

filters:  
  - file.hasTag("journal")views:  
  - type: table    name: "Journal Notes"

</details>

<details><summary>练习题37：每周日记总数 - Count weekly journals</summary>

**练习题描述 (Chinese):** 使用公式统计过去 7 天内的日记篇数（无法直接在 Base 中统计聚合数目，可通过为符合条件的笔记计为 1 来近似）。  
**Exercise Description (English):** Use a formula to count the number of journal entries in the last 7 days (since Base cannot directly aggregate counts, approximate by assigning 1 to each note that meets the condition).

**标准答案 (YAML):**

formulas:  
  countLastWeek: 'if(date(date) > date(now()) - "7d", 1, 0)'properties:  
  formula.countLastWeek:    displayName: "Last 7 Days Count"

</details>

<details><summary>练习题38：日记关键词过滤 - Keyword filter in journals</summary>

**练习题描述 (Chinese):** 编写 Base 配置，只显示内容中包含关键词 开心 的日记笔记。  
**Exercise Description (English):** Write a Base configuration to show only journal notes whose content includes the keyword 开心 (happy).

**标准答案 (YAML):**

filters:  
  - file.text contains "开心"  
views:  
  - type: table    name: "Journals with 开心"

</details>

<details><summary>练习题39：按周几过滤日记 - Filter journals by weekday</summary>

**练习题描述 (Chinese):** 使用公式过滤出周一（星期一）创建的日记笔记。示例：weekday(note.date) = 1（假设 Monday = 1）。  
**Exercise Description (English):** Use a formula to filter journals that were created on Monday. For example: weekday(note.date) == 1 (assuming Monday = 1).

**标准答案 (YAML):**

filters:  
  - "weekday(note.date) == 1"views:  
  - type: table    name: "Monday Journals"

</details>

<details><summary>练习题40：日记词数统计 - Word count of journals</summary>

**练习题描述 (Chinese):** 使用公式计算日记内容的词数（假设有函数 wordCount(content) 返回词数）。  
**Exercise Description (English):** Use a formula to calculate the word count of journal content (assuming a function wordCount(content) returns the word count).

**标准答案 (YAML):**

formulas:  
  wordCount: 'wordCount(note.content)'properties:  
  formula.wordCount:    displayName: "Word Count"

</details>

## 知识卡 (Knowledge Cards)

<details><summary>练习题41：显示带特定标签的概念 - Show notes with a specific tag</summary>

**练习题描述 (Chinese):** 编写 Base 配置，只显示带标签 concept 的笔记，用于构建术语卡片库。  
**Exercise Description (English):** Write a Base configuration to show only notes tagged with concept (for building a glossary of terms).

**标准答案 (YAML):**

filters:  
  - file.hasTag("concept")views:  
  - type: table    name: "Concepts"

</details>

<details><summary>练习题42：按类别过滤知识卡 - Filter knowledge cards by category</summary>

**练习题描述 (Chinese):** 假设知识卡笔记 frontmatter 有属性 category。编写 Base 配置，只显示 category = "Science" 的笔记。  
**Exercise Description (English):** Assuming knowledge card notes have a frontmatter property category, write a Base configuration to show only notes where category = "Science".

**标准答案 (YAML):**

filters:  
  - category = "Science"views:  
  - type: table    name: "Science Concepts"

</details>

<details><summary>练习题43：概念链接过滤 - Filter by internal link</summary>

**练习题描述 (Chinese):** 编写 Base 配置，只显示链接到名为 QuantumMechanics 笔记的知识卡。  
**Exercise Description (English):** Write a Base configuration to show only knowledge cards that link to the note named QuantumMechanics.

**标准答案 (YAML):**

filters:  
  - file.hasLink("QuantumMechanics")views:  
  - type: table    name: "Linked to QuantumMechanics"

</details>

<details><summary>练习题44：未分类概念 - Uncategorised knowledge cards</summary>

**练习题描述 (Chinese):** 编写 Base 配置，只显示没有设置 category 属性的概念笔记。  
**Exercise Description (English):** Write a Base configuration to show only concept notes that do **not have** a category property set.

**标准答案 (YAML):**

filters:  
  - "not category"views:  
  - type: table    name: "Uncategorized Concepts"

</details>

<details><summary>练习题45：重要概念过滤 - Important knowledge cards</summary>

**练习题描述 (Chinese):** 假设知识卡笔记带有标签 important 来标记重要项。编写 Base 配置，只显示带标签 important 的笔记。  
**Exercise Description (English):** Assuming knowledge cards have a tag important to mark key concepts, write a Base configuration to show only notes tagged important.

**标准答案 (YAML):**

filters:  
  - file.hasTag("important")views:  
  - type: table    name: "Important Concepts"

</details>

<details><summary>练习题46：概念按字母排序 - Sort concepts alphabetically</summary>

**练习题描述 (Chinese):** 编写 Base 配置，按文件名（通常是概念名称）升序对知识卡进行排序显示。  
**Exercise Description (English):** Write a Base configuration to sort the knowledge cards alphabetically by file name in ascending order.

**标准答案 (YAML):**

views:  
  - type: table    name: "Concepts A–Z"    order:      - file.name

</details>

<details><summary>练习题47：定义概念展示顺序 - Define display name for properties</summary>

**练习题描述 (Chinese):** 在 properties 部分，为前置属性 definition 设置显示名为 "Definition"。  
**Exercise Description (English):** In the properties section, set the display name of the frontmatter property definition to "Definition".

**标准答案 (YAML):**

properties:  
  definition:    displayName: "Definition"views:  
  - type: table    name: "Concept Definitions"

</details>

<details><summary>练习题48：概念关联过滤 - Filter by relation property</summary>

**练习题描述 (Chinese):** 假设知识卡笔记有属性 related 列表，列出相关概念。编写 Base 配置，只显示 related 中包含 "Physics" 的笔记。  
**Exercise Description (English):** Assuming concept notes have a list property related for related concepts, write a Base configuration to show only notes where related includes "Physics".

**标准答案 (YAML):**

filters:  
  - related contains "Physics"views:  
  - type: table    name: "Related to Physics"

</details>

<details><summary>练习题49：概念频率公式 - Frequency of usage (formula)</summary>

**练习题描述 (Chinese):** 假设每个概念笔记有属性 frequency 表示出现频率，编写公式将其单位化，例如乘以 1000 进行计算。  
**Exercise Description (English):** Assuming each concept note has a property frequency, write a formula to normalize it (for example, multiply by 1000).

**标准答案 (YAML):**

formulas:  
  freqScaled: 'frequency * 1000'properties:  
  formula.freqScaled:    displayName: "Scaled Frequency"

</details>

<details><summary>练习题50：参考文献列表 - Reference list property</summary>

**练习题描述 (Chinese):** 假设知识卡笔记有一个 references 列表属性。编写 Base 配置，将 references 添加为视图列，并显示名称为 "Refs"。  
**Exercise Description (English):** Assuming concept notes have a list property references, write a Base configuration to include references as a column in the view and display its name as "Refs".

**标准答案 (YAML):**

properties:  
  references:    displayName: "Refs"views:  
  - type: table    name: "Concept References"

</details>

## 学习记录 (Study Notes)

<details><summary>练习题51：显示所有学习笔记 - Show all study session notes</summary>

**练习题描述 (Chinese):** 编写 Base 配置，只显示带有标签 study 的笔记，以追踪学习记录。  
**Exercise Description (English):** Write a Base configuration to show only notes tagged with study (for tracking study sessions).

**标准答案 (YAML):**

filters:  
  - file.hasTag("study")views:  
  - type: table    name: "Study Sessions"

</details>

<details><summary>练习题52：按科目过滤学习记录 - Filter study sessions by subject</summary>

**练习题描述 (Chinese):** 假设学习笔记 frontmatter 有属性 subject（学科）。编写 Base 配置，只显示 subject = "Math" 的学习记录。  
**Exercise Description (English):** Assuming study notes have a frontmatter property subject, write a Base configuration to show only notes where subject = "Math".

**标准答案 (YAML):**

filters:  
  - subject = "Math"views:  
  - type: table    name: "Math Study Sessions"

</details>

<details><summary>练习题53：学习时长阈值过滤 - Filter sessions over 2 hours</summary>

**练习题描述 (Chinese):** 假设学习记录前置属性 timeSpent 以分钟为单位记录时长。编写 Base 配置，只显示 timeSpent > 120 的记录（超过 2 小时）。  
**Exercise Description (English):** Assuming study records have a frontmatter timeSpent in minutes, write a Base configuration to show only notes where timeSpent > 120 (i.e., over 2 hours).

**标准答案 (YAML):**

filters:  
  - timeSpent > 120views:  
  - type: table    name: "Long Study Sessions"

</details>

<details><summary>练习题54：学习记录时间转换 - Time conversion formula</summary>

**练习题描述 (Chinese):** 使用公式将 timeSpent（分钟）转换为小时数，并保留一位小数。  
**Exercise Description (English):** Use a formula to convert timeSpent (in minutes) into hours, keeping one decimal place.

**标准答案 (YAML):**

formulas:  
  hoursSpent: '(timeSpent / 60).toFixed(1)'properties:  
  formula.hoursSpent:    displayName: "Hours Spent"

</details>

<details><summary>练习题55：学习记录排序 - Sort study sessions by date</summary>

**练习题描述 (Chinese):** 假设学习记录前置属性 date 表示学习日期。编写 Base 配置，在表格中按 date 降序显示记录。  
**Exercise Description (English):** Assuming study records have a frontmatter property date, write a Base configuration to display the records in a table sorted by date descending.

**标准答案 (YAML):**

views:  
  - type: table    name: "Study Sessions by Date"    order:      - -note.date

</details>

<details><summary>练习题56：学习效率公式 - Efficiency formula</summary>

**练习题描述 (Chinese):** 假设学习记录有属性 pagesRead（阅读页数）和 timeSpent（分钟），使用公式计算阅读效率（页数/小时）。  
**Exercise Description (English):** Assuming study records have pagesRead and timeSpent (in minutes), use a formula to calculate reading efficiency (pages per hour).

**标准答案 (YAML):**

formulas:  
  pagesPerHour: '(pagesRead / (timeSpent/60)).toFixed(1)'properties:  
  formula.pagesPerHour:    displayName: "Pages/Hour"

</details>

<details><summary>练习题57：下次考试倒计时 - Days until next exam</summary>

**练习题描述 (Chinese):** 假设学习笔记有前置属性 examDate，使用公式计算距离考试日期还有多少天。  
**Exercise Description (English):** Assuming study notes have a frontmatter property examDate, use a formula to calculate how many days remain until that exam date.

**标准答案 (YAML):**

formulas:  
  daysToExam: '(date(examDate) - date(now())) / (1000*60*60*24)'properties:  
  formula.daysToExam:    displayName: "Days to Exam"

</details>

<details><summary>练习题58：学科分布过滤 - Subjects distribution</summary>

**练习题描述 (Chinese):** 编写 Base 配置，显示每个不同的 subject 的学习笔记（按学科分组视图）。提示：多视图实现。  
**Exercise Description (English):** Write a Base configuration to show separate views for each subject’s study notes (grouped by subject). Hint: use multiple views.

**标准答案 (YAML):**

views:  
  - type: table    name: "Math Study"    filters:      - subject = "Math"  - type: table    name: "Science Study"    filters:      - subject = "Science"  - type: table    name: "History Study"    filters:      - subject = "History"

</details>

<details><summary>练习题59：学习记录标签 - Filter by tags in study notes</summary>

**练习题描述 (Chinese):** 编写 Base 配置，只显示带标签 reviewed 的学习笔记（表示已复习）。  
**Exercise Description (English):** Write a Base configuration to show only study notes tagged with reviewed.

**标准答案 (YAML):**

filters:  
  - file.hasTag("reviewed")views:  
  - type: table    name: "Reviewed Sessions"

</details>

<details><summary>练习题60：闪卡模式: 生成问题 - Flashcard Q&A generation</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型，根据学习笔记内容自动生成问答卡片（例如生成 3 个问题）。在公式中集成提示词来调用模型。  
**Exercise Description (English):** Use the Gemini model to automatically generate flashcard Q&A from a study note (e.g. generate 3 questions). Integrate the prompt into a formula in the Base YAML.

**标准答案 (YAML):**

formulas:  
  flashcards:    prompt: "根据以下学习内容生成三个问题和答案：{{note.content}}"  
    model: Geminiproperties:  
  formula.flashcards:    displayName: "Flashcards"

</details>

## 自动摘要 (Auto Summarization)

<details><summary>练习题61：笔记自动摘要 - Auto-summarize note content</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型自动生成任意笔记的摘要。示例：对笔记内容生成一句话总结。  
**Exercise Description (English):** Use the Gemini model to auto-generate a summary of any note content (e.g. a one-sentence summary of the note).

**标准答案 (YAML):**

formulas:  
  summary:    prompt: "Summarize the following note in one sentence: {{note.content}}"    model: Geminiproperties:  
  formula.summary:    displayName: "Auto Summary"

</details>

<details><summary>练习题62：文章关键词提取 - Extract keywords from text</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型从笔记内容中提取关键词，并作为公式属性显示。  
**Exercise Description (English):** Use the Gemini model to extract keywords from the note content and display them as a formula property.

**标准答案 (YAML):**

formulas:  
  keywords:    prompt: "Extract 5 key keywords from the following text: {{note.content}}"    model: Geminiproperties:  
  formula.keywords:    displayName: "Keywords"

</details>

<details><summary>练习题63：生成摘要标题 - Generate summary title</summary>

**练习题描述 (Chinese):** 使用公式和 LLM（Gemini）为笔记内容生成一个简洁的摘要标题。  
**Exercise Description (English):** Use a formula with LLM (Gemini) to generate a concise summary title for the note content.

**标准答案 (YAML):**

formulas:  
  title:    prompt: "Generate a concise title summarizing this note: {{note.content}}"    model: Geminiproperties:  
  formula.title:    displayName: "AI Title"

</details>

<details><summary>练习题64：案例总结 - Case study summarization</summary>

**练习题描述 (Chinese):** 对包含案例分析的笔记内容，使用 Gemini 提示设计生成案例总结。  
**Exercise Description (English):** For a note containing a case study, use Gemini prompt engineering to generate a case summary of the content.

**标准答案 (YAML):**

formulas:  
  caseSummary:    prompt: "Summarize the key points of this case study: {{note.content}}"    model: Geminiproperties:  
  formula.caseSummary:    displayName: "Case Summary"

</details>

<details><summary>练习题65：学术摘要生成 - Academic abstract generation</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型为学术笔记生成一个摘要（Abstract）。  
**Exercise Description (English):** Use the Gemini model to generate an abstract for an academic-style note.

**标准答案 (YAML):**

formulas:  
  abstract:    prompt: "Generate an academic abstract for the following content: {{note.content}}"    model: Geminiproperties:  
  formula.abstract:    displayName: "Abstract"

</details>

<details><summary>练习题66：语言翻译 - Translate note content</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型将笔记内容从中文翻译为英文，或反之。  
**Exercise Description (English):** Use the Gemini model to translate note content from Chinese to English (or vice versa).

**标准答案 (YAML):**

formulas:  
  translation:    prompt: "Translate the following text to English: {{note.content}}"    model: Geminiproperties:  
  formula.translation:    displayName: "Translation"

</details>

<details><summary>练习题67：会议记录摘要 - Meeting notes summary</summary>

**练习题描述 (Chinese):** 假设有会议记录笔记，使用 Gemini 生成会议摘要重点。  
**Exercise Description (English):** Assuming there are meeting notes, use Gemini to generate key highlights summary of the meeting.

**标准答案 (YAML):**

formulas:  
  meetingHighlights:    prompt: "Summarize the key highlights of this meeting: {{note.content}}"    model: Geminiproperties:  
  formula.meetingHighlights:    displayName: "Meeting Highlights"

</details>

<details><summary>练习题68：产品说明总结 - Product description summarization</summary>

**练习题描述 (Chinese):** 对产品说明文档的笔记，使用 Gemini 生成简短的产品概述。  
**Exercise Description (English):** For a note containing a product description document, use Gemini to generate a brief product overview.

**标准答案 (YAML):**

formulas:  
  productOverview:    prompt: "Provide a short overview of the product described: {{note.content}}"    model: Geminiproperties:  
  formula.productOverview:    displayName: "Product Overview"

</details>

<details><summary>练习题69：代码注释自动生成 - Auto-generate code comments</summary>

**练习题描述 (Chinese):** 对包含代码片段的笔记，使用 Gemini 为代码生成注释或解释。  
**Exercise Description (English):** For a note containing code snippets, use Gemini to auto-generate comments or explanations for the code.

**标准答案 (YAML):**

formulas:  
  codeComments:    prompt: "Explain the following code snippet with comments: {{note.content}}"    model: Geminiproperties:  
  formula.codeComments:    displayName: "Code Explanation"

</details>

<details><summary>练习题70：智能摘要 (综合) - Smart summarization (comprehensive)</summary>

**练习题描述 (Chinese):** 结合以上方法，编写一个 Base 配置，对笔记自动生成摘要并存储到公式属性 smartSummary 中。  
**Exercise Description (English):** Combining the above methods, write a Base configuration that auto-generates a summary for each note and stores it in a formula property smartSummary.

**标准答案 (YAML):**

formulas:  
  smartSummary:    prompt: "Please summarize the key points of this note: {{note.content}}"    model: Geminiproperties:  
  formula.smartSummary:    displayName: "Smart Summary"

</details>

## AI 问答 (AI Q&A)

<details><summary>练习题71：基于笔记内容问答 - Q&A from note content</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型对笔记内容进行提问。举例：问 “主要观点是什么？” 并返回答案。  
**Exercise Description (English):** Use the Gemini model to ask questions based on note content. For example: ask "What is the main idea?" and return the answer.

**标准答案 (YAML):**

formulas:  
  llmAnswer:    prompt: "Q: What is the main idea of this note? A: {{note.content}}"    model: Geminiproperties:  
  formula.llmAnswer:    displayName: "AI Answer"

</details>

<details><summary>练习题72：知识检索问答 - Knowledge retrieval Q&A</summary>

**练习题描述 (Chinese):** 编写 Base 配置，通过向 Gemini 提问检索特定信息，例如：“解释文中提到的关键概念。”  
**Exercise Description (English):** Write a Base configuration to retrieve specific information by asking Gemini a question, for example: "Explain the key concept mentioned in the text."

**标准答案 (YAML):**

formulas:  
  keyConcept:    prompt: "Explain the key concept mentioned in the following text: {{note.content}}"    model: Geminiproperties:  
  formula.keyConcept:    displayName: "Key Concept"

</details>

<details><summary>练习题73：创建聊天接口 - Create a chat interface using Base</summary>

**练习题描述 (Chinese):** 设计一个简单的问答交互：在 Base 中定义一个提问字段和一个回答字段，通过 Gemini 生成回答。  
**Exercise Description (English):** Design a simple Q&A interaction: in the Base, define a question field and an answer field, using Gemini to generate the answer.

**标准答案 (YAML):**

formulas:  
  answer:    prompt: "Q: {{note.question}} A:"    model: Geminiproperties:  
  formula.answer:    displayName: "Answer"

</details>

<details><summary>练习题74：事实检验 - Fact checking with LLM</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型对给定陈述进行事实检验，例如：“以下陈述是否正确：{{note.content}}”。  
**Exercise Description (English):** Use the Gemini model to fact-check a given statement, for example: "Is the following statement correct: {{note.content}}?".

**标准答案 (YAML):**

formulas:  
  factCheck:    prompt: "Is the following statement correct? {{note.content}}"    model: Geminiproperties:  
  formula.factCheck:    displayName: "Fact Check"

</details>

<details><summary>练习题75：情感分析 - Sentiment analysis</summary>

**练习题描述 (Chinese):** 使用 Gemini 对笔记内容进行情感分析，生成正面、负面或中性等标签。  
**Exercise Description (English):** Use the Gemini model to perform sentiment analysis on the note content, generating labels like positive, negative, or neutral.

**标准答案 (YAML):**

formulas:  
  sentiment:    prompt: "Analyze the sentiment of this text: {{note.content}}"    model: Geminiproperties:  
  formula.sentiment:    displayName: "Sentiment"

</details>

<details><summary>练习题76：摘要问答 - Generate Q&A from summary</summary>

**练习题描述 (Chinese):** 首先使用 Gemini 生成摘要，然后基于摘要生成一个提问并回答。  
**Exercise Description (English):** First generate a summary using Gemini, then generate a question based on the summary and provide an answer.

**标准答案 (YAML):**

formulas:  
  summary:    prompt: "Summarize: {{note.content}}"    model: Gemini  summaryQA:    prompt: "Based on the summary {{formula.summary}}, ask a question and answer it."    model: Geminiproperties:  
  formula.summary:    displayName: "Summary"  formula.summaryQA:    displayName: "Summary Q&A"

</details>

<details><summary>练习题77：自定义问答模型 - Use a different LLM</summary>

**练习题描述 (Chinese):** 编写 Base 配置，调用 Gemini 以外的自定义模型（例如 Ollama 或 Claude）进行问答。  
**Exercise Description (English):** Write a Base configuration to call a custom model (e.g. Ollama or Claude) other than Gemini for Q&A.

**标准答案 (YAML):**

formulas:  
  customAnswer:    prompt: "Please answer based on this content: {{note.content}}"    model: Ollamaproperties:  
  formula.customAnswer:    displayName: "Custom AI Answer"

</details>

<details><summary>练习题78：问题生成 - Question generation using LLM</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型从笔记内容中生成一个或多个问题，以测试对内容的理解。  
**Exercise Description (English):** Use the Gemini model to generate one or more questions from the note content, to test understanding.

**标准答案 (YAML):**

formulas:  
  questionGen:    prompt: "Generate a question about the following content: {{note.content}}"    model: Geminiproperties:  
  formula.questionGen:    displayName: "Generated Question"

</details>

<details><summary>练习题79：语言风格转换 - Tone conversion with LLM</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型将笔记内容转换为不同的语言风格（例如正式、幽默）。  
**Exercise Description (English):** Use the Gemini model to convert note content into a different tone or style (e.g. formal, humorous).

**标准答案 (YAML):**

formulas:  
  styleConverted:    prompt: "Rewrite the following text in a formal tone: {{note.content}}"    model: Geminiproperties:  
  formula.styleConverted:    displayName: "Formal Tone"

</details>

<details><summary>练习题80：内容扩写 - Content elaboration</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型扩写笔记中的简短段落，使其更详细充实。  
**Exercise Description (English):** Use the Gemini model to elaborate on a short paragraph in the note, making it more detailed.

**标准答案 (YAML):**

formulas:  
  elaborated:    prompt: "Elaborate on the following paragraph: {{note.content}}"    model: Geminiproperties:  
  formula.elaborated:    displayName: "Elaborated Text"

</details>

## 智能提示生成 (Smart Prompt Generation)

<details><summary>练习题81：生成写作提示 - Writing prompt generation</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型为日记写作或创意写作生成一个提示（prompt）。  
**Exercise Description (English):** Use the Gemini model to generate a writing prompt for journaling or creative writing.

**标准答案 (YAML):**

formulas:  
  writingPrompt:    prompt: "Generate a creative writing prompt about the topic: {{note.topic}}"    model: Geminiproperties:  
  formula.writingPrompt:    displayName: "Writing Prompt"

</details>

<details><summary>练习题82：头脑风暴问题 - Brainstorm questions</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型根据给定主题生成多个探讨性问题，例如“AI 在教育中的作用是什么？”。  
**Exercise Description (English):** Use the Gemini model to generate several exploratory questions on a given topic, e.g. “What is the role of AI in education?”.

**标准答案 (YAML):**

formulas:  
  brainstorm:    prompt: "Brainstorm 3 questions about the topic: {{note.topic}}"    model: Geminiproperties:  
  formula.brainstorm:    displayName: "Brainstormed Questions"

</details>

<details><summary>练习题83：翻译提示生成 - Prompt translation</summary>

**练习题描述 (Chinese):** 给出一个英文提示语，使用 Gemini 将其翻译为高效的中文提示语。  
**Exercise Description (English):** Given an English prompt, use the Gemini model to translate it into an effective Chinese prompt.

**标准答案 (YAML):**

formulas:  
  promptCN:    prompt: "Translate the following prompt into Chinese: '{{note.prompt}}'"    model: Geminiproperties:  
  formula.promptCN:    displayName: "Chinese Prompt"

</details>

<details><summary>练习题84：关键词提示扩展 - Expand keywords into a prompt</summary>

**练习题描述 (Chinese):** 输入一组关键词，使用 Gemini 模型生成一个完整的提示语。例如：关键词 ["笔记", "整理", "智能"]。  
**Exercise Description (English):** Given a list of keywords, use the Gemini model to generate a full prompt. E.g.: keywords ["notes", "organization", "AI"].

**标准答案 (YAML):**

formulas:  
  promptFromKeywords:    prompt: "Create a prompt using these keywords: {{note.keywords}}"    model: Geminiproperties:  
  formula.promptFromKeywords:    displayName: "Generated Prompt"

</details>

<details><summary>练习题85：交互式提示改进 - Interactive prompt refinement</summary>

**练习题描述 (Chinese):** 给定初始提示，使用 Gemini 提问模型改进该提示以获得更好回答。  
**Exercise Description (English):** Given an initial prompt, use the Gemini model to refine the prompt for a better response.

**标准答案 (YAML):**

formulas:  
  refinedPrompt:    prompt: "Improve this prompt for clarity: '{{note.prompt}}'"    model: Geminiproperties:  
  formula.refinedPrompt:    displayName: "Refined Prompt"

</details>

<details><summary>练习题86：多语言提示生成 - Multilingual prompts</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型生成多语言提示，例如同时输出英语、中文和西班牙语版本的提示。  
**Exercise Description (English):** Use the Gemini model to generate prompts in multiple languages, e.g. output versions in English, Chinese, and Spanish.

**标准答案 (YAML):**

formulas:  
  multiLingualPrompt:    prompt: "Generate this prompt in English, Chinese, and Spanish: {{note.prompt}}"    model: Geminiproperties:  
  formula.multiLingualPrompt:    displayName: "Multilingual Prompt"

</details>

<details><summary>练习题87：图像生成提示 - Prompt for image generation</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型基于文本描述生成用于图像创作的提示。  
**Exercise Description (English):** Use the Gemini model to generate a prompt for image creation based on a text description.

**标准答案 (YAML):**

formulas:  
  imagePrompt:    prompt: "Create a detailed image generation prompt from the description: {{note.description}}"    model: Geminiproperties:  
  formula.imagePrompt:    displayName: "Image Prompt"

</details>

<details><summary>练习题88：广告文案提示 - Ad copy prompt</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型根据产品信息生成一条广告文案提示。  
**Exercise Description (English):** Use the Gemini model to generate an advertising copy prompt based on product information.

**标准答案 (YAML):**

formulas:  
  adPrompt:    prompt: "Generate an advertising slogan for the product described: {{note.productInfo}}"    model: Geminiproperties:  
  formula.adPrompt:    displayName: "Ad Prompt"

</details>

<details><summary>练习题89：教育问题提示 - Educational question prompt</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型为教师生成问题提示，例如根据课程大纲生成考试问题。  
**Exercise Description (English):** Use the Gemini model to generate question prompts for education, e.g. generating exam questions based on a syllabus.

**标准答案 (YAML):**

formulas:  
  examPrompt:    prompt: "Generate an exam question based on the following syllabus topic: {{note.topic}}"    model: Geminiproperties:  
  formula.examPrompt:    displayName: "Exam Question"

</details>

<details><summary>练习题90：代码解释提示 - Code explanation prompt</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型生成用于解释代码逻辑的提示，如“解释以下 Python 代码的作用”。  
**Exercise Description (English):** Use the Gemini model to generate a prompt for code explanation, such as “Explain what the following Python code does.”

**标准答案 (YAML):**

formulas:  
  codeExplainPrompt:    prompt: "Explain what the following Python code does: {{note.codeSnippet}}"    model: Geminiproperties:  
  formula.codeExplainPrompt:    displayName: "Code Explanation Prompt"

</details>

<details><summary>练习题91：科学研究提示 - Scientific research prompt</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型为科学研究生成研究问题提示，例如基于关键词生成研究问题。  
**Exercise Description (English):** Use the Gemini model to generate research question prompts for scientific studies, e.g. generate research questions based on keywords.

**标准答案 (YAML):**

formulas:  
  researchPrompt:    prompt: "Generate a research question from the following keywords: {{note.keywords}}"    model: Geminiproperties:  
  formula.researchPrompt:    displayName: "Research Question"

</details>

<details><summary>练习题92：市场分析提示 - Market analysis prompt</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型生成与市场分析相关的提示，例如为数据集生成分析方向。  
**Exercise Description (English):** Use the Gemini model to generate prompts related to market analysis, for example suggesting analytical approaches for a given dataset.

**标准答案 (YAML):**

formulas:  
  marketPrompt:    prompt: "Suggest an approach to analyze the market data: {{note.dataset}}"    model: Geminiproperties:  
  formula.marketPrompt:    displayName: "Market Analysis Prompt"

</details>

<details><summary>练习题93：健康建议提示 - Health advice prompt</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型根据健康信息生成健康建议提示。  
**Exercise Description (English):** Use the Gemini model to generate health advice prompts based on health information.

**标准答案 (YAML):**

formulas:  
  healthPrompt:    prompt: "Based on the following health information, generate advice: {{note.healthData}}"    model: Geminiproperties:  
  formula.healthPrompt:    displayName: "Health Advice"

</details>

<details><summary>练习题94：旅行计划提示 - Travel itinerary prompt</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型根据目的地和日期生成旅行计划提示。  
**Exercise Description (English):** Use the Gemini model to generate a travel itinerary prompt based on destination and dates.

**标准答案 (YAML):**

formulas:  
  travelPrompt:    prompt: "Create a travel itinerary for traveling to {{note.destination}} on {{note.dates}}"    model: Geminiproperties:  
  formula.travelPrompt:    displayName: "Travel Itinerary Prompt"

</details>

<details><summary>练习题95：购买决策提示 - Purchase decision prompt</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型根据预算和需求生成购买建议提示。  
**Exercise Description (English):** Use the Gemini model to generate purchase recommendation prompts based on budget and needs.

**标准答案 (YAML):**

formulas:  
  buyPrompt:    prompt: "Suggest a product to buy given budget {{note.budget}} and needs {{note.needs}}"    model: Geminiproperties:  
  formula.buyPrompt:    displayName: "Purchase Suggestion"

</details>

<details><summary>练习题96：心理测试提示 - Psychology quiz prompt</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型生成一个心理测试问题提示，如性格测试题目。  
**Exercise Description (English):** Use the Gemini model to generate a psychology quiz prompt, such as a personality test question.

**标准答案 (YAML):**

formulas:  
  psychPrompt:    prompt: "Generate a personality test question."    model: Geminiproperties:  
  formula.psychPrompt:    displayName: "Personality Test Prompt"

</details>

<details><summary>练习题97：营养计划提示 - Nutrition plan prompt</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型根据个人资料生成营养计划提示。  
**Exercise Description (English):** Use the Gemini model to generate a nutrition plan prompt based on personal profile.

**标准答案 (YAML):**

formulas:  
  nutritionPrompt:    prompt: "Create a nutrition plan for a 30-year-old male, 75kg, who wants to build muscle."    model: Geminiproperties:  
  formula.nutritionPrompt:    displayName: "Nutrition Plan Prompt"

</details>

<details><summary>练习题98：小说情节提示 - Story plot prompt</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型生成小说写作的情节或故事提示。  
**Exercise Description (English):** Use the Gemini model to generate story plot prompts for novel writing.

**标准答案 (YAML):**

formulas:  
  storyPrompt:    prompt: "Generate a plot idea for a mystery novel set in a haunted house."    model: Geminiproperties:  
  formula.storyPrompt:    displayName: "Story Plot Prompt"

</details>

<details><summary>练习题99：艺术创意提示 - Art creation prompt</summary>

**练习题描述 (Chinese):** 使用 Gemini 模型生成艺术创作的灵感提示，例如绘画主题。  
**Exercise Description (English):** Use the Gemini model to generate art creation inspiration prompts, e.g. a painting theme.

**标准答案 (YAML):**

formulas:  
  artPrompt:    prompt: "Suggest an artistic theme to paint involving nature and technology."    model: Geminiproperties:  
  formula.artPrompt:    displayName: "Art Inspiration Prompt"

</details>

<details><summary>练习题100：全局示例：多功能 Base 配置 - Global example: a multifunctional Base</summary>

**练习题描述 (Chinese):** 综合运用前述各种功能，创建一个 Base 包含多个视图和公式。例如，一个 DailyTracker.base 同时展示日记、任务和摘要。  
**Exercise Description (English):** As a comprehensive example, create a Base with multiple views and formulas. For instance, a DailyTracker.base that shows daily notes, tasks, and an AI-generated summary.

**标准答案 (YAML):**

filters:  
  - file.inFolder("Daily")views:  
  - type: table    name: "Today's Notes"    filters:      - file.inFolder("Daily")  - type: table    name: "Today's Tasks"    filters:      - status != "done"      - date(dueDate) >= date(now())  - type: table    name: "Daily Summary"formulas:  
  summary:    prompt: "Summarize today's highlights from: {{note.content}}"    model: Geminiproperties:  
  formula.summary:    displayName: "Today's Summary"

</details>

**参考资料：** 上述练习基于 Obsidian Bases 核心插件的官方文档和示例[_[1]_](https://obsidian.md/changelog/2025-05-21-desktop-v1.9.0/#:~:text=Introducing%20Bases%2C%20a%20new%20core,plans%2C%20reading%20lists%2C%20and%20more)[_[2]_](https://help.obsidian.md/bases/syntax#:~:text=SQL%20or%20Dataview.%20The%20,a%20recursively%20defined%20filter%20object)，以及社区博客教程[_[5]_](https://obsidian.rocks/getting-started-with-obsidian-bases/#:~:text=Bases%20is%20a%20brilliant%20new,Obsidian%20that%20we%E2%80%99ve%20ever%20seen)。练习涵盖了 Filters、Formulas、Properties、Views 等功能[_[6]_](https://help.obsidian.md/bases/syntax#:~:text=the%20column%20headers.%20,formula.formatted_price)[_[7]_](https://help.obsidian.md/bases/syntax#:~:text=formula%20properties%20that%20can%20be,or)，并示范了如何通过 YAML 配置使用 Gemini 模型生成摘要和提示。

---

[_[1]_](https://obsidian.md/changelog/2025-05-21-desktop-v1.9.0/#:~:text=Introducing%20Bases%2C%20a%20new%20core,plans%2C%20reading%20lists%2C%20and%20more) [_[4]_](https://obsidian.md/changelog/2025-05-21-desktop-v1.9.0/#:~:text=All%20the%20data%20in%20a,file%20format%20and%20syntax) Obsidian 1.9.0 Desktop (Early access) - Obsidian

[_https://obsidian.md/changelog/2025-05-21-desktop-v1.9.0/_](https://obsidian.md/changelog/2025-05-21-desktop-v1.9.0/)

[_[2]_](https://help.obsidian.md/bases/syntax#:~:text=SQL%20or%20Dataview.%20The%20,a%20recursively%20defined%20filter%20object) [_[6]_](https://help.obsidian.md/bases/syntax#:~:text=the%20column%20headers.%20,formula.formatted_price) [_[7]_](https://help.obsidian.md/bases/syntax#:~:text=formula%20properties%20that%20can%20be,or) Bases syntax - Obsidian Help

[_https://help.obsidian.md/bases/syntax_](https://help.obsidian.md/bases/syntax)

[_[3]_](https://obsidian.rocks/getting-started-with-obsidian-bases/#:~:text=Bases%20are%20designed%20to%20be,notes%20from%20meh%20to%20amazing) [_[5]_](https://obsidian.rocks/getting-started-with-obsidian-bases/#:~:text=Bases%20is%20a%20brilliant%20new,Obsidian%20that%20we%E2%80%99ve%20ever%20seen) Getting Started with Obsidian Bases - Obsidian Rocks

[_https://obsidian.rocks/getting-started-with-obsidian-bases/_](https://obsidian.rocks/getting-started-with-obsidian-bases/)