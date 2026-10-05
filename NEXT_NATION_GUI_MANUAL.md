# NEXT NATION 대전 시작하기

이 설명은 지금 사용하는 PC 기준입니다. 아래 순서대로 따라 하세요.

## 1. 프로그램 켜기

1. 이미 열린 NEXT NATION 창이 있으면 닫으세요.
2. 키보드의 **윈도우 키**를 누르고 **PowerShell**을 검색해서 여세요.
3. 아래 글을 전부 복사해서 PowerShell에 붙여넣고 **Enter**를 누르세요.

```powershell
Set-Location -LiteralPath 'C:\Users\yujaerim\OneDrive\Desktop\게임AI스터디\Next Nation Arena\publish-20260630T110726Z-3-001\publish'
$env:Path = 'C:\Program Files\JetBrains\CLion 2025.2.2\bin\mingw\bin;' + $env:Path
Start-Process -FilePath '.\NationGuiTestingTool.exe' -WorkingDirectory (Get-Location).Path
```

## 2. 화면 위쪽 채우기

아래 표대로 입력하세요. 긴 주소는 복사해서 붙여넣으면 됩니다.

| 화면에 적힌 이름 | 넣을 값 |
|---|---|
| Random maps | `1` |
| Base seed | `42` |
| Parallel | `1` |
| Python | `C:\Users\yujaerim\miniconda3\python.exe` |
| C++ compiler | `C:\Program Files\JetBrains\CLion 2025.2.2\bin\mingw\bin\g++.exe` |
| NP / KP | 빈칸으로 두세요 |
| Both orders | 체크하세요 |

## 3. 대전할 코드 두 개 고르기

**왼쪽 선수 고르기**

1. **LEFT sources** 아래의 **Add**를 누르세요.
2. 파일 선택 창의 **파일 이름** 칸에 아래 주소를 붙여넣으세요.
3. **열기**를 누르세요.

```text
C:\Users\yujaerim\OneDrive\Desktop\게임AI스터디\codes\preliminary\codes\current.cpp
```

**오른쪽 선수 고르기**

1. **RIGHT sources** 아래의 **Add**를 누르세요.
2. **파일 이름** 칸에 아래 주소를 붙여넣으세요.
3. **열기**를 누르세요.

```text
C:\Users\yujaerim\OneDrive\Desktop\게임AI스터디\codes\preliminary\codes\submissions\106925.cpp
```

양쪽 목록에 파일이 하나씩 보이면 준비 끝입니다. **Attach data.bin**은 누르지 않아도 됩니다.

## 4. 대전 시작하기

1. **Run Batch**를 누르세요.
2. 결과가 나올 때까지 기다리세요.
3. 경기 기록을 보려면 **Open Log Folder**를 누르세요.

잘 되면 **Random maps**를 `10`으로 바꾸고 다시 **Run Batch**를 눌러 보세요. 더 많은 맵에서 대전합니다.

**오류가 뜨면:** 오류가 나온 화면을 캡처해서 보내주세요.
