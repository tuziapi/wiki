# ⚙️ Node.js 调用GPT-4o

# 使用NodeJS接入gpt-4o生图

## 环境准备

### 克隆项目启动模版

* 模版包含基础项目配置: Node + TS + ESM

```shell
git clone git@github.com:KelvinQiu802/ts-node-esm-template.git
```

### 安装依赖

* **openai**: 通过OpenAI的SDK请求API
* **dotenv**: 加载环境变量

```shell
pnpm install
pnpm add openai dotenv
```

## 配置环境变量

在项目的`.env`中配置环境变量

```text
OPENAI_API_KEY=你的API密钥
OPENAI_BASE_URL=https://api.tu-zi.com/v1
OPENAI_MODEL=gpt-4o-all
```

## 编写脚本

```javascript
import 'dotenv/config';

import { OpenAI } from 'openai';
import { image2Base64 } from './utils';

const openai = new OpenAI({
    apiKey: process.env.OPENAI_API_KEY,
    baseURL: process.env.OPENAI_BASE_URL,
});

const imagePath = './assets/photo.jpg'; // 图片的路径
const imageType = imagePath.split('.').pop();

async function main() {
    try {
        console.log("开始请求")
        const stream = await openai.chat.completions.create({
            model: process.env.OPENAI_MODEL as string,
            messages: [{
                role: 'user', content: [
                    {
                        type: "image_url",
                        image_url: {
                            url: `data:image/${imageType};base64,${image2Base64(imagePath)}`
                        }
                    },
                    {
                        type: "text",
                        text: `把图片转换成文艺复兴时期的油画风格` // 提示词
                    },
                ]
            }],
            stream: true,
        });

        for await (const chunk of stream) {
            const content = chunk.choices[0]?.delta?.content || '';
            if (content) {
                process.stdout.write(content); // 输出内容
            }
        }
        process.stdout.write('\n');
    } catch (error) {
        console.error('Error processing image:', error);
        process.exit(1);
    }
}

main();
```

## image2Base64工具函数

```javascript
import fs from 'fs';

export function image2Base64(imagePath: string) {
    const image = fs.readFileSync(imagePath);
    return image.toString('base64');
}
```