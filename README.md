
# 본 프로젝트는 라즈베리파이를 이용한 사물인터넷 보안 테스트 플랫폼으로 계속 수정중에 있습니다. 


## 프로젝트소개 
본 프로젝트는 사물인터넷의 보안테스트 플랫폼으로 라즈베리파이 - 윈도우서버 - 안드로이드 애플리케이션간 TCP/IP 소켓통신 형태로 구성됩니다.
여기에 추가로 Bro를 이용한 IDS, AES키 관리서버를 구성합니다.
TCP/IP 소켓통신간 데이터와 데이터베이스의 AES암호화, Bro를 이용한 IDS 구현, RSA암호화를 이용한 AES키 관리가 가능합니다.

## 설치/실행환경 
TCP/IP 소켓통신은 무선인터넷환경에서 진행되었습니다.
본 프로젝트의 데이터베이스는 Mysql을 사용하였기때문에 다른 데이터베이스 가이드는 제공하지않습니다.
### 라즈베리파이 
* [라즈베리파이 하드웨어 구성](https://www.raspberrypi.org/learning/hardware-guide/equipment/)
  * 라즈베리파이 하드웨어 구성은 위 링크를 참조하시기 바랍니다.
* [라즈비안 설치 방법](https://www.raspberrypi.org/learning/software-guide/quickstart/)
  * 라즈비안 설치 방법은 위 링크를 참조하시기 바랍니다.
  * 라즈비안은 [Raspbian-jessie 버전](https://www.raspberrypi.org/downloads/raspbian/)을 사용하였습니다.
* 사용된 코드는 c언어로 작성되었습니다.
* 통신시 전송하는 데이터는 임의로 사용하였습니다.

### 윈도우서버 
* 윈도우 서버
  * 윈도우서버는 Visual Studio 2015에서 작성되었으며 mfc로 구현되었습니다.
  * 라즈베리파이에서의 전송데이터를 수신받아 안드로이드 애플리케이션으로 데이터를 전송 할수 있게 구현합니다.

  * 데이터베이스는 Mysql을 이용하여 구성합니다.
  * 윈도우 서버로 전송되는 데이터를 분류하여 저장하도록 구현합니다.
  * [Mysql 설치](https://dev.mysql.com/doc/refman/5.7/en/installing.html)
    *mysql 설치 방법은 위 링크를 참조하시기 바랍니다. 
  * 데이터베이스는 [Mysql 5.x 버전](https://dev.mysql.com/downloads/mysql/) 이상을 권장합니다. 
  * 설치완료 후 데이터베이스 및 테이블 생성
    * 본 테스트 플랫폼은 아래와 같이 생성하시면 됩니다.
      ```
      create database issi;
      use issi;
      create table data(
      data1 varchar(100) not null, 
      ....
      data5 varchar(100) not null,
      date varchar(20) not null);
      ```
    * 사용자환경에 따라 데이터베이스 구성을 바꿔서 사용하시면 됩니다.
    
* Apache
  * 준비중 입니다.

### 안드로이드 
* 안드로이드는 서버에서 전송하는 데이터값을 모니터링 할수 있도록 구현합니다.
* [Android Studio 설치](https://developer.android.com/studio/index.html)
  * 안드로이드는 Android Studio에서 작성되었습니다.
  * 설치는 위 링크에서 가능합니다.

### Bro IDS 
* 서버와 통신하는 모든 기기간 패킷 분석을 통해 비정상 행위를 탐지하도록 구현합니다.
* [Ubuntu 설치](https://www.ubuntu.com/download/desktop)
  * Ubuntu 16.04 LTS 버전을 사용합니다.
  * 설치파일 다운로드는 위 링크에서 가능합니다.
* [Bro 설치](https://www.bro.org/sphinx/install/install.html)
  * Ubuntu 설치 후 Bro를 설치하시면 됩니다.
  * Bro 설치 방법은 위 링크를 참조하시기 바랍니다.
  * Bro Script를 이용하여 작성 됩니다.
  
 
### 키관리서버 
* 키관리서버는 윈도우서버와 독립된 데이터베이스 서버입니다.
* Mysql
  * 설치방법은 [윈도우서버](###윈도우서버) 의 [mysql 설치]를 참조ㅉ하시면 됩니다.
  * 설치완료 후 데이터베이스 및 테이블 생성
    * 본 테스트 플랫폼은 아래와 같이 생성하시면 됩니다.
     ```
     준비 중입니다.
     ```
    * 사용자환경에 따라 데이터베이스 구성을 바꿔서 사용하시면 됩니다.

## 사용방법
설치/실행환경이 구성이 완료되면 플랫폼을 사용하실 수 있습니다.
사용방법은 아래항목을 참조하세요.

### 라즈베리파이
* 라즈베리파이 실행파일 사용방법
  * 소스코드파일과 실행파일을 라즈베리파이에 다운받습니다.
  * 터미널 실행 후 실행파일이 있는 경로로 이동 후 실행파일을 아래와 같이 실행하시면 됩니다.
    ```
    sudo ./TestClient
    ```
  * 소스코드 수정시에는 아래와 같이 실행파일을 재생성 해주어야 합니다.
    ```
    gcc -o TestClient TestClient.c
    ```
  
### 윈도우서버
* 윈도우서버 실행방법
  * 윈도우서버파일을 다운로드하여 디버그폴더의 exe파일을 실행하시면 됩니다.
  * 소스코드수정은 Visual Studio 2015에서 수정할 수 있습니다.
  * 이 외의 버전에서도 수정이 가능하나 사용자환경에 맞는 설정변경이 필요합니다.
  
### 안드로이드
* 안드로이드 애플리케이션 실행방법
  * 자신의 안드로이드로 apk파일을 다운로드하여 실행하시면 됩니다. 
  * 소스코드수정은 Android Studio에서 수정할 수 있습니다.
  
### Bro IDS
* 준비중 입니다.

### 키관리서버
* 준비중 입니다.

테스트중입니다.
-------
