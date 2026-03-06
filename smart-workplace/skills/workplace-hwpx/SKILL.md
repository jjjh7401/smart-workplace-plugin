---
name: workplace-hwpx
description: |
  한글(HWP/HWPX) 문서 생성 스킬. HWPX XML 구조를 사용하여 한글 문서를 프로그래밍 방식으로 생성합니다.
  Use when creating HWP documents, HWPX files, 한글 문서, HWP 생성, HWPX.
allowed-tools: Read, Write, Edit, Bash
user-invocable: true
version: 1.0.0
status: active
---

# 한글(HWPX) 문서 생성 가이드

## 빠른 참조 (Quick Reference)

### HWPX란?
- HWP(한글과컴퓨터)의 XML 기반 개방형 포맷
- 확장자: `.hwpx` (ZIP 아카이브 내부에 XML 파일 포함)
- 구조: `Contents/section0.xml` + `Contents/header.xml` 등으로 구성

### 주요 XML 요소
| 요소 | 설명 |
|------|------|
| `hc:HWPML` | 루트 요소 |
| `hc:Body` | 문서 본문 |
| `hc:Section` | 섹션 |
| `hc:P` | 단락(Paragraph) |
| `hc:Run` | 텍스트 런 |
| `hc:T` | 실제 텍스트 |
| `hc:Table` | 표 |
| `hc:Tr` | 표 행 |
| `hc:Tc` | 표 셀 |

### 빠른 생성 방법 (Python)
```python
# pip install python-docx (대안으로 docx 후 변환)
# 또는 hwpx 직접 생성
import zipfile, os

# HWPX = ZIP 형식의 XML 패키지
```

---

## HWPX 기본 구조

### 파일 구조
```
document.hwpx (ZIP 아카이브)
├── META-INF/
│   └── container.xml
├── Contents/
│   ├── header.xml      (문서 헤더: 스타일, 폰트 정의)
│   ├── section0.xml    (본문 내용)
│   └── ...
├── BinData/            (이미지 등 바이너리)
└── mimetype
```

### container.xml (필수)
```xml
<?xml version="1.0" encoding="UTF-8"?>
<container xmlns="urn:oasis:names:tc:opendocument:xmlns:container">
  <rootfiles>
    <rootfile full-path="Contents/header.xml"
      media-type="application/hwpml-package+xml"/>
  </rootfiles>
</container>
```

### header.xml 기본 구조
```xml
<?xml version="1.0" encoding="UTF-8"?>
<hh:Head xmlns:hh="http://www.hancom.co.kr/hwpml/2011/head"
         xmlns:hp="http://www.hancom.co.kr/hwpml/2011/paragraph">
  <hh:DocInfo>
    <hh:Title>문서 제목</hh:Title>
  </hh:DocInfo>
  <hh:IdMappings>
    <hh:Fonts>
      <hh:Font id="0" face="맑은 고딕" type="TTF"/>
      <hh:Font id="1" face="나눔고딕" type="TTF"/>
    </hh:Fonts>
    <hh:CharShapes>
      <hh:CharShape id="0" height="1000" fontId="0" bold="0"/>
      <!-- height: 포인트*100 (10pt = 1000) -->
    </hh:CharShapes>
    <hh:ParaShapes>
      <hh:ParaShape id="0" align="0"/>
      <!-- align: 0=왼쪽, 1=오른쪽, 2=가운데, 3=양쪽 -->
    </hh:ParaShapes>
  </hh:IdMappings>
</hh:Head>
```

### section0.xml 기본 구조
```xml
<?xml version="1.0" encoding="UTF-8"?>
<hs:Section xmlns:hs="http://www.hancom.co.kr/hwpml/2011/section"
            xmlns:hp="http://www.hancom.co.kr/hwpml/2011/paragraph">
  <hp:P id="0" parashapeId="0" styleId="0">
    <hp:Run charShapeId="0">
      <hp:T>안녕하세요. 한글 문서입니다.</hp:T>
    </hp:Run>
  </hp:P>
</hs:Section>
```

---

## 구현 가이드

### Python으로 HWPX 생성하기

