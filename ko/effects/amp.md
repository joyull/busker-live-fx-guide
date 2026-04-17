# AMP Simulator — 앰프 시뮬레이터

어쿠스틱 기타 앰프의 톤을 시뮬레이션합니다. 일렉트릭 앰프와 달리 **클린에 가까운 프리앰프 + 3밴드 톤 스택 + Color(캐릭터) + 스피커 시뮬**의 조합입니다.

![AMP Simulator 화면](../../screenshots/effect-amp.png)

## 화면 구성

```
┌────────────────────────────────────────────────┐
│  AMP Simulator                    [ ON ]       │
├────────────────────────────────────────────────┤
│   🎛 Gain   🎛 Bass   🎛 Middle  🎛 Treble     │
│   🎛 Color  🎛 Master [Speaker: ON ]           │
└────────────────────────────────────────────────┘
```

## 파라미터

| 파라미터 | 범위 | 설명 |
|---------|------|------|
| **Gain** | 0–40 dB | 프리앰프 게인. 어쿠스틱은 보통 **낮게** 유지 (0–10 dB) |
| **Bass** | −8 to +8 dB | 저역 쉘프 |
| **Middle** | −6 to +6 dB | 중역 벨 |
| **Treble** | −8 to +8 dB | 고역 쉘프 |
| **Color** | 0–100 % | 프리앰프 캐릭터 — 0=중립, 100=warm tube 느낌 |
| **Master** | −60 to 0 dB | 최종 출력 레벨 |
| **Speaker** | ON / OFF | 내장 스피커 캐비닛 시뮬 (OFF면 직결) |

## Gain과 Master의 차이

- **Gain**: 프리앰프 드라이브 수준. 높이면 약간 새츄레이션·고조파.
- **Master**: 최종 출력 볼륨. 앰프의 게인 스테이지에는 영향 없음.

어쿠스틱은 대부분 Gain 3–8 dB, Master −6~−3 dB 범위에서 시작.

## Color 노브

Color는 프리앰프 회로의 **비선형성(nonlinearity) 정도**를 제어합니다.
- 0 %: 투명, 리니어. 녹음·라인 출력 적합
- 30–50 %: 살짝 따뜻한 톤 (추천 기본값)
- 80–100 %: 진공관 같은 하모닉스, 스트러밍에서 두툼한 질감

## Speaker 시뮬

**ON**: 소형 어쿠스틱 앰프 캐비닛(8인치~10인치) 특성 시뮬 — 고역 롤오프 + 저역 공진.
- **라이브 PA**나 **DI 직결 녹음**을 한다면 **ON 추천**. PA의 평탄 응답 스피커가 DI 신호를 쏘면 너무 날카롭기 때문.
- **IR Loader를 쓴다면 OFF** — IR Loader가 캐비닛 역할을 대신합니다.

## 조작 예시

### 포크/팝 스트러밍
- Gain 5 dB, Bass +1, Middle 0, Treble +2, Color 40%, Master −3 dB, Speaker ON

### 핑거스타일 녹음
- Gain 2 dB, Bass 0, Middle −1, Treble +1, Color 20%, Master −6 dB, Speaker OFF

### 따뜻한 바디 강조 (드레드넛)
- Gain 6 dB, Bass +2, Middle +1, Treble 0, Color 60%, Master −4 dB, Speaker ON

### 라이브 안전
- Gain 4 dB, Bass 0, Middle 0, Treble 0, Color 30%, Master −8 dB, Speaker ON
- EQ·IR Loader로 추가 조정

## IR Loader와의 관계

**AMP Simulator → Boost → IR Loader** 순서. Speaker가 ON이면 AMP 내부 시뮬 캐비닛 + IR 캐비닛이 이중으로 들어가 소리가 답답해집니다. IR을 로드한 경우 **Speaker를 OFF** 해서 IR만 캐비닛 역할을 하도록 하세요.
