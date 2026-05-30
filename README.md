<div align="center">

<pre>
 █████╗ ██████╗  ██████╗██╗  ██╗██╗██╗   ██╗
██╔══██╗██╔══██╗██╔════╝██║  ██║██║██║   ██║
███████║██████╔╝██║     ███████║██║██║   ██║
██╔══██║██╔══██╗██║     ██╔══██║██║╚██╗ ██╔╝
██║  ██║██║  ██║╚██████╗██║  ██║██║ ╚████╔╝ 
╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝╚═╝  ╚═╝╚═╝  ╚═══╝ 
</pre>

**나만의 감성 장소를 아카이빙하는 iOS 플랫폼**

![Swift](https://img.shields.io/badge/Swift-FA7343?style=flat-square&logo=swift&logoColor=white)
![SwiftUI](https://img.shields.io/badge/SwiftUI-0D96F6?style=flat-square&logo=swift&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=flat-square&logo=supabase&logoColor=white)
![MapKit](https://img.shields.io/badge/MapKit-000000?style=flat-square&logo=apple&logoColor=white)

</div>

---

## 📖 프로젝트 소개

여행이나 일상 속에서 방문했던 장소들, 사진은 남아 있는데 "여기가 정확히 어떤 카페였지?" 하고 잊어버린 경험, 한 번쯤 있으셨나요?

**Archiv**는 그 페인 포인트에서 출발한 감성 장소 기록 앱입니다.
사진 한 장으로 시작해, 네이버 API로 장소 정보를 박제하고, 내가 다녀온 곳과 가고 싶은 곳을 하나의 앱에서 스마트하게 관리합니다.

> 인스타그램 감성의 피드 + 정확한 장소 정보 + 지도 기반 시각화

---

## ✨ 주요 기능

| 기능 | 설명 |
|------|------|
| 📷 **감성 피드 아카이브** | 사진 중심의 1:1 정방형 그리드 UI로 방문 장소를 포토북처럼 기록 |
| 🗺️ **토글 지도 뷰** | '내 발자취'와 '위시리스트' 핀을 하나의 지도에서 애니메이션과 함께 스위칭 |
| 🔍 **장소 검색 연동** | 네이버 지역 검색 API로 상호명 입력 시 주소 및 카테고리 실시간 자동 완성 |
| ❤️ **원터치 위시리스트** | 탐색 탭에서 원터치로 가고 싶은 장소 저장, 햅틱 피드백 + 토스트 메시지 제공 |
| 🔄 **무한 스크롤** | 스크롤 위치 감지 기반 페이지네이션으로 탐색 탭 성능 최적화 |
| 🔐 **인증** | Supabase 이메일 로그인 및 익명 로그인 지원 |

---

## 🛠 기술 스택

### Client
- **Language**: Swift
- **Framework**: SwiftUI / UIKit
- **Architecture**: MVVM (`ObservableObject`, `EnvironmentObject`)
- **Map**: Apple MapKit (커스텀 어노테이션 핀)
- **Media**: PhotosUI (`PHPickerViewController`)

### Backend & API
- **Database**: Supabase (PostgreSQL)
- **Storage**: Supabase Storage (이미지 서버)
- **Auth**: Supabase Authentication
- **Open API**: Naver Local Search API, Nominatim (OSM 폴백)

### Tools
- **IDE**: Xcode
- **Version Control**: Git / GitHub

---

## 📁 프로젝트 구조

```
Archiv_yewon/
├── ArchivApp.swift               # 앱 엔트리 포인트
├── Models/
│   └── Post.swift                # Identifiable, Codable, Equatable 데이터 모델
├── Services/
│   ├── PostStore.swift           # 상태 관리 및 Supabase DB 연동
│   └── NaverSearchService.swift  # Naver Local Search API 통신
├── Views/
│   ├── ContentView.swift         # 메인 탭바 및 라우팅
│   ├── AuthView.swift            # 로그인 / 회원가입
│   ├── ArchiveView.swift         # 내 아카이브 (3열 그리드)
│   ├── MapTabView.swift          # 풀스크린 지도 (내 발자취 / 위시리스트)
│   ├── DiscoveryView.swift       # 전체 피드 탐색 (2:3 카드 레이아웃)
│   └── UploadView.swift          # 사진 첨부, 장소 검색, 기록 작성
└── Assets.xcassets/              # 런처 아이콘 및 이미지 리소스
```

---

## 🗃 데이터 구조

```
users/{userId}
├── id, email, name, password
└── createdAt: Timestamp

posts/{postId}
├── id, userId, userName
├── imageData: Data / imageURL: String
├── placeName, category
├── address, roadAddress
├── lat, lng: Double
├── memo, rating: Int
└── createdAt: Timestamp
```

---

## 🌿 브랜치 전략

```
main              # 배포 및 최종본
dev               # 기능 개발 및 테스트 통합
├── feature/auth          # Supabase 로그인 및 사용자 인증
├── feature/map           # MapKit 연동 및 마커 커스텀
├── feature/upload        # Naver API 검색 및 데이터 저장
└── feature/ui-polishing  # UI 디테일 및 뷰 트랜지션 애니메이션
```

---

## 💡 UX 설계 포인트

- **직관적 레이블링**: `[내 발자취]` / `[위시리스트]` 등 사용자 친화적 용어 채택, 인스타그램 UI 벤치마킹으로 별도 설명 없이 즉시 사용 가능
- **즉각적 피드백**: 저장 버튼 터치 시 햅틱 진동 + 토스트 메시지로 조작 결과를 명확히 전달
- **오류 처리**: 검색 결과 없음 / 네트워크 오류 시 Alert로 명확한 안내 제공

---

## 👤 개발자

**유예원** · 한성대학교 모바일소프트웨어트랙 ·  2392112

