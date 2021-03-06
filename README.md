# preshoes-shoes

Preshoes - ESP-32S 센서 모듈

## 개요

<img src="/docs/preshoes-numbered.png" width="350px">

사용자의 신발 내에 위치한 센서를 사용하여 압력 데이터를 수집, Preshoes 모바일 애플리케이션으로 전달하는 역할을 수행합니다.

## 구성

센서 패널, 브릿지 보드, 그리고 MCU로 구성됩니다. 센서 패널과 브릿지 보드는 5264 14핀 커넥터 인터페이스를, MCU는 2.54mm pitch male 점퍼 케이블 커넥터 인터페이스를 제공합니다.

### 센서 패널

<img src="/docs/preshoes-dimension.png" width="350px">

센서 패널은 13줄로 연결됩니다. 12줄은 각 센서의 출력을, 1줄은 3.3v 전압을 전달합니다. Pull-down이 적용되지 않았습니다.

### 브릿지 보드

센서 패널은 pull-down 회로를 갖추지 않아 별도의 저항을 통한 GND 연결을 요구합니다. 이는 브릿지 보드에게 탑재되어 있습니다. 브릿지 보드는 MCU에게 ADC로 읽기 적절한 0v-3.3v 전압을 보내 줍니다.

## 연결

> **주의**   
브릿지 보드의 케이블 배열 순서와 센서 인덱스가 일치하지 않습니다. 아래 표를 참고하여 주세요.

| Cable | Sensor Index | GPIO |
|-------|--------------|------|
|  GND  |       -      |   -  |
|  Vcc  |       -      |   -  |
|   0   |       1      |   4  |
|   1   |       0      |   2  |
|   2   |       2      |   15 |
|   3   |       3      |   34 |
|   4   |       4      |   32 |
|   5   |       5      |   33 |
|   6   |       6      |   25 |
|   7   |       7      |   26 |
|   8   |       9      |   27 |
|   9   |       8      |   14 |
|   10  |       11     |   12 |
|   11  |       10     |   13 |

### MCU측 연결

<img src="/docs/pinout.png" width="350px">

아날로그 입력 핀은 보드 왼쪽에 9개, 오른쪽에 4개 존재합니다. 이중 `0`번 핀은 사용할 수 없습니다.

<img src="/docs/mcu-connection.png" width="350px">

브릿지 보드의 케이블 중 Vcc에 가까운 3줄은 MCU의 우측에, 나머지는 좌측에 연결합니다. 세로 방향으로는 순서대로 연결합니다.
