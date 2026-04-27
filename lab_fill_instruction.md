# 가상실험실 뼈대 채우기 지시서

> **이 지시서는 "처음부터 HTML을 다 만들어라"가 아닙니다.**
> 첨부한 `가상실험실_뼈대_v1.html`(공통 코드만 들어있는 뼈대 HTML)의
> **★① ~ ★⑧ 마커 영역만 채워주세요.** 마커 밖의 코드는 절대 수정하지 마세요.

> **사용법:**
> 1. 첨부된 `가상실험실_뼈대_v1.html` 파일을 엽니다.
> 2. 아래 ★① ~ ★⑧ 지시에 따라 각 마커 영역만 수정합니다.
> 3. 마커 밖의 코드(공통 구조, 변수명, 함수명, CSS 클래스명, 이벤트 시스템 등)는 **절대 변경하지 마세요.**
> 4. 결과 파일명: `가상실험실_고체에서 열의 이동 관찰하기.html`

---

## 실험 기본 정보

| 항목 | 내용 |
|------|------|
| 단원 | 5학년 2학기, 2단원 열과 우리 생활 |
| 제목 | 고체에서 열의 이동 관찰하기 |
| 탐구 목표 | 고체에서 열의 이동을 관찰하고 열이 어떻게 이동하는지 설명할 수 있다. |
| 핵심 개념 | 전도 - 온도가 높은 곳에서 낮은 곳으로 물체를 따라 열이 이동 |
| 준비물 | 길게 자른 구리판, 정사각형 구리판, ㄷ모양 구리판, 열 변색 붙임딱지, 삼발이, 쇠그물, 스탠드, 고정 집게, 초, 점화기 |

---

## ★① 색상 테마 (CSS 변수 3개)

뼈대 HTML 상단의 ★① 마커 영역(`<style>` 안의 `:root` 블록)에 있는 CSS 변수 **3개**를 아래 값으로 교체하세요.

**추천 테마: 열전도/고체 (따뜻한 톤)**

```css
:root {
  --accent: #ff6b9d;        /* 메인 강조 색상 — 버튼, 활성 dot, 그라데이션 시작점 */
  --accent2: #feca57;       /* 그라데이션 페어 색상 — 그라데이션 끝점 */
  --accent-light: #ffd9e6;  /* 완료 상태 표시용 — 완료된 dot 배경, 약한 강조 */
}
```

> 이 3개 변수만 바꾸면 헤더 그라데이션, dot, 버튼, 가이드 박스 강조선 등 전체 톤이 일관되게 변경됩니다. 다른 CSS는 건드리지 마세요.

---

## ★② HTML 요소 수정

뼈대 HTML 본문의 ★② 마커가 붙은 HTML 영역들을 아래 내용으로 채우세요.

### ★②-1 페이지 제목 / 헤더 타이틀

- `<title>` 태그: `고체에서 열의 이동 관찰하기`
- 헤더 서브타이틀(h1 옆 부제): `고체에서 열의 이동 관찰하기`

### ★②-2 탐구 목표 팝업 (`#objective-popup`)

- 팝업 제목: **`탐구 목표`** (이모지 ❌ — 텍스트만)
- 팝업 본문: `고체에서 열의 이동을 관찰하고 열이 어떻게 이동하는지 설명할 수 있다.`

### ★②-3 스텝 인디케이터 dot 개수

- 사용자가 설계한 단계 수: **3단계**
- 뼈대 HTML의 `#step-dots` 컨테이너 안에 `<div class="dot"></div>`를 **3개** 배치하세요.
- 첫 번째 dot에 `active` 클래스를 붙여 시작 시 강조되게 하세요.

### ★②-4 사이드 카드 패널 (단계별 선택지/장비 카드)

학생이 드래그 앤 드롭하는 장비 카드들을 사이드 패널에 배치하세요.
체크된 장비 목록 (탭 3에서 선택한 항목 + 커스텀 장비):

- 스탠드 (스탠드+클램프+고정집게)
- 삼발이+쇠그물+초 (통합)

각 단계마다 어떤 카드가 표시되어야 하는지는 아래 `★⑥` 영역의 단계별 흐름을 참고하세요.

### ★②-5 결과 요약 팝업 (`#summary-overlay`)

- 팝업 제목: **`실험 결과 정리`** (이모지 ❌ — 텍스트만)
- 본문: `고체에서 열이 이동하는 모습을 관찰했어요!`
- 핵심 개념 박스: 
```
고체에서는 온도가 높은 곳에서 온도가 낮은 곳으로 물체를 따라 열이 이동합니다.
이러한 열의 이동 방식을 전도라고 합니다.
```
  *(핵심 개념 박스 앞에 💡, 📌, ✨ 등 이모지를 절대 붙이지 마세요)*

---

## ★③ 오디오 매핑

뼈대 HTML의 `★③ 오디오 시스템` 영역 안에 있는 `audioFiles`와 `audioTexts` 두 객체를 아래 내용으로 채우세요.

> **중요 (v15)**: 한 단계 안에서 여러 mp3가 순차 재생되어야 하는 경우, 각 세그먼트에 별도의 키를 부여합니다. 키 형식은 `takeN_M` (N=Step 인덱스+2, M=세그먼트 번호)이며, 단일 세그먼트인 단계는 기존처럼 `takeN`으로 둡니다.

