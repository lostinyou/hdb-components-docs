# HDB Components Documentation

HDB 컴포넌트 라이브러리는 React와 TypeScript를 기반으로 구축된 현대적이고 접근성 높은 UI 컴포넌트 모음입니다.

## 특징

- 🎨 모던한 디자인 시스템
- 📱 완벽한 반응형 지원
- ♿ 접근성 (ARIA) 준수
- 🌏 다국어 지원 (한국어 기본 제공)
- 🎯 TypeScript로 작성된 타입 안정성
- 📚 상세한 문서화와 예제 코드

## 컴포넌트 카테고리

### 1. 기본 입력 컴포넌트
사용자 입력을 처리하는 기본적인 폼 컴포넌트들입니다.

- [Button](./docs/components/Button.md) - 다양한 스타일과 상태를 지원하는 버튼
- [Input](./docs/components/Input.md) - 텍스트 입력을 위한 기본 컴포넌트
- [Textarea](./docs/components/Textarea.md) - 여러 줄 텍스트 입력을 위한 컴포넌트
- [Select](./docs/components/Select.md) - 드롭다운 선택을 위한 컴포넌트
- [Checkbox](./docs/components/Checkbox.md) - 체크박스 선택을 위한 컴포넌트
- [RadioGroup](./docs/components/RadioGroup.md) - 라디오 버튼 그룹 컴포넌트
- [Switch](./docs/components/Switch.md) - 토글 스위치 컴포넌트
- [Slider](./docs/components/Slider.md) - 범위 선택을 위한 슬라이더
- [ColorPicker](./docs/components/ColorPicker.md) - 색상 선택 컴포넌트
- [FileUpload](./docs/components/FileUpload.md) - 파일 업로드 컴포넌트
- [Form](./docs/components/Form.md) - 폼 관리 및 유효성 검사

### 2. 데이터 표시 컴포넌트
데이터를 효과적으로 표시하기 위한 컴포넌트들입니다.

- [DataTable](./docs/components/DataTable.md) - 고급 데이터 테이블
- [Tree](./docs/components/Tree.md) - 계층 구조 표시
- [Table](./docs/components/Table.md) - 기본 테이블
- [Card](./docs/components/Card.md) - 카드 레이아웃
- [AspectRatio](./docs/components/AspectRatio.md) - 종횡비 유지 컨테이너

### 3. 네비게이션 컴포넌트
사용자 탐색을 위한 컴포넌트들입니다.

- [Menubar](./docs/components/Menubar.md) - 상단 메뉴바
- [ContextMenu](./docs/components/ContextMenu.md) - 우클릭 메뉴
- [Breadcrumb](./docs/components/Breadcrumb.md) - 경로 탐색
- [Pagination](./docs/components/Pagination.md) - 페이지 네비게이션
- [Tabs](./docs/components/Tabs.md) - 탭 네비게이션

### 4. 오버레이 컴포넌트
콘텐츠를 오버레이로 표시하는 컴포넌트들입니다.

- [Dialog](./docs/components/Dialog.md) - 모달 다이얼로그
- [AlertDialog](./docs/components/AlertDialog.md) - 경고 다이얼로그
- [Sheet](./docs/components/Sheet.md) - 슬라이드 패널
- [Popover](./docs/components/Popover.md) - 팝오버 툴팁
- [HoverCard](./docs/components/HoverCard.md) - 호버 카드
- [Tooltip](./docs/components/Tooltip.md) - 툴팁

### 5. 피드백 컴포넌트
사용자에게 피드백을 제공하는 컴포넌트들입니다.

- [Toast](./docs/components/Toast.md) - 토스트 메시지
- [Progress](./docs/components/Progress.md) - 진행 상태 표시
- [Spinner](./docs/components/Spinner.md) - 로딩 스피너
- [Skeleton](./docs/components/Skeleton.md) - 로딩 스켈레톤

### 6. 날짜/시간 컴포넌트
날짜와 시간 선택을 위한 컴포넌트들입니다.

- [RangeCalendar](./docs/components/RangeCalendar.md) - 날짜 범위 선택
- [TimePicker](./docs/components/TimePicker.md) - 시간 선택

### 7. 기타 유틸리티 컴포넌트
다양한 용도로 사용되는 유틸리티 컴포넌트들입니다.

- [Accordion](./docs/components/Accordion.md) - 아코디언
- [Collapsible](./docs/components/Collapsible.md) - 접을 수 있는 컨테이너
- [ScrollArea](./docs/components/ScrollArea.md) - 스크롤 영역
- [Separator](./docs/components/Separator.md) - 구분선
- [Badge](./docs/components/Badge.md) - 뱃지
- [Avatar](./docs/components/Avatar.md) - 아바타
- [Command](./docs/components/Command.md) - 명령 팔레트
- [Combobox](./docs/components/Combobox.md) - 콤보박스

## 설치 방법

```bash
npm install @hdb/components
# or
yarn add @hdb/components
# or
pnpm add @hdb/components
```

## 기본 사용법

```tsx
import { Button } from '@hdb/components/ui/button'
import { Input } from '@hdb/components/ui/input'

export default function LoginForm() {
  return (
    <form>
      <Input
        type="email"
        placeholder="이메일을 입력하세요"
      />
      <Button type="submit">
        로그인
      </Button>
    </form>
  )
}
```

## 스타일 커스터마이징

모든 컴포넌트는 Tailwind CSS를 기반으로 하며, className prop을 통해 쉽게 스타일을 커스터마이징할 수 있습니다.

```tsx
<Button
  className="bg-gradient-to-r from-purple-500 to-pink-500 hover:from-purple-600 hover:to-pink-600"
>
  그라데이션 버튼
</Button>
```

## 테마 설정

프로젝트에 ThemeProvider를 추가하여 다크 모드를 포함한 테마를 지원할 수 있습니다.

```tsx
import { ThemeProvider } from '@hdb/components/providers/theme-provider'

export default function App() {
  return (
    <ThemeProvider>
      <YourApp />
    </ThemeProvider>
  )
}
```

## 접근성

모든 컴포넌트는 WAI-ARIA 가이드라인을 준수하며, 키보드 네비게이션과 스크린 리더를 완벽하게 지원합니다.

## 라이선스

MIT License