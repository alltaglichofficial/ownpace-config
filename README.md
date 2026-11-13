# ownpace-config

OWNPACE 앱 홈 화면의 **팝업 배너**를 여기서 바꿉니다.
이 저장소의 `promo.json`을 고치면, 앱을 새로 배포하지 않아도 몇 분 안에 모든 사용자에게 적용됩니다.

> 이 저장소는 공개입니다. 비밀번호, 키, 개인정보는 절대 올리지 마세요.

## 고치는 방법

1. 위 파일 목록에서 `promo.json`을 누릅니다.
2. 오른쪽 위 연필(✏️) 버튼을 누릅니다.
3. 아래 표를 보고 값을 고칩니다.
4. 오른쪽 위 초록색 **Commit changes** 버튼을 두 번 눌러 저장합니다.

## promo.json 항목

| 항목 | 뜻 | 예 |
| --- | --- | --- |
| `enabled` | 배너를 띄울지. `true` = 띄움, `false` = 안 띄움 | `false` |
| `imageSrc` | 배너 이미지. 이 저장소에 올린 파일 이름, 또는 `https://`로 시작하는 이미지 주소 | `"banner.png"` |
| `actionType` | 배너를 눌렀을 때. `"none"` = 아무 일 없음, `"internal"` = 앱 안 화면, `"https"` = 웹 주소 열기 | `"https"` |
| `actionTarget` | 갈 곳. `internal`이면 `main.html` · `calendar.html` · `settings.html` · `profile.html` 중 하나, `https`면 웹 주소, `none`이면 `null` | `"https://example.com/event"` |
| `altText` | 화면 읽기 기능이 읽어 주는 배너 설명 | `"가을 이벤트 안내"` |

### 예: 배너 끄기

```json
{
  "enabled": false,
  "imageSrc": "banner.svg",
  "actionType": "none",
  "actionTarget": null,
  "altText": ""
}
```

### 예: 새 이미지 + 누르면 웹페이지 열기

```json
{
  "enabled": true,
  "imageSrc": "event-2026-12.png",
  "actionType": "https",
  "actionTarget": "https://example.com/event",
  "altText": "12월 이벤트 안내"
}
```

## 이미지 바꾸기

1. 저장소 첫 화면에서 **Add file → Upload files**를 누릅니다.
2. 이미지 파일을 끌어다 놓고 **Commit changes**를 누릅니다.
3. `promo.json`의 `imageSrc`를 그 파일 이름으로 바꿉니다.

- 파일 형식: `png`, `jpg`, `webp`, `svg`
- 파일 이름: 영어·숫자·`-`·`_`만 (띄어쓰기·한글 불가). 예: `event-2026-12.png`
- 권장 크기: 가로 720 × 세로 900 (세로로 긴 4:5), 1MB 이하
- 같은 이름으로 덮어쓰는 것보다 **새 이름으로 올리고 `imageSrc`를 바꾸는 것**이 바로 적용됩니다.

## 주의

- 쉼표(`,`)와 따옴표(`"`)를 지우면 파일이 깨집니다. 깨진 경우 앱은 마지막으로 정상이던 설정(없으면 앱에 들어 있는 기본 배너)을 씁니다.
- 저장 후 적용까지 5분쯤 걸릴 수 있습니다.
- 사용자가 배너를 닫으면 앱을 다시 켤 때까지 다시 뜨지 않습니다.