### audioFiles (실제 mp3 파일명 매핑)

```javascript
var audioFiles = {
  take1: 'tts_take1.mp3',  // 탐구 목표 팝업 나레이션
  take2: 'tts_take2.mp3',  // Step 1 나레이션
  take3: 'tts_take3.mp3',  // Step 2 나레이션
  take4_1: 'tts_take4.mp3',  // Step 3 (세그먼트 1) 나레이션
  take4_2: 'tts_take5.mp3',  // Step 3 (세그먼트 2) 나레이션
  summary_1: 'tts_take6.mp3',  // 결과 요약 (세그먼트 1) 나레이션
  summary_2: 'tts_take7.mp3',  // 결과 요약 (세그먼트 2) 나레이션
};
```

### audioTexts (mp3가 없을 때의 TTS 폴백 텍스트)

```javascript
var audioTexts = {
  take1: '고체에서 열의 이동을 관찰하고 열이 어떻게 이동하는지 설명할 수 있다.',
  take2: '구리판 한 개를 골라 고정 집게 쪽으로 옮겨 보세요.',
  take3: '초를 구리판 아래 초록색 표시 부분으로 옮겨 보세요.',
  take4_1: '열 변색 붙임딱지의 색깔 변화를 관찰해 보세요.',
  take4_2: '초에서 가까운 곳부터 구리판을 따라 색이 변해요.',
  summary_1: '[결과 요약 세그먼트 1 나레이션]',
  summary_2: '[결과 요약 세그먼트 2 나레이션]',
};
```

> **BGM 파일**: `bgm.mp3` (뼈대 HTML의 `startBgMusic()` 함수 안 `new Audio(...)` 부분에서 이미 처리됨 — 파일명만 일치시키세요)

---

## ★④ 가이드 메시지 + 세그먼트 체이닝

뼈대 HTML의 `★④` 마커 영역에 아래 두 가지를 모두 채우세요:

1. `guideMessages` 배열 — Step별 **첫 세그먼트** 가이드 메시지 (하위 호환용)
2. `stepSegments` 객체 — **세그먼트가 2개 이상인 Step**의 순차 재생 정보

### guideMessages (Step별 첫 세그먼트 가이드)

```javascript
var guideMessages = [
  '구리판 한 개를 골라 고정 집게 쪽으로 옮겨 보세요.',  // Step 1
  '초를 구리판 아래 초록색 표시 부분으로 옮겨 보세요.',  // Step 2
  '열 변색 붙임딱지의 색깔 변화를 관찰해 보세요.',  // Step 3
];
```

### stepSegments (다중 세그먼트 — 한 단계 안에서 가이드/mp3가 순차 변경되는 경우)

> 키는 Step 인덱스(0부터). 값은 `{ guide, audioKey, delayMs }` 객체의 배열. **앞 세그먼트의 mp3가 끝나면 `delayMs`만큼 기다린 뒤 다음 세그먼트의 가이드를 갱신하고 mp3를 재생합니다.**

```javascript
var stepSegments = {
  2: [
    { guide: '열 변색 붙임딱지의 색깔 변화를 관찰해 보세요.', audioKey: 'take4_1', delayMs: 0 },
    { guide: '초에서 가까운 곳부터 구리판을 따라 색이 변해요.', audioKey: 'take4_2', delayMs: 3000 },
  ],
};
```

### summarySegments (결과 요약 다중 mp3 순차 재생)

```javascript
var summarySegments = [
  { audioKey: 'summary_1', delayMs: 0 },
  { audioKey: 'summary_2', delayMs: 1000 },
];
```

### 호출 패턴

- 각 Step 진입 시 `playStepSegments(stepIndex)`를 호출하세요. 이 함수가 `stepSegments[stepIndex]`가 있으면 세그먼트 체인을 실행하고, 없으면 기존 방식(`updateGuideByStep` + `playAudio('take' + (n+2))`)으로 폴백합니다.
- 결과 요약 팝업 표시 직후 `playSummarySegments()`를 호출하세요. `summarySegments` 배열을 순차 재생합니다.

> **중요**: 뼈대 v2에는 `playStepSegments`, `playSummarySegments` 함수가 이미 구현되어 있습니다. 이 함수들이 mp3 종료 시점을 정확히 감지해 다음 세그먼트로 넘어가므로, **수동으로 `setTimeout`으로 mp3 길이를 추측하지 마세요.**

---

## ★⑤ 3D 장비 build 함수들

뼈대 HTML의 `★⑤` 마커 영역에 아래 장비들의 `buildXxx()` 함수를 추가하세요. 각 함수는 Three.js Group을 만들어 `scene.add(...)` 합니다.

### 필요한 장비 목록 (3개)

> ※ 통합 장비가 내부적으로 호출하는 빌더 함수의 정의도 함께 포함했습니다 (자동 보강).

#### 1. 스탠드 (스탠드+클램프+고정집게)

