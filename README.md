### [📥️ 플러그인 포함 (1.09GB)](https://drive.google.com/open?id=1A5LsWv1XZ70j1onYTFyVOTSqL5z6H8pL&usp=drive_fs)
### [📥️ 플러그인 미포함 (696MB)](https://drive.google.com/open?id=1AAypVbSScndX4peayZE9xHUkDp1nejeP&usp=drive_fs)

# 🔍️ Portable SonarQube

정적 코드 분석 도구 **SonarQube**를 **별도의 추가 설치** 및 **PC 환경변수의 편집** 없이 편리하게 실행할 수 있음

- 해당 메뉴얼이 대상으로 하는 환경

  1. Windows

- 해당 메뉴얼이 대상으로 하는 프로젝트의 개발환경

  1. React (javascript)
  2. Gradle (Java)  
  이하 Contains 참조

### 📚️ Contains
- [SonarQube 10.1.0.73491](https://www.sonarsource.com/open-source-editions/)
- [OpenJDK 17.0.8+7](https://adoptium.net/temurin/releases/)
- [Apache Maven 3.9.4](https://maven.apache.org/download.cgi)
- [Gradle 8.2](https://gradle.org/releases/)
- [NodeJS 18.17.1](https://nodejs.org/ko/download)
- [Python 3.10.10](https://www.python.org/downloads/windows/)
- Plugin: FindBugs
- Plugin: PMD

___
## 📥️ 설치

**⚠️중요** : 첨부된 압축 파일을 **C:\\** 경로에 해제  
![image](https://github.com/SJ70/SonarQubePortable/assets/50670730/a710b399-1597-422d-aab1-8c84e468ef11)

해당 Portable 프로그램은 이상의 개발 도구 및 언어에 대한 코드 분석을 지원함  
다른 버전을 사용 중이라면 별도의 설치 및 배치 파일의 변수 수정을 요할 수 있음  
![image](https://github.com/SJ70/SonarQubePortable/assets/50670730/c58e2b38-3afa-45ca-b808-b03af27f7e87)

___
## 🏃‍♂ 실행

1. PowerShell 혹은 cmd를 통해 배치파일을 실행
``` 
C:\StaticCodeAnalysis> StartSonarQube.bat
```
![image](https://github.com/SJ70/SonarQubePortable/assets/50670730/054e3378-238c-42d1-8063-7f890400ff39)

2. **localhost:9000** 접속 및 로그인
```
id: admin
pw: admin
```
![image](https://github.com/SJ70/SonarQubePortable/assets/50670730/2f9a948e-fde7-4e9e-8cc4-4c145c77e48d)

___
## 🛠️ 프로젝트 생성

1. **Manually** 선택
![image](https://github.com/SJ70/SonarQubePortable/assets/50670730/6e875ca3-decb-4a5f-9b52-63b015a317eb)

2. 프로젝트 생성  
![image](https://github.com/SJ70/SonarQubePortable/assets/50670730/4a7cff7b-0a71-4793-98b1-8eb9c155cbbe)
   - **Project display name** : 프로젝트명 입력
   - **Project key** : 기본적으로 Project display name과 동일

3. **Use the global setting** -> **Create project**
![image](https://github.com/SJ70/SonarQubePortable/assets/50670730/160751d2-26db-4bab-a48e-1799048b46f8)

___
## 🔎 진단 준비

1. **Locally** 선택
![image](https://github.com/SJ70/SonarQubePortable/assets/50670730/ac96cf00-6d8d-451c-a115-eb934a68816d)

2. 토큰 생성
![image](https://github.com/SJ70/SonarQubePortable/assets/50670730/140e03d0-5464-4a0f-8f1b-f3acae171f55)

3. 프로젝트에서 사용 중인 빌드 도구 선택
![image](https://github.com/SJ70/SonarQubePortable/assets/50670730/fd95c848-2d42-49b3-9858-b228c282874a)
**build.gradle**에 아래의 내용 추가
```
plugins {
  id "org.sonarqube" version "4.2.1.3168"
}
```

___
## 🔍️ 진단

초기에 **StartSonarQube.bat**을 실행하였던 콘솔창을 다룸  

1. 프로젝트의 경로로 이동 (**build.gradle**가 위치한 디렉터리의 경로)
![image](https://github.com/SJ70/SonarQubePortable/assets/50670730/3d64a761-f60c-461f-be5d-41ac0cbbba23)

2. 아래의 명령어를 실행
![image](https://github.com/SJ70/SonarQubePortable/assets/50670730/24b7d95d-ffcd-4ba4-9c3b-46404206559f)
개행 없이 명령어를 입력
```
gradlew sonar -Dsonar.projectKey=키 -Dsonar.projectName=이름 -Dsonar.host.url=http://localhost:9000 -Dsonar.token=토큰
```

3. 대기  
![image](https://github.com/SJ70/SonarQubePortable/assets/50670730/5376f8e7-30b6-447b-a18e-670cbd73ac37)

___
## 📄 진단 결과

![image](https://github.com/SJ70/SonarQubePortable/assets/50670730/71ee659f-b029-45b1-bdef-d73cd465aa36)

1. **신뢰성 (Reliability)**
코드의 안정성과 일관성
잠재적인 문제 식별

2. **유지보수성 (Maintainability)**
복잡한 코드 구조
주석 부족
코드 중복

3. **보안 (Security)** : **⚠️핵심⚠️**
취약점, 약점 식별

4. **보안 검토 (Security Review)**
보안 표준과 일치하도록 개선이 필요한 부분을 강조


___
## ⛔️ 프로그램 종료
실행 중인 콘솔 창에서 종료  
```
ctrl + c
```

---
### Quality Profiles
각 언어에 따른 진단 기준 모음집  

![image](https://github.com/SJ70/SonarQubePortable/assets/50670730/4131e627-fc76-4d3b-9d0e-8da2acc4206f)
**Set as Default** 을 통해 진단 기준을 변경할 수 있음  

### Rules
진단 기준들에 대하여 열람할 수 있음  

___
Reference
- [소프트웨어 개발보안 가이드(2021.12.29)](https://www.kisa.or.kr/2060204/form?postSeq=5&lang_type=KO&page=1)
- [공개SW를 활용한 소프트웨어 개발보안 점검가이드](https://www.kisa.or.kr/2060204/form?postSeq=10&lang_type=KO)
- [전자정부프레임워크 PMD Rule](https://www.egovframe.go.kr/wiki/doku.php?id=egovframework:dev:imp:inspection)
- [SonarQube 행자부 보안취약점 대응표](https://confluence.curvc.com/pages/releaseview.action?pageId=33327477)
