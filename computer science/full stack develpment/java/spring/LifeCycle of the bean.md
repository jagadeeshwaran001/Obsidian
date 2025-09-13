## **Spring [[bean]] Lifecycle in IoC Container**

1. **Bean Instantiation**
    
    - Spring creates an instance of the bean (using the constructor or factory method).
        
    - Example: `new MyBean()` happens behind the scenes.
        
2. **Populate Properties (Dependency Injection)**
    
    - Spring injects dependencies (via constructor, setter, or field injection).
        
    - This satisfies [[@Autowired]], `@Value`, etc.
        
3. **BeanNameAware (Optional)**
    
    - If the bean implements `BeanNameAware`, Spring calls `setBeanName()`, passing the bean’s name defined in the context.
        
4. **BeanFactoryAware / ApplicationContextAware (Optional)**
    
    - If the bean implements these, Spring gives access to the `BeanFactory` or `ApplicationContext`.
        
5. **BeanPostProcessors – Before Initialization**
    
    - All `BeanPostProcessor` beans get a chance to modify the bean _before_ initialization callbacks.
        
    - Method: `postProcessBeforeInitialization()`.
        
6. **InitializingBean / @PostConstruct / Custom init-method**
    
    - If the bean implements `InitializingBean`, Spring calls `afterPropertiesSet()`.
        
    - If annotated with `@PostConstruct`, that method is invoked.
        
    - If an `init-method` is defined in the config, Spring calls it.
        
    - This is where you put initialization logic.
        
7. **BeanPostProcessors – After Initialization**
    
    - `postProcessAfterInitialization()` runs, giving another chance to modify or wrap the bean (common in proxies like AOP).
        
8. **Bean Ready for Use**
    
    - At this stage, the bean is fully initialized and can be used by the application.
        
9. **Destruction Phase (when context shuts down)**
    
    - If the bean implements `DisposableBean`, Spring calls `destroy()`.
        
    - If annotated with `@PreDestroy`, that method runs.
        
    - If a custom `destroy-method` is defined, Spring calls it.
        
    - Finally, the bean is eligible for garbage collection.