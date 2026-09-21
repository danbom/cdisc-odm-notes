# 📌 Study 스터디
**Body** :<br>
🥇 `GlobalVariables` 전역 변수<br>
🥈 `BasicDefinitions?` 기본 정의<br>
🥉 `MetaDataVersion*` 메타데이터 버전

**Attributes** :<br>
`OID(Object Identifier)` oid

**Contained in** : ODM

<br>

```
This element collects static structural information about an individual study.
```
각 스터디에 대한 정적 구조 정보를 수집한다.

<br><hr>

# 🥇 GlobalVariables 전역 변수
**Body** :<br>
1️⃣ `StudyName` 스터디 이름<br>
2️⃣ `StudyDescription` 스터디 설명<br>
3️⃣ `ProtocolName` 프로토콜 이름

**Attributes** : NONE

**Contained in** : Study

<br>

```
GlobalVariables includes general summary information about the Study.
```
스터디에 대한 일반적인 요약 정보가 포함된다.

<br>

## 1️⃣ StudyName 스터디 이름
**Body** : `name`

**Attributes** : NONE

**Contained in** : GlobalVariables

<br>

```
This is a short external name for the study.
```
스터디의 짧은 외부 이름을 의미한다.

<br>

## 2️⃣ StudyDescription 스터디 설명
**Body** : `text`

**Attributes** : NONE

**Contained in** : GlobalVariables

<br>

```
This is a free-text description of the study.
```
스터디에 대한 자유 텍스트 설명을 의미한다.

<br>

## 3️⃣ ProtocolName 프로토콜 이름
**Body** : `name`

**Attributes** : NONE

**Contained in** : GlobalVariables

<br>

```
This is the sponsor's internal name for the protocol.
```
프로토콜에 대한 스폰서의 내부 이름을 의미한다.<br>
실질적으로는 `Protocol No.`로 주로 사용되며 `SPONSOR_001` 등 연구 고유 번호를 의미한다. 예를 들어 스터디 이름이 너무 긴 경우 스터디 이름의 약어로 쓰기도 한다.

<br><hr>

# 🥈 BasicDefinitions 기본 정의
**Body** :<br>
1️⃣ `MeasurementUnit*` 측정 단위

**Attributes** : NONE

**Contained in** : Study

<br>

## 1️⃣ MeasurementUnit 측정 단위
**Body** :<br>
🅰️ ️`Symbol` 기호<br>
🅱️ `Alias*` 별칭<br>

**Attributes** :<br>
🅰️ `OID` oid<br>
🅱 `Name` text

**Contained in** : BasicDefinitions

<br>

```
The physical unit of measure for a data item or value. The meaning of a MeasurementUnit is determined
by its Name attribute. Examples include kilograms, centimeters, cells/milliliter, etc.

Note: Standardizing the names of measurement units is beyond the scope of the ODM
```
데이터 항목 또는 값에 대한 물리적 측정 단위를 의미한다.<br>
**측정 단위**의 의미는 Name 속성에 의해 결정된다. 예를 들어 킬로그램(kg), 센티미터(cm), 셀(cell)/밀리리터(ml) 등이 있다.<br>

참고 : **측정 단위**의 이름 표준화는 ODM의 범위를 벗어난다.(?)

<br>

### 🅰️ ️Symbol(기호)
**Body** : `TranslatedText+` 번역 텍스트

**Attributes** : NONE

**Contained in** : MeasurementUnit

<br>

```
A human-readable name for a measurement unit.
```
사람이 읽을 수 있는 측정 단위의 이름을 의미한다.

<br>

### `TranslatedText` 번역 텍스트
**Body** : `text`

**Attributes** :<br>
**xml:lang** `languageTag` (optional)

**Contained in** :<br>
Decode, ErrorMessage, Question, Symbol, Description

<br>

```
Human-readable text that is appropriate for a particular language. TranslatedText elements typically occur
in a series, presenting a set of alternative textual renditions for different languages.

To find the text appropriate for a target language with tag LT, search for a TranslatedText element whose
xml:lang attribute matches LT exactly (ignoring case). If that fails, remove the ending subtag from LT and
repeat. If that fails, search for a TranslatedText without an xml:lang attribute and use that. If none is found,
there is no suitable text available.
```
특정 언어에 적합한 사람이 읽을 수 있는 텍스트를 의미한다. **번역 텍스트** 요소는 일반적으로 연속적으로 발생하며, 다른 언어에 대한 일련의 대체 텍스트 렌더링을 제공한다.

☝️ `LT` 태그가 있는 대상 언어에 적합한 텍스트를 찾으려면 `xml:lang` 특성이 `LT`와 정확히 일치(대소문자 무시)하는 **번역 텍스트**를 검색한다. `e.g. "fr-FR"`<br>
✌️ 실패한 경우, `LT`에서 종료 하위 태그를 제거하고 반복한다. `e.g. "fr"`<br>
👉 또 실패한 경우, `xml:lang` 속성이 없는 **번역 텍스트**를 검색해 사용한다. 만약 찾을 수 없는 경우, 사용 가능한 적절한 텍스트가 없는 것이다.

<br>

E.g.
 
|TranslatedTexts Present|Requested|Process|
|------|---|---|
|\<TranslatedText xml:lang="fr-CA">...<br> \<TranslatedText xml:lang="en-GB">...<br> \<TranslatedText>...|fr-FR|Look for xml:lang="fr-FR".<br>This is not found, so look for xml:lang="fr".<br>This is not found, so look for a TranslatedText with no `xml:lang`.<br>This is the text that should be used.|

<br>

```
To avoid ambiguity, a particular language tag must not occur more than once in a series of TranslatedText
elements. Also, it is not permitted to have more than one TranslatedText element without an xml:lang
attribute within the same parent.

Note: The xml:lang attribute is part of the XML standard.
```
모호성을 방지하려면 특정 언어 태그가 일련의 **번역 텍스트**에서 두 번 이상 발생하면 안된다.<br>
또한, 같은 부모에서 `xml:lang` 속성이 없는 **번역 텍스트**가 하나 이상 있으면 안된다.

참고: `xml:lang` 속성은 XML 표준의 일부이다.

<br><hr><br>

### 📑 메타문자
`*` : 반복을 의미하는 메타 문자. `*` 바로 앞에 있는 것이 0부터 무한대로 반복될 수 있다는 의미.<br>
`+` : 반복을 의미하는 메타 문자. 단, 최소 1번 이상 반복될 때 사용.<br>
`?` : 앞의 것이 있어도 되고 없어도 된다는 의미.

<br>

### 📑 데이터 형식
|Format Name|Schema Datatype|Allowed String Pattern|
|------|---|---|
|`text`|xs:string|any sequence of characters|
|`oid`|xs:string|any sequence of characters<br>(minLength="1")|
|`name`|xs:string|any sequence of characters<br>(minLength="1")|
|`languageTag`|xs:language|LL (-CC)* e.g. `fr-FR` |

> 참고 : `xs`는 `XSD` 스키마 선언시 접두사

<br><hr>

### 🔎 Reference
- https://wikidocs.net/4308#_3
- http://www.tcpschool.com/xml/xml_xsd_simpleType
