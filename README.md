# **Homework_1**

**作業影片**:https://youtu.be/CvFW8n6NzlU

### 平台 : Azure openai services ( Azure是公共雲端計算平台 )

### 目標 : 使用API

## 老師的範例程式碼
```ruby
curl "https://ntnu-ml.openai.azure.com/openai/deployments/ntnu-ml-gpt4-32k/chat/completions?api-version=2024-02-15-preview" \
  -H "Content-Type: application/json" \
  -H "api-key: API " \
  -d "{
  \"messages\": [{\"role\":\"system\",\"content\":\"根據 `` 中提供的 rating.csv 資料，用協同過濾的概念推薦餐廳給使用者  ，請以 json array 格式回答\n\`\ncustomerId,restaurantId,rating\nc1,r2,3\nc1,r3,1\nc1,r5,3\nc1,r6,2\nc2,r1,3\nc2,r3,1\nc2,r5,1\nc2,r6,1\nc3,r4,3\nc3,r5,3\nc3,r6,3\nc4,r1,1\nc4,r4,1\nc4,r5,3\nc5,r2,1\nc5,r3,2\nc5,r4,3\nc6,r2,3\nc6,r3,3\nc6,r5,3\nc7,r2,3\nc7,r3,3\nc7,r4,1\nc8,r1,2\nc8,r2,1\nc8,r5,1\nc8,r6,2\n\`\"},{\"role\":\"user\",\"content\":\"c1\"}],
  \"max_tokens\": 800,
  \"temperature\": 0.5,
  \"frequency_penalty\": 0,
  \"presence_penalty\": 0,
  \"top_p\": 0.95,
  \"stop\": null
  }"
```
助教的參考程式碼 https://github.com/41071119H-Irene/data_mining/blob/main/Lab%201.ipynb

## 現在遇到的困難
1. 不知道如何在Azure上跑，無法開啟遊樂場
2. 跑出來的資料都一樣

## 輸入
```ruby
import requests
# API
url = "https://ntnu-ml.openai.azure.com/openai/deployments/ntnu-ml-gpt4-32k/chat/completions?api-version=2024-02-15-preview"
# 輸入的資料型態 加 API-KEY
headers = {
    "Content-Type": "application/json",
    "api-key": "7c196b48c6c14f25adc5a8d7dcbc8d02"
}
# 資料 加 要找的資料{"role": "user", "content": "c1"} 加 模型參數
data = {
    "messages": [
        {"role": "system", "content": "根據 `` 中提供的 rating.csv 資料，用協同過濾的概念推薦餐廳給使用者  ，請以 json array 格式回答\n\`\ncustomerId,restaurantId,rating\nc1,r2,3\nc1,r3,1\nc1,r5,3\nc1,r6,2\nc2,r1,3\nc2,r3,1\nc2,r5,1\nc2,r6,1\nc3,r4,3\nc3,r5,3\nc3,r6,3\nc4,r1,1\nc4,r4,1\nc4,r5,3\nc5,r2,1\nc5,r3,2\nc5,r4,3\nc6,r2,3\nc6,r3,3\nc6,r5,3\nc7,r2,3\nc7,r3,3\nc7,r4,1\nc8,r1,2\nc8,r2,1\nc8,r5,1\nc8,r6,2\n\`"},
        {"role": "user", "content": "c1"}
    ],
    "max_tokens": 800,
    "temperature": 0.5,
    "frequency_penalty": 0,
    "presence_penalty": 0,
    "top_p": 0.95,
    "stop": None
}

response = requests.post(url, json=data, headers=headers)

print(response.text)
```

## 輸出轉json
```ruby
{
    "choices": [{
        "content_filter_results": {
            "hate": {
                "filtered": false,
                "severity": "safe"
            },
            "self_harm": {
                "filtered": false,
                "severity": "safe"
            },
            "sexual": {
                "filtered": false,
                "severity": "safe"
            },
            "violence": {
                "filtered": false,
                "severity": "safe"
            }
        },
        "finish_reason": "stop",
        "index": 0,
        "logprobs": null,
        "message": {
            "content": "[\n  {\n    \"customerId\": \"c1\",\n    \"recommendedRestaurants\": [\"r1\", \"r4\"]\n  }\n]",
            "role": "assistant"
        }
    }],
    "created": 1711469435,
    "id": "chatcmpl-973ffwjeGVHGL5u3wy5iDrB3snVnv",
    "model": "gpt-4-32k",
    "object": "chat.completion",
    "prompt_filter_results": [{
        "prompt_index": 0,
        "content_filter_results": {
            "hate": {
                "filtered": false,
                "severity": "safe"
            },
            "self_harm": {
                "filtered": false,
                "severity": "safe"
            },
            "sexual": {
                "filtered": false,
                "severity": "safe"
            },
            "violence": {
                "filtered": false,
                "severity": "safe"
            }
        }
    }],
    "system_fingerprint": null,
    "usage": {
        "completion_tokens": 28,
        "prompt_tokens": 272,
        "total_tokens": 300
    }
}
```

