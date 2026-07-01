# 🟣 Synthwave Terrain — 80년대 레트로웨이브 무한 네온 그리드 비행

> **Three.js + Perlin Noise** 기반 — 보라색 네온 그리드 지형이 카메라를 향해 끝없이 다가오고, 거대한 레트로 태양이 지평선 너머로 서서히 지며 붉은 빛을 내뿜는 무한 비행 시뮬레이션. 지형 정점이 Perlin 노이즈로 실시간 춤추듯 변형됩니다.

[🇰🇷 한국어 (기본)](#) · [🇺🇸 English](#english)

---

## 🎬 라이브 데모 (Live Demo)

> **👉 [https://synthwave-terrain.vercel.app/](https://synthwave-terrain.vercel.app/)** — 브라우저에서 바로 실행 (60fps)

| | |
|---|---|
| ![Demo](https://img.shields.io/badge/Live-Demo-7C3AED?style=for-the-badge&logo=vercel&logoColor=white) | [![Repo](https://img.shields.io/badge/GitHub-sigco3111%2Fsynthwave--terrain-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sigco3111/synthwave-terrain) |
| ![Status](https://img.shields.io/badge/Status-Live-22C55E?style=flat-square) | ![Stack](https://img.shields.io/badge/Stack-Three.js_r160-000000?style=flat-square&logo=three.js&logoColor=white) |
| ![License](https://img.shields.io/badge/License-MIT-F1C40F?style=flat-square) | ![Deps](https://img.shields.io/badge/Dependencies-0-9CA3AF?style=flat-square) |

### 🎮 빠른 사용법

1. 위 데모 링크 클릭 → 브라우저에서 페이지 열기
2. **마우스 이동** — 시차 시점 변환 (부드러운 댐핑)
3. **마우스 드래그** — 카메라 회전
4. **자동 비행** — 페이지 로드 즉시 끝없는 지형 위로 전진
5. **자동 일몰** — 거대한 태양이 지평선 너머로 서서히 가라앉음
6. **H** 또는 우상단 × — 컨트롤 가이드 토글

---

## 🤖 생성 정보 (How this was made)

이 프로젝트의 코드는 아래 모델과 프롬프트를 이용해 **자동으로 생성**되었습니다.

### 📝 사용된 프롬프트 (원문)

```
Three.js와 Perlin Noise 알고리즘을 활용해 80년대 레트로웨이브 스타일의 보라색 네온 그리드 지형이 카메라를 향해 끝없이 다가오는 비행 시뮬레이션을 구현하되, 지형의 높낮이가 실시간으로 춤추듯 역동적으로 변하고 배경에는 거대한 레트로 태양이 서서히 지며 붉은빛을 내뿜는 몽환적인 장면을 만들어줘.

Implementation Advice: Use Three.js and a Perlin Noise library (like simplex-noise). Displace the vertices of a PlaneGeometry based on the noise value. Move the plane or the camera to simulate flight, looping the position to create an infinite terrain. 모든 의존관계의 코드를 하나의 HTML에 담는 형태로 코드 작성.
```

### 구현 핵심 기술

| 항목 | 접근법 |
|---|---|
| **지형 메시** | `PlaneGeometry` (128×128 segments) 정점을 Perlin/Simplex 노이즈 값으로 변위 |
| **무한 비행** | 카메라 또는 지면을 Z축으로 연속 이동 + 위치 루핑으로 끝없는 지형 구현 |
| **네온 그리드** | 그리드 셰이더 + 마젠타-시안 라인 색상, 발광 효과 |
| **레트로 태양** | 큰 원형 디스크 + 그라데이션 셰이더 + 시간에 따라 가라앉음 (0.5 cycle/30s) |
| **시점 제어** | 마우스 위치에 따른 시차 + 드래그 회전 (스프링 댐핑) |
| **포스트 프로세싱** | Bloom (네온 발광) + Chromatic Aberration + Film Grain |
| **다층 스카이라인** | 어두운 보라 → 마젠타 → 주황-노랑 그라데이션 (synthwave 톤) |

### 생성 환경

| 항목 | 값 |
|------|-----|
| **AI 도구** | OpenCode CLI |
| **모델** | `MiniMax-M3` |
| **입력 방식** | 위 프롬프트 1-shot |
| **방식** | 단일 HTML + ESM CDN 인라인 임포트 |
| **후처리** | 사람이 README 작성 및 구조 정리 |

---

## ✨ Features

- 🌌 **무한 지형** — Perlin Noise로 변위된 PlaneGeometry가 카메라를 향해 끝없이 흐름
- 🌀 **춤추는 노이즈** — 정점 높이가 실시간으로 sin·noise 결합으로 변형
- 🌅 **거대한 레트로 태양** — 반투명 그라데이션 디스크, 서서히 가라앉으며 붉은 광원
- 🟣 **네온 그리드** — 라인 셰이더로 synthwave 톤의 보라-마젠타 그물 코트
- 🎨 **3색 광선** — 마젠타 + 시안 + 오렌지-옐로우, 클래식 synthwave 팔레트
- 💡 **Bloom + Chromatic Aberration** — 네온 발광 + 어두운 가장자리 미세 RGB 분리
- 🎬 **시점 시차** — 마우스 위치에 따른 부드러운 시점 변형
- 📦 **제로 의존성** — 단일 HTML, Three.js + simplex-noise (ESM CDN)
- 🌠 **미스트 입자** — 거리에 따른 안개 + 가산 블렌딩 점 입자 (대기감)
- 🎞️ **Film Grain** — CRT/80년대 VHS 분위기의 미세한 노이즈 오버레이

---

## 🚀 실행 방법 (Quick Start)

### 방법 1: 로컬 서버 (권장)
```bash
cd path/to/synthwave-terrain
python3 -m http.server 8000
# → http://localhost:8000 접속
```

> ⚠️ `index.html` 더블클릭은 CORS / ESM 제약으로 일부 모듈이 차단될 수 있어요. **로컬 서버 권장.**

### 방법 2: 라이브 데모
별도 설치 없이 바로 확인:
👉 **https://synthwave-terrain.vercel.app/**

---

## 🎮 조작법 (Controls)

| 입력 | 효과 |
|---|---|
| **마우스 이동** | 시점 시차 (부드러운 댐핑) |
| **마우스 드래그** | 카메라 회전 |
| **자동 비행** | 페이지 로드 즉시 무한 전진 (플레이 없이도 진행) |
| **자동 일몰** | 거대한 태양이 30초 주기로 가라앉음 |
| **H** 또는 우상단 × | 컨트롤 가이드 표시/숨김 |

---

## 🛠️ 기술 스택 (Tech Stack)

| 영역 | 사용 기술 |
|---|---|
| **렌더링** | Three.js r160 · WebGL2 |
| **씬 그래프** | `PlaneGeometry` + 사용자 정의 셰이더 |
| **노이즈** | `simplex-noise` (ESM CDN) — Perlin 호환 |
| **포스트 프로세싱** | `EffectComposer` · `UnrealBloomPass` · `ChromaticAberration` (옵션) |
| **색상** | HSL 실시간 보간 (자황-시안 그라데이션) |
| **그리드** | 사용자 정의 `ShaderMaterial` + 라인 패턴 |
| **루프** | `requestAnimationFrame` |
| **의존성** | 없음 (Three.js + simplex-noise ESM CDN) |

---

## 🎨 디자인 결정 (Design Choices)

브레인스토밍 단계에서 내린 결정:

| 결정 포인트 | 선택 | 이유 |
|---|---|---|
| **구조** | 단일 HTML (모든 인라인) | 아트워크 성격 + 의존성 제로 + 즉시 공유 가능 |
| **지형 방식** | `PlaneGeometry` 정점 변위 + Z축 이동 | 카메라가 정지 → PlaneGeometry 자체를 흐름 (렌더 비용 ↓) |
| **노이즈 선택** | `simplex-noise` (Perlin 호환) | 구현 단순 + CDN 안정 |
| **레이어 수** | 2-layer (지형 + 태양) + 미스트 입자 | 깊이감은 안개·블룸으로 처리 |
| **그리드 톤** | 보라 + 마젠타 + 시안 라인 | 클래식 80s synthwave |
| **시간 흐름** | 자동 일몰 (사용자 입력 없이도 분위기 변화) | 정적 페이지에서도 살아있는 느낌 |
| **인터랙션 깊이** | 2단 (자동 비행 + 마우스 시점) | 깊이 들어가도 한 손 조작 가능 |
| **포스트 체인** | Bloom + Chromatic Aberration + Grain | CRT/VHS 느낌 강화 |

### 직접 커스터마이즈하고 싶다면

`index.html` 상단에서 다음 상수를 조정하면 분위기를 바꿀 수 있어요:

```js
const CONFIG = {
  TERRAIN_SIZE: 200,        // PlaneGeometry 한 변 길이
  TERRAIN_SEGMENTS: 128,    // PlaneGeometry segments (성능 트레이드오프)
  NOISE_SCALE: 0.02,        // 노이즈 주파수 (클수록 요철 격해짐)
  NOISE_SPEED: 0.3,         // 시간에 따른 노이즈 변화 속도
  FLIGHT_SPEED: 0.4,        // 자동 비행 속도
  SUN_CYCLE_SECONDS: 30,    // 일몰 1주기
  PALETTE: 'synthwave',     // synthwave / outrun / vaporwave
  BLOOM_STRENGTH: 1.4,      // 네온 발광 강도
  // ... 더 많은 옵션은 코드 내 주석 참조
};
```

---

## 🗺️ Roadmap

- [x] **v0.0** — 저장소 초기화 + 코딩미션 1차 README
- [x] **v0.1** — Perlin 노이즈로 변위된 PlaneGeometry + 자동 비행
- [x] **v0.2** — 네온 그리드 셰이더 + Bloom 포스트 프로세싱
- [x] **v0.3** — 거대한 레트로 태양 + 자동 일몰
- [x] **v0.4** — 미스트 입자 + 시점 시차 + UI 폴리시
- [x] **v1.0** — Vercel 배포 + 라이브 데모 + README 다층 구조화 ✅
- [ ] **v1.1 (예정)** — 오디오 리액티브 (마이크 → 비행 속도 / 노이즈 진폭)
- [ ] **v2.0 (예정)** — WebXR 모드 (`VREntry` 진입으로 immersive 비행)

---

## 📂 프로젝트 구조

```
synthwave-terrain/
├── README.md        # 이 문서 (다층 구조 + 한/영 통합)
├── index.html       # 단일 HTML (모든 코드 인라인, ESM CDN)
└── preview.png      # README 미리보기 캡처
```

> **단일 파일 구조 채택 이유** — 아트워크 성격 + 의존성 제로 + 즉시 공유. 빌드 단계 없이 CDN 두 줄(`three` + `simplex-noise`)로 어디서든 실행됩니다.

---

## 📜 License

MIT © 2026 sigco3111

---

## 🇺🇸 English

### Overview

**Synthwave Terrain** is an infinite neon-grid flight simulation in pure 80s retro-wave aesthetics. Built on **Three.js r160** with **simplex-noise** (Perlin-compatible) displacement, a `PlaneGeometry` flows continuously toward the camera as a giant retro sun sets slowly over the magenta horizon. The terrain's vertices dance in real time, giving the ground a low-poly neon heartbeat.

### AI Generation

The code in this repository was authored via **OpenCode CLI** using the **MiniMax-M3** model with the prompt shown in the Korean section above. All design choices and prompt engineering were performed by the repository owner.

| Item | Value |
|---|---|
| **Model** | `MiniMax-M3` |
| **Runtime** | OpenCode CLI |
| **Output** | Single HTML (ESM CDN importmap) |
| **License** | MIT |
| **Dependencies** | None (three@0.160 + simplex-noise from ESM CDN) |

### Features

- 🌌 **Infinite terrain** — Perlin-displaced `PlaneGeometry` flows toward camera
- 🌀 **Dancing noise** — Vertex heights morph in real time via Perlin + time
- 🌅 **Giant retro sun** — Translucent gradient disc that sets slowly, casting warm light
- 🟣 **Neon grid** — Magenta-cyan grid shader for synthwave ground coat
- 🎨 **3-color glow** — Magenta + cyan + orange-yellow classic synthwave palette
- 💡 **Bloom + Chromatic Aberration** — Neon glow + subtle RGB split on bright edges
- 🎬 **Parallax view** — Mouse-driven smooth viewpoint shift
- 📦 **Zero build deps** — Single HTML, ESM CDN imports
- 🌠 **Mist particles** — Distance fog + additive drift points for atmosphere
- 🎞️ **Film grain** — Subtle CRT/80s VHS noise overlay

### Controls

| Input | Effect |
|---|---|
| **Mouse move** | Parallax viewpoint (spring damping) |
| **Mouse drag** | Camera orbit |
| **Auto-flight** | Continuous forward motion on page load |
| **Auto-sunset** | Giant sun sets on a 30s cycle |
| **H** or top-right × | Toggle controls guide |

### Quick Start

```bash
python3 -m http.server 8000
# → http://localhost:8000
```

Or just open the live demo: **https://synthwave-terrain.vercel.app/**

### Stack

- **Three.js r160** — WebGL2 rendering + scene graph
- **simplex-noise (ESM CDN)** — Perlin-compatible terrain displacement
- **`EffectComposer`** — `UnrealBloomPass` + chromatic aberration + grain
- **`ShaderMaterial`** — Custom grid shader
- **Vanilla JS** (ESM modules)

### Roadmap

- [x] **v0.0** — Initial repo + coding-mission v1 README
- [x] **v0.1** — Perlin-displaced `PlaneGeometry` + auto-flight
- [x] **v0.2** — Neon-grid shader + bloom post-processing
- [x] **v0.3** — Giant retro sun + auto-sunset
- [x] **v0.4** — Mist particles + parallax + UI polish
- [x] **v1.0** — Vercel deploy + live demo + multi-layer README
- [ ] **v1.1 (planned)** — Audio-reactive (mic → flight speed / noise amplitude)
- [ ] **v2.0 (planned)** — WebXR mode (immersive flight via `VREntry`)

### Customize

Top of `index.html`:

```js
const CONFIG = {
  TERRAIN_SIZE: 200,        // PlaneGeometry side length
  TERRAIN_SEGMENTS: 128,    // segments (perf tradeoff)
  NOISE_SCALE: 0.02,        // noise frequency (higher = bumpier)
  NOISE_SPEED: 0.3,         // noise time-evolution rate
  FLIGHT_SPEED: 0.4,        // auto-flight speed
  SUN_CYCLE_SECONDS: 30,    // full sunset cycle
  PALETTE: 'synthwave',     // synthwave / outrun / vaporwave
  BLOOM_STRENGTH: 1.4,      // neon glow intensity
};
```

### License

MIT © 2026 sigco3111

---

## 🙏 Credits

- **Three.js** — WebGL 렌더링 엔진 + 씬 그래프 (mrdoob & contributors)
- **simplex-noise** — Perlin-compatible 노이즈 라이브러리
- **80s Synthwave 미학** — 클래식 레트로웨이브 비주얼 문화
- **AI 생성** — OpenCode CLI + `MiniMax-M3`
- **코딩미션 참조 페이지**: [cokac.com — 코드깎는노인](https://cokac.com/list/announcement/24)

---

<p align="center">
  <sub>🟣 Built with Three.js · simplex-noise · sigco3111 · MIT · AI-generated by MiniMax-M3</sub>
</p>
