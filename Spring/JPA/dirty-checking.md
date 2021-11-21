# Dirty Checking(변경 감지)
- 엔티티의 변경 사항을 데이터베이스에 자동으로 반영하는 기능이다.
- 변경 데이터를 감지해서 트랜잭션 커밋 시점에 자동으로 update한다.

## 준영속 엔티티
- 영속성 컨텍스트가 더 이상 관리하지 않는 엔티티를 말한다. (**영속성 컨텍스트에 한 번 들어갔다온 엔티티**)
- 임의로 만들어진 객체가 기존 식별자를 갖는 경우도 준영속 엔티티로 볼 수 있다.
- 준영속 엔티티를 수정하는 방법에는 `변경 감지`와 `병합`이 있다.

```java
    @PostMapping(value = "/items/{itemId}/edit")
    public String updateItem(@ModelAttribute("form") BookForm form) {
    
        Book book = new Book();
        book.setId(form.getId());
        book.setName(form.getName());
        book.setPrice(form.getPrice()); book.setStockQuantity(form.getStockQuantity());
        book.setAuthor(form.getAuthor());
        book.setIsbn(form.getIsbn());
    
        itemService.saveItem(book);
        return "redirect:/items";
    }
```
> 해당 코드에서 book은 준영속 엔티티이기 때문에 setter를 통해서 데이터를 변경해도 값이 변경되지 않는다. <br>
이런 경우에 병합과 변경 감지를 사용해서 데이터를 변경해주어야 한다. <br>

## Dirty Checking(변경 감지)
- 변경 감지 기능은 영속성 컨텍스트에서 엔티티를 다시 조회한 후에 데이터를 변경하는 방법이다.
- 준영속 엔티티의 식별자를 이용해서 영속성 컨텍스트에서 영속 엔티티를 조회하고 변경 감지를 통해 데이터를 변경한다.
- 트랜잭션 커밋 시점에 변경된 데이터를 감지해서 데이터베이스에 Update SQL을 전송한다.
```java
  @Transactional
    public void updateItem(Long itemId, String name, int price, int stockQuantity) {

        Item findItem = itemRepository.findOne(itemId);
        findItem.change(name, price, stockQuantity);
    }
    
   // 영속 엔티티의 필드 변경 -> 변경 감지 작동
   public void change(String name, int price, int stockQuantity) {
        this.setName(name);
        this.setPrice(price);
        this.setStockQuantity(stockQuantity);
   }
```
- 해당 코드에서 넘어온 기존 식별자(itemId)를 사용해서 영속 엔티티를 조회하고 변경 메서드를 통해서 데이터를 변경하고 있다.
- 이처럼, setter를 남발해서 데이터를 변경하기 보단 의미있는 메서드를 만들어서 데이터를 변경하는 것이 좋다. <br>
➡ **변경지점이 엔티티로 넘어감, 어디서 변경되는지 바로 확인 가능**

## merge(병합)
- 준영속 상태의 엔티티를 영속 상태로 변경하는 기능이다.
- 병합은 코드 자체는 간단하지만, 모든 필드의 데이터가 변경되며 병합시 값이 없는 경우에는 `null`로 업데이트 될 위험이 있다.

### merge 동작 과정
![image](https://user-images.githubusercontent.com/61447654/142768932-8b9bcfed-624f-49c3-81d3-e1d7c56b358d.png)

✅ **병합 동작 방식 간단 정리**
1. 준영속 엔티티의 식별자 값으로 영속 엔티티를 조회한다.
2. 영속 엔티티의 값을 준영속 엔티티의 값으로 모두 교체한다.(병합)
3. 트랜잭션 커밋 시점에 변경 감지 기능이 동작하여 데이터베이스에 Update SQL이 실행된다.

## 변경 감지 vs 병합 둘 중에 무엇을 써야하나????
- 엔티티를 변경할 때는 항상 변경 감지를 사용하는 것이 좋다.
- 병합은 모든 속성을 변경하지만 변경 감지는 원하는 속성만 변경할 수 있기 때문에 더 효율적으로 데이터 수정이 가능하기 때문이다.
- 데이터 변경 시 컨트롤러에서 엔티티가 아닌 DTO 객체를 생성해서 필요한 값만 전달해야 한다.
