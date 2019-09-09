# **#1** **음원** **재생기** **애플리케이션**
> *iOS 프로그래밍의  환경을  익히고, AVAudioPlayer 클래스와 Auto Layout을  사용해보자*  


## 1. **Xcode** **톺아보기**
 - **Xcode**
   -   애플의  통합  개발  환경(IDE)
   -   주로  애플사의  제품의  애플리케이션을  제작하기  위해  사용함
   -   **Project**: 애플리케이션을  구성하는  데  필요한  파일  및  리소스를  제공
   -   **Editor Area**: 소스파일을  편집하거나  프로젝트의  속성을  편집할  수  있는  영역
   -   **Navigator Area**: 프로젝트의  다른  부분에  접근할  수  있는  영역
   -   **Debug Area**: 프로젝트를  빌드한  후  현재  상태를  볼  수  있는  영역
   -   **Scheme**: 대상(Target)의  빌드와  실행  가능한  환경을  지정하는  설정  모음, 프로젝트를  실행할  기기(또는  시뮬레이터)와 쌍을  이루어  애플리케이션을  빌드시킬  수  있다.    
  

## 2. **프로젝트에** **이미지** **추가하기**
 - **에셋**  **카탈로그(Asset Catalog)**  
     -   .xcassets 확장자를  가지는  폴더  (보통의  파일시스템의  폴더와  달리  확장자를  가진다)
     -   서로  다른  에셋* 타입을  조직화하고  관리할  수  있으며, 에셋과  다양한  디바이스의  속성에  대한  파일의  연결을  통해서  애플리케이션  리소스에  쉽게  접근할  수  있게  도와주는  역할을  한다.
			> 1.  Asset: 한  가지  타입의  관련된  속성과  파일들의  집합
			> 2.  서로  다른  에셋  타입의  예: 이미지, 스프라이트, 텍스쳐, 데이터  등
			> 3.  다양한  디바이스의  속성의  예: 디바이스의  특징, 사이즈  클래스, 주문형  리소스, 특정  타입  등

	 - **에셋**  **카탈로그의**  **콘텐츠**  
	    -   Folders: 에셋  카탈로그  폴더
	    -   JSON files: .json 확장자  파일, 속성에  대한  정보를  포함
	    -   Content files: 리소스  파일  -

	 - **에셋**  **카탈로그**  **타입**
	   -   App Icon Type: 다양한  크기와  해상도의  애플리케이션  아이콘  원본  이미지  타입
	   -   Catalog Type: 에셋  카탈로그  구조의  최상위  폴더  타입
	   -   Image Set Type: 이미지  에셋에서 UIImage와 NSImage의  인스턴스에  사용되는  이미지  파일  타입
	   -   Date Set Type: Xcode에  의해  생성된  모든  종류의  데이터를  포함하는  파일들의  집합  타입(device-executable code 제외)
	   -   Launch Image Type: 애플리케이션  실행화면  이미지  타입

 - **앱**  **시닝(App Thinning)**
   -   애플리케이션이  디바이스에  설치될  때  앱  스토어와  운영체제가  그  디바이스의  특성에  맞게  설치되도록  하는  설치  최적화  기술
   -   애플리케이션의  설치용량을  최소화하고  다운로드  속도를  향상시킬  수  있다.
   -   앱  시닝의  구성  요소: 슬라이싱(Slicing), 비트코드(Bitcode), 주문형  리소스(On-Demand Resource)

 - **앱**  **슬라이싱(App Slicing)**
   -   애플리케이션이  지원하는  다양한  디바이스에  대한  여러  조각의  애플리케이션  번들을  생성하고  디바이스에  알맞은  조각을  전달하는  기술
   -   개발자는  애플리케이션의  전체  버전을 iTunes Connect에  업로드 -> 앱  스토어에는  각  디바이스  특성에  대한  다양한  버전의  조각들  생성 -> 사용자가  애플리케이션을  설치할  때  슬라이싱된  조각  중 사용자의  디바이스에  가장  적합한  조각이  다운로드  됨(여기서  에셋  카탈로그에서  관리하는  이미지들은  자동으로 적용)