- 함수명: `buildStand()` (또는 적절한 이름)
- 상세 스펙:

  **실물 구조**:
  - **받침판**: 검정 직사각형 금속판, 모서리 4곳에 미끄럼 방지 발
  - **수직 봉**: 크롬 원기둥, 받침판 뒤쪽에서 위로 올라감
  - **클램프**: 은색 직육면체 몸체, 양쪽에 **검정 별모양 손잡이(star knob)** 2개
  - **수평 봉**: 크롬 원기둥, 수직 봉보다 가늘음
  - **고정 집게**: 크롬 프레임 + 피벗 리벳 + 코일 스프링 + **빨간색 집게 턱** 2개 + 하단 나비 나사

  **핵심 좌표 / 상수**:
  - 스탠드 그룹 위치 `STAND_POS = (-1.5, 0, 0)`
  - 집게 끝 X (스탠드 로컬) `CLAMP_TIP_X = 0.95`, 클램프 높이 `CLAMP_Y = 1.35`
  - 따라서 집게 끝 월드 좌표 = `(-0.55, 1.35, 0)` — 구리판이 고정될 위치
  - `getClampWorldPos()`: 집게 끝 월드 좌표를 반환하는 헬퍼

  **재질 (Material)**:
  - `chrome` (수직봉/수평봉/피벗): `MeshPhongMaterial({ map: createChromeTexture(), color: 0xaaaaaa, specular: 0xffffff, shininess: 300, reflectivity: 1.0 })`
  - `dark` (받침판/발/별모양 손잡이): `MeshStandardMaterial({ color: 0x1a1a1a, roughness: 0.4, metalness: 0.35 })`
  - `silverMetal` (클램프 몸체/리벳/나비너트): `MeshStandardMaterial({ color: 0xbbbbbb, roughness: 0.25, metalness: 0.85 })`
  - `red` (집게 턱): `MeshStandardMaterial({ color: 0xcc2222, roughness: 0.35, metalness: 0.2 })`

  **주요 구성요소 / 치수**:
  - **받침판**: `BoxGeometry(2.0, 0.13, 1.4)` 검정. 발 4개 `BoxGeometry(0.15, 0.06, 0.15)` 모서리에 배치
  - **수직 봉**: `CylinderGeometry(0.05, 0.05, 3.2, 24)` 크롬. 받침판 한쪽 끝(x=-0.2)에서 위로
  - **클램프 몸체**: `BoxGeometry(0.44, 0.20, 0.18)` 은색. 별모양 손잡이 2개 `CylinderGeometry(0.055, 0.055, 0.12 또는 0.08, 12)`
  - **수평 봉**: `CylinderGeometry(0.035, 0.035, 1.375, 16)` 크롬, z축으로 약간 뒤쪽(-0.07)에 위치
  - **고정 집게**: 피벗(`CylinderGeometry(0.02, 0.02, 0.26, 8)`) + 양쪽 리벳(`CylinderGeometry(0.032, 0.032, 0.025, 6)`) + 빨간 집게 턱 2개(`BoxGeometry(0.28, 0.045, 0.18)`, 살짝 기울임 ±0.05 rad) + 끝 부분 빨간 구체(`SphereGeometry(0.035, 8, 8)`, scale `(1, 0.6, 1.4)`) + 나비 나사(`CylinderGeometry(0.014, 0.014, 0.08, 6)` + `SphereGeometry(0.024, 6, 6)`)

  **치수 비율**: 받침판 가로:수직봉 높이 ≈ 1:2.5 / 수직봉:수평봉 굵기 ≈ 1.4:1

  **실행 가능한 구현 코드** (그대로 사용 권장):

  ```javascript
  var STAND_POS = new THREE.Vector3(-1.5, 0, 0);
  var CLAMP_TIP_X = 0.95;
  var CLAMP_Y = 1.35;

  function getClampWorldPos() {
    return new THREE.Vector3(STAND_POS.x + CLAMP_TIP_X, CLAMP_Y, 0);
  }

  function buildStand() {
    var standGroup = new THREE.Group();
    var ct = createChromeTexture();
    var chrome = new THREE.MeshPhongMaterial({
      map: ct, color: 0xaaaaaa, specular: 0xffffff, shininess: 300, reflectivity: 1.0
    });
    var dark = new THREE.MeshStandardMaterial({ color: 0x1a1a1a, roughness: 0.4, metalness: 0.35 });
    var silverMetal = new THREE.MeshStandardMaterial({ color: 0xbbbbbb, roughness: 0.25, metalness: 0.85 });
    var red = new THREE.MeshStandardMaterial({ color: 0xcc2222, roughness: 0.35, metalness: 0.2 });

    // 받침판
    standGroup.add(M(new THREE.BoxGeometry(2.0, 0.13, 1.4), dark, -0.6, 0.1, 0));
    var fx = [-1.4, 0.2], fz = [-0.55, 0.55];
    for (var i = 0; i < 2; i++) for (var j = 0; j < 2; j++)
      standGroup.add(M(new THREE.BoxGeometry(0.15, 0.06, 0.15), dark, fx[i], 0.02, fz[j]));

    // 수직 봉
    standGroup.add(M(new THREE.CylinderGeometry(0.05, 0.05, 3.2, 24), chrome, -0.2, 1.77, 0));

    // 클램프 몸체 (은색)
    standGroup.add(M(new THREE.BoxGeometry(0.44, 0.20, 0.18), silverMetal, -0.20, CLAMP_Y, -0.035));
    // 별모양 손잡이 (검정) 2개
    var kb1 = new THREE.Mesh(new THREE.CylinderGeometry(0.055, 0.055, 0.12, 12), dark);
    kb1.position.set(-0.50, CLAMP_Y, 0.05); kb1.rotation.z = Math.PI / 2; standGroup.add(kb1);
    var kb2 = new THREE.Mesh(new THREE.CylinderGeometry(0.055, 0.055, 0.08, 12), dark);
    kb2.position.set(0.00, CLAMP_Y, -0.15); kb2.rotation.x = Math.PI / 2; standGroup.add(kb2);

    // 수평 봉
    var hb = new THREE.Mesh(new THREE.CylinderGeometry(0.035, 0.035, 1.375, 16), chrome);
    hb.position.set(0.0325, CLAMP_Y, -0.07); hb.rotation.z = Math.PI / 2; hb.castShadow = true;
    standGroup.add(hb);

    // 고정 집게 — 피벗
    var px = 0.72;
    var pv = new THREE.Mesh(new THREE.CylinderGeometry(0.02, 0.02, 0.26, 8), chrome);
    pv.position.set(px, CLAMP_Y, 0); pv.rotation.x = Math.PI / 2; standGroup.add(pv);
    var r1 = new THREE.Mesh(new THREE.CylinderGeometry(0.032, 0.032, 0.025, 6), silverMetal);
    r1.position.set(px, CLAMP_Y, 0.14); r1.rotation.x = Math.PI / 2; standGroup.add(r1);
    var r2 = new THREE.Mesh(new THREE.CylinderGeometry(0.032, 0.032, 0.025, 6), silverMetal);
    r2.position.set(px, CLAMP_Y, -0.14); r2.rotation.x = Math.PI / 2; standGroup.add(r2);

    // 빨간 집게 턱 (위/아래)
    var ju = M(new THREE.BoxGeometry(0.28, 0.045, 0.18), red, CLAMP_TIP_X - 0.1, CLAMP_Y + 0.05, 0);
    ju.rotation.z = 0.05; standGroup.add(ju);
    var jd = M(new THREE.BoxGeometry(0.28, 0.045, 0.18), red, CLAMP_TIP_X - 0.1, CLAMP_Y - 0.05, 0);
    jd.rotation.z = -0.05; standGroup.add(jd);
    var tg = new THREE.SphereGeometry(0.035, 8, 8);
    var tu = M(tg, red, CLAMP_TIP_X + 0.04, CLAMP_Y + 0.06, 0); tu.scale.set(1, 0.6, 1.4); standGroup.add(tu);
    var td = M(tg, red, CLAMP_TIP_X + 0.04, CLAMP_Y - 0.06, 0); td.scale.set(1, 0.6, 1.4); standGroup.add(td);

    // 나비 나사
    standGroup.add(M(new THREE.CylinderGeometry(0.014, 0.014, 0.08, 6), chrome, CLAMP_TIP_X - 0.1, CLAMP_Y - 0.12, 0));
    standGroup.add(M(new THREE.SphereGeometry(0.024, 6, 6), silverMetal, CLAMP_TIP_X - 0.1, CLAMP_Y - 0.16, 0));

    standGroup.position.copy(STAND_POS);
    scene.add(standGroup);
    return standGroup;
  }
  ```

