# **Homework_1**

平台 : Azure openai services

目標 : 使用API

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
可參考程式碼 https://github.com/41071119H-Irene/data_mining/blob/main/Lab%201.ipynb

## 現在遇到的困難
1. 不知道如何在Azure上編輯程式碼
2. 老師給的金鑰和我的有什麼不同(不是說要申請，但我好像沒申請就有了?)
4. 部屬後，無法開啟遊樂場
