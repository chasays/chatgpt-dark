# ChatGPT-Dark
> 本项目基于 [chatgpt-vercel](https://github.com/ourongxing/chatgpt-vercel) 开发。
#  增加了多密码模式和记录不同对话历史的功能

![](assets/dark1.png)
![](assets/dark2.png)


在本地开发和调试:

0. `git clone https://github.com/CODEisArrrt/chatgpt-dark.git`
1. 升级到 `node18` (我的版本是v18.15.0)
2. 如果在内地部署 需要配置好环境变量 `SOCKS_PROXY` 我设置的是 `export SOCKS_PROXY=socks5://127.0.0.1:1080`因为内地需要通过代理访问API 内地有dns污染 hosts里要加 `104.18.7.192 api.openai.com` 这个是api官方域名的解析ip
3. `pnpm i` 安装依赖。
4. `pnpm run build && node server.js` 打包和运行 然后使用`http://localhost:80` 就能访问了

### 环境变量


环境变量可以用`export` 也可以将 `.env.example` 文件修改为 `.env`，在 `.env` 中设置。


| 环境变量                             | 说明                                                         | 默认值                                                       |
| ---------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------|
| `OPENAI_API_KEY`                   | OpenAI API Key                                               | 无                                                          |
| `DEFAULT_MESSAGE`                  | 默认提示信息                                                    | - 由 [OpenAI API (gpt-3.5-turbo)](https://platform.openai.com/docs/guides/chat) 提供支持。<br/>- 由 [@CODEisArt](https://github.com/CODEisArrrt) 基于 [chatgpt-vercel](https://github.com/ourongxing/chatgpt-vercel) 开发，查看 [源码](https://github.com/CODEisArrrt/chatgpt-dark)，欢迎自部署。<br/>- [[Shift]] + [[Enter]] 换行。只输入 [[/]] 可展开Prompt预设。只输入 [[空格]] 可选择切换到不同对话历史，点击输入框滚动到底部。<br/>- 为了节省GPT请求Token消耗，默认关闭了连续对话，若需要可在输入框左上角的设置里自行开启，也可开启记录对话内容，来新建和记录不同对话历史。|
| `DEFAULT_SETTING`                  | 默认设置 | {<br/>  "continuousDialogue": true,<br/>  "archiveSession": false,<br/>  "openaiAPIKey": "",<br />  "openaiAPITemperature": 60,<br/>  "systemRule": ""<br/>  "password": ""<br />} |
| `RESET_CONTINUOUS_DIALOGUE_OPTION` | 刷新时重置 `开启连续对话` 选项，在分享给很多人用的时候可以有效避免大量消耗。 | false                                                        |
| `OPENAI_API_BASE_URL`              | 本地开发时可以填写 OpenAI 的代理服务器，但是 Vercel 不需要。            | api.openai.com                                               |
| `PASSWORD`                         | 网站密码                                                         | 无                                                           |
| `PASSWORD_FILE`                    | 单人单密码JSON文件路径                                             | 无                                                           |
| `MAX_REPLY_QUOTA`                  | 单人单密码文件设置后，单个密码每日最多可用GPT回复次数 | 100 |
| `MAX_INPUT_TOKENS`                 | 输入的 token 最大值，如果开启 `连续对话`，将计算之前的所有对话内容。OpenAI 限制 token 最大值为 4096，但这是输入和输出之和，所以可以将这个值设置为 3072， 留 1024 作为输出。如果不想被滥用，可以将这个值设置的再小一点。 | 3072                                                         |




### 默认设置

> 记得删除注释，或者直接复制上面表格里的。

```json5
{
  "continuousDialogue": true, // 开启连续对话，每次都需要将上下文传给 API，比较费钱，而且同样有 4096 token 的限制
  "archiveSession": false, // 记录对话内容，刷新后不会清空对话
  "openaiAPIKey": "", // 默认填写的 key，不需要填写，否则其他人看得到。
  "password": "",// 默认填写的密码，不需要填写，否则其他人看得到。
  "openaiAPITemperature": 60, // 0-100 越高 ChatGPT 思维就越发散，开始乱答
  "systemRule": "" // 系统角色指令，会在每次提问时添加。主要用于对 ChatGPT 的语气，口头禅这些进行定制。
}
```

## 提交你的 Prompts

1. Fork 本项目。
2. 修改 `prompts.md`。
3. Pull Request 即可。

如果你不懂这个操作，也可以直接在 Issues 提交你的 Prompts。目前大部分 Prompts 来自于 [awesome-chatgpt-prompts-zh](https://github.com/PlexPt/awesome-chatgpt-prompts-zh)，当然，这个仓库大多数也是翻译的 [awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts)，一并感谢。

### 要求

- 把需要输入的内容放在最后，可以提示 ChatGPT 开始输入了，比如 “我的第一句话是：”。
- 尽可能去优化已有的 Prompts，而不是重复添加。
- 添加到结尾，我会定期整理。


## License

[MIT](./LICENSE)
