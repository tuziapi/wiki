# 💻 Continue 配置

## Continue配置

* **简介**：Continue 是一款开源的 AI 代码助手插件，通过接入多种大语言模型（如 OpenAI、DeepSeek、Claude 等）来实现代码补全、生成、优化、错误修复等功能。它提供了一个聊天界面，开发者可以通过自然语言与 AI 交互，帮助理解代码逻辑、解决问题或生成代码片段。
* **主要功能**：
  * **智能代码补全**：基于当前代码上下文生成相关代码片段，支持单行和整段代码的补全。
  * **自然语言到代码**：通过自然语言描述功能需求，直接生成相应的代码实现。
  * **代码解释与优化建议**：解释代码的功能和逻辑，提供优化建议，使代码更高效、易维护。
  * **多语言支持**：支持多种编程语言，包括 JavaScript、TypeScript、Python 和 Java 等。
  * **简易配置与集成**：安装和配置过程简单，与现有开发环境无缝集成。789
* **优势**：
  * **多模型支持**：支持多种 AI 模型，用户可以根据需要选择合适的模型。
  * **自然语言交互**：通过聊天界面与 AI 交互，操作直观方便。
  * **持续学习与改进**：通过用户反馈和使用习惯不断学习和改进，生成的代码质量会随着使用时间的增加而提升。
* 安装
  * https://github.com/continuedev/continue
  * [Continue- Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=Continue.continue)
  * 在vscode中安装
    * ![pasted_image_20250225234322.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/continue/pasted_image_20250225234322.png)
* 配置
  * 安装之后在vscode边栏出现对应的扩展图标 点击之后打开continue之后点击设计按钮
    * ![pasted_image_20250225234520.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/continue/pasted_image_20250225234520.png)
  * 打开设置页面之后点开对应的配置文件进行配置
    * 注意 不要使用内置的ui界面进行配置 无法接入自定义api进行配置 只能在在文件里面进行配置
    * 参考具体的配置如右边所示 对应的apiKey为 兔子api中的key 对应的apiBase为兔子api的接入点 模型为 https://api.tu-zi.com/pricing 中选择的 目前主要使用claude-3-7-sonnet-20250219 注意 目前不支持思考模型 不要接入带有think的模型
    * ![pasted_image_20250225234710.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/continue/pasted_image_20250225234710.png)
* 而后返回插件主要页面即可 选择模型使用
  * ![pasted_image_20250225234950.png](https://tuziai.oss-cn-shenzhen.aliyuncs.com/wiki/continue/pasted_image_20250225234950.png)