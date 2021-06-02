---
title: "Data loader : 초기 데이터를 넣기"
date: 2021-06-03 06:05:00 +0900
categories: spring study
---
# Data loader 초기 데이터를 설정하는 방법

CommandLineRunner는 스프링 어플리케이션이 실행된 이후에 실행된다.
이를 이용해서 초기값을 설정할 수 있다.

```Java
// DataLoader예제
// CommandLineRunner를 implements한다.
// run메소드에 실행될 것들을 적는다.
public class DataLoader implements CommandLineRunner {

    private final OwnerService ownerService;
    private final VetService vetService;

    public DataLoader() {
        ownerService = new OwnerServiceMap();
        vetService = new VetServiceMap();
    }

    @Override
    public void run(String... args) throws Exception {
        Owner owner1 = new Owner();
        owner1.setId(1L);
        owner1.setFirstName("Michael");
        owner1.setLastName("Weston");
        ownerService.save(owner1);
        
        Vet vet1 = new Vet();
        vet1.setId(1L);
        vet1.setFirstName("Sam");
        vet1.setLastName("Axe");
        vetService.save(vet1);
    }
}
```
