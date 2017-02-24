# cocoa-server : atWee 외주 관리 서버 어플리케이션

Project Url : https://gitlab.com/atwee/cocoa-server.git

atWee 외주 관리 서버 어플리케이션 

## 서버 어플리케이션 최소 지원 버전 
servlet 스펙 : 3.0 
jsp 스펙 : 2.2 
최소 Java 버전 : 1.6 

=> tomcat의 경우 7.0  이상 버전 부터 사용 가능 


## Build
To Build :

###  1. git 설정

*  소스 내려받기   
```  
git clone https://gitlab.com/atwee/cocoa-server.git  
```  
clone 명령을어를 이용하여 현재 디렉토리에 서버의 소스 데이터 및 히스토리를 내려받는다.
파일을 내려받으면서 자동으로 '.git' 디렉토리와 remote 정보를 내려받는다. init 과 remote 정보를 추가하는 과정을 생략 가능


```   
cd cocoa-server  
git init  
git remote add origin https://gitlab.com/atwee/cocoa-server.git  
git add .  
git commit  
git push -u origin master  
```


###  2. node.js 
* http://nodejs.org/에 접속하여 다운로드 받은 후 설치한다.  
	- 윈도우의 경우 설치후 간혹 npm 명령어가 동작하지 않을수도 있다 이경우 node.js 설치폴더에서 nude_module 폴더 안에 있는 npm 폴더를 복사하여 C:/사용자/로그온계정/AppData/Roaming/ 아래에 붙여넣기 한다.  
* npm을 사용 하여 gulp를 설치한다.  

```  
npm install -g gulp  
```




###  3. 이클립스 설정

####  1. Gradle
* 이클립스에 gradle 설치 >> 이클립스의 help 탭을 클릭하여 이클립스 마켓 오픈 >> 검색창에 gradle을 입력 >> Gradle IDE Pack 설치  
* 다운로드 받은 후 bulid.gradle로 이클립스에 imoprt 
* 'Root folder' 콤보 우측의 'Browse' 버튼을 눌러 내려받은 소스가 위치한 폴더를 선택 후 'Build Model' 버튼을 눌러 프로젝트를 탐색 후 선택 하여 등록한다.
* tomcat 실행 시 atwee.webroot 에 실제 프로젝트에 경로 설정 ( fsp  디렉토리까지의 경로 )
* Servers 탭에 추가된 Tomcat을 더블클릭하여 Overview 창을 연 후 > Open launch configuration 을 클릭하여 환경창을 열고 Arguments 탭에서 VM Arguments에 옵션 값을 추가 -Datwee.webroot="{ 프로젝트의 fsp 디렉토리 까지의 경로 }" 이클립스에서 입력시 '\' 기호를 '/' 변경하여 입력필요

#### 2. eXERD 
* http://ko.exerd.com/#download-section 사이트에 접속하여 설치 파일을 다운로드 후 설치를 진행 
* 또는 이클립스에서 플러그인을 추가하여 설치 가능 이클립스 설치 방법은 홈페이지의 가이드를 첨부함

>Eclipse 플러그인으로 설치  
>Windows 이외의 운영체제를 사용하시거나, 이클립스 기반의 원래 작업 환경에 eXERD를 이용하시려면, 플러그인 형태로 설치하실 수 있습니다.  

>* Update Site URL(이클립스 버전 3.4 ~ 3.7, 4.3 또는 이상 버전):http://exerd.com/update  

>플러그인 설치 가이드  
>위의 업데이트 사이트 URL을 복사합니다.  
>이클립스의 메뉴에서 Help > Install New Software를 선택합니다. (3.4의 경우 Help > Software Updates...)  
>복사한 주소를, Work with: 안에 붙여 넣고 Add를 누릅니다.  
>"Contact all update sites..." 체크 옵션을 제거 합니다.  
>목록에 eXERD Modeler가 나타나면 선택 후, Next를 눌러 설치합니다.  

##### exerd 설치후 파일을 열때 Exception 발생시 대처 방안  
* 1. Failed to create the part`s controls  
	```  
	java.lang.NullPointerException
	at com.tomato.exerd.part.RootPart.stackChanged(RootPart.java:197)  
	```  

 	위와 같은 에러가 발생할 경우 아래의 방법을 통하여 해결이 될수 있음  
 	이클립스의 Help > Install New Software > 아래의 주소를 Work with: 에 입력  
 
> http://download.eclipse.org/releases/mars  

 	호출되는 목록에서  Framework를 입력하여 조회 한 후 아래의 항목들을 체크 한 후 설치한다.  

> --EMF - Eclipse Modeling Framework SDK  
> --Graphical Editing Framework GEF SDK
    

### 4. 소스 컴파일 방법
1. 공통 자바스크립트 수정 시 반영방법
소스 : webapp/src/js 폴더에서 내려 받음. 
command 창에서  gulp make-sz-js 로 컴파일
이클립스에서 public 디렉토리 새로 고침으로 파일 반영

	
# js 초기 설정 
```  
sudo npm install -g gulp (window 환경일 경우 sudo 생략)  
npm install   
```

## js 및 css 생성 
* public 디렉토리에 파일이 생성됨. 
```
gulp make 
```
* site정보를  생성하기위해 아래의 명령어를 실행 
```  
gulp make-site-js  
```  
# 개발환경 정보 
---
1.Database  
	idc.softzam.com:1521/softzam (xmen/xmen1234)