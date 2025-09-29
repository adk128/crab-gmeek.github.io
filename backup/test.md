## 提示词要求 
- **推理模型**

需要明确任务目标和需求

- **通用模型**

需显式引导步骤，否则可能跳过关键步骤。例如要求分步思考，提供示例。

**错误示例：**给我写段生日祝福。

*不够具体*

**正确示例：**我是线下班主任，教大模型，帮我给喜欢动漫的学生写一段生日祝福信息，希望鼓励他学大模型，别说教。

## 提示词规范

<img width="855" height="694" alt="Image" src="https://github.com/user-attachments/assets/8a5fa31e-235a-42a3-bcc1-ca7e62aa57f6" />

**ICIO示例：结构化提示词**

<img width="545" height="498" alt="Image" src="https://github.com/user-attachments/assets/c20b813a-730c-4e01-b4dd-d26c9e7ed26c" />

**如何与AI沟通**

<img width="559" height="599" alt="Image" src="https://github.com/user-attachments/assets/691518b3-b334-42a7-9428-d7c51f96e623" />

**不指定思考步骤**

在R1模型中，不使用思维链CoT（Chain of Thoughts），即把中间过程都写出来，这样对R1可能会起反作用。

## 提示词示例

**示例：做一个抬杠高手**

结构化提示词

<img width="712" height="550" alt="Image" src="https://github.com/user-attachments/assets/c17fb380-cee9-49a7-ad17-df93a9bc12f6" />

结果：

<img width="928" height="445" alt="Image" src="https://github.com/user-attachments/assets/7e9ebd3c-32c6-4439-a8fa-74acd80a2f4e" />

### **示例：markdown生成思维导图**

1. deepseek提示词：把pdf整理成思维导图，以markdown形式输入给我。
2. xmind导入markdown

### **示例：生成ppt**

1. deepseek提示词

<img width="1064" height="336" alt="Image" src="https://github.com/user-attachments/assets/c2f0366c-df99-4103-9e62-5156c3142d10" />

2. 把markdown输入给kimi的ppt助手

### **示例：生成网站**

1. deepseek提示词

<img width="851" height="93" alt="Image" src="https://github.com/user-attachments/assets/75c6e3a1-7186-4e45-abf8-d8c45766fd4a" />

2. 把提示词复制aicode网站，生成网页代码

   - cursor（付费）

   - trae

     - 国外版本：https://www.trae.ai/

     - 国内版本：https://www.trae.com.cn/

   - bolt.new（直接渲染）