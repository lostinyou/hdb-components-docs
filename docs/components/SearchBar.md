# SearchBar 컴포넌트

검색 기능을 제공하는 고급 입력 컴포넌트입니다. 자동완성, 검색 히스토리, 필터링 등의 기능을 제공합니다.

## 주요 기능

- 🔍 자동완성
- 📝 검색 히스토리
- 🏷️ 필터링 옵션
- ⚡ 실시간 검색
- ⌨️ 키보드 네비게이션
- 💡 검색 제안
- ♿ 접근성 지원

## 설치 방법

```bash
npm install @hdb/components
```

## 사용 예시

### 기본 사용법

```tsx
import { SearchBar } from "@hdb/components"

function Example() {
  const handleSearch = (value: string) => {
    console.log('검색어:', value)
  }

  return (
    <SearchBar
      onSearch={handleSearch}
      placeholder="검색어를 입력하세요"
    />
  )
}
```

### 자동완성과 필터링

```tsx
const suggestions = ["상품1", "상품2", "고객1", "고객2"]
const filters = [
  { label: "전체", value: "all" },
  { label: "제품", value: "products" },
  { label: "고객", value: "customers" }
]

<SearchBar
  suggestions={suggestions}
  filters={filters}
  onSearch={(value, filter) => {
    console.log('검색어:', value, '필터:', filter)
  }}
/>
```

## Props

| 속성 | 타입 | 기본값 | 설명 |
|------|------|--------|------|
| `onSearch` | `(value: string, filter?: string) => void` | - | 검색 실행 시 호출되는 함수 |
| `placeholder` | `string` | `"검색..."` | 입력 필드 플레이스홀더 |
| `suggestions` | `string[]` | `[]` | 검색어 자동완성 목록 |
| `filters` | `SearchFilter[]` | `[]` | 검색 필터 옵션 |
| `maxHistory` | `number` | `5` | 최대 검색 기록 수 |
| `debounceMs` | `number` | `300` | 실시간 검색 디바운스 시간 (ms) |
| `className` | `string` | - | 추가 스타일 클래스 |

### SearchFilter 타입

```typescript
interface SearchFilter {
  label: string  // 필터 레이블
  value: string  // 필터 값
}
```

## 기능 설명

### 검색 히스토리

- 최근 검색어 자동 저장
- localStorage를 통한 영구 저장
- 중복 검색어 자동 제거
- 최대 저장 개수 제한

### 자동완성

- 입력 값에 따른 실시간 필터링
- 대소문자 구분 없는 검색
- 키보드 네비게이션 지원
- 클릭/엔터로 선택

### 필터링

- 다중 필터 옵션 지원
- 필터 토글 기능
- 선택된 필터 시각적 표시
- 필터와 검색어 조합 검색

## 접근성

- ARIA 레이블 및 역할 지원
- 키보드 네비게이션
- 스크린 리더 호환
- 고대비 모드 지원

## 스타일 커스터마이징

컴포넌트의 스타일은 Tailwind CSS 클래스를 통해 커스터마이징할 수 있습니다.

```tsx
<SearchBar
  className="w-full max-w-2xl"
  // 입력 필드 스타일
  style={{
    "--input-bg": "var(--background)",
    "--input-border": "var(--border)",
  }}
/>
```

## 사용시 주의사항

1. 실시간 검색 구현 시 고려사항
   - 적절한 `debounceMs` 설정
   - 서버 부하 고려
   - 검색 결과 캐싱 전략

2. 검색 히스토리 관리
   - 저장소 용량 고려
   - 민감한 검색어 처리
   - 동기화 전략

3. 자동완성 구현 시 고려사항
   - 데이터 로딩 전략
   - 표시할 결과 수 제한
   - 하이라이팅 처리

4. 필터링 기능
   - 필터 조합 로직
   - 기본 필터 설정
   - 필터 상태 관리