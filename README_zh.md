# zouxian 走线

Apple 限制在国行 Mac 上使用 Apple Intelligence 和 Xcode LLM（Predictive Code Completion）。如果你使用在中国购买的 Mac，即使你不在中国，你也无法使用 Apple Intelligence 和 Xcode Predictive Code Completion。

如果你不幸处于这种情况，现在是时候让你的 Mac 踏上 _[走线](https://en.wikipedia.org/wiki/Zouxian_(phenomenon))_ 之路了。

---

可在重启后保持的方案，基于 [Cyandev 的指南](https://gist.github.com/unixzii/6f25be1842399022e16ad6477a304286)。

## 系统版本

| From                   | To             |                                                                                                        |
| ---------------------- | -------------- | ------------------------------------------------------------------------------------------------------ |
| Macintosh System 1     | 14.6 (23G80)   | 不适用                                                                                                 |
| 15.0 Beta 1 (24A5264n) | 15.3.1 (24D70) | 安装 [Darwin Eligibility Override](https://github.com/CatMe0w/zouxian/blob/master/repatriate_guide.md) |
| 15.4 Beta 1 (24E5206s) | ?              | 安装 zouxian                                                                                           |

## 免责声明

禁用 SIP 会降低系统安全性，并且会使 App Store 中的 iOS app 与 Apple Pay 无法使用。

## 安装

### 前提条件

- 禁用 SIP 调试限制（在恢复模式下运行 `csrutil enable --without debug` 命令）。进入恢复模式的方法是：重启 Mac，按住电源键，直到看到启动选项窗口，选择“选项”，然后点击“继续”。请勿先按一次电源键再按住，可能会导致无法进入真正的恢复模式。
- 对于 Apple Intelligence：登录非国区 Apple ID，地区设置中国大陆以外的地区，这里推荐香港、台湾、美国，并且设置的系统语言与Siri语言要一致，地区的主语言要与设置的语言对应（例如美国-英文，香港-繁体中文）。
- 对于 Xcode Predictive Code Completion：安装 Xcode 并至少运行一次。

> [!NOTE]  
> 如果只想使用 Apple Intelligence，无需安装 Xcode。

请在终端中运行以下命令：

```shell
sudo curl https://raw.githubusercontent.com/hikaruchang/zouxian/master/zouxian.sh -o /usr/local/bin/zouxian
sudo chmod +x /usr/local/bin/zouxian
sudo curl https://raw.githubusercontent.com/hikaruchang/zouxian/master/rua.hikaru.zouxian.plist -o /Library/LaunchDaemons/rua.hikaru.zouxian.plist
sudo launchctl load -w /Library/LaunchDaemons/rua.hikaru.zouxian.plist
```

## 卸载

```shell
sudo launchctl unload -w /Library/LaunchDaemons/rua.hikaru.zouxian.plist
sudo rm /Library/LaunchDaemons/rua.hikaru.zouxian.plist
sudo rm /usr/local/bin/zouxian
```

## 感谢

感谢使得这一切成为可能的人们：[CatMe0w](https://github.com/CatMe0w)、[Kyle-Ye](https://github.com/Kyle-Ye)、[Cyandev](https://twitter.com/unixzii)、[Lakr233](https://twitter.com/Lakr233)、[Sou1gh0st](https://twitter.com/Sou1gh0st)、Yuriko。

## 许可证

MIT License
