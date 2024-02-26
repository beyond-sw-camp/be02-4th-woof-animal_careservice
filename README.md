<h1 align="center">데브옵스 아키텍쳐 구현 👍</h1>


<div align="center">
  <img src="./img/pic1.png"  style="zoom:76%;" align="center"/>
</div>



> [플레이 데이터] 한화시스템 BEYOND SW캠프 / WOOF

## 💻 STACKS
<div align=center>
<img src="https://img.shields.io/badge/GitHub-181717?style=flat&logo=GitHub&logoColor=white&color=black">
<img src="https://img.shields.io/badge/Git-F05032?style=flat&logo=Git&logoColor=white&color=ffa500">
<img src="https://img.shields.io/badge/jenkins-D24939?style=flat&logo=Jenkins&logoColor=white">
<img src="https://img.shields.io/badge/Docker-2496ED?style=flat&logo=Docker&logoColor=white&color=blue"/>
<img src="https://img.shields.io/badge/Kubernetes-326CE5?style=flat&logo=Kubernetes&logoColor=blue&color=skyblue"/>
<img src="https://img.shields.io/badge/Slack-4A154B?style=flat&logo=slack&logoColor=white">
</div>

***


## k8s 클러스터 구성 아키텍쳐 
***
<img src="./img/클러스터 구성 아키텍처.png">



## k8s상의 전체 서비스 아키텍쳐



<img src="img\시스템 아키텍처 데브옵스2.png"/>

```
디플로이먼트로 프론트, 백 파드를 생성하고 Stateful set으로
DB파드를 생성하였습니다.
서비스를 사용하여 파드에 고유한 Cluster IP를 할당하였습니다.
이를 통해 프론트 파드는 백엔드 서비스의 Cluster IP를 사용하여
백엔드와 통신하고, 백엔드 파드는 DB 서비스의 Cluster IP를
사용하여 DB와 통신할 수 있습니다.
또한 사용자가 프론트 서비스를 이용할 수 있도록
LoadBalancer 타입의 서비스를 생성하였습니다.
```
***


🎬[CI/CD 시연영상](https://www.youtube.com/watch?v=dhMrKTwNI8U&lc=UgzCJR3WxkvsckRyyO94AaABAg&ab_channel=%EB%94%B0%EB%9D%BC%ED%95%98%EB%A9%B4%EC%84%9C%EB%B0%B0%EC%9A%B0%EB%8A%94IT)   
📃[프로젝트 회고록](블로그주소)

<br>


## 📌 프로젝트 목표

```
팀원 각자가 수정한 코드를 자동으로 빌드, 통합하고
통합한 코드를 편리하게 배포하기 위해 젠킨스 파이프라인을 구축하여
CI/CD를 적용했습니다.
```

## 🖥️ 운영 환경
***

<img src="C:\Users\playdata\Downloads\image (11).png"/>

- 1개의 master와 4개의 worker들로 이루어져있다.

## ✨ CI/CD 
***

<details>
<summary>프론트엔드 CI/CD</summary>
<div>


1) 필요성

- 다양한 환경에서의 호환성 보장
 
  다양한 브라우저 및 디바이스에서 프론트엔드 애플리케이션이 제대로 동작하는지 확인하기 위해 CI/CD를 사용하여 자동화된 테스트를 실행할 수 있습니다.

- 버그 및 오류 조기 발견

  CI/CD를 통해 코드 변경 사항이 즉시 통합되고 테스트되므로 버그 및 오류를 조기에 발견하고 수정할 수 있습니다. 

- 자동화된 배포

  CI/CD를 통해 프론트엔드 애플리케이션의 배포 프로세스를 자동화하여 운영 환경으로의 안정적이고 신속한 배포를 가능하게 합니다. 

- 팀 협업 및 통합

  여러 개발자가 동시에 작업하는 경우, CI/CD를 사용하여 변경 사항을 통합하고 충돌을 방지할 수 있습니다. 

2) 효과

- 품질 향상

  자동화된 테스트를 통해 프론트엔드 애플리케이션의 품질을 지속적으로 향상시킬 수 있습니다. 

- 신속한 배포

  CI/CD를 사용하여 자동화된 빌드 및 배포 프로세스를 구축하면 운영 환경으로의 빠르고 신속한 배포가 가능합니다. 

