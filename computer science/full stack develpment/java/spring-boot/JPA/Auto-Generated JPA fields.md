
[[JPA]] has a advantage to auto generate the fields like createdBy, created_ts, updated_by, updated_ts

[[spring-annotation]] for these are 

```
@CreatedDate
@CreatedBy
@LastModifiedDate
@LastModifiedBy
```

## Now the question is how [[JPA]] knows that the created_by and updated_by

For that we need to create a new implementation class by implementing the interface `AuditorAware<T (created_by type| updated_by type)>` and we need to annotate the entity with the `@EntityListeners(AuditingEntityListener.class)` and also we need to annotate the main application class with `@EnableJpaAuditing(auditorAwareRef = {bean_name})`


```java
@Component("auditAwareImpl")
public class AuditAwareImpl implements AuditorAware<String> {     
    @Override  
    public Optional<String> getCurrentAuditor() {  
        return Optional.of("ACCOUNTS_MICRO_SERVICE");  
    }  
}
```

POJO class:

```java
@EntityListeners(AuditingEntityListener.class)  
public class BaseEntity {

	@Column(updatable = false)  
    @CreatedDate  
    private LocalDateTime createdAt;  
  
    @Column(insertable = false)  
    @CreatedBy  
    private String createdBy;  
  
    @Column(updatable = false)  
    @LastModifiedDate  
    private LocalDateTime updatedAt;  
  
    @LastModifiedBy  
    @Column(insertable = false)  
    private String updatedBy;  
    
}
```

Spring application:

```java
@SpringBootApplication  
@EnableJpaAuditing()
public class AccountsApplication {  
  
    public static void main(String[] args) {  
       SpringApplication.run(AccountsApplication.class, args);  
    }  
  
}
```
