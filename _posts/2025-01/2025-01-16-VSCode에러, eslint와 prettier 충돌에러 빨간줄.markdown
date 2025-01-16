---
title: [VSCode에러, eslint와 prettier 충돌 해결]
author: hanni
date: 2025-01-16 09:00:00 +0800
categories: TIL
tags: [NestJS, eslint, prettier]
---

----------------------------------------------------------------------------

NestJS,TypeScript로 프로젝트를 진행하면서 VScode에 빨간줄이 넘쳐나게 되었다. 여러가지 방법을 시도해본 과정에 대해서 가장 효과적으로 적용되었던 방법을 기록해두려고 한다.

1. 처음 시도 typescript와 버전에 따른 문제인가? <br>
- VScode에서 F1 -> typecsript이라고 치면 버전 선택 부분이 나오는데 `VS code의 버전 사용`을 클릭

2. `eslintrc.json` 설정<br>
- rules 부분에 아래 코드 삽입<br>
```
"rules": {
    "prettier/prettier": [
    "error",
    {
      "endOfLine": "auto"
    }
  ], 
```
### 🔓 이렇게 설정하는 이유는? 
- endOfLine: 'auto'는 운영 체제의 줄바꿈 방식을 자동으로 감지하고 맞추도록 설정합니다.<br>
- 예를 들어, Windows에서는 CRLF 방식, macOS와 Linux에서는 LF 방식이 기본인데, 이 규칙이 없으면 서로 다른 줄바꿈 방식 때문에 ESLint가 경고를 표시할 수 있습니다.<br>
- 이 설정으로 Prettier가 줄바꿈 방식을 자동으로 조정해 ESLint와 충돌하지 않게 됩니다. <br>

### 💡 결론
같이 프로젝트를 하는 팀원들은 운영체제가 macOS인데
나는 Windows라 줄바꿈 방식이 다르다보니 생긴 문제였다.
Window라.. 슬프군.....😂 

