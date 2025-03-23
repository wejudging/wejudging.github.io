
# 大语言模型（LLM）研究与实验指南

---

## 实验设置导语

在撰写大模型（LLM）相关论文时，实验设计是验证创新点、评估方法有效性和支撑论文主张的核心部分。良好的实验设置不仅能清晰展示模型能力，也能使论文更具说服力。因此，设计科学、合理、可复现的实验流程，是撰写高水平论文不可或缺的一环。

---

## 一、Prompt实验设计与案例

### 1.1 常见 Prompt 方法

- **Zero-shot Prompting**
- **Few-shot Prompting**
- **Chain-of-Thought Prompting**
- **Instruction Prompting**

### 1.2 Prompt 案例结果对比

| 方法 | 正确率 | 平均响应时长 | 人工评分（逻辑性） |
|------|--------|----------------|---------------------|
| Zero-shot Prompt | 42.1% | 1.2s | 3.0 / 5 |
| Few-shot Prompt（2例） | 58.7% | 1.4s | 3.8 / 5 |
| Chain-of-Thought Prompt | 70.3% | 1.7s | 4.5 / 5 |

---

## 二、主流大模型比较与选择建议


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

