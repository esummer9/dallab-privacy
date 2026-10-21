---
layout: default
title: "K-Calendar 개인정보 처리방침"
permalink: /chrome/k-calendar/
---

# K-Calendar 크롬 익스텐션 문제점 수정 및 개선 계획

K-Calendar 크롬 익스텐션의 코드 검토 결과 발견된 보안, 크롬 권한, UI 버그 및 JS 날짜 계산 오동작 문제를 보완하기 위한 기술 변경 계획입니다.

## User Review Required

> [!IMPORTANT]
> - `config.js`의 공공데이터포털 API Key 처리를 원본(디코딩된 키) 기준으로 통일하고 `encodeURIComponent`로 일관되게 암호화/호출하도록 수정합니다.
> - OpenStreetMap Nominatim API 허용을 위해 `manifest.json` 권한 목록에 호스트 주소가 추가됩니다.

## Proposed Changes

---

### Manifest & Background Component

#### [MODIFY] [manifest.json](file:///d:/Users/workspace/apps/chrome-ext_k-calendar/manifest.json)
- `host_permissions` 배열에 `"https://nominatim.openstreetmap.org/*"` 추가.

#### [MODIFY] [background.js](file:///d:/Users/workspace/apps/chrome-ext_k-calendar/background.js)
- `chrome.runtime.onInstalled` 이벤트 리스너 내부로 `chrome.sidePanel.setPanelBehavior` 설정 이동.

---

### Styling & Layout Component

#### [MODIFY] [popup.css](file:///d:/Users/workspace/apps/chrome-ext_k-calendar/popup.css)
- `#confettiCanvas`에 대한 `position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; pointer-events: none; z-index: 9999;` CSS 규칙 추가.

---

### Extension Logic Component

#### [MODIFY] [config.js](file:///d:/Users/workspace/apps/chrome-ext_k-calendar/config.js) / [config.js.sample](file:///d:/Users/workspace/apps/chrome-ext_k-calendar/config.js.sample)
- `HOLIDAY_API_KEY`와 `WEATHER_API_KEY` 사용 방식 일관성 정리.
- `config.js.sample` 주석 및 필수 키 항목 정돈.

#### [MODIFY] [popup.js](file:///d:/Users/workspace/apps/chrome-ext_k-calendar/popup.js)
1. **API Key 인코딩 통일**:
   - `fetchHolidays()`에서 `HOLIDAY_API_KEY` 전달 시 이미 인코딩된 키와 원본 키 모두 대응하도록 `encodeURIComponent(decodeURIComponent(...))` 처리.
2. **달력 월 이동 버그 수정**:
   - `prevBtn` / `nextBtn` 클릭 시 `currentDate.setDate(1)`을 먼저 실행 후 `setMonth`를 적용하여 31일 선택 상태에서 이전/다음 달 이동 시 발생하는 월 오버플로우 문제 수정.
3. **Nominatim API fetch 수정**:
   - `fetch` 옵션에서 브라우저 금지 헤더인 `User-Agent` 설정 제거.
4. **`renderForecast` 및 예보 페이징 구조 개선**:
   - `btnToggleForecast`에서 `renderForecast` 호출 시 객체 대신 `lastWeatherForecastList` 배열만 깨끗하게 전달하도록 리팩토링.
5. **에러 알림 UX 개선**:
   - `fetchWeather` 캐치 블록의 화면 차단 `alert()` 대신 콘솔 기록 및 기존 UI 알림 메시지/토스트로 에러 안내.

## Verification Plan

### Manual Verification
1. `chrome://extensions/` 페이지에서 **K-Calendar** 익스텐션 새로고침 (Unpacked Reload).
2. **월 이동 테스트**: 31일(예: 3월 31일, 5월 31일) 상태에서 이전 달/다음 달 클릭 시 정확히 해당 월의 1일로 정상 이동하는지 확인.
3. **폭죽 효과(Confetti) 테스트**: 날짜 복사 버튼 클릭 시 폭죽 애니메이션이 레이아웃을 왜곡하지 않고 마우스 클릭을 방해하지 않는지 확인.
4. **날씨 지역 검색 테스트**: 설정 탭에서 동/지역 이름(예: 역삼동) 검색 시 Nominatim API 결과가 정상 출력되고 콘솔 헤더 경고가 없는지 확인.
5. **공휴일/날씨 API 호출 테스트**: 휴일 및 날씨 정보가 문제없이 정상적으로 불러와지는지 확인.
