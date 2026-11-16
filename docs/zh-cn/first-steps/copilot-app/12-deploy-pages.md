---
title: "第 12 课 - 使用 GitHub Pages 部署网站"
description: "使用 GitHub Copilot app 配置 Pages 工作流、审查 pull request，并验证已发布的 Space Quiz。"
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

将 Space Quiz 部署到 GitHub Pages，让其他人也能访问。Copilot 可以准备工作流并指导部署，但你仍需审查更改并确认网站已上线。

本课将完成以下操作：

- 让 Copilot 配置 GitHub Pages 部署；
- 在合并前审查工作流和 pull request；
- 跟进部署并验证已发布的网站。

## 场景

Space Quiz 已在 GitHub 仓库中，但用户还没有方便的试用方式。使用 GitHub Pages 发布单文件网站后，用户便可通过公开 URL 访问，无需添加服务器或运行时依赖项。

## 让 Copilot 准备部署

> [!WARNING]
> 创建 pull request 可能会提交并推送代码。发送此提示前，请检查审批设置和目标仓库。如果选择了 **Approve all**，不要认为系统一定会再次提示确认。

在 `space-quiz` 的 Copilot app 会话中发送以下提示：

```plaintext
为此仓库准备 GitHub Pages 部署。创建一个 GitHub Actions 工作流，在需要时构建网站，并在更改进入默认分支后将其部署到 GitHub Pages。如果仓库还没有 README，请添加一个，介绍此应用以及如何在本地运行。使用这些更改创建 pull request，并报告其链接以及所需的 Pages 设置或权限。不要合并、启用自动合并、更改 Pages 设置或执行部署。停止并等待我审查。
```

## 审查工作流和 pull request

1. 确认仅当仓库原本没有 README 时才添加 README。
2. 审查 pull request 中的更改，包括工作流的构建和部署步骤、触发条件及权限。
3. 确认工作流从默认分支部署，而不是从尚未合并的 pull request 部署。
4. 请求修正并审查更新后的 diff。授权合并前，等待 pull request 的必需检查通过。

## 授权合并和部署

> [!WARNING]
> 以下提示授权代理合并已审查的 pull request、更改仓库的 Pages 设置并发布网站。只有在完成审查并确认仓库和 pull request 后，才能发送此提示。根据审批设置，这些操作可能不会再次请求确认。

将 `<PR_NUMBER>` 替换为已审查的 pull request 编号，然后单独发送以下提示：

```plaintext
我已审查此仓库中的 pull request <PR_NUMBER>，并授权合并和部署。启用 GitHub Pages 并使用 GitHub Actions；仅在必需检查通过后合并此 pull request，并持续监控部署，直到成功。报告已上线网站的最终 URL。如果你没有启用 Pages 或合并的权限，请准确说明我需要批准或执行什么操作；网站上线前不要报告成功。
```

![三阶段示意图：已合并的 space-quiz pull request；GitHub Actions 的 Deploy website 运行成功，包含 Build website、Upload artifact 和 Deploy to Pages 步骤；以及发布在 yourname.github.io/space-quiz/ 的 Space Quiz。](../../../_images/first-steps-app-pages-deploy.svg)

## 验证部署

1. 跟进 GitHub Actions 部署运行，直到成功。
2. 打开报告中的 URL，确认 Space Quiz 已加载。

如果代理无法启用 Pages 或合并 pull request，请按照它提供的具体说明操作。只有部署成功且网站正常加载后，才能将任务视为完成。

## 总结和后续步骤

Space Quiz 现已作为在线网站发布；你也亲自验证了部署，而不是依赖代理的报告。接下来学习[第 13 课：审查和后续步骤][next-lesson]。

[next-lesson]: ../13-review/