## 輸入
```ruby
import requests

url = "https://ntnu-ml.openai.azure.com/openai/deployments/ntnu-ml-gpt4-32k/chat/completions?api-version=2024-02-15-preview"

headers = {
    "Content-Type": "application/json",
    "api-key": "7c196b48c6c14f25adc5a8d7dcbc8d02"
}

data = {
    "messages": [
        {"role": "system", "content": "根據 `` 中提供的 rating.cAsv 資料，用協同過濾的概念推薦餐廳給使用者  ，請以 json array 格式回答\n\`\ncustomerId,restaurantId,rating\nc1,r2,3\nc1,r3,1\nc1,r5,3\nc1,r6,2\nc2,r1,3\nc2,r3,1\nc2,r5,1\nc2,r6,1\nc3,r4,3\nc3,r5,3\nc3,r6,3\nc4,r1,1\nc4,r4,1\nc4,r5,3\nc5,r2,1\nc5,r3,2\nc5,r4,3\nc6,r2,3\nc6,r3,3\nc6,r5,3\nc7,r2,3\nc7,r3,3\nc7,r4,1\nc8,r1,2\nc8,r2,1\nc8,r5,1\nc8,r6,2\n\`"},
        {"role": "user", "content": "c1"},
        {"role": "assistant", "content": "[r2,r4]"},
        {"role": "user", "content": "c4"},
        {"role": "assistant", "content": "[r5,r4]"},
        {"role": "user", "content": "c10"}
    ],
    "max_tokens": 800,
    "temperature": 0.5,
    "frequency_penalty": 0,
    "presence_penalty": 0,
    "top_p": 0.95,
    "stop": None
}

response = requests.post(url, json=data, headers=headers)

print(response.text)
```
## 輸出轉json
```ruby
{
    "choices": [{
        "content_filter_results": {
            "hate": {
                "filtered": false,
                "severity": "safe"
            },
            "self_harm": {
                "filtered": false,
                "severity": "safe"
            },
            "sexual": {
                "filtered": false,
                "severity": "safe"
            },
            "violence": {
                "filtered": false,
                "severity": "safe"
            }
        },
        "finish_reason": "stop",
        "index": 0,
        "logprobs": null,
        "message": {
            "content": "[r1,r2,r3,r4,r5,r6]",
            "role": "assistant"
        }
    }],
    "created": 1711502128,
    "id": "chatcmpl-97CAyBIjZjsdOzMJaclNILfV5tmYC",
    "model": "gpt-4-32k",
    "object": "chat.completion",
    "prompt_filter_results": [{
        "prompt_index": 0,
        "content_filter_results": {
            "hate": {
                "filtered": false,
                "severity": "safe"
            },
            "self_harm": {
                "filtered": false,
                "severity": "safe"
            },
            "sexual": {
                "filtered": false,
                "severity": "safe"
            },
            "violence": {
                "filtered": false,
                "severity": "safe"
            }
        }
    }],
    "system_fingerprint": null,
    "usage": {
        "completion_tokens": 13,
        "prompt_tokens": 302,
        "total_tokens": 315
    }
}
```

### Azure是公共雲端計算平台

四種模式:

Public cloud（公共雲）透過公共網路提供雲端服務，一般開放給大眾使用，租用彈性較大，安全性相對較低。

行業應用：中小企、初創

Private cloud（私有雲）透過內部網路提供雲端服務，僅供單一使用者使用，擁有獨立使用權限，相對穩定和安全，但維修與管理成本更高。

行業應用：銀行、金融

Hybrid cloud（混合雲）結合以上兩者，但不同雲端系統保持獨立。用戶可按資料的機密程度分別存檔，能節省成本，同時確保資料安全，故受企業歡迎。

行業應用：教育、零售

Community cloud（社群雲）由關注相同議題的企業組成，雲端系統由第三方管理，只有社群成員才可使用雲端資料及應用程式，例如醫院使用電子雲端平台新增及查看病歷。

行業應用：醫療衛生、政府

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://img.alicdn.com/tfs/TB14umhPOLaK1RjSZFxXXamPFXa-2305-1451.png_.webp">
  <source media="(prefers-color-scheme: light)" srcset="https://img.alicdn.com/tfs/TB14umhPOLaK1RjSZFxXXamPFXa-2305-1451.png_.webp">
  <img alt="Shows an illustrated sun in light mode and a moon with stars in dark mode." src="https://img.alicdn.com/tfs/TB14umhPOLaK1RjSZFxXXamPFXa-2305-1451.png_.webp">
</picture>

#### 本地與雲端的服務

### API ( Application Programming Interface )
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://www.dottedsign.com/zh-tw/blog/wp-content/uploads/2024/01/35.API-1-768x600.jpg">
  <source media="(prefers-color-scheme: light)" srcset="https://www.dottedsign.com/zh-tw/blog/wp-content/uploads/2024/01/35.API-1-768x600.jpg">
  <img alt="Shows an illustrated sun in light mode and a moon with stars in dark mode." src="https://www.dottedsign.com/zh-tw/blog/wp-content/uploads/2024/01/35.API-1-768x600.jpg">
</picture>

如何寫md : https://docs.github.com/zh/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/quickstart-for-writing-on-github
