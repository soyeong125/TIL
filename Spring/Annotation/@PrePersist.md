# @PrePersist
JPA 생명주기 콜백 어노테이션 중 하나이다. 
엔티티가 처음으로 데이터베이스에 저장되기 전에 특정 작업을 수행하도록 지시한다. 그래서 엔티티가 저장되기 전에 필요한 초기화 작업이나 설정 작업을 자동으로 수행한다.
주로 엔티티의 기본 값 설정, 생성 시간 기록, 고유 Id 생성같은 작업에 사용된다.

JPA 로직으로 생각해보면 EntityManager 인터페이스에서 제공하는 persist 메서드가 실행하기 전에 실행되도록 처리해주는 것이다.
> persist 메서드란? </br>
> 새로운 엔티티 인스턴스를 영속성 컨텍스트에 추가해주고 그 결과로 해당 엔티티가 데이터베이스에 저장될 상태로 지정한다. 

# 생성 조건
1. 반환 타입이 void
2. 파라미터를 받지 않아야한다.
3. 엔티티 클래스 내에서 정의되어야 한다.(이 엔티티의 생명주기에만 영향을 준다)


# 예시
```
@Entity
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String username;
    private LocalDateTime createdAt;

    @PrePersist
    public void prePersist() {
        this.createdAt = LocalDateTime.now();
    }
}
```
User 엔티티의 prePersist 메서드는 @PrePersist 어노테이션으로 태깅되어 있다. 따라서 User 엔티티 인스턴스가 데이터베이스에 처음 저장되기 전에 prePersist 메소드가 실행된다.
이 메소드를 통해 사용자가 생성된 시간을 기록하게 된다.
