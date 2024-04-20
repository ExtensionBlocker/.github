# 마드라스체크 사전과제
파일 확장자 차단 시스템 - 김민기
<br><br>

## 💡 개요
어떤 파일들은 첨부 시 보안에 문제가 될 수 있다. 특히 exe, sh 등의 실행 파일이 존재할 경우 서버에 올려서 실행이 될 수 있는 위험이 있어 파일 확장자 차단을 한다.
<br><br>

## ✔️ 요구사항
1-1. 고정 확장자는 차단을 자주하는 확장자를 리스트이며, default는 unCheck되어져 있습니다.
<br>
1-2. 고정 확장자를 check or uncheck를 할 경우 db에 저장됩니다. - 새로고침시 유지되어야합니다. (아래쪽 커스텀 확장자에는 표현되지 않으니 유의해주세요.)
<br><br>
2-1. 확장자 최대 입력 길이는 20자리
<br>
2-2. 추가버튼 클릭시 db 저장되며, 아래쪽 영역에 표현됩니다.
<br><br>
3-1. 커스텀 확장자는 최대 200개까지 추가가 가능
<br>
3-2. 확장자 옆 X를 클릭시 db에서 삭제
<br><br>

## 🚀 추가 고려사항 및 개선사항

### 추가 고려사항
1. 확장자는 영어만 가능하도록 정규표현식으로 제한한다.
2. 확장자 내용이 없는 경우 추가하지 못하도록 제한한다.
3. 고정 확장자인 경우 커스텀 확장자에 등록을 제한한다.
4. 이미 등록된 확장자의 경우 중복 등록을 제한한다.

### 개선사항
1. 로컬 스토리지를 활용한 고정확장자 체크박스 상태유지 기능구현
2. 여러 호스트에서 접속 했을 때 로컬스토리지와 DB의 데이터 불일치 현상 발생
<br><br>
시도1. DB조회
- 클라이언트에서 렌더링시점에 서버에 고정 확장자 목록을 요청하고 데이터를 응답받아 DB에 있는 고정 확장자의 체크박스를 유지시킨다.
<br><br>
시도2. cache DB 이용
- 여러 호스트에서 동일한 로컬스토리지 값을 공유해야한다는 아이디어
- 고정 확장자 등록 시 캐시 DB에 key, value 값 추가, 새로고침 시점에 캐시 DB 조회하여 체크박스를 유지 시킨다.
- 고정 확장자 삭제 시 key 값을 이용하여 remove
<br><br>

## 🖥️View
<img width="834" alt="스크린샷 2024-04-20 오후 5 21 09" src="https://github.com/ExtensionBlocker/.github/assets/80161984/3bed3c6a-91cd-4a3b-9245-636260ab37e0">

## 🔑사용기술

### WEB
<img src="https://img.shields.io/badge/react-61DAFB?style=for-the-badge&logo=react&logoColor=white"> <img src="https://img.shields.io/badge/styled components-DB7093?style=for-the-badge&logo=styled-components&logoColor=white">
<img src="https://img.shields.io/badge/html5-E34F26?style=for-the-badge&logo=html5&logoColor=white">
<img src="https://img.shields.io/badge/css3-1572B6?style=for-the-badge&logo=css3&logoColor=white">
<img src="https://img.shields.io/badge/node.js-6DB33F?style=for-the-badge&logo=nodedotjs&logoColor=white">
<img src="https://img.shields.io/badge/npm-CB3837?style=for-the-badge&logo=npm&logoColor=white"> 

### SERVER
<img src="https://img.shields.io/badge/java-007396?style=for-the-badge&logo=java&logoColor=white"> <img src="https://img.shields.io/badge/springboot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white"> <img src="https://img.shields.io/badge/spring data jpa-6DB33F?style=for-the-badge&logoColor=white"> <img src="https://img.shields.io/badge/hibernate-59666C?style=for-the-badge&logo=hibernate&logoColor=white"> <img src="https://img.shields.io/badge/gradle-02303A?style=for-the-badge&logo=gradle&logoColor=white"> <img src="https://img.shields.io/badge/amazon rds-527FFF?style=for-the-badge&logo=amazonrds&logoColor=white"> <img src="https://img.shields.io/badge/mysql-4479A1?style=for-the-badge&logo=mysql&logoColor=white"> 


## 🛠️Development
![image](https://github.com/ExtensionBlocker/.github/assets/80161984/f105ba39-1162-48cc-80ff-6c04ffcae50a)