#### 2. 쇠그물 (석면 대용 철망) _(자동 포함 — `삼발이+쇠그물+초 (통합)`의 내부 호출에 필요)_

- 함수명: `buildWireGauze()` (또는 적절한 이름)
- 상세 스펙:

  **실물 구조**:
  - **정사각형 철망**: 한 변 ≈ 삼발이 링 지름 × 1.18, 삼발이 링 위에 올려놓음
  - **외곽 프레임**: 두꺼운 금속 테두리 4변
  - **철망 격자**: 촘촘한 와이어 20×20 이상, 프레임 안쪽에 가로·세로로 교차
  - **세라믹 패드**: 가운데 원형, 연한 베이지색 (열원이 직접 닿지 않는 절연부)
  - 세라믹 위에는 미세한 그을음 표현 (작은 반투명 원)

  **핵심 치수**:
  - 정사각형 한 변의 절반 `gauzeSize = 0.225` (전체 변 길이 0.45)
  - 프레임 두께 `frameT = 0.018`, 프레임 높이 `frameH = 0.008`
  - 철망 가닥 수 `wireCount = 20` (가로/세로 각 20개)
  - 철망 굵기 `wireThick = 0.0025`
  - 세라믹 반경 `ceramicR = gauzeSize * 0.58`
  - 그을음 반경 `ceramicR * 0.55`

  **재질**:
  - `frameMat` (외곽 프레임): `MeshStandardMaterial({ color: 0x888888, roughness: 0.3, metalness: 0.8 })`
  - `wireMat` (철망 가닥): `MeshBasicMaterial({ color: 0x666666 })`
  - `ceramicMat` (세라믹 패드): `MeshStandardMaterial({ color: 0xe8e0d4, roughness: 0.85, metalness: 0.0 })`
  - `sootMat` (그을음): `MeshBasicMaterial({ color: 0x888877, transparent: true, opacity: 0.18 })`

  **적층 순서** (y 좌표):
  - 프레임/철망: `gauzeY` 부근
  - 세라믹: `gauzeY + 0.005`
  - 그을음: `gauzeY + 0.006`

  **치수 비율**: 프레임 한 변 : 삼발이 링 지름 ≈ 1.18:1 / 세라믹 반지름 : 프레임 반 ≈ 0.58:1 / 철망 간격 ≈ 0.020

  **실행 가능한 구현 코드** (그대로 사용 권장):

  ```javascript
  function buildWireGauze(parentGroup, gauzeY) {
    var gauzeSize = 0.225;  // 정사각형 한 변의 절반 (전체 변 길이 0.45)

    // — 외곽 프레임 (두꺼운 금속 테두리) —
    var frameMat = new THREE.MeshStandardMaterial({ color: 0x888888, roughness: 0.3, metalness: 0.8 });
    var frameT = 0.018;  // 프레임 두께
    var frameH = 0.008;  // 프레임 높이
    // 상변
    parentGroup.add(M(new THREE.BoxGeometry(gauzeSize * 2, frameH, frameT), frameMat,
      0, gauzeY + frameH / 2, -gauzeSize + frameT / 2));
    // 하변
    parentGroup.add(M(new THREE.BoxGeometry(gauzeSize * 2, frameH, frameT), frameMat,
      0, gauzeY + frameH / 2, gauzeSize - frameT / 2));
    // 좌변
    parentGroup.add(M(new THREE.BoxGeometry(frameT, frameH, gauzeSize * 2), frameMat,
      -gauzeSize + frameT / 2, gauzeY + frameH / 2, 0));
    // 우변
    parentGroup.add(M(new THREE.BoxGeometry(frameT, frameH, gauzeSize * 2), frameMat,
      gauzeSize - frameT / 2, gauzeY + frameH / 2, 0));

    // — 철망 격자 (촘촘하게) —
    var wireMat = new THREE.MeshBasicMaterial({ color: 0x666666 });
    var wireCount = 20;
    var innerSize = gauzeSize - frameT;
    var wireSpacing = (innerSize * 2) / (wireCount + 1);
    var wireThick = 0.0025;

    for (var wi = 1; wi <= wireCount; wi++) {
      var offset = -innerSize + wi * wireSpacing;
      // 가로선
      var hw = new THREE.Mesh(
        new THREE.BoxGeometry(innerSize * 2, 0.002, wireThick), wireMat);
      hw.position.set(0, gauzeY + 0.003, offset);
      parentGroup.add(hw);
      // 세로선
      var vw = new THREE.Mesh(
        new THREE.BoxGeometry(wireThick, 0.002, innerSize * 2), wireMat);
      vw.position.set(offset, gauzeY + 0.003, 0);
      parentGroup.add(vw);
    }

    // — 세라믹 패드 (가운데 원형, 연한 베이지) —
    var ceramicR = gauzeSize * 0.58;
    var ceramicMat = new THREE.MeshStandardMaterial({
      color: 0xe8e0d4, roughness: 0.85, metalness: 0.0
    });
    var ceramic = new THREE.Mesh(new THREE.CircleGeometry(ceramicR, 32), ceramicMat);
    ceramic.rotation.x = -Math.PI / 2;
    ceramic.position.y = gauzeY + 0.005;
    parentGroup.add(ceramic);

    // 세라믹 위 그을음 자국 (반투명 어두운 원)
    var sootMat = new THREE.MeshBasicMaterial({
      color: 0x888877, transparent: true, opacity: 0.18
    });
    var soot = new THREE.Mesh(new THREE.CircleGeometry(ceramicR * 0.55, 20), sootMat);
    soot.rotation.x = -Math.PI / 2;
    soot.position.y = gauzeY + 0.006;
    parentGroup.add(soot);
  }
  ```

