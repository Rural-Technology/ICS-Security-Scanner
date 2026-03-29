# Day 1 - Modbus Protocol Analysis with Wireshark

## Environment
- OpenPLC (Modbus TCP server, Docker IP: 172.17.0.2, port 502)
- FUXA (Modbus client, IP: 172.17.0.1)
- Wireshark filter: `tcp.port == 502`

## Modbus Protocol Core

**Total length: 12 bytes**

**Only Byte 7 matters for security analysis - Function Code**

| Function Code | Meaning |
|---------------|---------|
| 0x01 | Read Coils (read ON/OFF) |
| 0x03 | Read Holding Registers (read numbers) |
| 0x05 | Write Single Coil (write ON/OFF - unauthorized risk) |

**Other bytes (Transaction ID, Protocol ID, Length, Unit ID, Data bytes) change per request. Ignore them.**

## Captured Packets

### Read Holding Registers (Function Code 0x03)
- Function Code: 0x03
- Action: Client read register value

### Read Coils (Function Code 0x01)  
- Function Code: 0x01
- Action: Client read coil status, got value 1 (ON)

## Security Analysis
- Modbus has **no authentication** (no password required)
- Any client can send requests
- Unauthorized write is possible

## Key Takeaway
> **Just look at Byte 7. It tells you what the client is doing.**

---

## Vocabulary (生词注解)

| English | 中文 |
|---------|------|
| protocol | 协议 |
| core | 核心 |
| total length | 总长度 |
| byte | 字节 |
| matters | 重要、关键 |
| security analysis | 安全分析 |
| function code | 功能码 |
| coil | 线圈 |
| holding register | 保持寄存器 |
| unauthorized | 未授权的 |
| request | 请求 |
| response | 响应 |
| authentication | 认证、身份验证 |
| key takeaway | 关键结论 |

## Screenshots
![Read Coils](./read_coils.png)
