# **DO** prefix local calls with this

> Insert the this prefix before a call to a class member.  

``` csharp
// DO
public class Student : Person
{
    private string id;
    private double grade;
    
    public Person(string id, double grade, int age)
    {
        base.age = age;
        this.id = id;
        this.grade = grade;
    }
}
```

``` csharp
// DON'T
public class Student : Person
{
    private string m_id;
    private double _grade;
    
    public Person(string id, double grade, int age)
    {
        base.age = age;
        m_id = id;
        _grade = grade;
    }
}
```