## 3. **인터페이스** **빌더를** **사용해** **앱** **화면** **구성하기**
 - **인터페이스**  **빌더(Interface Builder)**
      -   앱의  인터페이스를 GUI를  통해  제작할  수  있는 Mac OS 용  소프트웨어  개발  응용  프로그램
      -   스토리보드  파일에서  인터페이스를  그림판처럼  하나씩  그려가며(옮겨가며) 제작할  수  있다.
      -   Object Library 여는  단축키: command + shift + L
      -   Open Quick 단축키: command + shift + O

 - **IBOutlet**
	-   인터페이스  빌더의  유저  인터페이스  요소와  뷰컨트롤러의  인스턴스  프로퍼티*를  연결
		> 1. Instance Property: 특정  타입의  인스턴스(구조체  또는  클래스에서  생성한 (값  타입/참조 타입)객체)에 속하는  프로퍼티

  - **인터페이스와**  **프로퍼티를**  **연결하는**  **방법**
	   -   뷰  컨트롤러에서  해당  프로퍼티를  인터페이스로  드래그하여  연결
	   -   커넥션  인스펙터에서  해당  프로퍼티를  인터페이스로  드래그하여  연결
	   -   어시스턴트  에디터  화면에서  해당  프로퍼티를  인터페이스로  드래그하여  연결
	   -   어시스턴트  에디터  화면에서  인터페이스를  뷰컨트롤러와  연결된 swift 파일로  드래그하여  프로퍼티  생성

 - **IBAction**  
	 -   인터페이스  빌더의  인스턴스에서  발생한  액션과  코드를  연결  

	 - **컨트롤**  **이벤트와**  **액션과의**  **관계**    
	     -   UIKit에는 UIControl을  상속받은  다양한  컨트롤  클래스가  있으며, 컨트롤  객체에서  발생한  다양한  이벤트를  특정  액션  메서드에  연결할  수  있다. => 사용자가  버튼을  누르는  등의  액션을  취했을 
   때  특정  메서드를  실행시킨다.
	     -   UIControl.Event.(컨트롤  이벤트)의  형식을  가진다.

	  -   **인터페이스와**  **액션을**  **연결하는**  **방법**
		   -   뷰  컨트롤러에서  해당  액션을  인터페이스로  드래그하여  연결  후  컨트롤  이벤트  지정
		   -   커넥션  인스펙터에서  해당  액션을  인터페이스로  드래그하여  연결  후  컨트롤  이벤트  지정
		   -   어시스턴트  에디터  화면에서  해당  액션을  인터페이스로  드래그하여  연결  후  컨트롤  이벤트  지정
		   -   어시스턴트  에디터  화면에서  인터페이스를  뷰컨트롤러와  연결된 swift 파일로  드래그하여  액션  생성


  -   **UIButton**: 사용자의  상호  작용(터치/탭  등의  이벤트)에  반응해  미리  지정된  코드를  실행하는  컨트롤  요소
		-   주요  메서드
```swift
func setTitle(String?, for: UIControlState) // 특정 상태의 버튼의 문자열 설정
func title(for: UIControlState) -> String? // 특정 상태의 버튼의 문자열 반환
func setImage(UIImage?, for: UIControlState) // 특정 상태의 버튼 이미지 설정
func image(for: UIControlState) -> UIImage? // 특정 상태의 버튼 이미지 반환
func setBackgroundImage(UIImage?, for: UIControlState) // 특정 상태의 백그라운드 이미지 설정
func backgroundImage(for: UIControlState) -> UIImage? // 특정 상태의 백그라운드 이미지 반환
func setTitleColor(UIColor?, for: UIControlState) // 특정 상태의 문자열 색상 설정
func setAttributedTitle(NSAttributedString?, for: UIControlState) // 특정 상태의 attributed 문자열 설정 
```
   -   **UILabel**: 한  줄  또는  여러  줄의  텍스트를  보여주는  뷰
	    -   UILabel은  액션이  발생하지  않는다.

   -   **UISlider**: 연속된  값  중에서  특정  값을  선택하는데  사용되는  컨트롤  요소
	    -   주요  메서드
```swift
func setValue(Float, animated: Bool) /* 슬라이더의 현재 값 설정 */
func minimumTrackImage(for: UIControlState) -> UIImage? /* 특정 상태의 minimumTrackImage 반환 */
func setMinimumTrackImage(UIImage?, for: UIControlState) /* 특정 상태의 minimumTrackImage 설정 */
func maximumTrackImage(for: UIControlState) -> UIImage? /* 특정 상태의 maximumTrackImage 반환 */
func setMaximumTrackImage(UIImage?, for: UIControlState) /* 특정 상태의 minimumTrackImage 설정 */
func thumbImage(for: UIControlState) -> UIImage? /* 특정 상태의 thumbImage 반환 */
func setThumbImage(UIImage?, for: UIControlState) /* 특정 상태의 thumbImage 설정 */
```


## 4. **AVFoundation** **클래스** **사용하기**
-   **AVFoundation**
	-   다양한 Apple 플랫폼에서  사운드  및  영상  미디어의  처리, 제어, 입출력  등  광범위한  기능을  제공하는  프레임워크
   -   **주요**  **프로퍼티**
```swift
var isPlaying: Bool /* 사운드가 현재 재생되고 있는지 아닌지 여부 */
var volume: Float /* 사운드의 볼륨값, 최소 0.0 ~ 최대 1.0 */
var rate: Float /* 사운드의 재생 속도 */

var numberOfLoops: Int /* 사운드 재생 반복 횟수 */
// 기본값은 0으로 사운드 1회 재생 후 자동 종료
// 양수값으로 설정시 (설정값+1회) 재생
// 음수값으로 설정시 stop 메서드가 호출 될 때까지 무한 재생

var dutation: TimeInterval /* 사운드의 총 재생 시간(초 단위) */
var currentTime: TimeInterval /* 사운드의 현재 재생 시각(초 단위) */

protocol AVAudioPlayerDelegate /* 사운드 재생 완료, 재생 중단 및 디코딩 오류에 응답할 수 있는 프로토콜 */
```

   - **주요**  **메서드**
```swift
func init(contentOf: URL) /* 특정 위치에 있는 사운드 파일로 초기화 */
func init(data: Data) /* 메모리에 올라와있는 데이터를 이용해 초기화 */

func play() /* 사운드 재생 */
func play(atTime: TimeInterval) /* 특정 시점에서 사운드 재생 */
func pause() /* 사운드 일시 정지 */
func stop() /* 사운드 재생 정지 */
```
