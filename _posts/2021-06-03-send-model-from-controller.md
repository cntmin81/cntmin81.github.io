---
title: "컨트롤러에서 모델을 이용해 타임리프에 데이터 보내기"
date: 2021-06-03 08:17:00 +0900
categories: spring study
---
# 컨트롤러에서 모델을 이용해 타임리프에 데이터 보내기

```java
// VetsController.java
// 컨트롤러 메소드의 파라미터에 Model을 지정
// addAttribute메소드를 사용하면 알아서 타임리프로 넘어감
@RequestMapping({"", "/", "/index", "/index.html"})
public String listVets(Model model) {
    model.addAttribute("vets", vetService.findAll());
    return "vets/index";
}
```

```html
<!-- vets/index.html -->
<!-- th:each를 사용하여 반복할 수 있다 -->
<tbody>
<tr th:each="vet : ${vets}">
    <td th:text="${vet.id}">1</td>
    <td th:text="${vet.firstName}">Joe</td>
    <td th:text="${vet.lastName}">Buck</td>
</tr>
</tbody>
```