#### 3. 삼발이+쇠그물+초 (통합)

- 함수명: `buildCandleAssembly()` (또는 적절한 이름)
- 상세 스펙:

  **※ 구성**: 가열 실험에서 삼발이, 쇠그물, 초는 **하나의 Group으로 묶어서** 사용자가 드롭한 위치에 동적 생성합니다.

  **전체 구조**:
  - 삼발이 (링 + 다리 3개) — `buildTripod`와 동일 형상
  - 쇠그물 (외곽 프레임 + 철망 격자 + 세라믹 패드 + 그을음) — `buildWireGauze`와 동일 형상
  - 초 (납작한 티라이트 모양 + 심지)
  - 불꽃 (외부 콘 + 내부 코어 + PointLight)

  **핵심 치수**:
  - 삼발이 링 반경 `ringR = 0.19`, 링 높이 `ringY = 0.63`
  - 쇠그물 위치: `ringY + 0.016` (링보다 살짝 위)
  - 초 (티라이트): `CylinderGeometry(0.090, 0.090, 0.036, 18)` — 납작하고 넓은 형태
  - 초 위치: `y = ringY + 0.036` (쇠그물 바로 위)
  - 심지: `y = ringY + 0.066` 부근
  - 불꽃: `y = ringY + 0.112`
  - **전체 그룹 스케일**: `1.4156` (전체적으로 약 41% 확대)
  - **그룹 위치**: `(wx, 0.02, wz)` — 사용자가 드롭한 좌표 + 바닥에서 살짝 띄움

  **재질**:
  - `lm` (삼발이 링/다리/발받침): `MeshStandardMaterial({ color: 0xc8c8c8, roughness: 0.2, metalness: 0.9 })`
  - `waxMat` (초 본체): `MeshStandardMaterial({ color: 0xf0ece0, roughness: 0.65, transparent: true, opacity: 0.88 })`
  - 심지 위/아래: `MeshBasicMaterial({ color: 0x444444 })` / `MeshBasicMaterial({ color: 0x333333 })`
  - 외부 불꽃: `MeshBasicMaterial({ color: 0xfdcb6e, transparent: true, opacity: 0.9 })`
  - 내부 불꽃: `MeshBasicMaterial({ color: 0xfff8ee, transparent: true, opacity: 0.95 })`
  - 불꽃 빛: `PointLight(0xff9500, 1.6, 4)`

  **중요한 이름(name) 속성** — `animate()` 루프에서 흔들림 애니메이션을 위해 참조:
  - 외부 불꽃: `name = "flame"`
  - 내부 불꽃: `name = "flameInner"`
  - 불꽃 빛: `name = "flameLight"`

  **불꽃 흔들림** (animate() 루프에서 호출):
  ```javascript
  if (flameMesh) {
    var tt = Date.now();
    flameMesh.scale.x = 1 + Math.sin(tt * 0.013) * 0.1;
    flameMesh.scale.y = 1 + Math.sin(tt * 0.016) * 0.15;
    if (innerFlameMesh) {
      innerFlameMesh.scale.x = 1 + Math.sin(tt * 0.017) * 0.08;
      innerFlameMesh.scale.y = 1 + Math.cos(tt * 0.011) * 0.12;
    }
    if (flameLight) flameLight.intensity = 1.6 + Math.sin(tt * 0.01) * 0.3;
  }
  ```

  **실행 가능한 구현 코드** (그대로 사용 권장):

  ```javascript
  function buildCandleAssembly(wx, wz) {
    var group = new THREE.Group();
    var lm = new THREE.MeshStandardMaterial({ color: 0xc8c8c8, roughness: 0.2, metalness: 0.9 });
    var ringR = 0.19, ringY = 0.63;
    group.add(function(){ var r = new THREE.Mesh(new THREE.TorusGeometry(ringR, 0.010, 8, 36), lm);
      r.position.y = ringY; r.rotation.x = Math.PI / 2; return r; }());
    for (var li = 0; li < 3; li++) {
      var ang = li * 2 * Math.PI / 3, sa = Math.sin(ang), ca = Math.cos(ang);
      var tx = ringR * sa, tz = ringR * ca, bx = 0.28 * sa, bz = 0.28 * ca;
      var dx = bx - tx, dy = -ringY, dz = bz - tz;
      var al = Math.sqrt(dx * dx + dy * dy + dz * dz);
      var arm = new THREE.Mesh(new THREE.CylinderGeometry(0.011, 0.013, al, 8), lm);
      arm.position.set((tx + bx) / 2, ringY / 2, (tz + bz) / 2);
      var aq = new THREE.Quaternion();
      aq.setFromUnitVectors(new THREE.Vector3(0, 1, 0), new THREE.Vector3(dx, dy, dz).normalize());
      arm.setRotationFromQuaternion(aq); arm.castShadow = true; group.add(arm);
      group.add(M(new THREE.CylinderGeometry(0.014, 0.014, 0.02, 8), lm, bx, 0.012, bz));
    }
    buildWireGauze(group, ringY + 0.016);

    // 초 (티라이트 — 납작하고 넓은 형태)
    var waxMat = new THREE.MeshStandardMaterial({ color: 0xf0ece0, roughness: 0.65, transparent: true, opacity: 0.88 });
    var wax = new THREE.Mesh(new THREE.CylinderGeometry(0.090, 0.090, 0.036, 18), waxMat);
    wax.position.y = ringY + 0.036; wax.castShadow = true; group.add(wax);
    group.add(M(new THREE.CylinderGeometry(0.003, 0.003, 0.022, 4),
      new THREE.MeshBasicMaterial({ color: 0x444444 }), 0, ringY + 0.066, 0));
    group.add(M(new THREE.CylinderGeometry(0.003, 0.002, 0.008, 4),
      new THREE.MeshBasicMaterial({ color: 0x333333 }), 0, ringY + 0.081, 0));

    // 불꽃 (외부 + 내부 + PointLight)
    var fg = new THREE.SphereGeometry(0.035, 10, 14); fg.scale(1, 2.4, 1);
    var fm = new THREE.Mesh(fg, new THREE.MeshBasicMaterial({ color: 0xfdcb6e, transparent: true, opacity: 0.9 }));
    fm.position.y = ringY + 0.112; fm.name = "flame"; group.add(fm);
    var ig = new THREE.SphereGeometry(0.018, 8, 10); ig.scale(1, 2.0, 1);
    var im = new THREE.Mesh(ig, new THREE.MeshBasicMaterial({ color: 0xfff8ee, transparent: true, opacity: 0.95 }));
    im.position.y = ringY + 0.122; im.name = "flameInner"; group.add(im);
    var fl = new THREE.PointLight(0xff9500, 1.6, 4); fl.position.y = ringY + 0.112; fl.name = "flameLight"; group.add(fl);

    group.scale.set(1.4156, 1.4156, 1.4156);
    group.position.set(wx, 0.02, wz);
    return group;
  }
  ```

