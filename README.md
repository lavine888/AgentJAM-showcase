# AgentJam

> 在 Minecraft 里多人协作的 AI 编程空间  
> Google Docs for code, but spatial, voice-driven, and AI-powered.

![Status](https://img.shields.io/badge/AI%20Coding-Collaboration-79ff8f)
![Style](https://img.shields.io/badge/Interface-Minecraft%203D-52d8ff)
![Demo](https://img.shields.io/badge/Demo-GitHub%20Pages-ffd166)

[在线预览](https://lavine888.github.io/AgentJAM-showcase/) · [展示页源码](./index.html)

## 创意名称与介绍

**AgentJam** 是一个把 AI 编程协作搬进 3D 空间的创意产品。它想解决一个正在变得越来越明显的问题：AI agent 写代码越来越快，但团队协作仍然停留在个人电脑、个人终端、个人分支和异步 PR 的旧流程里。

每个人都可以让 AI 快速改代码，却很难实时看见队友的 agent 正在做什么、项目现在以哪个版本为准、运行效果有没有同步。速度被 AI 提高了，协作上下文却更容易碎掉。

AgentJam 的产品形态是一个基于 **Minecraft / Web / AI agent runtime** 的多人编程系统。用户进入共享的 3D 房间，每个人拥有自己的 agent 工位，可以通过语音或终端指挥 AI 修改项目；房间中央有共同的项目墙，实时展示代码变更、运行页面、任务状态和历史快照。

它把 AI coding 从“一个人和一个助手”推进到“多人 + 多个 AI agent 在同一个空间里一起工作”。

## 目标用户与痛点

AgentJam 面向需要快速共创 Demo 的小团队，尤其适合黑客松团队、AI 开发者、创业团队、编程教育场景中的老师和学生。

典型场景是三到五个人在黑客松或项目冲刺中一起做产品原型。过去的协作方式通常是：每个人各开一个编辑器，各自向 AI 提问，各自生成代码，最后再手动合并。AI agent 一旦连续生成大量代码，重复劳动、版本冲突、上下文丢失和运行环境不一致就会更频繁出现。

| 协作问题 | AgentJam 的空间化体验 |
| --- | --- |
| 不知道队友的 AI agent 正在做什么 | 每个 agent 工位显示当前任务、状态和修改范围 |
| 不知道项目以谁的版本为准 | 中央项目墙展示统一的运行页面与代码变更 |
| 修改结果反复复制、粘贴、合并 | 变更以空间事件的方式实时同步 |
| 新成员难以理解项目状态 | 进入房间即可看到任务、历史快照和运行结果 |
| 老师难以观察真实协作过程 | 学生的分工、提问、调试和修复过程都可视化 |
| agent 执行过程像黑箱 | 过程、日志、Diff 和测试状态被投射到公共界面 |

AgentJam 希望把这些分散的信息放进一个共享空间，让协作变成“大家在同一个房间里一起建东西”。

## 价值与意义

从效率角度看，AgentJam 让多人 AI 编程从异步协作变成实时协作。团队不再只是等待 PR 合并，而是可以看到 agent 正在执行什么任务、当前项目能不能运行、谁负责哪个模块、下一步该由谁接力。

从学习和教育角度看，它让编程过程变得更可视化。老师看到的不只是最后提交的代码，也能看到学生如何分工、如何向 AI 提问、如何修复错误，以及如何把一个想法变成可运行 Demo。对初学者来说，Minecraft 式空间比传统 IDE 更容易理解：终端、网页、任务和 agent 都变成了可以走近、点击、观察的对象。

从产品创新角度看，AgentJam 重新想象了 AI coding 的协作界面。过去的代码协作工具主要解决远程异步合并；AgentJam 关注的是多人和多个 AI agent 在同一个实时项目里共同创造。

## 一句话总结

> GitHub 解决距离，AgentJam 删除距离。

## 项目文件

- `index.html`：GitHub Pages 展示入口。
- `_shared/fonts/`：展示页使用的字体资源。
- `.nojekyll`：保证 GitHub Pages 正常读取 `_shared` 静态资源。
