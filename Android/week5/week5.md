## 사용자 인터페이스

* 내비게이션 바
* 액션 바
* 다중 패널 레이아웃
* 제스처

## 메뉴의 종류
* **옵션 메뉴**: 사용자가 Menu 키를 누를 때 나타난다
* **컨텍스트메뉴**: 사용자가 화면을 일정시간 길게 누르면 나타나는 메뉴이다
* **팝업 메뉴**: 버튼을 통해서 나타난 메뉴

## 메뉴 생성의 방법
* 코드로 메뉴 생성
* XML로 메뉴 생성

## XML 타입 메뉴 정의


```
<?XML version = "1.0" encoding="utf-8"?>
<menu xmls:android = "http://schemas.android.com/apk/res/android">

    <item
        android:id="@+id/apple"
        android:icon="@drawable/ic_launcher"
        android:title="사과"/>
    <item
        android:id="@+id/grape"
        android:icon="@drawable/ic_launcher"
        android:title="포도"/>
    <item
        android:id="@+id/banana"
        android:icon="@drawable/ic_launcher"
        android:title="바나나"/>
</menu>
```

## 메뉴 팽창
* 메뉴 리소스를 팽창(inflate)하면 실제 메뉴가 생성
  * XML파일을 읽어서 실제 메뉴를 생성하는 과정

```
@override
public boolean onCreateOptionsMenu(Menu memu){
    MenuInflater inflater = getMenuInflater();
    inflater.inflate(R.menu.mymenu, menu);
    return true;
}
```

## 옵션 메뉴
* 현재 액티비티와 관련된 동작
* 옵션메뉴 클릭 이벤트 메소드 재정의가 필요하다

```
@override
public boolean onOptionsItemSelected(MenuItem item){
    switch (item.getItemId()){
    //"새로운 게임" 메뉴 항목이 클릭되면 실행
    case R.id.new_game:
        newGame();
        return true;

    //"도움말" 메뉴 항목이 클릭되면 실행
    case R.id.help:
        showHelp();
        return true;
    
    //이벤트를 상위 클래스로 전달
    default:
        return super.onOptionsItemSelected(item);
    }
}
```

## 옵션 메뉴 생성

### 옵션 요소 생성
```
//mymenu.xml
<?XML version = "1.0" encoding="utf-8"?>
<menu xmls:android = "http://schemas.android.com/apk/res/android">

    //메뉴의 한 요소
    <item
        android:id="@+id/apple"
        android:icon="@drawable/ic_launcher_background"
        android:title="사과"/>
    <item
        android:id="@+id/grape"
        android:icon="@drawable/ic_launcher_background"
        android:title="포도"/>
    <item
        android:id="@+id/banana"
        android:icon="@drawable/ic_launcher_background"
        android:title="바나나"/>
</menu>
```

### showAsAction

```
<?xml version = "1.0" encoding = "utf-8"?>
<menu xmIns:android="http://schemas.android.com/apk/res/android">
    <item android:id="@+id/new_game"
        androidLicon="@drawable/ic_new_game"
        android:title="@string/new_game"
        //추가된 내용(액션바에 열거타입으로 정리 가능)
        android:showAsAction="ifRoom"/>

    <item android:id="@+id/help"
        androidLicon="@drawable/ic_help"
        android:title="@string/help"    
</menu>
```

### 사용자가 옵션 키를 누르면 다음의 메소드가 호출된다.

```
package kr.co.company.optionmenu2;
public class MainActivity extends AppCompatActivity{

    @Override
    protected void onCreate(Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        MenuInflater inflater = getMenuInflater();
        //메뉴 mymenu.xml을 팽창하여 메뉴 객체로 만든다.
        inflater.inflate(R.menu.mymenu, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item){
        switch (item.getItemId()){
            case R.id.apple:
                Toast.makeText(this,"사과", Toast.LENGTH_SHORT).show();
                return true;
            case R.id.grape:
                Toast.makeText(this,"포도", Toast.LENGTH_SHORT).show();
                return true;
            case R.id.banana:
                Toast.makeText(this,"바나나", Toast.LENGTH_SHORT).show();
                return true;
            default:
                return super.onOptionItemSelected(item);
        }
    }

}

```

