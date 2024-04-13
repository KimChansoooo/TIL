# Use BeanUtils copyProperties

> 동일한 필드 값을 재사용하는 경우
> 
> 전체 필드를 공유하는데, 필드의 갯수가 많고 가독성이 떨어지는 경우 사용할 수 있다.

******

```java
import org.springframework.beans.BeanUtils;

CreateDto create = new CreateDto();
UpdateDto update = new UpdateDto();

/* 일일히 매핑 */
update.setCompany(create.getCompany());
update.setRefSeq(create.getSeq());

/* BeanUtils 라이브러리 사용 */
BeanUtils.copyProperties(create, update);   // create를 update로 복사
```
```java
/**
 * source {원본 객체}
 * target {대상 객체}
 */
public static void copyProperties(Object source, Object target) throws BeansException {
    copyProperties(source, target, (Class)null, (String[])null);
}
```

[//]: # (MapStruct를 사용할 수 도있다.)