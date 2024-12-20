# 2024/12/20 星河計劃 HTTP Response Data Operation debug  

## Goal

Using Azure Logic App data operation to process HTTP Response from GPT Module.

## Data

```json
{
  "choices": [
    {
      "finish_reason": "stop",
      "index": 0,
      "message": {
        "content": "```json\n{\n  \"Name\": \"妍蜜Yanmi的沙龍\",\n  \"LINK\": \"https://example.com\",\n  \"提及內容\": [\"自學\", \"動機\", \"心路轉變\", \"申請計畫(方式)\", \"申請計畫(內容)\"],\n  \"這篇文章想溝通的對象\": [\"外界\", \"家長\"],\n  \"發表者角色\": \"自學生\",\n  \"資料類別\": [\"內容\", \"網站\"],\n  \"內容所屬教育階段或形態\": [\"國中\", \"個人自學\"],\n  \"學習領域\": [\"語言\", \"國際教育\", \"課外活動\"],\n  \"發布時間\": \"2020-07-20\",\n  \"期程\": \"三年\",\n  \"篇幅\": \"5分鐘\"\n}\n```",
        "refusal": null,
        "role": "assistant"
      }
    }
  ],
  "created": 1734682944,
  "id": "", // Sensitive data
  "model": "gpt-4o-2024-05-13",
  "object": "chat.completion",
  "system_fingerprint": "", // Sensitive data
  "usage": {
    "completion_tokens": 186,
    "completion_tokens_details": {
      "accepted_prediction_tokens": 0,
      "audio_tokens": 0,
      "reasoning_tokens": 0,
      "rejected_prediction_tokens": 0
    },
    "prompt_tokens": 5182,
    "prompt_tokens_details": {
      "audio_tokens": 0,
      "cached_tokens": 0
    },
    "total_tokens": 5368
  }
}
```

## Details

### Extract `choice` element

Operation: Compose

#### Parse the JSON

- Use the Parse JSON action to parse the output from the HTTP request body. This step makes the JSON data accessible for subsequent actions.  
- Provide a sample of the JSON structure in the Schema field (can be generated using a sample payload).

```json
{
  "type": "object",
  "properties": {
    "choices": {
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "finish_reason": { "type": "string" },
          "index": { "type": "integer" },
          "message": {
            "type": "object",
            "properties": {
              "content": { "type": "string" },
              "role": { "type": "string" }
            }
          }
        }
      }
    },
    "created": { "type": "integer" },
    "id": { "type": "string" },
    "model": { "type": "string" },
    "object": { "type": "string" },
    "system_fingerprint": { "type": "string" },
    "usage": {
      "type": "object",
      "properties": {
        "completion_tokens": { "type": "integer" },
        "prompt_tokens": { "type": "integer" },
        "total_tokens": { "type": "integer" }
      }
    }
  }
}
```

### Compose Action to Extract the First choice

- Add a Compose action after the Parse JSON step.  
- In the Inputs field of the Compose action, use the following expression:

```json
body('Parse_JSON')?['choices'][0]

// If you want specific properties within the first choice (e.g., message.content), you can further extend the expression:

body('Parse_JSON')?['choices'][0]['message']['content']

// The last step named "Parse Response from GPT"

body('Parse_Response_from_GPT')?['choices'][0]['message']['content']
```

- body('Parse_JSON'): Accesses the parsed JSON body from the previous step.
- ?['choices']: Navigates to the choices array.
- [0]: Retrieves the first element of the array.

#### Result

```json
```json
{
  "Name": "妍蜜Yanmi的沙龍",
  "LINK": "https://example.com",
  "提及內容": ["自學", "動機", "心路轉變", "申請計畫(方式)", "申請計畫(內容)"],
  "這篇文章想溝通的對象": ["外界", "家長"],
  "發表者角色": "自學生",
  "資料類別": ["內容", "網站"],
  "內容所屬教育階段或形態": ["國中", "個人自學"],
  "學習領域": ["語言", "國際教育", "課外活動"],
  "發布時間": "2020-07-20",
  "期程": "三年",
  "篇幅": "5分鐘"
}
// Should be ```
\```
```

### Remove ````json` tag

Operation: Compose  

- Add another Compose action to clean up the extracted data.
- Use the replace() function to remove the unwanted characters:

```json
// GPT response

replace(replace(outputs('Compose'), '```json\n', ''), '\n```', '')

// The last step named "Pick `Message` from `Choice".
// The last line of code don't have "\n", so '\n```' might not works.
// The first line have a new line charater need to be replaced.

replace(replace(outputs('Pick_`Message`_from_`Choice`'), '```json\n', ''), '```', '')

```

- outputs('Compose'): Refers to the output of the first Compose action.
- replace(outputs('Compose'), '```json\n', ''): Removes the opening backticks and json.
- replace(..., '\n```', ''): Removes the closing backticks.

#### Result

```json
{
  "Name": "妍蜜Yanmi的沙龍",
  "LINK": "https://example.com",
  "提及內容": ["自學", "動機", "心路轉變", "申請計畫(方式)", "申請計畫(內容)"],
  "這篇文章想溝通的對象": ["外界", "家長"],
  "發表者角色": "自學生",
  "資料類別": ["內容", "網站"],
  "內容所屬教育階段或形態": ["國中", "個人自學"],
  "學習領域": ["語言", "國際教育", "課外活動"],
  "發布時間": "2020-07-20",
  "期程": "三年",
  "篇幅": "5分鐘"
}
```

### Parse the cleaned JSON

Operation: Parse JSON  

- Put previous output into Parse JSON Block for further Data Process

```json
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
            "type": "string"
        },
        "資料類別": {
            "type": "array",
            "items": {
                "type": "string"
            }
        },
        "內容所屬教育階段或形態": {
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
        "篇幅": {
            "type": "string"
        }
    }
}

## Reference

