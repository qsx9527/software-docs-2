---
title: "AIO-1126BJD4V0"
description: "AIO-1126BJD4V0 主板产品文档导航。"
---

# 上手教程
- [介绍](started.md)
- [串口调试](debug.md)
# 升级固件
- [介绍](upgrade_bootmode.md)
- [使用USB线缆升级固件](upgrade_firmware.md)
- [MaskRom模式](upgrade_maskrom_mode.md)
- [使用SD卡升级固件](upgrade_firmware_sd.md)
# Linux开发
- [编译 Linux 固件](linux_compile.md)
- [Firefly Linux 开发指南](linux_firefly_linux_manual.md)
# 接口使用
- [ADC 使用](usage_adc.md)
- [Camera 使用](usage_camera.md)
- [Display 使用](usage_display.md)
- [Ethernet 使用](usage_ethernet.md)
- [GPIO 使用](usage_gpio.md)
- [LED 使用](usage_led.md)
- [RTC 使用](usage_rtc.md)
- [UART 使用](usage_uart.md)
- [Watchdog 使用](usage_watchdog.md)
- [Sound Card 使用](usage_sound_card.md)
- [POE 使用](usage_poe.md)
# 配件
- [摄像头模组](module_camera.md)
- [显示屏模组](module_display.md)
- [通信模组](module_wireless.md)
# 其他
- [NPU使用](usage_npu.md)
# 常见问题解答
- [Linux 设备树 (DTS) 指南](linux_dts_manual.md)
# 参考资料
- [接口定义](interface_definition.md)

# Mermaid 渲染测试

本章节用于验证 Wiki 文档的 Mermaid 服务端渲染效果。

## 流程图（flowchart）

```mermaid
flowchart LR
    A[上电启动] --> B{BootRom}
    B -->|SPI NOR| C[Loader]
    B -->|eMMC| D[U-Boot]
    C --> D
    D --> E[Kernel]
    E --> F[根文件系统]
    F --> G[应用启动]
```

## 时序图（sequenceDiagram）

```mermaid
sequenceDiagram
    participant C as 客户端
    participant S as Wiki 服务端
    participant G as GitHub 仓库
    C->>S: 请求文档页面
    S->>G: 同步拉取 master
    G-->>S: 返回 Markdown
    S->>S: MDX 编译 + Mermaid 渲染
    S-->>C: 返回含 SVG 的页面
```

## 实体关系图（erDiagram）

```mermaid
erDiagram
    PRODUCT ||--o{ DOC : 拥有
    PRODUCT {
        string name 产品名
        string board 型号
    }
    DOC {
        string title 标题
        string lang 语言
    }
```

## 不支持的图（gantt，应降级为源码块）

```mermaid
gantt
    title 固件发布计划
    section 开发
    SDK 适配 :a1, 2026-09-01, 30d
    section 测试
    整机验证 :a2, after a1, 20d
```
