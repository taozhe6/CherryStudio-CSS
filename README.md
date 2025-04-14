# `CherryStudio-Claude CSS`
这是借鉴`Claude Web`样式Cherry Studio主题。主要特点包括：
- 双主题支持：模仿Claude的浅色和深色模式
- 优化的排版：使用"Noto Serif SC"作为主字体，提供舒适的阅读体验
- 代码显示增强：使用"JetBrains Mono"等宽字体优化代码块显示

## 效果演示：
### 浅色模式
![浅色模式](/LightMode.png)

---

### 深色模式
![深色模式](/DarkMode.png)

## 使用方式
下载或复制以下代码到CherryStudio里即可：
```css
/*** CherryStudio-Claude CSS ***/
:root {
    --chat-background-white: #F5F4ED; /* 初始值，会被主题覆盖 */
    --color-border: rgba(120,120,120,0.08) !important; /* 初始值，会被主题覆盖 */
}

/* 全局样式设置 - 设置基本字体、行高、字母间距和字体粗细 */
* {
    font-family: "Noto Serif SC", system-ui !important;
    line-height: 1.7 !important;
    letter-spacing: 0.018em !important;
    font-weight: 500;
}

/* 设置代码字体为 JetBrains Mono - 提高选择器优先级 */
code, pre, .code,
.bubble pre code,
.message-content pre,
.message-content code,
.ant-collapse-content-box code,
.prose code,
.prose pre,
.code-block,
.hljs,
pre code,
div pre code,
div.code,
pre.code-block,
.markdown-body code,
.markdown-body pre {
    font-family: "JetBrains Mono", monospace !important; /* 确保最高优先级 */
    font-weight: normal !important;
    font-size: 1.0em !important;
    line-height: 1.5 !important; /* 设置代码的行高更适合阅读 */
}

/* 确保代码块内的文本使用正确字体 */
code *{
    font-family: "JetBrains Mono", monospace !important;
}

/* 通用组件样式 */
/* Claude 样式的消息容器 */
.message-content-container {
    background: var(--chat-background-white) !important; /* 默认使用浅色主题变量 */
    margin: 8px 0 !important;
    padding: 10px 10px 0 10px !important;
    transition: transform 0.22s cubic-bezier(0.34,1.56,0.64,1) !important;
    border: none !important;
    box-shadow: none !important;
}

.message-user .message-content-container {
    background: var(--chat-background-user, #F0EEE6) !important; /* 默认使用浅色主题用户消息背景色 */
    box-shadow: 0 8px 32px -12px rgba(0,0,0,0.03) !important;
    border: 1px solid var(--color-border) !important;
}

#inputbar {
    margin: 0px 10px 10px 10px;
    background: #FFFFFF !important; /* 默认纯白色输入框背景 */
    border: 2px solid var(--color-border) !important;
    border-radius: 20px !important;
    box-shadow: 0 8px 32px -12px rgba(0,0,0,0.03) !important;
    backdrop-filter: blur(8px) !important;
}


/* 浅色模式颜色定义 - 采用Claude的色调 */
body[theme-mode='light'] {
    --color-primary: #C96442;
    --color-primary-soft: rgba(201, 100, 66, 0.6);
    --color-primary-mute: rgba(201, 100, 66, 0.2);

    --color-background: #F5F4ED;       /* 侧边栏背景色保持不变 */
    --color-background-mute: #F0EFEB;  /* 略深的背景色 */
    --color-background-soft: #F0EEE6;  /* 中浅色背景 */

    --navbar-background:  #F5F4ED;      /* 导航栏背景色 */
    --chat-background: #FAF9F5;        /* 新增：聊天区域总体背景 */
    --chat-background-white: #FAF9F5;  /* 修改为与cherryStudio一致的值 */
    --chat-background-user: #F0EEE6;   /* 用户消息气泡背景色 */
    --chat-background-assistant: #FAF9F5; /* AI助手消息气泡背景色修改 */

    --color-text: #262624;             /* 文字颜色（深色） */
    --color-border: rgba(35, 35, 45, 0.12); /* 边框颜色 */
}

/* 浅色模式下的特定样式 (如果需要可以添加) */
/* 例如: body[theme-mode='light'] .some-element { ... } */


/* 深色模式颜色定义 - 融合Claude深色主题 */
body[theme-mode='dark'] {
    --color-primary: #C96442;     /* 保持主色调一致 */
    --color-primary-soft: rgba(201, 100, 66, 0.6);
    --color-primary-mute: rgba(201, 100, 66, 0.2);

    --color-background: #1F1E1D;       /* Claude深色背景色 */
    --color-background-mute: #2E2E2B;  /* 略浅的背景色 */
    --color-background-soft: #141413;  /* 中等深色 */

    --navbar-background-mac: rgba(35, 35, 45, 0.85); /* Mac导航栏半透明背景 */
    --navbar-background: #262624;      /* 导航栏背景色 */
    --chat-background: #262624;        /* 新增：聊天区域总体背景 */
    --chat-background-white: #262624;  /* 深色背景 */
    --chat-background-user: #141413;   /* 用户消息背景 */
    --chat-background-assistant: #262624; /* AI助手消息背景 */

    --color-border: rgba(239, 239, 241, 0.15); /* 边框颜色 */
    --chat-text-user: #F5F4ED;         /* 用户消息文字颜色 */
    --color-text: #F5F4ED;             /* 全局文字颜色 */
}

/* 深色模式下的消息容器 */
body[theme-mode='dark'] .message-content-container {
    background: var(--chat-background-assistant) !important;
    /* box-shadow: 0 4px 16px -8px rgba(0,0,0,0.4) !important; */ /* 原始阴影，被后续覆盖 */
    box-shadow: none !important;
    border: none !important;
}

body[theme-mode='dark'] .message-user .message-content-container {
    background: var(--chat-background-user) !important;
    box-shadow: 0 8px 32px -12px rgba(0,0,0,0.3) !important;
    border: 1px solid var(--color-border) !important;
}

body[theme-mode='dark'] #inputbar {
    background: #30302E !important; /* 暗色模式下的输入框背景 */
    border: 1px solid var(--color-border) !important;
    box-shadow: 0 8px 32px -12px rgba(0,0,0,0.3) !important;
    backdrop-filter: blur(8px) !important;
}

/* Bug fixes */
.bubble .message-user .message-action-button:hover {
    background-color: var(--color-background-mute); /* 使用背景色变量修复悬停效果 */
}
```
CSDN🔗：![CherryStudio 自定义 Claude Web样式主题 - CSDN](https://blog.csdn.net/weixin_55068057/article/details/147230529?sharetype=blog&shareId=147230529&sharerefer=APP&sharesource=weixin_55068057&sharefrom=link)
