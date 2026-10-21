---
layout: default
title: "K-Work Memo 개인정보 처리방침"
permalink: /chrome/k-work-memo/
---

# K-Work Memo 개인정보 처리방침 (Privacy Policy)

**최종 수정일 / Last Updated**: 2026년 10월 21일 (October 21, 2026)  
**적용 대상 / Applies To**: K-Work Memo Chrome Extension

---

K-Work Memo(이하 "본 확장 프로그램")는 사용자의 개인정보와 프라이버시를 최우선으로 생각합니다.  
본 개인정보 처리방침은 본 확장 프로그램이 사용자 데이터를 어떻게 취급, 저장 및 보호하는지 투명하게 안내하기 위해 작성되었습니다.

> [!NOTE]  
> **핵심 요약 (Summary)**:  
> 본 확장 프로그램은 사용자의 메모와 개인정보를 **개발자의 외부 서버로 일체 전송하거나 수집하지 않습니다**.  
> 모든 데이터는 사용자의 웹 브라우저 로컬 환경(또는 사용자의 Google 계정 동기화 저장소)에만 저장됩니다.

---

## 1. 수집 및 처리하는 정보 항목

본 확장 프로그램은 업무용 메모 관리 기능을 수행하기 위해 다음의 정보만을 사용자의 로컬 환경 내에서 처리합니다.

1. **메모 데이터 (직접 입력)**
   - 내용: 메모 제목, 본문 내용, 지정 태그, 관련 URL, 생성/수정 일시, 메모 고정 여부
   - 목적: 사용자의 메모 저장, 검색, 분류 및 표시
2. **현재 탭 정보 (사용자 동작 시)**
   - 내용: 활성 탭의 URL 및 웹페이지 제목
   - 목적: 에디터에서 사용자가 **'현재 탭 URL 가져오기(Capture URL)' 버튼을 직접 클릭했을 때만** 해당 탭의 제목과 주소를 메모 입력란에 자동으로 채워 넣기 위해 일시적으로 조회합니다.
3. **보안 인증 정보 (PIN)**
   - 내용: 잠금 해제용 4~6자리 PIN 번호
   - 보안 처리: 평문(Plain text)으로 저장되지 않으며, 브라우저 표준 Web Crypto API(SHA-256)를 통해 **단방향 암호화 해시값**으로만 로컬에 저장됩니다.
4. **환경 설정 정보**
   - 내용: 자동 잠금 시간 설정값 (1~60분)

---

## 2. Chrome 확장 프로그램 권한(Permissions) 사용 목적

본 확장 프로그램은 Manifest V3 규정에 따라 서비스 제공에 반드시 필요한 최소한의 권한만을 선언하고 사용합니다.

| 권한 (Permission) | 사용 목적 |
| :--- | :--- |
| `sidePanel` | 사용자가 브라우징 중 언제든 편리하게 메모장을 열람·작성할 수 있도록 브라우저 사이드 패널 UI를 제공합니다. |
| `storage` | 사용자가 작성한 메모 및 설정(PIN 해시, 자동 잠금 시간)을 브라우저 로컬 저장소(`chrome.storage.local`) 및 계정 동기화 저장소(`chrome.storage.sync`)에 저장하고 유지합니다. |
| `idle` | 지정된 시간 동안 마우스나 키보드 입력이 없는 비활동(유휴) 상태를 감지하여, 민감한 업무 메모를 보호하기 위해 앱을 자동으로 잠금 처리합니다. |
| `tabs` | 사용자가 메모 에디터에서 'URL 가져오기' 기능을 실행할 때, 활성화된 탭의 제목 및 URL을 가져와 메모에 간편하게 첨부할 수 있도록 지원합니다. 사용자의 전체 방문 기록이나 비활성 탭 정보에는 접근하지 않습니다. |
| `alarms` | 백그라운드에서 매일 1회 정기 작업을 실행하여, 휴지통에 보관된 지 30일이 지나거나 장기간 미사용된 메모를 사용자가 설정한 정책에 따라 자동 보관/영구 삭제합니다. |

---

## 3. 데이터의 저장, 보관 및 파기

- **저장 위치**: 모든 데이터는 사용자의 로컬 브라우저 저장소(`chrome.storage.local`) 또는 Google 계정과 연계된 브라우저 동기화 저장소(`chrome.storage.sync`)에만 저장됩니다.
- **외부 서버 전송 없음**: 개발자나 제3자가 관리하는 별도의 원격 서버, 데이터베이스, 클라우드로 데이터를 전송하지 않습니다.
- **데이터 파기**:
  - 사용자가 메모를 직접 삭제하거나 휴지통을 비울 경우 즉시 완전히 파기됩니다.
  - 30일 이상 휴지통에 방치된 메모 또는 60일 이상 활동이 없는 메모는 자동 유지보수 로직에 의해 영구 삭제됩니다.
  - 사용자가 브라우저에서 확장 프로그램을 삭제(제거)하면 저장되어 있던 모든 로컬 데이터가 즉시 영구 삭제됩니다.

