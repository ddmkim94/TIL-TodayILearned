# JPA Annotation

**@Repository:** Spring-Boot가 `Component-Scan`을 통해 스프링 빈으로 등록될 수 있게 만들어주는 어노테이션, 실제 JPA와 연동하는 곳

**@PersistenceContext:** `EntityManager` 주입 어노테이션

```java
package jpabook.jpashop.repository;

import jpabook.jpashop.domain.Member;
import org.springframework.stereotype.Repository;

import javax.persistence.EntityManager;
import javax.persistence.EntityManagerFactory;
import javax.persistence.PersistenceContext;
import javax.persistence.PersistenceUnit;
import java.util.List;

@Repository
public class MemberRepository {

    @PersistenceContext
    private EntityManager em;


    // 회원 저장
    public void save(Member member) {
        em.persist(member); // member 객체를 영속성 컨텍스트에서 관리
        // member.getId();
    }

    // 특정 회원 조회(ID)
    public Member findOne(Long id) {
        return em.find(Member.class, id); // 식별자를 통해서 해당 회원을 검색
    }

    // 전체 회원 조회
    public List<Member> findAll() {
        // createQuery: JPQL을 사용해서 DB를 검색할 때 사용하는 Method
        return em.createQuery("select m from Member m", Member.class).getResultList();
    }

    // 특정 회원 조회(NAME)
    public List<Member> findByName(String name) {
        return em.createQuery("select m from Member m where m.name = :name", Member.class)
                .setParameter("name", name).getResultList();
    }
}
```

**@Transactional** <br>
➡️ 해당 클래스의 메서드를 `트랜잭션` 안에서 동작하도록 만들어주고, 성공은 `commit`, 실패는 `rollback` 처리 <br>
➡️ 반복 가능한 테스트 지원, 각각의 테스트를 실행할 때마다 트랜잭션을 시작하고 테스트가 끝나면 강제로 롤백`(테스트 케이스에서만 이렇게 동작)`

**@RequiredArgsConstructor:** final 필드들만 모아서 생성자를 생성해주는 Lombok 어노테이션

**@Autowired** <br>
➡️ 스프링 빈을 자동주입해주는 어노테이션 <br>
➡️ 필드 주입, 수정자(setter) 주입, 생성자 주입이 있으며 생성자 주입을 가장 많이 사용함 `(생성자가 하나인 경우 @Autowired 생략이 가능)`

```java
package jpabook.jpashop.service;

import jpabook.jpashop.domain.Member;
import jpabook.jpashop.repository.MemberRepository;
import lombok.RequiredArgsConstructor;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;
import org.springframework.transaction.annotation.Transactional;

import java.util.List;

@Service
@Transactional(readOnly = true)
@RequiredArgsConstructor // final field만 이용해서 생성자 생성 || Lombok
public class MemberService {

    private final MemberRepository memberRepository;

    /* Constructor Injection(생성자 주입)
    @Autowired => 생성자가 1개인 경우 @Autowired 생략이 가능!
    public MemberService(MemberRepository memberRepository) {
        this.memberRepository = memberRepository;
    }
    */

    // 회원 가입
    @Transactional(readOnly = false) // default = false
    public Long join(Member member) {
        validateDuplicateMember(member);

        memberRepository.save(member);
        return member.getId();
    }

    // 중복 회원 검사 Method!
    private void validateDuplicateMember(Member member) {
        List<Member> findMembers = memberRepository.findByName(member.getName());
        if(!findMembers.isEmpty()) {
            throw new IllegalStateException("이미 존재하는 회원입니다!");
        }
    }

    // 회원 전체 조회
    public List<Member> findMembers() {
        return memberRepository.findAll();
    }

    // 특정 회원 조회
    public Member findOne(Long id) {
        return memberRepository.findOne(id);
    }
}
```

<br>

## [출처] - <a href="https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8-JPA-%ED%99%9C%EC%9A%A9-1/">실전! 스프링부트 JPA 활용 1 (우아한형제들 - 김영한님)</a>
