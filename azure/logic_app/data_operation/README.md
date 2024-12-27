# Azure Logic App Data Operation

- [Perform data operations in Azure Logic Apps](https://learn.microsoft.com/en-us/azure/logic-apps/logic-apps-perform-data-operations?tabs=consumption#parse-json-action)

## Table of Content

- [Pick data from previous step](#pick-data-from-previous-step)
- [Parse JSON](#parse-json)
  - [Example](#example)
    - [Access Data](#access-data)
      - [String](#string)
      - [Array](#array)
- [Compose](#compose)
- [Select](#select)

## Pick data from previous step

```json
// From Parse JSON Action
body('Parse_JSON')

// From Compose Action
output('compose')
```

## Parse JSON

- Input
  - Provide a valid JSON
  - Provide correspond JSON schema
- Output: 
  - Detail JSON data for next step

### Example

#### Input

```json
// Input Data
{
  "Name": "妍蜜Yanmi的沙龍",
  "LINK": "https://example.com/yanmi_blog",
  "提及內容": ["動機", "心路轉變", "申請計畫(內容)", "學習資源"],
  "這篇文章想溝通的對象": ["外界", "家長", "自己"],
  "發表者角色": ["自學生"],
  "資料類別": ["內容"],
  "學習領域": ["寫作", "語言", "跨文化"],
  "期程": "一學年",
  "發布時間": "2020-07-20"
}

// Input Schema
{
  "type": "object",
  "properties": {
    "Name": {
      "type": "string"
    },
    "LINK": {
      "type": "string"
    },
    "提及內容": {
      "type": "array",
      "items": {
        "type": "string"
      }
    },
    "這篇文章想溝通的對象": {
      "type": "array",
      "items": {
        "type": "string"
      }
    },
    "發表者角色": {
      "type": "array",
      "items": {
        "type": "string"
      }
    },
    "資料類別": {
      "type": "array",
      "items": {
        "type": "string"
      }
    },
    "學習領域": {
      "type": "array",
      "items": {
        "type": "string"
      }
    },
    "發布時間": {
      "type": "string"
    },
    "期程": {
      "type": "string"
    },
  }
}
```

#### Access Data

##### String

```json
// Access string
// From: 解析資料
// Data: Body 期程
"兩年"

// Access date
body('解析資料')?['期程']
// Result
"兩年"
```

##### Array

```json
// Access array
// From: 解析資料
// Data: Body 學習領域 
[
  "寫作",
  "語言",
  "跨文化"
]

// Access array[0]
body('解析資料')?['學習領域'][0]
// Result
"寫作"
```

## Compose

- Input
  - Data from previous step or create new data.
  - Process data by Azure Data Operation built-in function
- Output: 
  - Processed data

### Example

#### replace

```json
// From: 取出 message
```json
{
  "Name": "妍蜜Yanmi的沙龍",
  "LINK": "https://example.com",
  "提及內容": ["動機", "跨體制", "心路轉變", "學習資源", "申請計畫(動機)"],
  "這篇文章想溝通的對象": ["外界", "家長", "自己"],
  "發表者角色": ["自學生"],
  "資料類別": ["作者/人物"],
  "內容所屬教育階段或形態": ["國中", "個人自學"],
  "學習領域": ["語言", "寫作"],
  "期程": "兩年",
  "篇幅": "內容大約要花5分鐘閱讀",
  "發布時間": "2020-07-20"
}```

// replace ```json and ```
// https://chatgpt.com/share/676534c8-97b4-8008-ad3b-7f8ee62db8b0
replace(replace(outputs('取出_message'), '```json', ''), '```', '')
```

## Select

- Input
  - A vaild Array
  - A key:value to process data
- Output: 
  - A JSON format data for next step

### Example

```json
// Input Data
{
  "Name": "妍蜜Yanmi的沙龍",
  "LINK": "https://example.com/yanmi_blog",
  "提及內容": ["動機", "心路轉變", "申請計畫(內容)", "學習資源"],
  "這篇文章想溝通的對象": ["外界", "家長", "自己"],
}

// make ["動機", "心路轉變"] to [{"name": "動機"}, {"name": "心路轉變"}]
// https://chatgpt.com/share/676d850d-38fc-8008-92a2-6fd0d51ad968
// key: value
"name": @item()
```
