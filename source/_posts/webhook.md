---
title: webhook 实现项目自动部署
urlname: webhook
date: 2019-11-05 16:28:47
tags:
---

## 利用 github webhook 实现项目自动部署

[项目地址 https://github.com/gdrpAPeng/webhooks](https://github.com/gdrpAPeng/webhooks)

<!-- more -->

将接口地址挂到 github 仓库上的 webhooks 之后，触发更新条件 github 就会给你发送如下一堆数据，然后你就可以根据自己的需求为所欲为为所欲为为所欲为了
```js
{
  "ref": "refs/heads/master",
  "repository": {
    "name": "webhooks",
    "full_name": "gdrpAPeng/webhooks",
    "private": false,
    "html_url": "https://github.com/gdrpAPeng/webhooks",
    "description": "自动化部署工程",
    "git_url": "git://github.com/gdrpAPeng/webhooks.git",
    "clone_url": "https://github.com/gdrpAPeng/webhooks.git",
    "svn_url": "https://github.com/gdrpAPeng/webhooks",
    "default_branch": "master",
    "stargazers": 0,
    "master_branch": "master"
  }
}
```

### 代码代码代码 👇👇👇

```js
async webhooks(req, res, next) {
    // 避免超时，接收到 github 发来的消息直接返回 success
    res.json({
        message: 'Success'
    })
    // 在传来的消息里获取到仓库名字、git clone 地址
    const { name, git_url } = req.body.repository
    // 自定义配置的项目根路径
    const { rootPath } = config
    // repository.name
    // repository.git_url
    const dirPath = path.join(rootPath, `/${name}`)
    try {
       await fs.accessSync(dirPath) // 检查是否存在目录
    } catch(e) {
        // clone
       await execSync(`git clone ${git_url}`, {
           // cwd 执行环境， 位置 类似 cd 命令
           cwd: rootPath
       })
    }

    // 获取项目配置命令
    let projectConfig = JSON.parse(
        // webhook.config.json 每个项目的 webhook 配置都在这里
        // {
        //     "projectName": "webhooks",
        //     "rootPath": "/home/project",
        //     "commands": [
        //         "yarn"
        //     ]
        // }
        fs.readFileSync(`${dirPath}/webhook.config.json`).toString('utf-8')
    ) 

    // 拉取更新代码 并 执行 各个项目不同的指令
    let commandsStr = [
        `git pull`,
        ...projectConfig.commands
    ].join(' & ')

    try {
        await execSync(commandsStr, {
            cwd: dirPath
        })
    } catch(e) {
        console.log(e)
    }
}
```