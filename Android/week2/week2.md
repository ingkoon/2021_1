# 안드로이드 응용 프로그래밍 2주차
----
## 어플리케이션 기본 구조
----
* **비주얼 도구**를 사용하여서 앱을 작성한다.

## 애플리케이션의 구성
* 동작을 나타내는 Java 파일
* XML 파일을 통한 화면의 표시 기술
* 사운드, 그림과 같은 여러 리소스 파일

## 일반적인 애플리케이션 작성 절차
* 사용자 인터페이스 작성 (XML)
* 자바 코드 작성 (JAVA)
* 매니페스트 파일 작성 (XML)

1. 사용자 인터페이스 작성
    - 첫번째 단계는 XML을 이용하여서 사용자 이넡페이스 화면을 **디자인**하는 단계
2. 자바코드 작성
    - 두번째 단계는 자바를 이용하여 코드를 작성하는 단계
3. 매니페스트 파일 작성
    - 애플리케이션을 구성하고 있는 컴포넌트를 기술하고 실행시에 필요한 권한을 지정한다.

패키지 폴더의 설명

|폴더 또는 파일|설명|
|------|---|
|Java|자바 소스 파일들이 들어있는 폴더이다. 폴더 안의 kr.co.company.hello는 패키지의 이름이다.|
|Gradle Scripts|그레이들은 빌드 시에 필요한 스크립트이다.|
|res|각종 리소스들이 저장되는 폴더이다. drawable에는 해상도 별로 아이콘 파일들이 저장된다. layout에는 화면의 구성을 정의한다. values에는 문자열과 같은 리소스가 저장된다. menu에는 메뉴 리소스들이 저장되어 있다.|
|manifest|XML 파일로 앱의 전반적인 정보, 즉 앱의 이름이나 컴포넌트 구성과 같은 정보를 가지고 있다.|

## 패키지
* 패키지는 클래스들을 보관하는 컨테이너
* 일반적으로 인터넷의 도메인 이름을 역순으로 사용

## import android.support.v7.app.App...
* import 문장은 외부에서 패키지나 클래스를 포함
* 앞에 android 가 붙은 패키지는 안드로이드가 제공하는 패키지를 의미한다.

## public class MainActivity extends AppCompatActivity {...}
* 클래스의 정의
* Activity로부터 상속받았으므로 액티비티가 된다.
* 액티비티는 안드로이드에서 애플리케이션을 구성하는 4가지의 컴포넌트 중의 하나이다.

## @Override
* 어노테이션의 하나
* 어노테이션은 컴파일러에게 추가적인 정보를 주는것
* @Override은 메소드가 부모 클래스의 메소드를 재정의(Override) 하였다는 것을 나타낸다.

## public void onCreate() {...}
* onCreate() 메소드는 액티비티가 생성되는 순간에 딱 한번 호출
* 모든 초기화와 사용자 인터페이스 설정이 여기에 들어간다.
  
## super.onCreate(savedlnstanceState);
* 위의 문장은 부모 클래스인 AppCompatActivity 클래스의 onCreate()를 호출하는 문장
  
## setContentView(R.layout.activity_main);
* setContentView()라는 함수는 액티비티의 화면을 설정하는 함수
* R.layout.activity_main은 activity_main.xml 파일을 나타낸다.

* 필요한 패키지를 가장 쉽게 프로젝트에 추가하려면 file - settings - editor - general - auto import로 가서 add unambigious imports on the fly 옵션과 optimize imports on the fly 옵션을 체크하면 된다.

## 안드로이드 애플리케이션의 실행이 시작되는 곳 
* 안드로이드에는 main()이 없음
* 액티비티별로 실행된다.
* 액티비티 중에서는 onCreate() 메소드가 가장 먼저 실행된다.

## XML을 이용하여서 사용자 인터페이스 기술
* 사용자 인터페이스 작성 방법
  * 코드를 사용하는 방법(기존의 자바)
  * XML을 사용하는 방법(안드로이드 선호 방법)


* 안드로이드에서는 UI 화면의 구성을 XML을 이용하여서 선언적으로 나타내는 방법을 선호
  * 애플리케이션의 외관과 애플리케이션의 로직을 서로 분리
  * 빠르게 UI를 구축

## XML을 이용한 사용자 인터페이스 작성
* UI 컴포넌트들은 XML의 하나의 요소로 표현된다.
* TextView 컴포넌트는 <TextView.../>요소로 표현된다.


## XML
* 시작 태그로 시작되어 종료 태그로 끝나는 논리적인 구성요소를 요소(element)
* <Greeting> Hello, world</Greeting>가 요소
* 속성(attribute)는 요소의 속성으로서 "이름/값"의 쌍으로 구성
* <img src = "madonna.jpg" alt = 'by raphael'/>에서는 img요소는 src와 alt라는 2개의 속성을 가진다.