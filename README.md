# ESP + HomeKit 生成器

单文件网页：在浏览器里配置 ESP8266 / ESP32 的 ESPHome + HomeKit 固件，点一下编译、插上板子就能烧。

**在线使用**：https://esp-homekit.pages.dev/

## 能做什么

| 功能 | 说明 |
|---|---|
| 可视化配置 | 芯片 / FLASH / 板型 / WiFi / 配对码 / 巴法云远程，全部是卡片，点选即可 |
| 设备类型 | 继电器、温湿度（DHT）、人体感应（PIR）、光照（BH1750）、门磁、物理按键 |
| 联动 | 继电器之间可配置 HomeKit 自动化联动 |
| 编译 | 云端编译（GitHub Actions 构建 ESPHome），产出可直接烧录的 bin |
| 烧录 | 浏览器 Web Serial 直接烧，支持 ESP8266 与 ESP32（写入合并后的 factory.bin） |
| 整机模板 | 粘贴一份完整 YAML 即可做成"整机"，自动把写死的 GPIO 变成可调引脚参数 |
| 模板云同步 | 模板可存到 Cloudflare KV，换设备/清缓存不丢 |

## 组件依赖

生成的 YAML 通过 `external_components` 拉取 [txhtxh11/homekit](https://github.com/txhtxh11/homekit)：

- `homekit-esp8266` — Arduino 版，支持开关/传感器/二进制传感器，配对码可配
- `homekit-esp32` — 基于乐鑫 HAP SDK，走 ESP-IDF，支持灯/锁/风扇/开关/空调/传感器/二进制传感器，配对码可配

## 本地文件

整个页面就是 `index.html` 一个文件，没有构建步骤、没有外部依赖（esptool-js 从 CDN 加载）。

```bash
git clone https://github.com/txhtxh11/esp-homekit
cd esp-homekit
# 直接双击 index.html 也能用（file:// 下烧录正常，编译需要联网）
```

## 浏览器要求

- 桌面版 Chrome / Edge（Web Serial 只在桌面 Chromium 系可用）
- 需要 HTTPS 或 localhost 才能访问串口

## 相关仓库

- 组件：[txhtxh11/homekit](https://github.com/txhtxh11/homekit)
- 编译服务：[txhtxh11/esphome-online-compiler](https://github.com/txhtxh11/esphome-online-compiler)

## 许可

MIT
