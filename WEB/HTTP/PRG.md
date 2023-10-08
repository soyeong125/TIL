# PRG 
- Post/Redirect/Get
- 웹 개발 패턴 중 자주쓰이는 패턴으로, HTTP POST 요청에 대한 응답을 GET 방식의 리다이렉트 요청으로 만드는 것이다.

> 사용자가 주문을 했다. POST로 주문이 이루어졌고 주문 완료 후 새로고침을 했다.
> 중복 주문이 발생했다. 이 경우 어떻게 해결하면 좋을까?

- PRG 사용 전 로직을 그리면 아래와 같다.
<img width="666" alt="image" src="https://github.com/soyeong125/TIL/assets/57309311/86e05043-0e48-4251-8ec5-eb3b606211cf">

```
@Controller
class TestController {

    @GetMapping
    public String main(){
        return "main";
    }

    @PostMapping("/order")
    public String order(){
        // 결제 로직
        return "success";
    }
}

```

PRG 적용 전엔 결제 버튼을 클릭하면 성공페이지로 가지만 새로고침을 하게 되면 똑같은 POST 요청이 보내지면서 오류가 발생한다.

- PRG 를 사용하면 이런 문제를 해결할 수 있다.
- POST로 주문 후 결과 화면을 GET 메서드로 리다이렉트함으로써 새로고침 해도 결과 화면이 GET으로 조회 요청이 된다.
- 그래서 주문이 아닌 조회를 요청하게 된다.
  
<img width="662" alt="image" src="https://github.com/soyeong125/TIL/assets/57309311/b146293a-b76d-49aa-94bb-877b8af03c9c">

```
@Controller
class TestController {

    @GetMapping
    public String main(){
        return "main";
    }

    @PostMapping("/order")
    public String order(){
        // 결제 로직
        return "redirect:/order-result";
    }

    @GetMapping("/order-result")
    public String orderResult(){
        return "order-result";
    }
}

```

</br>
이렇게 수정하면 /order 에서 POST 요청이 오면 302 응답코드를 받게 되고 302 응답코드를 받은 브라우저는
/order-result 라는 곳으로 리다이렉트 된다. /order-result 로 이동했기 때문에 새로고침을 하더라도 GET /order-result 로 새로고침을 하게 된다.