> 장비를 만들고 `scene.add(group)` 한 뒤, 적절한 위치에 배치하세요. 뼈대 HTML의 `init3DScene()` 함수 끝부분(★⑤ 마커가 있는 곳)에서 호출합니다.

---

## ★⑥ 드래그 인터랙션 (단계별 바인딩)

뼈대 HTML의 `★⑥` 마커 영역에 단계별 드래그 이벤트와 단계 전환 로직을 작성하세요.
공통 드래그 시스템(마우스+터치, 고스트 엘리먼트, screenToWorld)은 뼈대에 이미 구현되어 있으니, **단계별 바인딩**만 추가하면 됩니다.

### 단계별 흐름 (3단계)

**Step 1** — 학생 행동: 길게 자른 구리판, 정사각형 구리판, ㄷ모양 구리판 중 하나를 3D 씬의 고정 집게 쪽 드롭 존으로 드래그

  - UI 전환: 사이드 패널 숨김 -> '초' 패널 표시
  - 완료 조건: 3D 드롭 존에 구리판 드롭 성공
  - 가이드: "구리판 한 개를 골라 고정 집게 쪽으로 옮겨 보세요."
  - mp3: `tts_take2.mp3`

**Step 2** — 학생 행동: 초를 구리판 아래 초록색 표시 부분 드롭 존으로 드래그
  - UI 전환: 사이드 패널에 '다시 하기' 버튼 및 텍스트 표시
  - 완료 조건: 3D 드롭 존에 초 드롭 성공
  - 가이드: "초를 구리판 아래 초록색 표시 부분으로 옮겨 보세요."
  - mp3: `tts_take3.mp3`

