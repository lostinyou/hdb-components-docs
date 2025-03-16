# ImageUpload 컴포넌트

이미지 업로드와 미리보기 기능을 제공하는 컴포넌트입니다. 드래그 앤 드롭, 이미지 크롭, 다중 이미지 업로드 등을 지원합니다.

## 주요 기능

- 🖱️ 드래그 앤 드롭 업로드
- 👁️ 이미지 미리보기
- ✂️ 이미지 크롭
- 📁 다중 이미지 업로드
- 🔄 이미지 최적화
- ⚖️ 파일 크기 제한
- ♿ 접근성 지원

## 설치 방법

```bash
npm install @hdb/components react-dropzone react-image-crop
```

## 사용 예시

### 기본 사용법

```tsx
import { ImageUpload } from "@hdb/components"

function Example() {
  const handleUpload = (files: File[]) => {
    console.log('업로드된 파일:', files)
  }

  return (
    <ImageUpload
      onUpload={handleUpload}
      maxFiles={5}
      maxSize={5 * 1024 * 1024} // 5MB
    />
  )
}
```

### 크롭 기능 활성화

```tsx
<ImageUpload
  enableCrop
  aspectRatio={16/9}
  onUpload={handleUpload}
  maxFiles={1}
/>
```

## Props

| 속성 | 타입 | 기본값 | 설명 |
|------|------|--------|------|
| `onUpload` | `(files: File[]) => void` | - | 파일 업로드 시 호출되는 함수 |
| `maxFiles` | `number` | `1` | 최대 업로드 가능한 파일 수 |
| `maxSize` | `number` | `5 * 1024 * 1024` | 최대 파일 크기 (바이트) |
| `accept` | `string[]` | `["image/jpeg", "image/png", "image/webp"]` | 허용되는 파일 형식 |
| `enableCrop` | `boolean` | `false` | 이미지 크롭 기능 활성화 |
| `aspectRatio` | `number` | - | 크롭 영역의 종횡비 |
| `className` | `string` | - | 추가 스타일 클래스 |
| `disabled` | `boolean` | `false` | 비활성화 여부 |

## 이벤트 처리

### 파일 업로드 처리

```tsx
const handleUpload = (files: File[]) => {
  // FormData 생성
  const formData = new FormData()
  files.forEach((file, index) => {
    formData.append(`image${index}`, file)
  })

  // API 호출
  fetch('/api/upload', {
    method: 'POST',
    body: formData
  })
}
```

## 접근성

- 키보드 탐색 지원
- 스크린 리더 호환
- 드래그 앤 드롭 영역 ARIA 레이블

## 스타일 커스터마이징

컴포넌트의 스타일은 Tailwind CSS 클래스를 통해 커스터마이징할 수 있습니다.

```tsx
<ImageUpload
  className="w-full max-w-2xl"
  // 드롭존 스타일
  style={{
    "--dropzone-bg": "var(--background)",
    "--dropzone-border": "var(--border)",
  }}
/>
```

## 사용시 주의사항

1. 대용량 이미지 업로드 시 성능 고려사항
   - 이미지 최적화 활용
   - 적절한 `maxSize` 설정
   - 프로그레스 표시 구현

2. 크롭 기능 사용 시 고려사항
   - 적절한 `aspectRatio` 설정
   - 크롭 결과물의 품질 확인
   - 원본 이미지 보존 여부 결정

3. 다중 업로드 시 고려사항
   - 적절한 `maxFiles` 설정
   - 순서 관리
   - 일괄 처리 방식 결정

4. 에러 처리
   - 파일 크기 초과
   - 지원하지 않는 파일 형식
   - 업로드 실패