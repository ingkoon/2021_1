# 안드로이드 개발
---
교재는 생능, 그림으로 쉽게 설명하는 안드로이드 프로그래밍

## 스마트폰
- 스마트폰 = 컴퓨터 + mp3플레이어 + 휴대용 게임기
- 다양한 앱 설치 가능
  
## 모바일 운영체제
- 구글의 안드로이드 
- 애플의 ios

## 모바일 운영체제 비교
- 개발언어는 각각 갈리는 추세
- 둘다 유닉스계열이다

||안드로이드|ios|
|------|---|---|
|개발 언어|Java, Kotlin, C, C++|C, C++, objective-C, Swift|
|라이센스|apache 2.0|Proprietary|
|사용자 인터 페이스|Graphical|Cocoa Touch|

## 개발자와 소비자가 만나는 공간
- 개발자와 소비자가 만나는 공간
- 개발자 -> 마켓 <- 소비자


## 안드로이드의 역사
- 2005년에 안드로이드 인수
- 2007년에 OHA(Open Handest Aliance)라는 컨소시엄 구성
- 2007년 안드로이드 SDK 1.0 발표
- 최초의 안드로이드 폰: HTC의 G1

## 안드로이드의 특징
- 재사용이 가능한 애플리케이션 프레임 워크
- 최적화된 달빅 가상 머신
- WebKit 기반의 내장된 웹브라우저
- OpenGL 2.0 지원하는 최적화된 그래픽
- SQLite 데이터베이스 지원
- 각종 오디오, 비디오 규격 지원
- 블루투스, EDGE, 3G, WiFi 지원
- 카메라, GPS, 나침판, 기속도계 지원
- 풍부한 개발 환경 제공 장치

## 새로운 자바 가상머신 ART
- ART는 4.4에서 새로 배포되는 자바 가상머신
- 사용자는 달빅과 ART 중에서 하나를 선택할 수 있다.
- ART의 특징
  - Ahead-of-time(AOT) 컴파일: 달빅은 필요할 때마다 앱을 컴파일하여 실행하지만 ART는 미리 앱을 컴파일 한다.
  - 향상된 가비지 콜렉션
  - 디버깅 향상

## 안드로이드 버전 vs 자바버전
- 람다식: 모두 호환
- 디폴트 및 정적 인터페이스 메소드: 모두 호환
- 메소드 참조: 모두 호환
- 형식 주석: 모두 호환
- 주석 반복: 모두 호환

## 애플리케이션의 기초 개념
- 실행 단계
  - 자바파일 -> 클래스파일 -> desugared -> dex

## 컴포넌트
- 애플리케이션은 컴포넌트로 이루어진다.
  - 액티비티
  - 서비스
  - 방송 수신자
  - 컨텐츠 제공자

## 액티비티
- 사용자 인터페이스 화면을 가지는 하나의 작업
- 액티비티들이 모여 애플리케이션이 된다.
- 이메일 애플리케이션 예
  1. 수신된 이메일 리스트 표시
  2. 이메일 작성
  3. 수신된 이메일 내용 표시

## 서비스
- 백그라운드에서 실행되는 컴포넌트로서 오랫동안 실행되는 작업이나 원격 프로세스를 위한 작업
- 예시로 배경음악을 연주하는 작업
  1. 음악 재생화면
  2. 음악 재생 서비스

## 방송 수신자
- 방송을 받고 반응하는 컴포넌트(요새는 잘 안쓰는 추세이다.= 버벅거림 때문에)

## 컨텐츠 제공자
- 데이터를 관리하고 다른 애플리케이션에게 제공하는 컴포넌트

## PC의 애플리케이션
- pc의 경우엔 다른 애플리케이션의 코드를 사용할 수 없다.(완전히 단절되어 있다)

## 안드로이드 애플리케이션
- 다른 애플리케이션의 컴포넌트를 사용할 수 있다. 목적은 성능의 향상을 위해서 쓰는 것이다.
- 애플리케이션에서 사용자가 사진을 촬영하고 싶은 경우
  - 카메라 에플리케이션과 우리 애플리케이션이 상호작용을 통해 이루어짐

## 인텐트
- 애플리케이션의 의도를 적어서 안드로이드에 전달하면 안드로이드가 가장 적절한 컴포넌트를 찾아서 활성화하고 실행
- ex)  action: view, data = 여러 파일 등등

## 매니페스트 파일
- 적재목록(적하 목록) 이 패키지에 포함된 컴포넌트, ex) 액티비티1, 컨텐츠 제공자,.... 등등
- \<activity>요소: 액티비티 선언
- \<service>요소: 서비스 선언
- \<receiver>요소: 방송 수신자
- \<provide>요소: 컨텐츠 제공자
## XML
- 안드로이드에서 많이 사용된다.
- SGML의 부분집합으로 웹 상에서 구조화된 텍스트 형식의 문서를 전송하고 수신하며 처리가 가능하도록 만들어진 마크업 언어

>> \<?xml version="1.0" encoding="utf-8"?> 
<manifext...>
    <application android:icon = "@drawble/ic_launcher"...>
        <activity android:name = "kr.co.company.MainActivity"
            android:label = "@string/app_name"
        ...>
    \</activity>
    ...
    \</application>
\</manifest>

## 개발 과정의 개요
- 개발 환경 구축
  - 개발환경 설정
    - 안드로이드 SDK, 개발 도구, 플랫폼 설치
  - AVD와 장치 설정
    - 가상장치 생성 또는 실제장치 연결
- 개발
  - 애플리케이션 생성
    - 프로젝트를 생성하고 소스코드, 리소스, 매니페스트 파일 작성
- 디버깅 및 테스팅
  - 애플리케이션 빌드와 실행
    - 애플리케이션 빌드와 디버그 모드로 실행
  - 애플리케이션 디버깅
    - 디버그 도구와 로깅 도구를 이용하여 디버그
  - 애플리케이션 테스팅
    - 안드로이드 테스팅 및 측정 프레임워크 이용
- 배포
  - 애플리케이션 배포 준비
    - 배포 모드로 애플리케이션을 구성, 테스트
  - 애플리케이션 배포
    - 사용자에게 애플리케이션 공개, 배포, 판매

## 개발 도구
- JDK
  - 7이후 버전 필요
- 안드로이드 스튜디오
- 안드로이드 SDK

## 안드로이드 스튜디오 
- 그레이들 기반의 유연한 빌드 시스템
- 다중 apk파일 생성 시스템
- 앱의 공통 특징을 지원하는 코드 템플릿 제공
- 마우스 드래그 앤 드롭 방식의 테마 편집이 가능한 레이아웃 에디터
- 구글 클라우드 플랫폼 지원 내장: 구글 클라우드 메시징과 앱 엔진을 쉽게 통합할 수 있다.