**Step 3**
  - UI 전환: 열 변색 붙임딱지의 색깔이 모두 변하면 우측 하단에 '실험 정리하기' 버튼 나타남.
  - 가이드 + 나레이션 (2개 세그먼트, **순차 재생**):
    1) 가이드 "열 변색 붙임딱지의 색깔 변화를 관찰해 보세요." / mp3 `tts_take4.mp3` / 단계 시작 즉시 재생
    2) 가이드 "초에서 가까운 곳부터 구리판을 따라 색이 변해요." / mp3 `tts_take5.mp3` / 이전 세그먼트 종료 후 3초 지연

### 구현 방식

- 각 카드 요소(`.card[data-step="N"]`)에 `mousedown` + `touchstart` 이벤트 바인딩
- 드래그 시 고스트 엘리먼트 생성 → 따라다니기
- `mouseup`/`touchend` 시 3D 드롭 존(`#drop-zone-indicator` 또는 raycaster) 안인지 검사
- 성공 시 `currentStep++`, `updateDots()`, `updateGuide(...)`, 다음 패널 표시, 다음 take 오디오 재생
- **드래그 영역(드롭 존)은 화면 확대/축소/회전과 무관하게 3D 좌표에 고정** — 매 프레임 raycaster로 화면 좌표 갱신

---

## ★⑦ 시뮬레이션 코어 (실험의 본체)

뼈대 HTML의 `★⑦` 마커 영역에 시뮬레이션 코어 코드를 작성하세요.

### 사용 패턴: (자유 구현 — 사용자 기술 기반)

### 핵심 현상 (사용자 기술)

- 열 변색 붙임딱지의 색깔이 분홍색에서 흰색으로 변할 때 초를 중심으로 원 모양으로 초에서 멀어질수록 색깔이 변함. 초에서 가까운 곳부터 변해야 되고, 초를 드래그하자마자 변하기 시작해야 돼.
- 길게 자른 구리판, 정사각형 구리판, ㄷ모양 구리판에서 열 변색 붙임딱지의 색깔이 변하는 빠르기는 모두 똑같게 만들어 줘.

### 시각화 방법

- 초를 구리판 아래로 드래그하면 열 변색 붙임딱지의 색깔이 바로 변하기 시작하도록 만들어 줘.
- 구리판 아래 책상 바닥에 구리판과 똑같은 모양으로 초록색으로 표시해 줘. 초록색 영역 내에서 초를 원하는 곳에 드래그할 수 있도록 만들어 줘.
- 길게 자른 구리판, 정사각형 구리판, ㄷ모양 구리판 모두 두께를 1mm로 표현해 줘.

### 추가 참고

- 길게 자른 구리판, 정사각형 구리판, ㄷ모양 구리판 모두 구리판을 고정집게로 드래그했을 때 구리판이 고정집게의 끝부분에 고정되도록 구현해 줘.
- 3D 길게 자른 구리판, 정사각형 구리판, ㄷ모양 구리판 모두 구리판 윗면에 분홍색 열 변색 붙임딱지가 붙어 있는 모습으로 만들어 줘.
- 우측 패널에 있는 길게 자른 구리판, 정사각형 구리판, ㄷ모양 구리판도 모두 구리판 윗면에 분홍색 열 변색 붙임딱지가 붙어 있는 모습으로 만들어 줘.
- ㄷ모양 구리판의 모양은 ㄷ모양으로 잘 표현해 줘.

### 구현 가이드

- 시뮬레이션 시작 트리거: 마지막 학생 행동 단계 완료 시 `isSimulating = true`
- `animate()` 루프에서 `isSimulating`이 true이면 매 프레임 시뮬레이션 업데이트
- 속도 조절(`simSpeed`)을 시뮬 코어에서 참조하여 가속/감속 지원 — 뼈대의 `★⑦` 영역에는 `simSpeed` 변수와 속도 조절 UI가 이미 들어있습니다
- 시뮬레이션 시작 약 10~15초 후 `summaryBtn` 또는 `next-btn`을 표시 (뼈대 코드에 패턴 있음)
- **추가/제거 시 뼈대의 공통 함수(`updateSimulation()`, `simSpeed` 변수, `next-btn` 표시 로직)는 그대로 활용** — 새로 만들지 마세요

