## API接口
https://one-api.weijiajin.com

## Chat
https://chat.weijiajin.com

https://ai.weijiajin.com


## OpenAI文档介绍

英文仓库
https://github.com/openai/openai-cookbook

中文文档翻译
https://openai.xiniushu.com

## LinuxDO论坛

https://linux.do

## 中文大语言模型

https://github.com/HqWu-HITCS/Awesome-Chinese-LLM

整理开源的中文大语言模型，以规模较小、可私有化部署、训练成本较低的模型为主，包括底座模型，垂直领域微调及应用，数据集与教程等。


## 论文怎么找创新点

大模型LLM+推荐系统找创新点
https://zhuanlan.zhihu.com/p/673058941


## 一、Prompt实验设计与案例

Prompt（提示词）设计是大语言模型使用中的关键环节，不同的提示方式会显著影响模型输出的效果。以下列举几种主流的 Prompt 方法，并结合实际案例进行说明。

#### 🔹 Zero-shot Prompting（零样本提示）
#### 🔹 Chain-of-Thought Prompting（思维链提示）
#### 🔹 Few-shot Prompting（少样本提示）
#### 🔹 Instruction Prompting（指令提示）

## 二、主流大模型比较与选择建议

当前市面上主流的大语言模型（LLMs）各具优势，适用场景也存在一定差异。以下从模型能力、开放性、价格策略、上下文长度、接口易用性等角度对比主流模型，并在最后给出选择建议。

### 1. 模型总览表

| 模型名称    | 提供方         | 代表版本     | 上下文长度 | 多轮对话能力 | 代码能力 | 中文能力 | 价格策略      | 接口开放性     |
|-------------|----------------|--------------|------------|---------------|-----------|-----------|----------------|----------------|
| **DeepSeek R1** | DeepSeek AI     | R1            | 128K        | ⭐⭐⭐⭐          | ⭐⭐⭐⭐       | ⭐⭐⭐⭐       | 免费/按量        | API 提供        |
| **ChatGPT**    | OpenAI          | GPT-4-turbo   | 128K        | ⭐⭐⭐⭐⭐         | ⭐⭐⭐⭐⭐      | ⭐⭐⭐⭐       | GPT-3.5 免费；GPT-4 收费 | API、插件、工具链 |
| **Claude**     | Anthropic       | Claude 3 Opus | 200K+       | ⭐⭐⭐⭐⭐         | ⭐⭐⭐⭐       | ⭐⭐⭐⭐       | 免费/订阅        | API 提供（有限） |
| **Grok**       | xAI (Elon Musk) | Grok-1.5      | ~32K?       | ⭐⭐⭐           | ⭐⭐⭐        | ⭐⭐         | X平台内订阅      | 暂无开放API     |
| **LLaMA**      | Meta            | LLaMA 2 / 3   | 4K–32K+     | ⭐⭐⭐⭐          | ⭐⭐⭐⭐       | ⭐⭐⭐        | 开源免费        | 需自行部署       |

> 说明：星级为相对评分，5星为最优。上下文长度单位为 tokens。

---

### 2. 各模型简要分析

#### 🔹 DeepSeek R1（国产亮眼新星）
- **亮点**：强大的数学和代码能力，推理能力优于 GPT-4-turbo 在部分中文任务上。
- **适用场景**：中文问答、代码生成、教育类应用。
- **特点**：支持128K上下文，响应速度快，API稳定。

#### 🔹 ChatGPT（生态最完整）
- **亮点**：强大的工具调用能力（函数调用、插件、浏览器、代码解释器等）。
- **适用场景**：通用对话、复杂任务编排、Agent系统。
- **特点**：GPT-4-turbo 价格降低且更高效；生态完善，开发者友好。

#### 🔹 Claude（长文本之王）
- **亮点**：超长上下文（超过200K token），总结与分析长文档效果优秀。
- **适用场景**：法律文档处理、长篇文本总结、写作辅助。
- **特点**：语言风格温和，安全性高，适合企业级部署。

#### 🔹 Grok（社交场景专用）
- **亮点**：整合 Twitter（现为 X）数据，适合社交语境内容生成。
- **适用场景**：社交媒体内容生成、趣味型问答。
- **特点**：非通用 LLM，X 平台集成使用，API 暂未开放。

#### 🔹 LLaMA（开源部署首选）
- **亮点**：完全开源，支持本地或私有云部署，数据隐私友好。
- **适用场景**：科研、自定义训练、企业内网模型部署。
- **特点**：需具备一定工程能力，社区活跃，适合技术团队。

---

### 3. 模型选择建议

| 使用场景         | 推荐模型         | 理由                                 |
|------------------|------------------|--------------------------------------|
| 通用对话助手       | ChatGPT (GPT-4)   | 能力全面，支持多模态和函数调用           |
| 长文档处理与总结    | Claude 3 Opus     | 上下文最长，逻辑梳理强                   |
| 中文问答或数学任务  | DeepSeek R1       | 本土化训练优良，中文表现稳定              |
| 私有化部署需求     | LLaMA             | 开源可控，自定义性强                     |
| 社交媒体创作       | Grok              | 结合 X 平台语境，内容风格轻松幽默         |


---

## 三、输出规范化与结构化处理

### 3.1 正则提取示例

```python
import re
output = "答案是：42"
match = re.search(r"答案是[:：\s]*(\d+)", output)
print(match.group(1) if match else "未提取")
```

### 3.2 JSON结构化与数据库写入示意

```python
import json, sqlite3
llm_output = '{"公司":"小米公司","时间":"2024年2月","地点":"上海","事件":"发布电动汽车","人物":"雷军"}'
info = json.loads(llm_output)
conn = sqlite3.connect("events.db")
c = conn.cursor()
c.execute("CREATE TABLE IF NOT EXISTS events (company TEXT, time TEXT, location TEXT, event TEXT, person TEXT)")
c.execute("INSERT INTO events VALUES (?, ?, ?, ?, ?)", (
    info["公司"], info["时间"], info["地点"], info["事件"], info["人物"]
))
conn.commit()
conn.close()
```

---

## 四、大模型 API 调用示例

### 4.1 OpenAI GPT 接口

```python
import openai
openai.api_key = "your-api-key"
response = openai.ChatCompletion.create(
  model="gpt-3.5-turbo",
  messages=[{"role": "user", "content": "用一句话总结：苹果今天发布新品"}]
)
print(response["choices"][0]["message"]["content"])
```

---

