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

## MVC 패터의 흐름

* Get : 리소스 자원을 read(조회)
> Parameter값이 URL에 표기됨

* Put : update/create(추가)

* Post : 수정
> URL에 표시되지 않고 requestBody에 담아서 전달한다

* Delete : delete
