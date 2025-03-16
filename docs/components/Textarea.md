# Textarea

Textarea 컴포넌트는 여러 줄의 텍스트 입력을 위한 확장 가능한 입력 영역을 제공합니다.

## 특징

- 크기 조절 가능
- 최소/최대 높이 설정
- 자동 높이 조절
- 에러 상태 표시
- 비활성화 상태
- 플레이스홀더 텍스트
- 접근성 지원
- 반응형 디자인

## 설치

```bash
npm install @hdb/components
```

## 사용법

```tsx
import { Textarea } from "@hdb/components/ui/textarea"

export default function Example() {
  return (
    <Textarea
      placeholder="내용을 입력하세요"
      rows={4}
    />
  )
}
```

## Props

| Prop | 타입 | 기본값 | 설명 |
|------|------|--------|------|
| `resize` | `"none" \| "vertical" \| "horizontal" \| "both"` | `"vertical"` | 크기 조절 방향을 지정합니다. |
| `minHeight` | `number \| string` | - | 최소 높이를 지정합니다. |
| `maxHeight` | `number \| string` | - | 최대 높이를 지정합니다. |
| `autoHeight` | `boolean` | `false` | 내용에 따라 자동으로 높이를 조절합니다. |
| `error` | `boolean` | `false` | 에러 상태를 표시합니다. |
| `disabled` | `boolean` | `false` | 입력 영역의 비활성화 상태를 지정합니다. |
| `rows` | `number` | `3` | 기본 표시 줄 수를 지정합니다. |
| `className` | `string` | - | 추가적인 CSS 클래스를 지정합니다. |

## 예제

### 자동 높이 조절

```tsx
function AutoHeightExample() {
  return (
    <Textarea
      autoHeight
      minHeight={100}
      maxHeight={300}
      placeholder="내용을 입력하면 자동으로 높이가 조절됩니다"
    />
  )
}
```

### 에러 상태

```tsx
function ErrorExample() {
  const [value, setValue] = useState("")
  const [error, setError] = useState(false)
  
  const handleChange = (e: React.ChangeEvent<HTMLTextAreaElement>) => {
    setValue(e.target.value)
    setError(e.target.value.length < 10)
  }
  
  return (
    <div>
      <Textarea
        value={value}
        onChange={handleChange}
        error={error}
        placeholder="최소 10자 이상 입력하세요"
      />
      {error && (
        <p className="text-red-500 text-sm mt-1">
          10자 이상 입력해주세요
        </p>
      )}
    </div>
  )
}
```

### 크기 조절 제한

```tsx
function ResizeExample() {
  return (
    <div className="space-y-4">
      <Textarea
        resize="none"
        placeholder="크기 조절 불가"
      />
      
      <Textarea
        resize="horizontal"
        placeholder="가로 방향만 조절 가능"
      />
      
      <Textarea
        resize="both"
        placeholder="모든 방향으로 조절 가능"
      />
    </div>
  )
}
```

### 폼 유효성 검사

```tsx
import { useForm } from "react-hook-form"
import { z } from "zod"
import { zodResolver } from "@hookform/resolvers/zod"

const schema = z.object({
  description: z.string()
    .min(10, "설명은 최소 10자 이상이어야 합니다")
    .max(1000, "설명은 1000자를 초과할 수 없습니다"),
})

function ValidationExample() {
  const form = useForm({
    resolver: zodResolver(schema),
  })
  
  return (
    <form onSubmit={form.handleSubmit(console.log)}>
      <Textarea
        {...form.register("description")}
        error={!!form.formState.errors.description}
        placeholder="상품 설명을 입력하세요"
      />
      {form.formState.errors.description && (
        <p className="text-red-500 text-sm mt-1">
          {form.formState.errors.description.message}
        </p>
      )}
    </form>
  )
}
```

## 접근성

- 모든 입력 영역은 키보드로 접근 가능합니다.
- 라벨과 입력 영역이 적절하게 연결되어 있습니다.
- 에러 메시지는 스크린 리더에서 자동으로 읽힙니다.
- ARIA 속성이 상태에 따라 적절하게 적용됩니다.

## 스타일 커스터마이징

Textarea의 스타일은 className prop을 통해 커스터마이징할 수 있습니다:

```tsx
<Textarea
  className="border-2 border-purple-500 focus:border-purple-600 focus:ring-purple-600"
  placeholder="커스텀 스타일 입력 영역"
/>
```

또는 전역 CSS를 통해 특정 상태나 변형을 수정할 수 있습니다:

```css
.textarea {
  border-radius: theme("borderRadius.lg");
}

.textarea:focus {
  box-shadow: 0 0 0 2px theme("colors.primary.200");
}

.textarea-error {
  border-color: theme("colors.red.500");
}
```

## 사용 시 주의사항

1. 자동 높이 조절 기능을 사용할 때는 성능을 고려해야 합니다.
2. 최대 높이를 설정할 때는 스크롤이 자연스럽게 동작하는지 확인해야 합니다.
3. 모바일 환경에서는 가상 키보드가 표시될 때 레이아웃이 깨지지 않도록 주의해야 합니다.