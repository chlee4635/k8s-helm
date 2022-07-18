# k8s-helm

### heml이란? 
k8s 패키지매니저 ( brew, apt 와 같은.. )

### helm 소개와 구조
##### helm 소개
쿠퍼네티스용 패키지 매니저 
* 패키지 = 쿠버네티스 리소스 집합 = 차트 
쿠버네티스 어플리케이션의 라이프 사이클 관리

기존 리눅스 설치방법?
소스 다운로드 -> 의존성 어플(패키지) 설치 -> 소스 컴파일 -> 실팽파일 복사 -> 어플리케이션 설정
패키지 매니저가 이러한 문제를 해결 ( yum install.. apt install.. )

쿠퍼네티스에서는? helm iuninstall

히스토리?
<img width="897" alt="스크린샷 2022-07-18 10 30 00" src="https://user-images.githubusercontent.com/71858757/179433707-edfeb89d-5a9a-4740-9f8d-bf037d91e7d2.png">

컨셉?
- 차트(chart) : 쿠버네티스용 어플리케이션 패키지 (명칭)
- 설정(config) : 차트에 적용될 어필르케이션 설정 ( volumne ...등 )
- 릴리즈(release) : helm 차트로 배포된 어플리케이션

컨포넌트?
- helm CLI
- heml 라이브러리
- Golang 개발
- 쿠버네이트스 시크릿을 데이터베이스 개념으로 사용

---
Helm 구조
- Helm CLI, Library 
- CLI 만 다운받으면 사용가능

버전
- helm 1.0 : client only
- helm 2.0 : client - server ( 미들웨어로 TILLER를 사용, 문제점 - 보안이슈, 에러 트러블 슈팅이 힘듬 ) 
- helm 3.0 : client only ( api로 통신 - 인증을 쿠버네티스에 위임, 쿠버네티스에 부여된 사용자만 사용가능 )

Helm Storate Backend
- 모든 정보가 Secret에 저장(default)
- Configmap, PostgreSQL 지원 

Helm Release in Namespace
- 어플리케이션 릴리즈는 네임스페이스에 종속
- 해당 네이임스페이스의 시크릿을 보면 설정정보를 알수 있음

Helm Chart
- 쿠버네티스 어플리케이션을 만들기 위한 모든 정보를 묶어놓은 단위
- 차트를 작성하고 실행하여 배포

Helm Chart Repository
- Helm 차트를 저장하는 저장소
- helm repo list
- 원격 저장소 ArtifactHub, bitnami by vmware
- 로컬 저장소 Chart Museum


### helm 차트 개발 및 테스트 
[ Helm CLI 설치 ]
준비사항 
- kubectl 실행 환경 ( = kubernetes cluster )
- mikube ( [minikube.io](https://minikube.sigs.k8s.io/docs/start/) )
- https://helm.sh/docs/intro/install/ ( From Script 방식 사용 - 환경에 맞춰 버전을 선택하여 설치됨 )
- helm version

[ Helm 차트 설치 ]
helm install [NAME-어떤이름으로 설치할지] [CHART-어떤 어플리케이션차트를 설치할지] [flags-옵션]
helm repo list
helm search repo [NAME]
heml ls 

kubectl get po 
kubectl get cm
kubectl get svc
kubectl get pvc
kubectl get secret


[ Helm 차트 업그레이드 ]

[ Helm 차트 롤백 ]

[ Helm 명령어 ]

### helm 차트 저장소 구축 실습
