# Input

Input 컴포넌트는 사용자로부터 텍스트 입력을 받기 위한 기본적인 폼 요소를 제공합니다.

## 특징

- 다양한 입력 타입 지원 (text, email, password 등)
- 크기 변형: sm, md, lg
- 에러 상태 표시
- 비활성화 상태
- 접두사/접미사 요소
- 라벨과 설명 텍스트
- 유효성 검사 통합
- 접근성 지원
- 반응형 디자인

## 설치

```bash
npm install @hdb/components
```

## 사용법

```tsx
import { Input } from "@hdb/components/ui/input"

export default function Example() {
  return (
    <div className="space-y-4">
      <Input
        type="email"
        placeholder="이메일을 입력하세요"
      />
      
      <Input
        type="password"
        placeholder="비밀번호를 입력하세요"
      />
    </div>
  )
}
```

## Props

| Prop | 타입 | 기본값 | 설명 |
|------|------|--------|------|
| `type` | `"text" \| "email" \| "password" \| "number" \| "tel" \| "url" \| "search"` | `"text"` | 입력 필드의 타입을 지정합니다. |
| `size` | `"sm" \| "md" \| "lg"` | `"md"` | 입력 필드의 크기를 지정합니다. |
| `error` | `boolean` | `false` | 에러 상태를 표시합니다. |
| `disabled` | `boolean` | `false` | 입력 필드의 비활성화 상태를 지정합니다. |
| `prefix` | `ReactNode` | - | 입력 필드 앞에 표시될 요소입니다. |
| `suffix` | `ReactNode` | - | 입력 필드 뒤에 표시될 요소입니다. |
| `className` | `string` | - | 추가적인 CSS 클래스를 지정합니다. |

## 예제

### 에러 상태

```tsx
function ErrorExample() {
  const [value, setValue] = useState("")
  const [error, setError] = useState(false)
  
  const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    setValue(e.target.value)
    setError(e.target.value.length < 3)
  }
  
  return (
    <Input
      value={value}
      onChange={handleChange}
      error={error}
      placeholder="3자 이상 입력하세요"
    />
  )
}
```

### 접두사/접미사

```tsx
import { SearchIcon } from "@radix-ui/react-icons"

function AffixExample() {
  return (
    <div className="space-y-4">
      <Input
        prefix={<SearchIcon />}
        placeholder="검색어를 입력하세요"
      />
      
      <Input
        type="number"
        suffix="원"
        placeholder="금액을 입력하세요"
      />
    </div>
  )
}
```

### 크기 변형

```tsx
function SizeExample() {
  return (
    <div className="space-y-4">
      <Input size="sm" placeholder="Small input" />
      <Input size="md" placeholder="Medium input" />
      <Input size="lg" placeholder="Large input" />
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
  email: z.string().email("올바른 이메일 주소를 입력하세요"),
})

function ValidationExample() {
  const form = useForm({
    resolver: zodResolver(schema),
  })
  
  return (
    <form onSubmit={form.handleSubmit(console.log)}>
      <Input
        {...form.register("email")}
        error={!!form.formState.errors.email}
        placeholder="이메일을 입력하세요"
      />
      {form.formState.errors.email && (
        <p className="text-red-500 text-sm mt-1">
          {form.formState.errors.email.message}
        </p>
      )}
    </form>
  )
}
```

## 접근성

- 모든 입력 필드는 키보드로 접근 가능합니다.
- 라벨과 입력 필드가 적절하게 연결되어 있습니다.
- 에러 메시지는 스크린 리더에서 자동으로 읽힙니다.
- ARIA 속성이 상태에 따라 적절하게 적용됩니다.

## 스타일 커스터마이징

입력 필드의 스타일은 className prop을 통해 커스터마이징할 수 있습니다:

```tsx
<Input
  className="border-2 border-purple-500 focus:border-purple-600 focus:ring-purple-600"
  placeholder="커스텀 스타일 입력 필드"
/>
```

또는 전역 CSS를 통해 특정 상태나 변형을 수정할 수 있습니다:

```css
.input {
  border-radius: theme("borderRadius.lg");
}

.input:focus {
  box-shadow: 0 0 0 2px theme("colors.primary.200");
}

.input-error {
  border-color: theme("colors.red.500");
}
```

## 사용 시 주의사항

1. 비밀번호 입력 필드의 경우 자동 완성 기능을 고려해야 합니다.
2. 숫자 입력 시 지역화된 숫자 형식을 고려해야 합니다.
3. 모바일 환경에서는 적절한 가상 키보드가 표시되도록 type 속성을 올바르게 지정해야 합니다.