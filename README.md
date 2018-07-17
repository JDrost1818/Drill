[![drill](http://jakedrost.me/drill/img/drill-logo-with-text.png)](http://jakedrost.me/drill)
```
Specification
    .<Person>where((root, criteriaQuery, criteriaBuilder) -> criteriaBuilder.notEqual(root.get(Person_.id), 1))
    .<Person>and((root, criteriaQuery, criteriaBuilder) -> criteriaBuilder.like(criteriaBuilder.upper(root.get(Person_.firstName)), "John".toUpperCase()))
    .<Person>and((root, criteriaQuery, criteriaBuilder) -> criteriaBuilder.lessThan(root.get(Person_.dateOfBirth), new Date()));
```

Goes To


```
Drill
    .where(Person_.id).not().equalTo(1L)
    .andString(Person_.firstName).equalToIgnoreCase("John")
    .andDate(Person_.dateOfBirth).before(new Date());
```

Since `Drill` extends `Specification`, you can easily replace all uses of specifications with a `Drill` instance.