## 코드로 옵션 메뉴 생성하기

---

**MainActivity.java**

```
@Override
public boolean onCreateOptionsMenu(Menu menu){
    super.onCreateOptionsMenu(menu);

    //메뉴 항목의 아이디는 1
    MenuItem item1 = menu.add(0, 1, 0, "사과");
    item1.setIcon(R.drawable.ic_launcher);
    item1.setAlphabeticShortcut('a');

    //반환되는 값을 이용하여서 이렇게 하여도 된다.
    menu.add(0, 2, 0, "포도").setIcon(R,drawable.ic_launcher);
    menu.add(0, 3, 0, "바나나").setIcon(R,drawable.ic_launcher);

    return true;
}
```

### tip
* Android 3.0에는 android:onClick 특성을 사용하여 XML에 있는 메뉴 항목에 대한  
 온-클릭 동작을 정의하는 기능이 추가되었다.
* 특성값은 메뉴를 사용하여 액티비티가 정의한 메서드의 이름이어야 한다.
* 메서드는 공개여야 하며 하나의 MenuItem 매개변수를 수락해야 한다.
* 시스템이 해당 메서드를 호출하면 메서드가 선택한 메뉴 항목을 전달해야 한다.


## 컨텍스트 메뉴

---

### UI의 어떤 항목과 관련된 동작
* 플로팅 컨텍스트 메뉴
  * 사용자가 항목 위에서 오래 누르기를 하면 메뉴가 대화상자처럼 떠서 표시된다.
* 컨텍스트 액션 모드
  * 현재 선택된 항목에 관련된 메뉴가 액션바에 표시돤다. 여러 항목을 선택하여 특정한 
  액션을 한꺼번에 적용할 수 있다.

* 사용자가 항목 위에서 "오래누르기(long-press)"를 하면 컨텍스트 메뉴가 표시
* PC에서 마우스 오른쪽 버튼을 눌렀을 때 나오는 메뉴와 개념적으로 유사

## 컨텍스트 메뉴 예제

--- 

```
<?xml version = "1.0" encoding = "utf-8"?>
<LinearLayout xmIns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/LinearLayour01"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    android:orientation="verticla">

    <TextView
        android:id="@+id/TextView01"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Only i can change my life. No one can do it for me."
        android:textSize="200px"
        andriod:typeface="serif"/>
</LinearLayout>
```


```
public claass MainActivity extends AppCompatActivity{
    TextView text;

    @Override
    public void onCreate(Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        text = (TextView) findViewById(R.id.TextView01);
        registerForContextMenu(text);
    }

    @Override
    public void onCreateContextMenu(ContextMenu menu, View v, ContextMenuInfo menuInfo){
        super.onCreateContextMenu(menu, v, menuInfo);
        menu.setHeaderTitle("컨텍스트 메뉴");
        menu.add(0, 1, 0, "배경색: RED");
        menu.add(0, 2, 0, "배경색: GREEN");
        menu.add(0, 3, 0, "배경색: BLUE");
    }

}
```

```
public boolean onContextItemSelected(MenuItem item){
    switch (item.getItemId()){
        case 1:
            text.setVackgroundColor(Color.RED);
            return true;
        case 2:
            text.setVackgroundColor(Color.GREEN);
            return true;
        case 3:
            text.setVackgroundColor(Color.BLUE);
            return true;
        default:
            return super.onContextItemSelected(item);
    }
}
```

## 컨텍스트 액션 모드

---

현재 선택된 항목에 대하여 수행할 수 있는 액션들을 제공하는 컨텍스트 액션바가 화면의 상단에 표시된다.


## 팝업 메뉴

---

* 뷰에 부착된 모달 메뉴(modal menu)
* API 레벨 11 부터 제공
* 팝업 메뉴의 용도
  * 오버플로우 스타일 메뉴 제공
  * 서브 메뉴의 역할
  * 드롭다운 메뉴


**activity_main.xml**