---

## ★⑧ 리셋 처리 (실험별 상태 초기화)

뼈대 HTML의 `★⑧` 마커 영역(`resetExperiment()` 함수 안의 실험별 정리 블록 + `restartExperiment()` 안)에 아래 코드를 추가하세요.

```javascript
// ★⑧ 실험별 상태/3D 오브젝트 정리 코드
function resetExperimentSpecific() {
  // 1) 동적으로 생성된 3D 오브젝트 제거
  //    예: scene.remove(inkParticles); inkParticles = null;
  //         scene.remove(flameMesh);   flameMesh   = null;

  // 2) 시뮬레이션 상태 변수 초기화
  //    예: convTime = 0; particleData = []; heatGrid = [];

  // 3) 사이드 패널 초기화 (모든 카드 다시 표시 또는 첫 단계 카드만 표시)
  //    공통 함수가 처리하는 부분(currentStep, updateDots, updateGuide)은 뼈대이 자동 처리
}
```

### 결과 요약 나레이션 트리거 (있는 경우)

`★⑧` 영역의 `goToSummary()` 함수 안에서 결과 요약 팝업을 띄운 직후 다음을 호출하세요:

```javascript
playSummarySegments();  // 결과 요약 다중 세그먼트 순차 재생 (뼈대 v2 함수)
```

---

## 최종 체크리스트

뼈대 HTML 수정 후 다음을 확인하세요:

- [ ] ★① CSS 변수 3개만 변경됐는가? (다른 CSS는 그대로)
- [ ] ★② `<title>`, 헤더, 탐구 목표 팝업, dot 개수(3개), 사이드 카드, 결과 요약이 모두 채워졌는가?
- [ ] ★③ `audioFiles`와 `audioTexts`의 키가 일치하는가? (`take1`, `take2`, `take3`, `take4_1`, `take4_2`, `summary_1`, `summary_2`)
- [ ] ★④ `guideMessages` 배열 길이가 3인가?
- [ ] ★④ `stepSegments` / `summarySegments` 객체가 정확히 정의되어 있고, 각 audioKey가 audioFiles의 키와 일치하는가?
- [ ] ★④ Step 진입 시 `playStepSegments(stepIndex)`가 호출되는가? (다중 세그먼트 단계에서 가이드가 자동 갱신되어야 함)
- [ ] ★⑤ 모든 장비 build 함수가 `init3DScene` 끝에서 호출되는가?
- [ ] ★⑥ 단계별 드래그 → 단계 전환 → 다음 take 오디오 재생이 끊김 없이 작동하는가?
- [ ] ★⑦ 시뮬레이션이 마지막 학생 행동 후 자동 시작하는가? `isSimulating` 플래그가 토글되는가?
- [ ] ★⑧ 리셋 시 모든 동적 오브젝트가 정리되고, 새로 시작 시 잔재가 남지 않는가?
- [ ] **마커 밖 코드(공통 구조, 변수명, 함수명, 클래스명)를 변경하지 않았는가?**

## 팝업창 UI 규칙 (필수)

**탐구 목표 팝업창(`#objective-popup`)과 실험 결과 정리 팝업창(`#summary-overlay`)의 제목·본문·핵심 개념 박스에 이모지를 절대 사용하지 마세요.**

- 제목 예시: `🎯 탐구 목표` ❌ → `탐구 목표` ✅
- 제목 예시: `🌊 실험 결과 정리` ❌ → `실험 결과 정리` ✅
- 핵심 개념 박스 앞의 `💡`, `📌`, `✨` 등도 모두 제거
- 사용자가 이모지를 포함해 입력했더라도, 팝업 렌더링 시에는 이모지를 제외하고 텍스트만 표시

헤더·마스코트·버튼 등 팝업 외 UI 요소에는 기존 이모지를 유지해도 됩니다. 이 규칙은 **팝업창 내부 텍스트에만** 적용됩니다.

## 주의사항 (꼭 지켜주세요)

1. **마커 밖 코드는 절대 수정 금지** — CSS 클래스명, 변수명, 함수명, 이벤트 시스템, 공통 구조는 그대로 유지하세요.
2. **var만 사용** (let/const 금지) — 뼈대 전체가 ES5 호환으로 작성되어 있습니다.
3. **mouse + touch 이벤트 모두 바인딩** — 둘 중 하나만 하면 모바일 또는 데스크톱 중 하나에서 작동하지 않습니다.
4. **오디오는 외부 mp3 파일** (base64 내장 금지) — 같은 폴더에 mp3 파일들을 함께 두세요.
5. **드래그 고스트 offset 계산** — `ox = clientX - rect.left`로 카드 좌상단 기준 오프셋을 정확히 잡으세요.
6. **각 Step별 UI 표시/숨김 정확히 구현** — 한 단계의 카드는 다음 단계로 넘어갈 때 사라져야 합니다.
7. **나레이션은 교과서 전체 문장 그대로 사용** — 학생이 들을 텍스트는 입력값을 그대로 쓰고, 임의로 줄이거나 늘리지 마세요.
8. **결과 파일은 단일 HTML** — 외부 CSS/JS 파일로 분리하지 마세요. (mp3는 별개)
