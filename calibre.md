지금까지 확인한 Calibre 관련 명령어들을 종합하여, 그 정체와 용도를 표로 정리하고 성격별로 분류해 드립니다. 반도체 설계 환경에서 각 도구가 어떤 단계에서 쓰이는지 파악하는 데 도움이 되실 것입니다.

### **1. Calibre 명령어 종합 정리표**

| 명령어 | 추정 프로그램 이름 | 주요 용도 및 설명 |
| --- | --- | --- |
| **`calibredrv`** | **DESIGNrev** | **표준 레이아웃 뷰어.** 대용량 GDS/OASIS 파일을 빠르게 열고 확인하며, Tcl 스크립트를 통한 자동화 지원. |
| **`caliberedp`** | **EDP** | **데이터 처리 자동화 엔진.** 레이아웃 편집, 데이터 추출, 속성(Property) 변경 등 배치(Batch) 작업에 특화. |
| **`calibrewb`** | **WORKbench** | **고급 공정 설계 도구.** 리소그래피 시뮬레이션 및 마스크 패턴 보정(OPC) 작업에 사용되는 상위 툴. |
| **`calibrerdwb`** | **Remote WB** | **원격 최적화 WORKbench.** VNC나 원격 접속 환경에서 화면 전송 효율을 높인 버전. |
| **`calibrerve`** | **RVE** | **결과 분석 환경.** DRC/LVS 등 검증 결과 리스트를 보여주고 레이아웃의 에러 위치와 연동해주는 창. |
| **`calview`** | **Calibre View** | **기생 성분 데이터 변환.** PEX(기생 성분 추출) 결과를 Cadence Virtuoso 시뮬레이션용 데이터로 변환. |
| **`calibredfme`** | **DFM Explorer** | **제조 최적화 분석.** 수율에 영향을 주는 디자인 취약점을 분석하고 결과를 관리하는 도구. |
| **`calibredfm`** | **DFM** | **제조 설계 보정.** Metal Fill(더미 채우기)이나 비아 보강 등 제조 수율을 높이기 위한 실제 레이아웃 수정 수행. |
| **`calibreshield`** | **IP Shield** | **IP 보안.** 설계 데이터(GDS)의 핵심 부분을 암호화하거나 외부 유출 시 보이지 않게 처리하는 보안 도구. |
| **`calibrepm`** | **Pattern Matching** | **패턴 검색.** 복잡한 룰 대신 이미지(패턴)를 정의하여 레이아웃 내에서 동일한 모양을 찾아내는 기능. |
| **`calibremt`** | **Multi-Threading** | **성능 옵션.** 단독 프로그램이 아니라, CPU 코어를 여러 개 써서 작업 속도를 높이는 실행 옵션. |

---

### **2. 성격 및 기능별 분류**

사용 목적에 따라 도구들을 그룹화하면 다음과 같습니다.

#### **① 레이아웃 확인 및 편집 (Viewer & Viewer-based Editor)**

실제 설계 도면을 눈으로 보거나 간단한 수정을 할 때 사용합니다.

* `calibredrv`, `calibrewb`, `calibrerdwb`

#### **② 검증 결과 디버깅 (Analysis & Debugging)**

설계 규칙(DRC) 위반이나 회로 일치 여부(LVS) 결과를 확인하고 분석합니다.

* `calibrerve`, `calibredfme`

#### **③ 대량 데이터 처리 및 자동화 (Batch Processing & Automation)**

사람이 눈으로 보지 않고, 컴퓨터가 수천 개의 좌표나 데이터를 자동으로 처리하게 할 때 사용합니다.

* `caliberedp`, `calibrepm` (좌표 캡처 자동화에 가장 적합한 카테고리)

#### **④ 특수 공정 및 데이터 변환 (Specialized Process)**

보안, 제조 수율 향상, 시뮬레이션 연동 등 특수한 목적을 위해 사용합니다.

* `calview`, `calibredfm`, `calibreshield`

---

### **3. 결론: "자동 캡처"를 위해 집중해야 할 도구**

현재 사용자님이 계획 중인 **"특정 좌표 자동 캡처"** 작업에 가장 적합한 도구 우선순위입니다.

1. **`calibredrv` (또는 `calibrewb`)**: 캡처 스크립트를 실행할 가장 표준적인 환경입니다. 이미 서버에 `calibrewb`가 있는 것을 확인하셨으니 이를 활용하면 됩니다.
2. **`calibrerve`**: 이미 나온 DRC 결과 파일이 있다면, 이 툴의 메뉴(`Export Screen Captures`)를 사용하는 것이 코딩 없이 가장 빠르게 캡처하는 방법입니다.
3. **`caliberedp`**: 만약 화면을 아예 띄우지 않고(Headless) 서버 자원만 써서 대량으로 캡처를 생성해야 할 때 사용합니다.

