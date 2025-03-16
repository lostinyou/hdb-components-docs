# StatusBadge 컴포넌트

상태를 시각적으로 표시하는 배지 컴포넌트입니다. 다양한 색상 변형과 아이콘 통합, 애니메이션 효과를 지원합니다.

## 주요 기능

- 🎨 다양한 상태 색상
- 🔣 아이콘 통합
- ✨ 애니메이션 효과
- 📏 크기 변형
- 💬 툴팁 지원
- ♿ 접근성 지원

## 설치 방법

```bash
npm install @hdb/components
```

## 사용 예시

### 기본 사용법

```tsx
import { StatusBadge } from "@hdb/components"

function Example() {
  return <StatusBadge status="active" />
}
```

### 아이콘과 툴팁 사용

```tsx
import { Clock } from "lucide-react"

<StatusBadge
  status="pending"
  icon={<Clock className="h-4 w-4" />}
  tooltip="처리 대기중"
/>
```

### 크기와 애니메이션

```tsx
<StatusBadge
  status="error"
  size="lg"
  pulse={true}
  showDot={true}
/>
```

## Props

| 속성 | 타입 | 기본값 | 설명 |
|------|------|--------|------|
| `status` | `"active" \| "inactive" \| "pending" \| "error" \| "warning"` | `"active"` | 상태 종류 |
| `size` | `"sm" \| "md" \| "lg"` | `"md"` | 배지 크기 |
| `pulse` | `boolean` | `false` | 펄스 애니메이션 효과 |
| `icon` | `ReactNode` | - | 커스텀 아이콘 |
| `tooltip` | `string` | - | 툴팁 텍스트 |
| `showDot` | `boolean` | `false` | 상태 도트 표시 |
| `className` | `string` | - | 추가 스타일 클래스 |

## 상태별 스타일

각 상태는 고유한 색상과 스타일을 가집니다:

| 상태 | 색상 | 기본 아이콘 | 설명 |
|------|------|------------|------|
| `active` | 초록색 | CheckCircle | 활성 상태 |
| `inactive` | 회색 | XCircle | 비활성 상태 |
| `pending` | 노란색 | Clock | 대기 상태 |
| `error` | 빨간색 | AlertCircle | 오류 상태 |
| `warning` | 주황색 | AlertCircle | 경고 상태 |

## 크기 변형

세 가지 크기 옵션을 제공합니다:

```tsx
<div className="space-x-2">
  <StatusBadge status="active" size="sm" />
  <StatusBadge status="active" size="md" />
  <StatusBadge status="active" size="lg" />
</div>
```

## 애니메이션

펄스 애니메이션을 통해 동적인 상태 표시가 가능합니다:

```tsx
<StatusBadge
  status="pending"
  pulse={true}
  tooltip="데이터 동기화 중..."
/>
```

## 접근성

- ARIA 레이블 자동 생성
- 툴팁의 키보드 접근성
- 고대비 모드 지원
- 상태 변경 알림

## 스타일 커스터마이징

컴포넌트의 스타일은 Tailwind CSS 클래스를 통해 커스터마이징할 수 있습니다.

```tsx
<StatusBadge
  className="font-bold"
  style={{
    "--badge-bg": "var(--custom-color)",
    "--badge-text": "var(--custom-text)",
  }}
/>
```

### 색상 변형 추가

```tsx
const customStatusVariants = {
  custom: "bg-purple-50 text-purple-700 ring-purple-600/20",
}

<StatusBadge
  className={cn(customStatusVariants.custom)}
  icon={<Star className="h-4 w-4" />}
/>
```

## 사용시 주의사항

1. 상태 표시 일관성
   - 동일한 상태는 항상 같은 시각적 표현 사용
   - 상태 변경 시 적절한 애니메이션 활용
   - 상태별 의미가 명확하도록 설계

2. 접근성 고려사항
   - 색상만으로 상태를 구분하지 않기
   - 적절한 툴팁 텍스트 제공
   - 상태 변경 시 스크린 리더 알림

3. 성능 최적화
   - 불필요한 리렌더링 방지
   - 애니메이션 성능 모니터링
   - 아이콘 최적화

4. 반응형 디자인
   - 작은 화면에서의 가독성
   - 터치 인터페이스 고려
   - 적절한 크기 선택