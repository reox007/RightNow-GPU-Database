# RightNow GPU Database

Comprehensive GPU specifications database with architecture, manufacturing, API support, performance details, and kernel development specs.

**2,824 GPUs** across NVIDIA, AMD, and Intel

Part of [RightNow](https://www.rightnowai.co) — AI-powered code editor for GPU kernel development

## Data

| Vendor | GPUs | File |
|--------|------|------|
| NVIDIA | 1,286 | [`data/nvidia/all.json`](data/nvidia/all.json) |
| AMD | 1,292 | [`data/amd/all.json`](data/amd/all.json) |
| Intel | 180 | [`data/intel/all.json`](data/intel/all.json) |
| **All** | 2,824 | [`data/all-gpus.json`](data/all-gpus.json) |

## Schema

Each GPU contains up to 55 fields:

```json
{
  "name": "GeForce RTX 4090",
  "vendor": "nvidia",
  "manufacturer": "NVIDIA",
  "gpuName": "AD102",
  "architecture": "Ada Lovelace",
  "generation": "GeForce 40",

  "foundry": "TSMC",
  "processSize": 5,
  "transistors": 76.3,
  "transistorDensity": 125.3,
  "dieSize": 609.0,
  "chipPackage": "BGA-2150",
  "releaseDate": "2022-09-20",

  "baseClock": 2235.0,
  "boostClock": 2520.0,
  "memoryClock": 1313.0,

  "memorySize": 24.0,
  "memoryType": "GDDR6X",
  "memoryBus": 384,
  "memoryBandwidth": 1010.0,

  "shaders": 16384,
  "tmus": 512,
  "rops": 176,
  "sms": 128,
  "tensorCores": 512,
  "rtCores": 128,
  "coresPerSM": 128,

  "l1Cache": 128.0,
  "l2Cache": 72.0,

  "tdp": 450,
  "suggestedPSU": 850,
  "powerConnectors": "1x 16-pin",

  "length": 304.0,
  "width": 61.0,
  "slot": "Triple-slot",
  "displayOutputs": "1x HDMI 2.1, 3x DisplayPort 1.4a",
  "busInterface": "PCIe 4.0 x16",

  "pixelRate": 443.5,
  "textureRate": 1290.2,
  "fp16": 82.58,
  "fp32": 82.58,
  "fp64": 1.29,

  "directX": "12.2",
  "openGL": "4.6",
  "vulkan": "1.4",
  "openCL": "3.0",
  "cuda": "8.9",
  "shaderModel": "6.8",

  "warpSize": 32,
  "maxThreadsPerBlock": 1024,
  "maxThreadsPerSM": 1536,
  "maxBlocksPerSM": 24,
  "sharedMemPerSM": 102400,
  "registersPerSM": 65536,

  "url": "https://www.techpowerup.com/gpu-specs/geforce-rtx-4090.c3889"
}
```

Only populated fields are included — no nulls or zeros.

## Usage

**Direct URL:**
```
https://raw.githubusercontent.com/RightNowAI/gpu-database/main/data/nvidia/all.json
```

**JavaScript:**
```javascript
const gpus = await fetch(
  'https://raw.githubusercontent.com/RightNowAI/gpu-database/main/data/nvidia/all.json'
).then(r => r.json());

const rtx4090 = gpus.find(g => g.name === 'GeForce RTX 4090');
console.log(rtx4090.cuda);           // "8.9"
console.log(rtx4090.sharedMemPerSM); // 102400
console.log(rtx4090.coresPerSM);     // 128
```

**Python:**
```python
import requests

gpus = requests.get(
    'https://raw.githubusercontent.com/RightNowAI/gpu-database/main/data/nvidia/all.json'
).json()

rtx4090 = next(g for g in gpus if g['name'] == 'GeForce RTX 4090')
print(rtx4090['cuda'])            # 8.9
print(rtx4090['maxThreadsPerSM']) # 1536
```

## Source

Data sourced from [TechPowerUp GPU Database](https://www.techpowerup.com/gpu-specs/) via [dbgpu](https://github.com/painebenjamin/dbgpu).

## License

[Apache 2.0](LICENSE)

---

Built by [RightNow](https://www.rightnowai.co)
