---
title: "Spring Bean Scope"
date: 2021-06-02 20:30:00 +0900
categories: spring
---
# Spring Bean Scope

여러가지 Scope가 있지만,
99%는 Singleton쓰는 거로 괜찮다.(John Thompson)

''' Java
// SingletonBean.java
// 싱글톤 예제 : 디폴트가 싱글톤이다
import org.springframework.stereotype.Component;

@Component
public class SingletonBean {
    // 스프링 실행시 한번만 실행
    public SingletonBean() {
        System.out.println("Creating a Singleton Bean!!!");
    }

    public String getMyScope() {
        return "I'm a singleton.";
    }
}
'''

''' Java
// PrototypeBean.java
// 프로토타입 예제
import org.springframework.beans.factory.config.ConfigurableBeanFactory;
import org.springframework.context.annotation.Scope;
import org.springframework.stereotype.Component;

// 프로토타입 스코프는 매번 생성된다
@Scope(ConfigurableBeanFactory.SCOPE_PROTOTYPE)
@Component
public class PrototypeBean {
    public PrototypeBean() {
        System.out.println("Creating a Prototype Bean!!!!!");
    }

    public String getMyScope() {
        return "I'm a prototype.";
    }
}
'''
