---
name: workplace-excel-automation
description: |
  엑셀 업무 자동화 스킬. VBA 매크로, 수식, 피벗 테이블, 데이터 유효성 검사 등 한국 직장인의 엑셀 업무를 자동화합니다.
  Use when automating Excel tasks, Excel VBA, formulas, 엑셀 자동화, VBA, 피벗테이블, VLOOKUP.
allowed-tools: Read, Write, Edit, Bash
user-invocable: true
version: 1.0.0
status: active
---

# 엑셀 업무 자동화 가이드

## 빠른 참조 (Quick Reference)

### 핵심 수식 치트시트
| 수식 | 용도 | 예시 |
|------|------|------|
| VLOOKUP | 세로 조회 | `=VLOOKUP(A2,D:F,2,0)` |
| INDEX+MATCH | 유연한 조회 | `=INDEX(E:E,MATCH(A2,D:D,0))` |
| SUMIF | 조건부 합계 | `=SUMIF(B:B,"영업팀",C:C)` |
| COUNTIF | 조건부 개수 | `=COUNTIF(D:D,"완료")` |
| IFERROR | 오류 처리 | `=IFERROR(수식,"없음")` |
| TEXT | 형식 변환 | `=TEXT(A1,"YYYY-MM-DD")` |
| CONCATENATE | 텍스트 결합 | `=A1&" "&B1` |
| LEFT/MID/RIGHT | 문자열 추출 | `=LEFT(A1,3)` |

### VBA 단축키
- `Alt + F11`: VBA 편집기 열기
- `Alt + F8`: 매크로 실행
- `F5`: 현재 매크로 실행
- `F9`: 중단점 설정

---

## 필수 엑셀 수식

### VLOOKUP vs INDEX+MATCH 비교
```excel
' VLOOKUP - 왼쪽에서 오른쪽만 조회 가능
=VLOOKUP(A2, 직원DB!$A:$D, 3, 0)
' A2의 값을 직원DB A열에서 찾아 3번째 열 반환

' INDEX+MATCH - 방향 제한 없음, 더 강력
=INDEX(직원DB!$C:$C, MATCH(A2, 직원DB!$A:$A, 0))
' 더 유연하고 빠름 (대용량 데이터 권장)

' XLOOKUP (엑셀 365/2019 이상)
=XLOOKUP(A2, 직원DB!A:A, 직원DB!C:C, "없음")
' 가장 간단하고 강력
```

### 자주 쓰는 수식 모음
```excel
' 조건부 합계
=SUMIFS(금액열, 팀열, "영업팀", 월열, "3월")

' 중복 제거 개수
=SUMPRODUCT(1/COUNTIF(A2:A100, A2:A100))

' 날짜 계산
=DATEDIF(시작일, 종료일, "D")  ' 근속 일수
=NETWORKDAYS(시작일, 종료일)   ' 영업일 수

' 순위
=RANK(A2, $A$2:$A$100, 0)  ' 내림차순

' 조건부 텍스트
=IF(C2>=90,"우수",IF(C2>=70,"보통","미달"))
```

---

## VBA 매크로 모음

### 1. 데이터 정제 매크로
```vba
Sub 데이터정제()
    Dim ws As Worksheet
    Dim lastRow As Long

    Set ws = ActiveSheet
    lastRow = ws.Cells(ws.Rows.Count, "A").End(xlUp).Row

    ' 앞뒤 공백 제거
    Dim i As Long
    For i = 2 To lastRow
        ws.Cells(i, 1).Value = Trim(ws.Cells(i, 1).Value)
    Next i

    ' 중복 행 삭제
    ws.Range("A1:Z" & lastRow).RemoveDuplicates Columns:=1, Header:=xlYes

    MsgBox "데이터 정제 완료!"
End Sub
```

### 2. 월간 보고서 자동 생성
```vba
Sub 월간보고서생성()
    Dim wsData As Worksheet
    Dim wsReport As Worksheet
    Dim month As String

    month = Format(Date, "YYYY년 MM월")

    ' 보고서 시트 생성
    On Error Resume Next
    Application.DisplayAlerts = False
    Sheets("월간보고").Delete
    Application.DisplayAlerts = True
    On Error GoTo 0

    Set wsReport = Sheets.Add(After:=Sheets(Sheets.Count))
    wsReport.Name = "월간보고"

    ' 헤더 작성
    With wsReport
        .Cells(1, 1).Value = month & " 업무 현황 보고"
        .Cells(1, 1).Font.Size = 16
        .Cells(1, 1).Font.Bold = True

        .Cells(3, 1).Value = "항목"
        .Cells(3, 2).Value = "목표"
        .Cells(3, 3).Value = "실적"
        .Cells(3, 4).Value = "달성률"

        ' 헤더 스타일
        .Range("A3:D3").Interior.Color = RGB(70, 130, 180)
        .Range("A3:D3").Font.Color = RGB(255, 255, 255)
        .Range("A3:D3").Font.Bold = True
    End With

    MsgBox "월간 보고서 시트 생성 완료!"
End Sub
```