---

## 4. 제3자 제공 및 외부 통신

- 본 확장 프로그램은 사용자의 어떠한 개인정보나 사용 기록도 **제3자에게 판매, 대여, 공유 또는 제공하지 않습니다**.
- 본 확장 프로그램 내에는 광고(Ad), 사용자 추적기(Tracker), 서드파티 분석 도구(Google Analytics 등)가 일체 포함되어 있지 않습니다.
- 외부 API나 서버와의 네트워크 통신(Network Fetch/XHR)을 전혀 수행하지 않는 완전한 독립형(Stand-alone) 오프라인 확장 프로그램입니다.

---

## 5. 사용자의 권리 및 관리 방법

사용자는 언제든지 본인의 데이터에 대해 다음과 같은 권리를 가집니다.

- **데이터 열람/수정/삭제**: 확장 프로그램 UI를 통해 본인의 메모와 설정을 언제든지 자유롭게 열람, 수정, 삭제할 수 있습니다.
- **데이터 백업 및 복원**: '설정' 화면에서 JSON 형식 파일로 자신의 모든 메모를 로컬 PC로 내보내거나(백업), 백업 파일을 가져와 복원할 수 있습니다.
- **초기화 및 완전 삭제**: 브라우저 확장 프로그램 관리 페이지(`chrome://extensions/`)에서 본 확장 프로그램을 삭제하면 모든 데이터가 깨끗하게 소멸됩니다.

---

## 6. 개인정보 처리방침의 변경

본 개인정보 처리방침은 법령 또는 서비스 기능 변경에 따라 개정될 수 있습니다. 중요한 변경 사항이 발생할 경우 Chrome 웹 스토어 업데이트 및 문서 저장소를 통해 사전 공지합니다.

---

## 7. 문의처 (Contact Us)

본 개인정보 처리방침 또는 확장 프로그램 사용과 관련하여 질문이나 의견이 있으신 경우 아래로 문의해 주시기 바랍니다.

- **프로젝트 저장소 (GitHub)**: [k-work-memo Issues](https://github.com/dasanstudio/k-work-memo/issues)
- **문의 이메일**: `smartup.kr@gmail.com`

---
---

# Privacy Policy (English Version)

**Last Updated**: October 21, 2026  
**Extension Name**: K-Work Memo

K-Work Memo ("the Extension") values and respects your privacy. This Privacy Policy outlines how your information is handled, stored, and protected when you use our Chrome Extension.

### 1. Data Collection and Usage

The Extension operates strictly on a **local-first** approach:
- **No External Transmission**: We do **NOT** transmit, collect, or store any of your personal data, memos, or browsing habits on external servers.
- **Memo Content**: Titles, notes, tags, URLs, and timestamps created by the user are stored strictly inside the browser's local or sync storage (`chrome.storage`).
- **Current Tab Information**: Used only when you explicitly click the "Capture URL" button to auto-fill the active tab's title and URL into the memo fields.
- **Security PIN**: If you configure a lock PIN, it is hashed locally using the Web Crypto API (SHA-256) and never stored in plain text.
- **App Settings**: Preferences such as auto-lock timeout are stored locally.

### 2. Permissions Justification

- **`sidePanel`**: Allows the extension to display its user interface conveniently in the browser side panel.
- **`storage`**: Used to save your memos, PIN hashes, and application preferences locally (`chrome.storage.local` and `chrome.storage.sync`).
- **`idle`**: Detects when the user's computer has been idle for a designated period to automatically lock the memo pad and protect sensitive notes.
- **`tabs`**: Used strictly on-demand to fetch the active tab's URL and title when you click the "Capture URL" button.
- **`alarms`**: Runs periodic background maintenance (once a day) to clean up old or trashed memos based on your retention rules.

### 3. Data Storage & Deletion

- All data resides on your local device or your personal Google Account sync profile provided by Google Chrome.
- You can export, restore, or delete all memos at any time within the Extension.
- Uninstalling the Extension immediately deletes all associated local data.

### 4. Third-Party Sharing and Trackers

- **No Third-Party Sharing**: We do not sell, rent, or trade your data with any third parties.
- **No Analytics / No Trackers**: The Extension does not contain any third-party analytics, ads, or tracking code.

### 5. Contact Information

For any inquiries, bug reports, or privacy concerns regarding K-Work Memo, please reach out via:
- **GitHub Issues**: [k-work-memo Repository](https://github.com/dasanstudio/k-work-memo/issues)
- **Email**: `smartup.kr@gmail.com`
