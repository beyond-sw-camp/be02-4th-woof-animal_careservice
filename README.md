<h1 align="center">데브옵스 아키텍쳐 구현 👍</h1>


<div align="center">
  <img src="./img/pic1.png"  style="zoom:76%;" align="center"/>
</div>



> [플레이 데이터] 한화시스템 BEYOND SW캠프 / WOOF

## 💻 STACKS
<div align=center>
<img src="https://img.shields.io/badge/GitHub-181717?style=flat&logo=GitHub&logoColor=white&color=black">
<img src="https://img.shields.io/badge/Git-F05032?style=flat&logo=Git&logoColor=white&color=ffa500">
<img src="https://img.shields.io/badge/jenkins-D24939?style=flat&logo=jenkins&logoColor=white">
<img src="https://img.shields.io/badge/Docker-2496ED?style=flat&logo=Docker&logoColor=white&color=blue"/>
<img src="https://img.shields.io/badge/Kubernetes-326CE5?style=flat&logo=Kubernetes&logoColor=blue&color=skyblue"/>
<img src="https://img.shields.io/badge/slack-4A154B?style=flat&logo=slack&logoColor=white">
</div>

***

🎬[CI/CD 시연영상](https://www.youtube.com/watch?v=dhMrKTwNI8U&lc=UgzCJR3WxkvsckRyyO94AaABAg&ab_channel=%EB%94%B0%EB%9D%BC%ED%95%98%EB%A9%B4%EC%84%9C%EB%B0%B0%EC%9A%B0%EB%8A%94IT)   
📃[프로젝트 회고록](블로그주소)

<br>


## 📌 프로젝트 목표

```
팀원 각자가 수정한 코드를 자동으로 빌드, 통합하고 통합한 코드를 편리하게 배포하기 위해 젠킨스 파이프라인을 구축하여 CI/CD를 적용했습니다.
```

***
1. Jenkins란?

```
모든 언어의 조합과 소스 코드 레포지토리에 대한 지속적인 통합(Continuous integration, CI)과 지속적 배포(continuous delivery, CD) 환경을 구축하기 위한 도구이다.
이를 통해 빌드, 테스트, 배포 프로세스를 자동화하여 소프트웨어 품질과 개발 생산성을 높일 수 있다.
또한, 안정적인 빌드 및 배포 환경 구축이 가능하여 소스 버전 관리 툴과 연동하여 코드 변경을 감지하고, 자동화 테스트를 포함한 빌드를 수행하여 소프트웨어 품질을 향상시킬 수 있다.

Jenkins는 오픈 소스 소프트웨어로서 잘 문서화되어 있으며, 다양한 적용 사례들을 참고할 수 있다. 
빌드 및 배포 외에도 Jenkins는 스케줄링을 이용한 배치 작업에도 활용될 수 있다. 
또한 사용자는 플러그인을 개발하여 Jenkins의 기능을 확장할 수 있다. 
```

2. 기능
```
젠킨스와 같은 CI툴이 등장하기 전에는 일정시간마다 빌드를 실행하는 방법이 일반적이었는데, 젠킨스는 서브버전, Git과 같은 버전 관리 시스템과 연동해서 소스의 커밋을 감지하면 자동적으로 자동화 테스트가 포함된 빌드가 작동하도록 도와주게 되어 편의성이 증가되었다.
이러한 기능을 수행하는 젠킨스는 컴파일 오류를 검출하고, 자동화 테스트를 수행하며, 정적 코드 분석으로 인한 코딩 규약 준수 여부를 체크하고 프로파일링 툴을 이용한 성능 변화 감시, 결합 테스트 환경에 대한 배포 작업의 큰 도움을 준다.
프로젝트 기간 중에 개발자들은 순수한 개발 작업 이외의 DB 설정, 환경 설정, Deploy 작업과 같은 단순 작업에 시간과 노력을 들이는데, 이러한 작업들을 젠킨스를 사용함으로 젠킨스에서 지원하는 웹 인터페이스를 통해 쉽게 수행할 수 있게 된다.
```

3. 최종 목표

```


```


4. 운영중인 환경에 CI/CD 적용

```


```



## 🖥️ 운영 환경
***
K8S 관련 이미지 및 간단 설명
-> 사양 표시되는 노드들 캡쳐하기!!


## ✨ CI/CD 시나리오 설명
***

- CI : 어떤 과정을 통해 자동으로 테스트 후 결과에 따라 통합 된다는 내용 추가
- CD : 어떤 과정을 통해자동으로 운영중인 서버에 무중단 배포 된다는 내용 추가


<details>
<summary>프론트엔드 CI/CD</summary>
<div>

```
1. git clone 단계는 주어진 git 레포에서 프론트 코드를 가져옵니다.
2. install dependencies 단계를 통해 프로젝트 의존성 설치 후 npm run build를 사용해 빌드하였습니다.
3. build 단계를 통해 프로젝트 빌드 후 archinve dist 단계에서 빌드된 파일 배포 준비를 하고 dist 디렉토리 이용해서 빌드된 파일을 front.tar로 압축시킵니다.
4. ssh transfer 단계에서 빌드된 아카이브 파일 원격 서버로 전송 후 배포, ssh 연결 설정 후 front.tar 파일 원격 서버의 /usr/share/nginx/html 디렉토리로 전송 후 해당 디렉토리에서 압축 해제합니다.



*각 단계는 프로젝트 특정 단계를 자동화 후 빌드 및 배포 프로세스를 효율적으로 관리할 수 있도록 도와줍니다. 
이 파이프 라인은 프론트엔드 프로젝트의 CI/CD를 위해 사용 되었으며, 각 단계는 프로젝트의 해당 작업을 처리하기 위해 설정되었습니다.*
```


</div>
</details>

<details>
<summary>백엔드 CI/CD</summary>
<div>

```
1. git clone 단계를 통해 git 레포에서 소스 코드를 가져옵니다.
2. install dependencies 단계에서 프로젝트 의존성 설치 위해 npm install 명령을 실행 후, build 단계에서 프로젝트 빌드 위해 npm run build 명령을 실행하였다. 
3. 다음 archive dist 단계를 통해 빌드된 결과물을 아카이브에 압축파일로 만들고 dist 디렉토리로 이동 후 tar 명령어로 압축 수행, 결과를 파일 상위 디렉토리로 이동시켰습니다. 
4. 다음 ssh transfer 단계를 통해 압축된 파일 원격 서버 전송하기 위해 ssh 연결 설정을 하고,
5. ssh publisher 내 ssh pulisher desc 연결 설정 후 ssh transer 파일로 전송 구성, sourcefile에는 전송 파일을 remote directory에는 파일 전송할 원격 디렉토리 지정, 
execcommand 원격 서버 실행할 명령을 지정하였습니다.


*jenkins에서 백엔드 CI/CD 자동화 하는데 사용, 각 단계는 빌드 및 배포 과정에 필요한 작업을 수행하며, jenkins는 파이프라인을 실행해 정의된 단계를 차례로 수행하였습니다.*

```
</div>
</details>



## CI/CD 테스트 및 결과
***
<details>
<summary>프론트 엔드 CI/CD 결과</summary>
<div>

</div>
</details>

<details>
<summary>백엔드 CI/CD 결과</summary>
<div>

</div>
</details>


## k8s상의 전체 서비스 아키텍쳐



<img src="img\시스템 아키텍처 데브옵스2.png"/>

```
디플로이먼트로 프론트, 백, DB파드를 생성하고 서비스를 사용하여 각 파드에 고유한 Cluster IP를 할당하였습니다.
이를 통해 프론트 파드는 백엔드 서비스의 Cluster IP를 사용하여 백엔드와 통신하고, 백엔드 파드는 DB 서비스의 Cluster IP를 사용하여 DB와 통신할 수 있습니다.
또한 사용자가 프론트 서비스를 이용할 수 있도록 LoadBalancer 타입의 서비스를 생성하였습니다.
```
***

## k8s 클러스터 구성 아키텍쳐 
***
<img src="./img/클러스터 구성 아키텍처.png">



## 🤼‍♂️팀원
***

Master  : 🐯**김주연**

Worker : 🐶 **강지흔**

Worker : 🐺 **이창훈**

Worker : 🐱 **강문혜**

Worker : 🦁 **김지은**