### 3. 이메일 자동 발송 (Outlook 연동)
```vba
Sub 이메일일괄발송()
    Dim olApp As Object
    Dim olMail As Object
    Dim ws As Worksheet
    Dim i As Long, lastRow As Long

    Set olApp = CreateObject("Outlook.Application")
    Set ws = ThisWorkbook.Sheets("발송목록")
    lastRow = ws.Cells(ws.Rows.Count, "A").End(xlUp).Row

    For i = 2 To lastRow
        If ws.Cells(i, 4).Value = "발송예정" Then
            Set olMail = olApp.CreateItem(0)
            With olMail
                .To = ws.Cells(i, 2).Value        ' 이메일 주소
                .Subject = ws.Cells(i, 3).Value   ' 제목
                .Body = ws.Cells(i, 5).Value      ' 본문
                .Send
            End With
            ws.Cells(i, 4).Value = "발송완료"
        End If
    Next i

    MsgBox lastRow - 1 & "건 발송 완료!"
End Sub
```

---

## 피벗 테이블 활용

### 피벗 테이블 빠른 설정
```
1. 데이터 범위 선택 → 삽입 → 피벗 테이블
2. 권장 레이아웃:
   - 행(Row): 분류 기준 (팀, 월, 제품명)
   - 열(Column): 비교 기준 (년도, 분기)
   - 값(Value): 집계할 수치 (금액, 수량)
   - 필터(Filter): 전체 필터 조건
```

### VBA로 피벗 테이블 생성
```vba
Sub 피벗테이블생성()
    Dim ws As Worksheet
    Dim wsData As Worksheet
    Dim pc As PivotCache
    Dim pt As PivotTable

    Set wsData = Sheets("데이터")

    ' 피벗 시트 생성
    Set ws = Sheets.Add
    ws.Name = "피벗분석"

    ' 피벗 캐시 생성
    Set pc = ThisWorkbook.PivotCaches.Create(
        SourceType:=xlDatabase,
        SourceData:=wsData.Range("A1").CurrentRegion
    )

    ' 피벗 테이블 생성
    Set pt = pc.CreatePivotTable(
        TableDestination:=ws.Range("A3"),
        TableName:="분석피벗"
    )

    ' 필드 배치 (컬럼명에 맞게 수정)
    With pt
        .PivotFields("팀명").Orientation = xlRowField
        .PivotFields("월").Orientation = xlColumnField
        .AddDataField .PivotFields("매출"), "합계:매출", xlSum
    End With

    MsgBox "피벗 테이블 생성 완료!"
End Sub
```

---

## 구현 가이드

### 엑셀 자동화 설계 순서
1. **현황 파악**: 현재 수작업으로 하는 작업 목록화
2. **반복 패턴 식별**: 매일/매주 동일하게 하는 작업
3. **수식으로 가능한지 먼저 검토**
4. **수식으로 안 되는 것만 VBA 적용**
5. **매크로 버튼 생성**: 비기술자도 사용 가능하게

### 데이터 유효성 검사 설정
```
1. 셀 범위 선택
2. 데이터 탭 → 데이터 유효성 검사
3. 허용: 목록 → 원본에 선택지 입력
   예: 영업팀,개발팀,마케팅팀,HR팀
4. 오류 메시지 탭: 친절한 안내 문구 설정
```

---

## 고급 패턴

### Power Query로 데이터 가져오기
```
데이터 탭 → 데이터 가져오기/변환 → Power Query
- 여러 파일 일괄 처리
- 자동 데이터 정제
- 조인/병합 작업
```

### 조건부 서식 활용
```excel
' 상위 10% 강조
홈 → 조건부 서식 → 상위/하위 규칙 → 상위 10%

' 데이터 막대로 시각화
홈 → 조건부 서식 → 데이터 막대

' 신호등 아이콘
홈 → 조건부 서식 → 아이콘 집합
```

---

## 관련 스킬

- workplace-data-report: 엑셀 데이터를 분석 보고서로 변환
- workplace-kpi-dashboard: KPI 대시보드 엑셀 구현
- workplace-workflow-design: 반복 업무 프로세스 자동화 설계
