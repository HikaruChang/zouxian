# zouxian 走线

中文版请见[这里](https://github.com/hikaruchang/zouxian/blob/master/README_zh.md)。

Apple restricted the access to Apple Intelligence and Xcode LLM (Predictive Code Completion) feature on China models of Mac. That is, if you are using a Mac bought in China, even if you are not in China, you will not be able to use Apple Intelligence or Xcode Predictive Code Completion.

If you are unfortunate to be in this situation, now it is time take your Mac on a journey of _[Zouxian](https://en.wikipedia.org/wiki/Zouxian_(phenomenon))_.

---

Persistent solution after rebooting, based on [Cyandev's guide](https://gist.github.com/unixzii/6f25be1842399022e16ad6477a304286).

## Version table

| From                   | To             |                                                                                                           |
| ---------------------- | -------------- | --------------------------------------------------------------------------------------------------------- |
| Macintosh System 1     | 14.6 (23G80)   | Not applicable                                                                                            |
| 15.0 Beta 1 (24A5264n) | 15.3.1 (24D70) | Install [Darwin Eligibility Override](https://github.com/CatMe0w/zouxian/blob/master/repatriate_guide.md) |
| 15.4 Beta 1 (24E5206s) | ?              | Install zouxian                                                                                           |

## Disclaimer

You must agree to the following terms when using this script:
1. You must back up your data before using this script.
2. This script is for learning and research purposes only, and is prohibited for any commercial use.

## Install

### Prerequisites

- SIP debugging restrictions are disabled (via `csrutil disable` command in recovery mode). To enter recovery mode, restart your Mac and hold the power button until you see the startup options window. Select "Options" and click "Continue". Do not press the power button once and then hold it, as this may prevent you from entering true recovery mode.
- For Apple Intelligence: Sign in with a non-Mainland China Apple ID and set your region to somewhere outside Mainland China. Hong Kong, Taiwan, and the United States are recommended. Also, make sure that the system language and Siri language are the same, and that the region's primary language matches the language you set (for example, United States - English, Hong Kong - Traditional Chinese).
- For Xcode Predictive Code Completion: Xcode is installed and run at least once.
- After running the automatic mode script, you can enter recovery mode and run the `csrutil enable` command to enable SIP.

> [!NOTE]  
> No need to install Xcode if you only want to use Apple Intelligence.

### Automatic mode (recommended)
Please run the following command in the terminal:

```shell
curl -sL https://raw.githubusercontent.com/HikaruChang/zouxian/master/enable_ai.sh | bash
```

### Manual mode
Please run the following commands in the terminal:

```shell
sudo curl https://raw.githubusercontent.com/hikaruchang/zouxian/master/zouxian.sh -o /usr/local/bin/zouxian
sudo chmod +x /usr/local/bin/zouxian
sudo curl https://raw.githubusercontent.com/hikaruchang/zouxian/master/rua.hikaru.zouxian.plist -o /Library/LaunchDaemons/rua.hikaru.zouxian.plist
sudo launchctl load -w /Library/LaunchDaemons/rua.hikaru.zouxian.plist
```

## Uninstall

```shell
sudo launchctl unload -w /Library/LaunchDaemons/rua.hikaru.zouxian.plist
sudo rm /Library/LaunchDaemons/rua.hikaru.zouxian.plist
sudo rm /usr/local/bin/zouxian
```

## Acknowledgement

Thanks for those who make this possible together: [CatMe0w](https://github.com/CatMe0w), [Kyle-Ye](https://github.com/Kyle-Ye), [Cyandev](https://twitter.com/unixzii), [Lakr233](https://twitter.com/Lakr233), [Sou1gh0st](https://twitter.com/Sou1gh0st), Yuriko, [KanShuRichard](https://github.com/kanshurichard).

## License

MIT License
