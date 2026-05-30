# Archiv-iOS
[iOS 프로그래밍 기말프로젝트] 2392112_ 유예원


█████╗ ██████╗  ██████╗██╗  ██╗██╗██╗   ██╗
██╔══██╗██╔══██╗██╔════╝██║  ██║██║██║   ██║
███████║██████╔╝██║     ███████║██║██║   ██║
██╔══██║██╔══██╗██║     ██╔══██║██║╚██╗ ██╔╝
██║  ██║██║  ██║╚██████╗██║  ██║██║ ╚████╔╝ 
╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝╚═╝  ╚═╝╚═╝  ╚═══╝  
📍 나만의 장소와 기록을 담는 공간, 로케이션 아카이빙 플랫폼

    

방문했던 특별한 장소를 나만의 감성으로 기록하고 싶으신가요?
Archiv가 당신의 발자취와 핫플레이스를 아름답게 보관해 드릴게요 📸
---

## 🎬 3분 시연 영상 (정보성)
[![Archiv 시연 영상](https://img.shields.io/badge/YouTube-시연%20영상%20보러가기-red?style=for-the-badge&logo=youtube)]([여기에_유튜브_동영상_링크를_넣으세요])
* ※ 동영상 총 길이: [예: 2분 50초] (3분 30초 초과 시 감점 반영 확인)*

---

## 1. 프로젝트 개요 (효용성 & 정보성)
- **기획 의도**: 여행이나 일상 속 방문 이후, 스마트폰 갤러리의 사진을 보며 "여기가 정확히 어떤 카페(식당)였지?" 하고 장소명을 잊어버리는 페인 포인트(Pain Point)에서 출발했습니다.
- **핵심 효용 가치**: 유저가 다녀온 공간을 인스타그램 감성의 피드로 아카이빙하고, 정확한 정보를 네이버 API로 박제하며, '가고 싶은 곳'과 '다녀온 곳'을 영리하게 분리하여 개인의 공간 취향을 자산화합니다.

---

## 2. 핵심 기능 및 UI/UX (직관성, 시각디자인, 피드백)

| 1. 메인 피드 (My Archive) | 2. 투트랙 지도 (Map View) | 3. 무한 스크롤 탐색 (Discovery) |
| :---: | :---: | :---: |
| ![메인피드_피그마_캡처본_링크_혹은_삭제] | ![지도_피그마_캡처본_링크_혹은_삭제] | ![탐색_피그마_캡처본_링크_혹은_삭제] |
| **사진 중심의 1:1 정방형 격자 UI**<br>텍스트를 배제하고 이미지를 강조하여 감성적인 포토북 느낌의 시각 디자인 구현 | **상단 토글 제어 기반 지도**<br>하나의 맵 안에서 '내 발자취'와 '위시리스트' 핀을 부드러운 애니메이션과 함께 스위칭 | **2:3 세로형 카드 레이아웃**<br>시각적 몰입감을 극대화한 탐색 탭과 원터치 위시리스트 저장 기능 |

### 🛠 세부 구현 기능 (완결성)
- **Naver 지역 검색 Open API 연동**: 상호명 입력 시 실시간 주소 및 카테고리 데이터를 비동기(`URLSession`)로 받아와 구조체(`Codable`)에 매칭.
- **iOS PhotosUI & MapKit 활용**: 안전한 미디어 피커(PHPicker) 사용 및 애플 순정 지도 위에 사용자 맞춤형 어노테이션(Annotation) 핀 배치.
- **데이터 페이지네이션(Pagination)**: 탐색 탭 무한 스크롤 시 스크롤 위치를 감지하여 데이터를 분할 로딩함으로써 앱 성능 최적화.

---

## 3. 기술 스택 (Technical Stack)
- **Language & Framework**: Swift, SwiftUI / UIKit
- **UI Kit**: MapKit, PhotosUI
- **Backend & DB**: Supabase (PostgreSQL), Supabase Storage (이미지 서버)
- **Open API**: Naver Local Search API

---

## 4. 앱 사용성 평가 지표 대응 (학습용이성, 라벨링, 오류 정정)
- **라벨링 & 학습용이성**: 사용자가 직관적으로 이해할 수 있는 용어([내 발자취], [위시리스트])를 채택하고, 대중적인 인스타그램의 인터페이스를 벤치마킹하여 별도의 설명서 없이 즉시 조작할 수 있도록 설계했습니다.
## 5. 파일 구조

- Archiv/
├── Models/
│   └── Post.swift
├── Services/
│   ├── PostStore.swift       ← localStore.ts 역할
│   └── KakaoSearchService.swift
├── Views/
│   ├── ContentView.swift     ← App.tsx 역할
│   ├── AuthView.swift
│   ├── ArchiveView.swift
│   ├── MapView.swift
│   ├── DiscoveryView.swift
│   └── UploadView.swift
└── ArchivApp.swift
- **피드백 & 오류 정정**: 
  - 탐색 탭에서 '저장' 버튼 터치 시 **햅틱 피드백(진동)**과 토스트 메시지를 제공하여 조작 상황을 명확히 인지시킵니다.
  - 검색 결과가 없거나 네트워크 연결이 끊겼을 때 예외 처리를 통해 "장소를 찾을 수 없습니다"라는 명확한 Alert 창을 띄워 시스템의 실수를 방지합니다.
✨ 주요 기능


| 기능 | 설명 | 상태 |
| :--- | :--- | :--- |
| **🔐 로그인/회원가입** | Supabase Auth 기반 이메일 인증 및 LocalStorage 자동 로그인 | ✅ 완료 |
| **🗂 내 아카이브** | 기록한 장소들을 3열 그리드로 표시 및 상세 정보 슬라이드 업 | ✅ 완료 |
| **🗺 풀스크린 지도** | MapKit 기반 지도. 세그먼트 컨트롤로 내 발자취 / 위시리스트 핀 전환 | ✅ 완료 |
| **🔍 장소 검색/등록** | 네이버 플레이스 스타일 장소 검색, 사진, 별점, 한 줄 메모 업로드 | ✅ 완료 |
| **🧭 탐색 및 공유** | 다른 유저들의 핫플레이스 피드 탐색 및 즉시 위시리스트(북마크) 추가 | ✅ 완료 |


📱 앱 화면

| 회원가입 / 로그인 | 내 아카이브 | 탐색 | 지도 | 장소 기록 (+) |
| :---: | :---: | :---: | :---: | :---: |
| [이미지 삽입] | [이미지 삽입] | [이미지 삽입] | [이미지 삽입] | [이미지 삽입] |
| Supabase Auth | 3열 그리드 UI | 카드 피드 & 북마크 | MapKit & 인터랙티브 마커 | Naver Local API 검색 |


🛠 기술 스택


**📱 Client**
* **Language:** Swift
* **UI:** SwiftUI
* **Map:** Apple MapKit
* **Architecture:** MVVM (ObservableObject, EnvironmentObject)

**🔥 Backend (Supabase) & API**
* **Auth:** Supabase Authentication (익명 로그인 & 이메일 폴백)
* **Storage:** Supabase Storage (장소 사진 업로드) / LocalStorage
* **Open API:** Naver Local Search API, Nominatim (OSM 폴백)

**🔧 Tools**
* **Version Control:** Git / GitHub
* **IDE:** Xcode


🗂 프로젝트 구조


Archiv_yewon/
├── ArchivApp.swift
├── Views/
│   ├── ContentView.swift      # 메인 탭바 및 라우팅
│   ├── AuthView.swift         # 로그인 및 회원가입
│   ├── ArchiveView.swift      # 내 아카이브 (3열 그리드)
│   ├── MapTabView.swift       # 풀스크린 지도 (내 발자취/위시리스트)
│   ├── DiscoveryView.swift    # 전체 피드 탐색
│   └── UploadView.swift       # 사진 첨부, 네이버 장소 검색, 기록
├── Services/
│   ├── PostStore.swift        # 상태 관리 및 DB 연동 (ObservableObject)
│   └── KakaoSearchService.swift / Naver API # 외부 검색 API 로직
├── Models/
│   └── Post.swift             # Identifiable, Codable, Equatable 데이터 모델
└── Assets.xcassets/           # 런처 아이콘 및 이미지 리소스


🗃 데이터 구조


users/{userId} (Local & Supabase Auth)
├── id, email, name, password
└── createdAt: Timestamp

posts/{postId} (PostStore)
├── id, userId, userName
├── imageData: Data / URL
├── placeName, category
├── address, roadAddress
├── lat, lng (Double)
├── memo, rating (Int)
└── createdAt: Timestamp


🌿 브랜치 전략 (1인 프로젝트)


main              배포 및 최종본 브랜치
 └── dev          기능 개발 및 테스트 통합 브랜치
      ├── feature/auth         Supabase 로그인 및 사용자 인증
      ├── feature/map          MapKit 연동 및 마커 커스텀
      ├── feature/upload       Naver API 검색 및 데이터 저장
      └── feature/ui-polishing UI 디테일 및 뷰 트랜지션 애니메이션


🗓 개발 기간


2026.05  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━  2026.06

  1주차          2주차          3주차          4주차
  기획 및 UI     MapKit 연동    Naver API    Supabase 연동
  구조 설계      마커 구현      장소 검색    버그 픽스 & 배포
  ✅ 완료        ✅ 완료        ✅ 완료        ✅ 완료


👤 Developer


* **유예원** (한성대학교 캡스톤 디자인)
* **Role:** iOS App Design, Frontend Architecture, API Integration & Backend Setup
