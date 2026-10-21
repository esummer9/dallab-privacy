---
layout: default
title: "K-Calendar 개인정보 처리방침"
permalink: /chrome/k-calendar/
---

# K-Calendar 개인정보 처리방침 (Privacy Policy)

**최종 수정일 / Last Updated**: 2026년 10월 21일 (October 21, 2026)  
**적용 대상 / Applies To**: K-Calendar Chrome Extension (v1.3.3 이상)  
**제공자 / Developer**: SummerApps (esummer.lee@gmail.com)  
**저장소 / Repository**: [https://github.com/esummer9/chrome-ext_k-calendar](https://github.com/esummer9/chrome-ext_k-calendar)

---

K-Calendar(이하 "본 확장 프로그램")는 사용자의 개인정보와 프라이버시를 매우 소중하게 생각하며, 관련 법령 및 Google Chrome 웹 스토어 개발자 프로그램 정책을 준수합니다.  
본 개인정보 처리방침은 본 확장 프로그램이 사용자의 데이터를 어떻게 취급, 처리 및 보호하는지 투명하게 안내하기 위해 작성되었습니다.

> [!NOTE]  
> **핵심 요약 (Summary)**:  
> 본 확장 프로그램은 사용자를 식별할 수 있는 어떠한 개인정보도 **개발자의 외부 서버로 수집·전송·저장하지 않습니다**.  
> 모든 사용자 환경설정은 **사용자 기기의 웹 브라우저 내부 로컬 저장소(`chrome.storage.local`)에만 안전하게 저장**됩니다.

---

## 1. 수집 및 처리하는 정보 항목

본 확장 프로그램은 달력 표시, 공휴일 및 날씨 정보 제공, 날짜 클립보드 복사 기능을 수행하기 위해 다음 항목만을 사용자의 로컬 환경 내에서 최소한으로 처리합니다.

### 1) 환경 설정 데이터 (로컬 브라우저 저장)
- **처리 항목**: 
  - 테마 설정값 (기본 / 유리모피즘 테마)
  - 공휴일 목록 표시 여부 (`holidaysVisible`)
  - 클립보드 복사 시 경과일/D-Day 포함 여부 (`copyDday`)
  - 날씨 표시 활성화 여부 및 선택된 지역 정보 (지역명, 위도, 경도 좌표)
- **처리 목적**: 사용자 맞춤 설정 유지 및 브라우저 재실행 시 설정 복원
- **보관 위치**: 사용자의 기기 브라우저 내부 저장소(`chrome.storage.local`)에만 저장되며, 외부 서버로 전송되지 않습니다.

### 2) 클립보드 데이터 (일방향 쓰기)
- **처리 항목**: 사용자가 선택한 날짜 포맷 문자열 (예: `2026-05-05 (화) +125 [어린이날]`)
- **처리 목적**: 사용자가 복사 버튼을 클릭했을 때 시스템 클립보드에 해당 텍스트를 기록(`clipboardWrite`)
- **보호 조치**: 사용자의 기존 클립보드 데이터를 읽거나(Read), 감시하거나, 외부로 전송하지 않습니다.

### 3) 외부 API 통신 데이터 (기능 제공 목적의 일시적 요청)
- **대한민국 공공데이터포털 (apis.data.go.kr)**
  - 공휴일 정보: 연도(`solYear`) 및 월(`solMonth`) 파라미터만 전송하여 해당 월의 한국 공휴일/대체공휴일 정보를 실시간 조회합니다.
  - 기상청 단기예보 정보: 날씨 기능을 켰을 때, 사용자가 지정한 지역의 격자 좌표(nx, ny)와 기준 시간만을 전송하여 날씨 예보를 조회합니다.
- **OpenStreetMap Nominatim (nominatim.openstreetmap.org)**
  - 사용자가 날씨 설정 화면에서 특정 지역을 검색할 때, 입력한 검색어(예: "서울", "강남구")만을 전송하여 해당 지역의 위경도 좌표를 조회합니다.
- **공통 사항**: 상기 모든 API 호출 시 사용자의 개인 식별 정보, IP 주소 기록, 쿠키 등은 개발자에게 수집되거나 저장되지 않습니다.

---

## 2. Chrome 확장 프로그램 권한(Permissions) 사용 목적

본 확장 프로그램은 기능 제공에 반드시 필요한 최소한의 권한(Least Privilege)만을 요청하며, 각각의 용도는 다음과 같습니다.

| 권한 항목 (Permission) | 사용 목적 (Purpose) |
| :--- | :--- |
| `clipboardWrite` | 사용자가 날짜 패널 또는 휴일 카드에서 복사 버튼을 눌렀을 때, 포맷팅된 날짜 텍스트를 시스템 클립보드에 복사하기 위해 사용합니다. (클립보드 읽기 권한 없음) |
| `sidePanel` | 사용자가 웹 서핑 중에도 브라우저 우측 사이드 패널에서 언제든 편리하게 달력과 날짜 도구를 열어볼 수 있도록 지원합니다. |
| `storage` | 사용자가 지정한 테마, 공휴일 표시 옵션, 복사 포맷 옵션, 날씨 위치 설정값을 브라우저 로컬 저장소(`chrome.storage.local`)에 저장하여 유지합니다. |
| `host_permissions` | 공공데이터포털(`https://apis.data.go.kr/*`)의 공휴일 및 기상청 예보 API를 호출하고, OpenStreetMap(`https://nominatim.openstreetmap.org/*`)의 위치 검색 API를 호출하기 위해 필요합니다. |

---

## 3. 데이터의 저장, 보관 및 파기

1. **저장 위치**: 모든 설정 데이터는 사용자의 로컬 컴퓨터 브라우저 내부 저장소(`chrome.storage.local`)에만 보관됩니다.
2. **외부 서버 전송 없음**: 개발자는 별도의 백엔드 데이터베이스나 클라우드 서버를 운영하지 않으며, 사용자의 어떠한 데이터도 원격으로 수집하지 않습니다.
3. **데이터 파기**: 
   - 사용자는 확장 프로그램 설정 팝업에서 언제든 설정값을 변경하거나 초기화할 수 있습니다.
   - Chrome 브라우저에서 본 확장 프로그램을 삭제(제거)할 경우, 로컬에 저장되어 있던 모든 데이터는 즉시 영구적으로 자동 파기됩니다.

---

## 4. 제3자 제공 및 외부 위탁

본 확장 프로그램은 사용자의 어떠한 정보도 제3자에게 판매, 대여, 공유 또는 마케팅 목적으로 제공하지 않습니다.

---

## 5. 이용자의 권리 및 행사 방법

사용자는 언제든지 본 확장 프로그램의 사용을 중단하거나 브라우저에서 확장 프로그램을 제거함으로써 모든 데이터의 처리를 중단하고 저장된 데이터를 영구히 파기할 수 있습니다.

---

## 6. 개인정보 보호책임자 및 문의처

본 확장 프로그램의 개인정보 처리와 관련하여 문의사항이나 의견이 있으신 경우 아래 연락처로 문의해 주시기 바랍니다.

- **개발자/제공자**: SummerApps
- **담당자 이메일**: esummer.lee@gmail.com
- **프로젝트 저장소 (GitHub Issues)**: [https://github.com/esummer9/chrome-ext_k-calendar/issues](https://github.com/esummer9/chrome-ext_k-calendar/issues)

---

## 7. 개인정보 처리방침의 변경

본 개인정보 처리방침은 법령, 관련 정책 또는 확장 프로그램 기능 변경에 따라 개정될 수 있습니다. 중요한 변경 사항이 발생할 경우 버전 업데이트 로그 및 GitHub 저장소를 통해 공지할 것입니다.

<br>

---
---

<br>

# Privacy Policy for K-Calendar Chrome Extension

**Last Updated**: October 21, 2026  
**Applies To**: K-Calendar Chrome Extension (v1.3.3 or higher)  
**Developer**: SummerApps (esummer.lee@gmail.com)  
**Repository**: [https://github.com/esummer9/chrome-ext_k-calendar](https://github.com/esummer9/chrome-ext_k-calendar)

---

SummerApps ("we", "our", or "us") respects your privacy and is committed to protecting it.  
This Privacy Policy explains how **K-Calendar** ("the Extension") handles, stores, and protects user data in compliance with the Google Chrome Web Store Developer Program Policies.

> [!NOTE]  
> **Key Summary**:  
> The Extension **does NOT collect, transmit, or store any personally identifiable information (PII) on any external or developer-owned server**.  
> All user preferences and configurations are stored **exclusively within your local browser storage (`chrome.storage.local`)**.

---

### 1. Data Collected and Processed

The Extension processes the minimal amount of data necessary to provide calendar navigation, South Korean holiday data, weather forecasts, and date copy functionality:

1. **User Preferences (Stored Locally)**:
   - UI Theme selection (Default / Glassmorphism)
   - Visibility settings for holidays (`holidaysVisible`)
   - Option to include elapsed day count / D-Day in copied text (`copyDday`)
   - Weather feature toggle and selected region coordinates (region name, latitude, longitude)
   - *Storage Location*: Stored exclusively in `chrome.storage.local` on your local device.
2. **Clipboard Data (One-way Write Only)**:
   - When you click a copy button for a date or holiday, formatted text (e.g., `2026-05-05 (화) +125 [어린이날]`) is written to your system clipboard (`clipboardWrite`).
   - The Extension **never reads, inspects, or transmits** existing clipboard contents.
3. **External API Requests (For Core Features Only)**:
   - **Korea Public Data Portal (apis.data.go.kr)**: Queries official Korean statutory holidays and KMA weather forecasts using date and grid coordinates.
   - **OpenStreetMap Nominatim (nominatim.openstreetmap.org)**: Queries geocoordinates when you search for a location name in the weather settings.
   - *No personal identification or browsing history is sent with these queries.*

---

### 2. Chrome Extension Permissions

The Extension requests only the minimum required permissions to function properly:

| Permission | Purpose |
| :--- | :--- |
| `clipboardWrite` | Enables writing the formatted date and holiday information to the system clipboard upon user click. |
| `sidePanel` | Allows the calendar interface to open seamlessly within the Chrome browser's side panel. |
| `storage` | Saves user preferences (theme, weather coordinates, copy options) locally in `chrome.storage.local`. |
| `host_permissions` | Required to communicate with `apis.data.go.kr` (holiday & weather data) and `nominatim.openstreetmap.org` (location search). |

---

### 3. Data Storage, Retention, and Deletion

- **Storage**: All data is stored locally on the user's device via `chrome.storage.local`.
- **No Remote Servers**: We do not maintain remote databases or servers. No user data is sent to external servers for tracking or analytics.
- **Deletion**: All stored data can be reset in the extension settings or permanently removed by uninstalling the extension from Chrome.

---

### 4. Third-Party Sharing

We do not sell, rent, trade, or otherwise share your data with third parties for commercial or marketing purposes.

---

### 5. Contact Information

If you have questions or concerns regarding this Privacy Policy, please contact:

- **Developer**: SummerApps
- **Email**: esummer.lee@gmail.com
- **Issue Tracker**: [https://github.com/esummer9/chrome-ext_k-calendar/issues](https://github.com/esummer9/chrome-ext_k-calendar/issues)
