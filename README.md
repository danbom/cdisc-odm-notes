# CDISC ODM 스터디 노트

CDISC ODM(Operational Data Model) v1.3 명세를 읽으며 정리한 한국어 노트 모음입니다.

임상시험 데이터 교환 표준을 개발자 관점에서 이해하려고 시작했습니다. EDC 화면을 만들 때 각 입력 필드가 결국 ODM의 어떤 요소로 직렬화되는지 모르면, "왜 이 필드에 이런 제약이 붙는지"를 계속 남의 결정으로만 받게 되더군요.

한국어로 된 ODM 명세 정리가 거의 없어서 공개해 둡니다.

## 기여자

네 명이 매일 정해진 분량을 읽고 각자 노트를 쓴 뒤 PR로 공유하는 방식으로 진행했습니다.

- [@danbom](https://github.com/danbom) (mineunyoung)
- [@ssso-pro1](https://github.com/ssso-pro1) (Soyeon Jang)
- [@mond1219](https://github.com/mond1219)
- [@mugju](https://github.com/mugju) (DongD)

각 노트의 저작자는 파일명에 표기된 작성자입니다.

## 내용

```
notes/
├── study/            Study 요소 전체 구조 — 4인 각자의 정리
├── day1/             GlobalVariables (StudyName, StudyDescription, ProtocolName)
├── day2/             MetaDataVersion — Include, Protocol, StudyEventDef, FormDef, ItemDef
├── day3/             CodeList, ArchiveLayout, MethodDef, ConditionDef
├── day4-codelist/    CodeList 심화
└── define/           Define-XML Dataset
```

항목별 상세 정리는 별도 문서로 두었습니다 →
**[CDISC ODM 한국어 정리 (GitBook)](https://mineunyoung.gitbook.io/3.1.1.3-metadataversion/)**

## 원문

노트는 **CDISC ODM 공식 명세**를 읽고 정리한 것입니다. 원문은 CDISC에서 직접 받으세요.

- [CDISC ODM 표준 페이지](https://www.cdisc.org/standards/data-exchange/odm)

명세 본문의 저작권은 CDISC에 있습니다. 이 저장소는 명세 원문을 재배포하지 않으며, 인용은 이해를 돕기 위한 범위로 한정했습니다.

예제 XML에 등장하는 식별자(`SPONSOR_001`, `EXAMPLE_ODM study` 등)는 모두 임의의 예시값입니다.

## 라이선스

노트 본문은 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.ko).
인용된 CDISC 원문은 해당 저작권자의 권리를 따릅니다.
