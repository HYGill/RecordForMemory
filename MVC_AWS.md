## MVC 구조

1. View
>HTML, jsp 와 같은 Front 부분을 나타낸다
2. Controller
> 요청이 들어오는 URL
3. Service
> 실제 구동이 되게 구현
4. Repository
> DB액세스해서 데이터를 관리해주는 모델의 역할
5. Mapper
> DB


## AWS Cloud

* CloudFront : 엣지 로케이션을 이용하기 때문에 즉 캐시 서버를 이용하기 때문에 빠르고 사용자가 S3에 직접 접근이 어렵도록 하기 때문에 보안에 도움이 된다.

* CloudFrong-invaildation(캐싱 무효화 기능) : 접근한 적이 있으면 cache로 접근하게 되는데 이것을 삭제해준다.

* Load Balancer(ALB) : 하나의 인터넷 서비스가 발생하는 트래픽이 많을 때 여러 대의 서버가 분산처리하여 서버의 로드율 증가, 부하량, 속도저하 등을 고려하여 적절히 분산처리하여 해결해주는 서비스(도메인 사용가능하게해준다)

* AutoScale : 하드웨어 증가 감소(up, down), 하드웨어 개수줄이기 늘리기(in, out) ==> 개수가 로드밸런서와 관련되어 있다.

* BastonServer : SSH 보안 강화
