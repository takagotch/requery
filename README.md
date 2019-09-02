### requery
---
https://github.com/requery/requery

```java
@Entity
abstract class AbstractPerson {
  
  @Key @Generated
  int id;
  
  @Index("name_index")
  String name;
  
  @OneToMany
  Set<Phone> phoneNumbers;
  
  @PostLoad
  void aferLoad() {
    updatePeopleList();
  }
}

@Entity
public interface Person {
  
  @Key @Generated
  int getId();
  
  String getName();
  
  @OneToMany
  Set<Phone> getPhoneNumbers();
  
  String getEmail();
}

```

```
```

```
```


