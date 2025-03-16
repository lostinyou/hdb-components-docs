# Select

Select 컴포넌트는 사용자가 여러 옵션 중 하나를 선택할 수 있는 드롭다운 메뉴를 제공합니다.

## 특징

- 단일/다중 선택 지원
- 검색 기능
- 옵션 그룹화
- 비활성화 상태
- 사용자 정의 옵션 렌더링
- 키보드 네비게이션
- 가상 스크롤링
- 접근성 지원

## 설치

```bash
npm install @hdb/components
```

## 사용법

```tsx
import { Select } from "@hdb/components/ui/select"

export default function Example() {
  return (
    <Select
      placeholder="옵션을 선택하세요"
      options={[
        { value: "apple", label: "사과" },
        { value: "banana", label: "바나나" },
        { value: "orange", label: "오렌지" },
      ]}
    />
  )
}
```

## Props

| Prop | 타입 | 기본값 | 설명 |
|------|------|--------|------|
| `options` | `Option[]` | `[]` | 선택 가능한 옵션 목록입니다. |
| `value` | `string \| string[]` | - | 현재 선택된 값입니다. |
| `defaultValue` | `string \| string[]` | - | 초기 선택 값입니다. |
| `onChange` | `(value: string \| string[]) => void` | - | 선택 값이 변경될 때 호출되는 함수입니다. |
| `multiple` | `boolean` | `false` | 다중 선택을 활성화합니다. |
| `searchable` | `boolean` | `false` | 옵션 검색 기능을 활성화합니다. |
| `disabled` | `boolean` | `false` | 선택 상자를 비활성화합니다. |
| `loading` | `boolean` | `false` | 로딩 상태를 표시합니다. |
| `error` | `boolean` | `false` | 에러 상태를 표시합니다. |
| `placeholder` | `string` | - | 기본 표시 텍스트입니다. |
| `className` | `string` | - | 추가적인 CSS 클래스를 지정합니다. |

## 예제

### 다중 선택

```tsx
function MultipleExample() {
  return (
    <Select
      multiple
      placeholder="과일을 선택하세요"
      options={[
        { value: "apple", label: "사과" },
        { value: "banana", label: "바나나" },
        { value: "orange", label: "오렌지" },
        { value: "grape", label: "포도" },
      ]}
    />
  )
}
```

### 옵션 그룹화

```tsx
function GroupExample() {
  return (
    <Select
      placeholder="음식을 선택하세요"
      options={[
        {
          label: "과일",
          options: [
            { value: "apple", label: "사과" },
            { value: "banana", label: "바나나" },
          ],
        },
        {
          label: "채소",
          options: [
            { value: "carrot", label: "당근" },
            { value: "tomato", label: "토마토" },
          ],
        },
      ]}
    />
  )
}
```

### 검색 기능

```tsx
function SearchableExample() {
  return (
    <Select
      searchable
      placeholder="도시를 검색하세요"
      options={[
        { value: "seoul", label: "서울" },
        { value: "busan", label: "부산" },
        { value: "incheon", label: "인천" },
        { value: "daegu", label: "대구" },
        { value: "gwangju", label: "광주" },
      ]}
    />
  )
}
```

### 사용자 정의 옵션 렌더링

```tsx
function CustomOptionExample() {
  return (
    <Select
      placeholder="사용자를 선택하세요"
      options={[
        {
          value: "user1",
          label: "홍길동",
          render: (option) => (
            <div className="flex items-center gap-2">
              <img
                src={option.avatar}
                alt=""
                className="w-6 h-6 rounded-full"
              />
              <span>{option.label}</span>
              <span className="text-gray-500 text-sm">
                ({option.email})
              </span>
            </div>
          ),
        },
        // ... 더 많은 옵션
      ]}
    />
  )
}
```

## 접근성

- 키보드 네비게이션을 완벽하게 지원합니다.
- ARIA 레이블과 설명이 적절하게 제공됩니다.
- 스크린 리더 사용자를 위한 상태 안내가 포함되어 있습니다.
- 포커스 관리가 자연스럽게 이루어집니다.

## 스타일 커스터마이징

Select의 스타일은 className prop을 통해 커스터마이징할 수 있습니다:

```tsx
<Select
  className="border-2 border-purple-500 focus:border-purple-600"
  menuClassName="bg-gray-100 rounded-lg shadow-xl"
  optionClassName="hover:bg-purple-100"
  placeholder="커스텀 스타일 선택 상자"
  options={[...]}
/>
```

또는 전역 CSS를 통해 특정 부분을 수정할 수 있습니다:

```css
.select-trigger {
  border-radius: theme("borderRadius.lg");
}

.select-menu {
  box-shadow: theme("boxShadow.lg");
}

.select-option:hover {
  background-color: theme("colors.primary.50");
}
```

## 사용 시 주의사항

1. 많은 수의 옵션이 있는 경우 가상 스크롤링이 자동으로 적용됩니다.
2. 검색 기능을 사용할 때는 디바운스가 적용되어 있습니다.
3. 모바일 환경에서는 네이티브 선택 상자로 대체될 수 있습니다.
4. 다중 선택 시 선택된 항목의 순서가 유지됩니다.