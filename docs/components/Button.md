# Button

Button 컴포넌트는 사용자 상호작용을 위한 기본적인 버튼 요소를 제공합니다.

## 특징

- 다양한 변형: solid, outline, ghost, link
- 여러 크기: sm, md, lg
- 로딩 상태 지원
- 비활성화 상태 지원
- 아이콘 통합
- 키보드 접근성
- 커스텀 스타일링

## 설치

```bash
npm install @hdb/components
```

## 사용법

```tsx
import { Button } from "@hdb/components/ui/button"

export default function Example() {
  return (
    <div className="flex gap-4">
      <Button variant="solid">
        기본 버튼
      </Button>
      
      <Button variant="outline">
        외곽선 버튼
      </Button>
      
      <Button variant="ghost">
        고스트 버튼
      </Button>
      
      <Button variant="link">
        링크 버튼
      </Button>
    </div>
  )
}
```

## Props

| Prop | 타입 | 기본값 | 설명 |
|------|------|--------|------|
| `variant` | `"solid" \| "outline" \| "ghost" \| "link"` | `"solid"` | 버튼의 시각적 스타일을 지정합니다. |
| `size` | `"sm" \| "md" \| "lg"` | `"md"` | 버튼의 크기를 지정합니다. |
| `isLoading` | `boolean` | `false` | 로딩 상태를 표시합니다. true일 경우 스피너가 표시되고 버튼이 비활성화됩니다. |
| `isDisabled` | `boolean` | `false` | 버튼의 비활성화 상태를 지정합니다. |
| `leftIcon` | `ReactNode` | - | 버튼 텍스트 왼쪽에 표시될 아이콘입니다. |
| `rightIcon` | `ReactNode` | - | 버튼 텍스트 오른쪽에 표시될 아이콘입니다. |
| `className` | `string` | - | 추가적인 CSS 클래스를 지정합니다. |

## 예제

### 로딩 상태

```tsx
function LoadingExample() {
  const [isLoading, setIsLoading] = useState(false)
  
  return (
    <Button
      isLoading={isLoading}
      onClick={() => {
        setIsLoading(true)
        setTimeout(() => setIsLoading(false), 2000)
      }}
    >
      저장하기
    </Button>
  )
}
```

### 아이콘 버튼

```tsx
import { PlusIcon } from "@radix-ui/react-icons"

function IconExample() {
  return (
    <Button leftIcon={<PlusIcon />}>
      새로 만들기
    </Button>
  )
}
```

### 크기 변형

```tsx
function SizeExample() {
  return (
    <div className="flex items-center gap-4">
      <Button size="sm">Small</Button>
      <Button size="md">Medium</Button>
      <Button size="lg">Large</Button>
    </div>
  )
}
```

## 접근성

- 모든 버튼은 키보드로 접근 및 활성화가 가능합니다.
- 로딩 상태일 때 적절한 ARIA 속성이 자동으로 적용됩니다.
- 비활성화 상태일 때 스크린 리더에서 적절하게 안내됩니다.

## 스타일 커스터마이징

버튼의 스타일은 className prop을 통해 커스터마이징할 수 있습니다:

```tsx
<Button
  className="bg-gradient-to-r from-purple-500 to-pink-500 hover:from-purple-600 hover:to-pink-600"
>
  그라데이션 버튼
</Button>
```

또는 전역 CSS를 통해 특정 변형을 수정할 수 있습니다:

```css
.button-solid {
  background-color: theme("colors.primary.500");
  color: white;
}

.button-solid:hover {
  background-color: theme("colors.primary.600");
}
```

## 사용 시 주의사항

1. 로딩 상태에서는 사용자 상호작용을 방지하기 위해 자동으로 버튼이 비활성화됩니다.
2. 아이콘은 적절한 크기로 자동 조정되지만, 필요한 경우 className을 통해 크기를 조정할 수 있습니다.
3. 링크 형태의 버튼을 사용할 때는 실제 링크(`<a>` 태그)가 필요한 경우를 고려해야 합니다.