# React-Native 공식문서

[React Native · Learn once, write anywhere](https://reactnative.dev/)

## 0. 환경세팅

- Expo CLI Quickstart : 교육용으로 좋지만 실무용으로는 비추천
- React Native CLI Quickstart : 실무용으로 추천
- Window : 안드로이드 , Mac : IOS, 안드로이드

## Chocolatey (초콜레티)

> **6000개가 넘는 소프트웨어(git, 파이썬, 크롬, 비주얼스튜디오) 통합 관리**
> 

<aside>
💡 Chocolatey (초콜레티) - 윈도우 사용자를 위한 패키지 매니저 
*Homebrew (macOS 용 패키지 관리자)

</aside>

[Chocolatey(초콜레티) - 윈도우 패키지 매니저](https://www.youtube.com/watch?v=ekq4vln2TQ0)

### **자주쓰는 명령어**

```jsx
choco list --localonly 
// 설치된 패키지 목록 보기 

choco install 패키지명 
// 패키지 설치하기 

choco uninstall 패키지명
// 패키지 삭제하기 
```

## 1. 설치

### 1) Chocolatey 설치

- React Native > Guides > Enviroment setup > Setting up the development environment
- React Native CLI Quickstart > windows > Android > Chocolatey
- Windows PowerShell  (관리자권한 실행)
- [Chocolatey](https://chocolatey.org/install) > Install now > 설치 CLI 복사 > Power Shell 붙여 놓고 설치
- 크롬버전 > Chocolatey chrome install 구글 검색 > 명령어 복사

### 2) Android Studio 설치

- https://developer.android.com/studio >Download Android studio
- Android Studio 실행 > file > setting > system setting > Android SDK > Android 11.0 설치 (30버전)
- Android SDK > SDK tool > Android Emulator 설치 확인 > Intel x86 설치 확인
    - 설치 경로 확인 > 내pc > c드라이브 > User > 내이름 > AppData > Local > Android > Sdk > platforms, platforms-tools > adb.exe 확인

### 3) 환경변수 설정

- Windows 검색 > 환경 변수 > 고급 > 환경 변수
- ANDROID_HOME, JAVA_HOME 추가
    - git bash (경로검색) : $which javac, $which adb
    - PATH에  등록해야지 프로그램 실행가능
    - PATH : %JAVA_HOME%\bin 추가
    - ANDROID_HOME :  C:\Users\davidyang\AppData\Local\Android\Sdk
    - JAVA_HOME : C:\Program Files\Java\jdk-11

## 2. 프로젝트 시작

### 1) 프로젝트 저장

- CMD: C:\Users\davidyang> npm i -g react-native 설치
- [https://github.com/ZeroCho/food-delivery-app#첫-시작.setting](https://github.com/ZeroCho/food-delivery-app#%EC%B2%AB-%EC%8B%9C%EC%9E%91.setting)  에서
- `react-native init FoodDeliveryApp --template react-native-template-typescript` 설치
- Visual Studio 실행 > 폴더열기 > C:\Users\davidyang>Fooddeliveryapp 열기
- C:\Users\davidyang\FoodDeliveryApp > npm run android  > npmstart

<aside>
💡 **Error: listen EADDRINUSE: address already in use :::8081
// 다른 서버가 돌아가고 있음 ex) node.js**

</aside>

- Android Studio 실행 > Device Manager > Create >Nexus 5 > R 다운로드 >npm run android

***error** 

[[react-native] npm run android 실행 시 오류 해결](https://anywaydevlog.tistory.com/16)

- What went wrong:
The supplied javaHome seems to be invalid. I cannot find the java executable. Tried location: C:\Program Files\Java\jdk-20\bin\java.exe
- 자바 경로 수정 20버전 삭제 후 > 11버전 경로이용

## 3. 기본 프로젝트 구조와 index.js

### 1) appName

```jsx
AppRegistry.registerComponent(appName, () => App);
//appName으로 컴포넌트 ios,android 전달 
```

### 2) Style

```jsx
const styles = StyleSheet.create({
sectionTitle: {
    fontSize: 24,
    fontWeight: '600',
  },
});
```

- style 컴포넌트를 활용하여 스타일 지정
- px은 사용안함 %가능
- margin-top   > marginTop

```jsx
 import {
		SafeAreaView // 최상단 부분 제외
		ScrollView // 스크롤을 생기게 함 > FlatList 쓰는게 좋음 
		StatusBar // 최상단 배터리 와이파이 디자인부분 
		Text, //span 역할
	  View, //div 역할 
} from 'react-native';

<View><Text>텍스트는 텍스트로 감싸줘야함</Text></View>
```

- SafeAreaView :  https://aboutreact.com/react-native-safeareaview/

```jsx
<Text
        style={[
          styles.sectionTitle,
          {
            color: isDarkMode ? Colors.white : Colors.black,
          },
        ]}>
        {title}
</Text>
```

- 배열 조건문 ? 흰색 & 검정색
- stylesheet로 쓸수 있는건 쓰고 조건문 쓸때는 따로 덮어서 작성해야함

### 3) Debug

[Extensible mobile app debugger | Flipper](https://fbflipper.com/)

- 페이스북이 만든 디버그 확인용 플러그인 React-native와 호환이 잘됨

### 4) 앱 이름 변경

app.json의 displayName

```jsx
{
  "name": "FoodDeliveryApp",
  "displayName": "이름 바꾸기"
}
```

\android\app\src\main\res\values\strings.xml

```jsx
<resources>
    <string name="app_name">이름 바꾸기</string>
</resources>
```

\ios\FoodDeliveryApp\Info.plist의 CFBundleDisplayName

```jsx
<string>이름 바꾸기</string>
```

### 5) **React Navigation**

- react-router-native도 대안임(웹에서 넘어온 개발자들에게 친숙, 웹처럼 주소 기반)
```shell

```jsx
npm i @react-navigation/native
npm i @react-navigation/native-stack
npm i react-native-screens react-native-safe-area-context
npx pod-install # 맥 전용
```

### 6) 리액트 네이티브 폴더 구조
