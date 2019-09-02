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

@AutoValue
@Entity
abstract class Person {
  
  @AutoValue.Builder
  static abstract class Builder {
    abstract Builder setId(int id);
    abstract Builder setName(String name);
    abstract Builder setEamil(String email);
    abstract Person build();
  }
  
  static Builder builder() {
    return new AutoValue_Person.Builder();
  }
  
  @Key
  abstract int getId();
  
  abstract String getName();
  abstract String getEmail();
  
}

Result<Person> query = data
  .select(Person.class)
  .where(Person.NAME.lower().like("b%")).and(Person.AGE.gt(20))
  .orderBy(Person.AGE.desc())
  .limit(5)
  .get();

@Entity
abstract class AbstractPerson {
  
  @Key @Generated
  int id;
  
  @ManyToMany
  Result<Group> groups;
}

data {
  val result = select(Person::class) where (Person::age gt 21) and (Person::name eq "Bob") limit 10
}

data.select(Person.class)
  .orderBy(Person.AGE.desc())
  .get()
  .stream().forEach(System.out::println);

public interface Person {

  @Key @Generated
  int getId();
  
  String getName();
  Optional<String> getEmail();
  ZoneDateTime getBirthday();
}

Observable<Person> observable = data
  .select(Person.class)
  .orderBy(Person.AGE.desc())
  .get()
  .observable();

int row = data.update(Person.class)
  .set(Person.ABORT, "student")
  .where(Person.AGE.lt(21)).get().value();
```

```
```

```
```