```python
import zipfile
import os

def create_hwpx(filename, title, content):
    """
    간단한 HWPX 문서 생성
    content: 단락 텍스트 리스트
    """

    container_xml = '''<?xml version="1.0" encoding="UTF-8"?>
<container xmlns="urn:oasis:names:tc:opendocument:xmlns:container">
  <rootfiles>
    <rootfile full-path="Contents/header.xml"
      media-type="application/hwpml-package+xml"/>
  </rootfiles>
</container>'''

    header_xml = f'''<?xml version="1.0" encoding="UTF-8"?>
<hh:Head xmlns:hh="http://www.hancom.co.kr/hwpml/2011/head">
  <hh:DocInfo>
    <hh:Title>{title}</hh:Title>
  </hh:DocInfo>
  <hh:IdMappings>
    <hh:Fonts>
      <hh:Font id="0" face="맑은 고딕" type="TTF"/>
    </hh:Fonts>
    <hh:CharShapes>
      <hh:CharShape id="0" height="1000" fontId="0"/>
      <hh:CharShape id="1" height="1400" fontId="0" bold="1"/>
    </hh:CharShapes>
    <hh:ParaShapes>
      <hh:ParaShape id="0" align="0"/>
    </hh:ParaShapes>
  </hh:IdMappings>
</hh:Head>'''

    # 단락 생성
    paragraphs = ""
    for i, text in enumerate(content):
        paragraphs += f'''
  <hp:P id="{i}" parashapeId="0" styleId="0">
    <hp:Run charShapeId="0">
      <hp:T>{text}</hp:T>
    </hp:Run>
  </hp:P>'''

    section_xml = f'''<?xml version="1.0" encoding="UTF-8"?>
<hs:Section xmlns:hs="http://www.hancom.co.kr/hwpml/2011/section"
            xmlns:hp="http://www.hancom.co.kr/hwpml/2011/paragraph">
{paragraphs}
</hs:Section>'''

    # ZIP 파일로 패키징
    with zipfile.ZipFile(filename, 'w', zipfile.ZIP_DEFLATED) as zf:
        zf.writestr('mimetype', 'application/hwpml-package+xml')
        zf.writestr('META-INF/container.xml', container_xml)
        zf.writestr('Contents/header.xml', header_xml)
        zf.writestr('Contents/section0.xml', section_xml)

    print(f"HWPX 파일 생성 완료: {filename}")

# 사용 예시
create_hwpx(
    "업무보고.hwpx",
    "업무 보고서",
    [
        "업무 보고서",
        "",
        "1. 완료 업무",
        "  - 프로젝트 A 완료",
        "  - 보고서 작성",
        "",
        "2. 진행 중 업무",
        "  - 프로젝트 B 개발 중 (60%)",
    ]
)
```

### 표(Table) 포함 HWPX
```xml
<!-- section0.xml 내 표 삽입 -->
<hp:P id="0" parashapeId="0">
  <hp:Table id="1" rowCount="3" colCount="3">
    <hp:Tr>
      <hp:Tc colSpan="1" rowSpan="1">
        <hp:P id="2" parashapeId="0">
          <hp:Run charShapeId="0">
            <hp:T>항목</hp:T>
          </hp:Run>
        </hp:P>
      </hp:Tc>
      <hp:Tc colSpan="1" rowSpan="1">
        <hp:P id="3" parashapeId="0">
          <hp:Run charShapeId="0">
            <hp:T>내용</hp:T>
          </hp:Run>
        </hp:P>
      </hp:Tc>
    </hp:Tr>
  </hp:Table>
</hp:P>
```

---

## 고급 패턴

### 폰트 및 스타일 설정
```xml
<!-- 한글 문서 권장 폰트 설정 -->
<hh:Fonts>
  <hh:Font id="0" face="맑은 고딕" type="TTF"/>   <!-- 본문용 -->
  <hh:Font id="1" face="나눔명조" type="TTF"/>     <!-- 제목용 -->
  <hh:Font id="2" face="굴림" type="TTF"/>         <!-- 표/캡션용 -->
</hh:Fonts>

<!-- 글자 크기: height = 포인트 * 100 -->
<!-- 10pt = 1000, 12pt = 1200, 14pt = 1400 -->
```

### 대안: python-docx 활용 후 변환
```python
# python-docx로 생성 후 LibreOffice로 변환
from docx import Document

doc = Document()
doc.add_heading('업무 보고서', 0)
doc.add_paragraph('1. 완료 업무')
doc.save('report.docx')

# LibreOffice CLI로 변환 (LibreOffice 설치 필요)
# libreoffice --convert-to hwp report.docx
```

### 기존 HWPX 파일 읽기
```python
import zipfile

def read_hwpx_text(filename):
    """HWPX 파일에서 텍스트 추출"""
    import xml.etree.ElementTree as ET

    with zipfile.ZipFile(filename, 'r') as zf:
        with zf.open('Contents/section0.xml') as f:
            tree = ET.parse(f)
            root = tree.getroot()

            # 네임스페이스 처리
            ns = {'hp': 'http://www.hancom.co.kr/hwpml/2011/paragraph'}
            texts = root.findall('.//hp:T', ns)
            return '\n'.join(t.text or '' for t in texts)
```

---

## 관련 스킬

- workplace-korean-report: 보고서 내용 작성 후 HWPX로 변환
- workplace-proposal: 제안서를 HWPX 형식으로 생성
- workplace-hr-documents: 인사 문서 HWPX 생성
