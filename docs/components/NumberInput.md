# NumberInput 컴포넌트

숫자 입력에 특화된 입력 컴포넌트입니다. 증감 버튼, 최소/최대값 설정, 소수점 자릿수 제어, 단위 표시 등의 기능을 제공합니다.

## 주요 기능

- ✨ 증감 버튼을 통한 값 조절
- 🔒 최소/최대값 설정
- 🔢 소수점 자릿수 제어
- 📏 단위 표시
- ⌨️ 키보드 조작 지원
- ♿ 접근성 지원
- 📱 반응형 디자인

## 설치 방법

```bash
npm install @hdb/components
```

## 사용 예시

### 기본 사용법

```tsx
import { NumberInput } from "@hdb/components"

function Example() {
  const [value, setValue] = useState(5)
  
  return (
    <NumberInput 
      value={value} 
      onChange={setValue} 
    />
  )
}
```

### 최소/최대값 설정

```tsx
<NumberInput 
  min={0} 
  max={100} 
  step={5}
  value={value}
  onChange={setValue}
/>
```

### 소수점 자릿수와 단위 표시

```tsx
<NumberInput 
  decimalPlaces={2}
  unit="kg"
  value={10.5}
  onChange={setValue}
/>
```

## Props

| 속성 | 타입 | 기본값 | 설명 |
|------|------|--------|------|
| `value` | `number` | - | 입력 필드의 현재 값 |
| `onChange` | `(value: number) => void` | - | 값이 변경될 때 호출되는 함수 |
| `min` | `number` | - | 최소값 |
| `max` | `number` | - | 최대값 |
| `step` | `number` | `1` | 증감 단위 |
| `decimalPlaces` | `number` | `0` | 소수점 자릿수 |
| `unit` | `string` | - | 단위 표시 |
| `showControls` | `boolean` | `true` | 증감 버튼 표시 여부 |
| `controlPosition` | `"right" \| "both"` | `"right"` | 증감 버튼 위치 |
| `disabled` | `boolean` | `false` | 비활성화 여부 |
| `className` | `string` | - | 추가 스타일 클래스 |

## 접근성

- 키보드 탐색 지원 (화살표 위/아래로 값 조절)
- ARIA 레이블 및 역할 지원
- 고대비 모드 지원

## 스타일 커스터마이징

컴포넌트의 스타일은 Tailwind CSS 클래스를 통해 커스터마이징할 수 있습니다.

```tsx
<NumberInput
  className="w-32 text-lg"
  // 버튼 스타일 커스터마이징
  style={{
    "--btn-bg": "var(--primary)",
    "--btn-color": "white",
  }}
/>
```

## 사용시 주의사항

1. `value`와 `onChange` props를 함께 사용하여 제어 컴포넌트로 활용하세요.
2. `min`과 `max` 값을 설정할 때는 적절한 `step` 값도 함께 설정하는 것이 좋습니다.
3. `decimalPlaces`를 설정할 때는 사용자의 입력 값이 적절히 반올림되는 것에 주의하세요.
4. 단위를 표시할 때는 충분한 여백을 확보하세요.