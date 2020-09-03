# blingbling-everyday

[![CI](https://github.com/eyea/blingbling-everyday/workflows/CI/badge.svg)](https://github.com/eyea/blingbling-everyday/actions)

自动保持 GitHub 提交状态常绿。

## 原理

使用 GitHub Actions 的定时任务功能。

## 使用

- 点右上角 **Fork** 按钮复制本 GitHub 仓库
- 在自己的项目中，点上方 **Actions** 选项卡进入项目 GitHub Actions 页面, 点击绿色按钮 “**I understand my workflows, go ahead and enable them**” 开启自动提交功能
- (可选) 你可以通过修改 [ci.yml 文件的第 13 行](https://github.com/eyea/blingbling-everyday/blob/master/.github/workflows/ci.yml#L13)来调整频率

计划任务语法有 5 个字段，中间用空格分隔，每个字段代表一个时间单位。

```plain
┌───────────── 分钟 (0 - 59)
│ ┌───────────── 小时 (0 - 23)
│ │ ┌───────────── 日 (1 - 31)
│ │ │ ┌───────────── 月 (1 - 12 或 JAN-DEC)
│ │ │ │ ┌───────────── 星期 (0 - 6 或 SUN-SAT)
│ │ │ │ │
│ │ │ │ │
│ │ │ │ │
* * * * *
```

每个时间字段的含义：

|符号   | 描述        | 举例                                        |
| ----- | -----------| -------------------------------------------|
| `*`   | 任意值      | `* * * * *` 每天每小时每分钟                  |
| `,`   | 值分隔符    | `1,3,4,7 * * * *` 每小时的 1 3 4 7 分钟       |
| `-`   | 范围       | `1-6 * * * *` 每小时的 1-6 分钟               |
| `/`   | 每         | `*/15 * * * *` 每隔 15 分钟                  |

**注**：由于 GitHub Actions 的限制，如果设置为 `* * * * *` 实际的执行频率为每 5 分执行一次。

## License

[blingbling-everyday](https://github.com/eyea/blingbling-everyday) is released under the [MIT](./LICENSE) License.

##### 感谢
[justjavac](https://github.com/justjavac/auto-green)