- 안정성 향상

  CI/CD를 통해 자동화된 테스트와 배포 과정을 통해 운영 환경에서의 안정성을 향상시킬 수 있습니다. 
  변경 사항을 테스트하고 배포하는 동안 발생할 수 있는 잠재적인 문제를 사전에 감지하여 예방할 수 있습니다.

- 효율적인 협업 

  CI/CD를 사용하여 변경 사항을 자동으로 통합하고 테스트하는 프로세스를 통해 팀 간 협업이 원활해집니다.
<br/>



</div>
</details>

<details>
<summary>백엔드 CI/CD</summary>
<div>

1) 필요성

 - 빠른 피드백 루프
   CI/CD를 사용하면 코드 변경 사항이 자동으로 테스트되어 빠른 피드백을 받을 수 있습니다. 이는 버그를 빠르게 발견하고 수정하여 품질을 향상시키는 데 도움이 됩니다.

 - 품질 향상
   자동화된 테스트를 통해 백엔드 시스템의 품질을 지속적으로 향상시킬 수 있고, 테스트 커버리지를 높이고 테스트 실패를 최소화하여 더욱 견고한 시스템을 제공할 수 있습니다.

 - 안정성 향상
 CI/CD를 사용하여 자동화된 테스트와 배포 과정을 통해 운영 환경에서의 안정성을 향상시킬 수 있습니다. 이는 잠재적인 문제를 사전에 감지하여 예방할 수 있으며, 서비스의 가용성과 신뢰성을 높이는 데 도움이 됩니다.

2) 효과

 - 품질 향상

   자동화된 테스트를 통해 백엔드 서비스의 품질을 지속적으로 향상시킬 수 있습니다. 테스트를 자동으로 실행하여 버그를 빠르게 발견하고 수정함으로써 소프트웨어의 신뢰성과 안정성을 높일 수 있습니다.

 - 안정적인 배포
 
   CI/CD를 사용하여 자동화된 빌드 및 배포 프로세스를 구축하면 운영 환경으로의 안정적인 배포를 보장할 수 있습니다. 

 - 스케일링 및 확장성
 
   CI/CD를 통해 배포 프로세스를 자동화하면 애플리케이션의 스케일링 및 확장성을 향상시킬 수 있습니다. 새로운 인스턴스를 빠르게 배포하고 관리하여 트래픽 증가에 유연하게 대응할 수 있습니다.

</div>
</details>



## CI/CD 시나리오 및 테스트
***

<details>
<summary>배포 시나리오</summary>
<div>
<br/>
롤링 업데이트 방식을 사용한 이유
<br/>
<br/>
<img src="C:\Users\playdata\Desktop\롤링.png"/>

- 인스턴스를 늘리지 않고 하나씩 새로운 버전으로 업데이트 하는 방식

<br/>

1. 서비스 중단 최소화 : 롤링 업데이트는 서비스 중단 없이 서버를 업데이트할 수 있기 때문에 사용자에게 불편을 최소화합니다. <br/>

2. 고가용성 및 신뢰성 향상 : 롤링 업데이트는 서버의 부분적인 업데이트를 가능하게 하므로 전체 서비스에 영향을 주지 않으면서 서비스의 가용성과 신뢰성을 유지할 수 있습니다.<br/>

3. 부하 분산 : 롤링 업데이트를 통해 업데이트된 서버로 순차적으로 트래픽을 이동시키면서 부하를 분산할 수 있습니다. <br/>

4. 빠른 롤백 : 롤링 업데이트를 사용하면 문제가 발생한 경우 빠르게 롤백할 수 있습니다. <br/>

5. 지속적인 서비스 제공 : 롤링 업데이트를 사용하면 서비스 중단 없이 지속적으로 서비스를 제공할 수 있으므로 사용자에게 연속성 있는 서비스를 제공할 수 있습니다.<br/>

</div>
</details>

<details>
<summary>프론트 엔드 CI/CD 테스트</summary>
<div>
<br/>

TEST

</div>
</details>


## 🤼‍♂️팀원
***

Master  : 🐯**김주연**

Worker : 🐶 **강지흔**

Worker : 🐺 **이창훈**

Worker : 🐱 **강문혜**

Worker : 🦁 **김지은**
