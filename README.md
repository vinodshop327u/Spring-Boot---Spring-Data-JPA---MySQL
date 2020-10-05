# Spring-Boot---Spring-Data-JPA---MySQL


As you can see, this interface extends the CrudRepository interface which defines standard CRUD operations. In the generic parameters, we specify the domain type to work with is Expense and the type of domain's ID is Long.
In the body of the interface, we define two custom methods. The first one is:
1
public List<Expense> findByItem(String item);
This method signature follows convention for a finder method findByXXX()where XXX is the property name in the model class - it finds the exact match of the method's argument. Spring Data JPA will generate implementation code at runtime.
And we use a custom query in the second method:
1
2
@Query("SELECT e FROM Expense e WHERE e.amount >= :amount")
public List<Expense> listItemsWithPriceOver(@Param("amount") float amount);
This method will return expense items whose amount greater than a specified value.
Note that we just declare the method signatures, no actual code. And the great thing is Spring Data JPA automatically create implementation code (via proxy instances) at runtime.
  
