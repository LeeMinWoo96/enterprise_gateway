#### Jupyter enterprise gateway 

**목적 : kernel custom**

----

1. 환경

Helm v3 , okd4 및 ec2 ubuntu minikube(test)

---

2. 진행사항

***Minikube 환경***

- [x] Enterprise gatway 구조 파악 및 노트북 설치
- [x] 설치된 Notebook과 pod으로 올린 gateway와 연동 (ec2 ubuntu minikube 환경)
- [x] Custom kernel을 위한 volume mount(hostPath) (ec2)
- [x] Custom kernel image 생성 (기존 Kernel image 확장)
- [x] jupyter docker-stack 에 들어가 있는 이미지로 kernel Custom
- [x] jupyter docker-stack 과 관련하지 않은 이미지로 Kernel Custom
- [x] Custom kernel 과 Enterprise gatway 연동



***OKD 환경***

- [x] test 환경에 구축한 helm 차트 수정(OKD에 이미 올라온 것과 동일한 내용 수정)
- [x] Jupyter notebook pod 생성
- [x] scc 권한 해제
- [x] notebook pod과 enterpris gateway 연동
- [x] OkD 환경에서 기존 진행해보던 작업 진행


---

 

3. 주의사항

- 이미지는 local 저장소가 아닌 저장소에 있어햐함 
- baseimage 는 jupyter docker-stack일 경우와 완전 custom일 경우 나뉨
- jupyter module 은 설치외어 있어야함
- jupyter_enterprise_gateway_kernel_image_files-2.1.1 부터 pycrypto 모듈 이름 변경
- helm chart의 value 의 white list 는 커널의 디렉토리 명
- kernel lancher 는 환경이나 언어 별로 다름
- 현재는 hostPath로 이루어진 chart


---

4. 사용

helm chart deploy

enterprise service port 확인

ip 와 port를 통해 jupyter 실행

jupyter-lab --gateway-url=*** --ip 0.0.0.0 --allow-root &


---

5. 참고사이트

[Example document](https://jupyter-enterprise-gateway.readthedocs.io/en/latest/docker.html)

[github](https://github.com/jupyter/enterprise_gateway)

[release download](https://github.com/jupyter/enterprise_gateway/releases)

