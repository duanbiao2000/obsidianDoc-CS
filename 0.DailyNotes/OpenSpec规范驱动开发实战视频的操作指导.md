为开发者提炼自OpenSpec规范驱动开发实战视频的操作指导，具体内容如下：

**OpenSpec开发流程五大阶段**（适用于AI辅助开发）：

1. **创建提议（Proposal Creation）**
    
    - 明确要实现的具体功能（如为iOS APP新增自定义时长），编写规范需求（spec/proposal），可借助如Claude Code等AI助手辅助完善需求说明。
        
2. **审核规范（Review Specification）**
    
    - 对proposal（需求规范）和tasks（任务拆解）文件进行严格审核，确保需求、边界和验收标准均明确、无歧义。
        
3. **AI自动编码（AI-Driven Coding）**
    
    - 利用AI编码助手（Claude Code、Cursor、Codex等）根据规范自动生成代码，实现功能模块开发。关键在于AI只基于审核通过的规范做输出，保证代码可控可预测。
        
4. **功能测试（Feature Testing）**
    
    - 按规范、用例对AI生成的代码进行实际功能验证，及时反馈问题、调整规范迭代。
        
5. **归档文档（Documentation & Merge）**
    
    - 合并变更，归档开发文档，形成完整审计轨迹，便于团队协作与历史追溯。
        

**实用操作技巧总结**：

- 初次环境准备需安装Node.js及OpenSpec框架（终端操作）。
    
- 全流程工具无关，能与多种主流AI助手无缝对接，适用于项目迭代与团队协作。
    
- “需求澄清”与AI助手交互优化，可多轮对话精准锁定开发意图。
    
- 每一步形成标准化文档，可自动归档与版本管理。
    
- 通过完善规范，杜绝AI“乱写代码”现象，实现100%可控与高质量输出。
    

**额外资源：**

- 视频附完整配置与实操教程，相关项目与文档笔记见：
    
    - 笔记：[https://www.aivi.fyi/llms/introduce-OpenSpec](https://www.aivi.fyi/llms/introduce-OpenSpec)
        
    - 开源项目：[https://github.com/win4r/AISuperDomain](https://github.com/win4r/AISuperDomain)
        

以上流程与方法论适用于所有希望强化AI赋能、规范化开发实践和提升项目可控性的开发者环境。youtube+2​

1. [https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbjB4cmZKT1JPc3U4dzhuM0ZEdlFqaV9uYmRld3xBQ3Jtc0tsQ1pfazhPMXJWd0xlU2JjYjhXYVRYMld4V2hQVHZtdGNWRDFpWEkwMVNZajFNZFBlVWZCQ1RnaWgzRUxwZTBibEZCZkxXQ3FGOVNUcmdTRlBPZEFIZjd4V2RzZnExblRabTJRc2xmZ2kwQnZzTnNsYw&q=https%3A%2F%2Fwww.aivi.fyi%2Fllms%2Fintroduce-OpenSpec&v=ANjiJQQIBo0](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbjB4cmZKT1JPc3U4dzhuM0ZEdlFqaV9uYmRld3xBQ3Jtc0tsQ1pfazhPMXJWd0xlU2JjYjhXYVRYMld4V2hQVHZtdGNWRDFpWEkwMVNZajFNZFBlVWZCQ1RnaWgzRUxwZTBibEZCZkxXQ3FGOVNUcmdTRlBPZEFIZjd4V2RzZnExblRabTJRc2xmZ2kwQnZzTnNsYw&q=https%3A%2F%2Fwww.aivi.fyi%2Fllms%2Fintroduce-OpenSpec&v=ANjiJQQIBo0)
2. [https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqblY5Nl80d2g0S013N0xnQTRpcVEwS2I3LVpTQXxBQ3Jtc0trZGFNY1lhQ1FtQnE3RXlwRGZ0Y2cxYlpmVDlwcUVFVHdUZFpnWFQtZll6MmE3OFpPcUNHLUM3ZG96Vm92Z3loaHo2SmhmMWRxQ3hoNm5uQUFGT3pFVG45MnJHX1RjdUtadTFGRnh3Rm1EdjFueTBmbw&q=https%3A%2F%2Fgithub.com%2Fwin4r%2FAISuperDomain&v=ANjiJQQIBo0](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqblY5Nl80d2g0S013N0xnQTRpcVEwS2I3LVpTQXxBQ3Jtc0trZGFNY1lhQ1FtQnE3RXlwRGZ0Y2cxYlpmVDlwcUVFVHdUZFpnWFQtZll6MmE3OFpPcUNHLUM3ZG96Vm92Z3loaHo2SmhmMWRxQ3hoNm5uQUFGT3pFVG45MnJHX1RjdUtadTFGRnh3Rm1EdjFueTBmbw&q=https%3A%2F%2Fgithub.com%2Fwin4r%2FAISuperDomain&v=ANjiJQQIBo0)
3. [https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbHh4MXpFY0g3ODZzSTVaSlF1Mlh6MllMTE8yQXxBQ3Jtc0tuZlZrQW9UNFhoX0NkdWRfdDBqaDloYU1SMXhRU096VUhzeE5jdmVqeGhmbHR6NGY5M2R5aENtV2x0UmFiSTNRX3Bqa0k3YTVpSlBJcF96bUM1VEF6S05zVWxUQl9tQV9LMnNqLUVNbk8tVWs1NUdyYw&q=https%3A%2F%2Fko-fi.com%2Faila&v=ANjiJQQIBo0](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbHh4MXpFY0g3ODZzSTVaSlF1Mlh6MllMTE8yQXxBQ3Jtc0tuZlZrQW9UNFhoX0NkdWRfdDBqaDloYU1SMXhRU096VUhzeE5jdmVqeGhmbHR6NGY5M2R5aENtV2x0UmFiSTNRX3Bqa0k3YTVpSlBJcF96bUM1VEF6S05zVWxUQl9tQV9LMnNqLUVNbk8tVWs1NUdyYw&q=https%3A%2F%2Fko-fi.com%2Faila&v=ANjiJQQIBo0)
4. [https://www.youtube.com/watch?v=ANjiJQQIBo0](https://www.youtube.com/watch?v=ANjiJQQIBo0)
5. [https://www.youtube.com/feed/subscriptions](https://www.youtube.com/feed/subscriptions)