```

<LinearLayout xmIns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="verticla">

    <Button android:layout_width="wrap_cotent"
            android:layout_height="wrap_cotent"
            android:layout_gravity="center"
            android:onClick="on_click"
            android:text="show popup menu"/>    
</LinearLayout>
```

**popup.xml**


```
<?xml version = "1.0" encoding = "utf-8"?>
<LinearLayout xmIns:android="http://schemas.android.com/apk/res/android"

    //메뉴의 한 요소
    <item
        android:id="@+id/search"
        android:icon="@drawable/ic_menu_search"
        android:title="search"/>
    <item
        android:id="@+id/add"
        android:icon="@drawable/ic_menu_add"
        android:title="add"/>
    <item
        android:id="@+id/edit"
        android:icon="@drawable/ic_menu_edit"
        android:title="edit"/>
        <menu>
            <item
                android:id="@+id/share"
                android:icon="@drawable/ic_menu_share"
                android:title="share"/>            
        </menu>
    </item>

</menu>
```


**MainActivity.java**
```

package kr.co.company.optionmenu;
public class MainActivity extends AppCompatActivity{

    @Override
    protected void onCreate(Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

   public void onClick(View button){
       PopupMenu popup = new PopupMenu(this, button);
       popup.getMenuInflater().inflate(R.menu.popup, popup.getMenu());

       popup.setOnMenuItemClickListener(
           new PopupMenu.onMenuItemClickListener(){
               public boolean onMenuItemClick(MenuItem item){
                   Toast.makeText(getApplicationContext(),
                        + item.getTitle(),
                        Toast.LENGTH_SHORT).show();
                return true;
               }
               });
               popup.show();
           }
       
   }
```

## 대화 상자

---

**대화상자**는 사용자에게 메시지를 출력하고 사용자로부터 입력을 받아들이는 사용자 인터페이스

### 대화 상자의 종류

* AlertDialog
* ProgressDialog
* DatePickerDialog
* TimePickerDialog

### AlertDialig
* 제목
* 콘텐츠 영역
  * 메시지나 리스트, 커스텀 레이아웃을 표시한다.
* 액션 버튼: 3개 이내의 버튼

### DatePickerDialog
* ``날짜``와 ``시간``을 입력받는 대화 상자


## 알림 기능

---

``알림기능``은 어떤 이벤트가 발생하였을 때, 앱이 사용자에게 전달하는 메시지이다.

### 알림을 만드는 절차

1. 알림 채널 생성
2. 알림 빌더 생성
3. 알림 속성을 설정
4. 액션을 첨부(선택 사항)
5. 알림 객체 생성후 전송


### 1. 알림 채널 생성하기

```

String NOTIFICATION_CHANNEL_ID = "my_channel_id_01";

private void createNotificationChannel() {

    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O){
        NotificationChannel notificationChannel = new
NotificationChannel(NOTIFICATION_CHANNEL_ID, "My Notificaitons",
NotificationManager.IMPORTANCE_DEFAULT);
        notificationChannel.setDescription("Channel description");
        NotificationManager notificationManager = (NotificationManager)
getSystemService(Context, NOTIFICATION_SERVICE);
            notificationManager.createNotificationChannel(notificationChannel)
    }
}
```

### 2. 알림 빌더 생성


```

NotificationCompat.Builder builder = new NotifiactionCompat.Builder(this);=
```

### 3. 알림 속성을 설정

```

builder.setSmallIcon(R.drawable.notification_icon);
builder.setContentTitle("알려드립니다.");
builder.setContentText("이것은 시험적인 알림입니다.");
```

### 4. 액션을 첨부한다.

```

Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse("http://www.google.com/"));
PendingIntent pendingIntent =
PendingIntent.getActivity(this, 0,  Intent, 0);
builder.setContentIntent(pendingIntent);
```

### 5. 알림 객체 생성하여 보내기

```
NotiicationManager notificationManager = (NotificationManager)getSystemService
(NOTIFICATION_SERVICE);
notificationManager.notify(NOTIFICAITON_ID, builder.build());
```