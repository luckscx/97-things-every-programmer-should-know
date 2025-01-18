#潮湿冲淡性能瓶颈

Dry原则(不要重复自己)的重要性在于，它将系统中的每一条知识都应该有一个单一的表示形式的想法编成了法典。换句话说，知识应该包含在单一的实现中。Dry的对立面是湿的(每次都要写)。当知识被编码到几个不同的实现中时，我们的代码是湿的。当您考虑它们对性能配置文件的众多影响时，干式和湿式的性能影响就变得非常明显。

让我们首先考虑我们系统的一个特性，比如说*X*，这是一个CPU瓶颈。假设功能*X*消耗了30%的CPU。现在让我们假设功能*X*有十个不同的实现。平均而言，每次实施将消耗3%的CPU。如果我们想要快速取胜，那么这个CPU利用率水平并不值得担心，所以我们很可能会忽略这个特性是我们的瓶颈。然而，假设我们以某种方式认识到特性*X*是一个瓶颈。我们现在面临的问题是找到并修复每一个实现。对于WEW，我们有十个不同的实现需要查找和修复。使用DRY，我们将清楚地看到30%的CPU利用率，并且我们将有十分之一的代码需要修复。我有没有提到过，我们不必花时间去寻找每个实现？

有一个用例，我们经常犯违反DRY的错误：我们对集合的使用。实现查询的一种常见技术是遍历集合，然后将查询依次应用于每个元素：

```
公共类UsageExample{
Private ArrayList<客户>allCustomers=new ArrayList<Customer>()；
//...
公共ArrayList<Customer>findCustomersThatSpendAtLeast(金额){
ArrayList<Customer>CustomersOfInterest=new ArrayList<Customer>()；
针对(客户客户：所有客户){
If(Customer.spendsAtLeast(Amount))
CustomersOfInterest.Add(客户)；
}
返回客户OfInterest；
}
}
```

通过向客户端公开这个原始集合，我们违反了封装。这不仅限制了我们的重构能力，还迫使我们代码的用户通过让每个用户重新实现可能相同的查询来违反DRY。通过从API中删除公开的原始集合，可以很容易地避免这种情况。在本例中，我们可以引入一个新的、特定于域的集合类型，称为`CustomerList`。这个新类在语义上更符合我们的领域。它将作为我们所有查询的自然之家。

有了这个新的集合类型，我们还可以轻松地看到这些查询是否会成为性能瓶颈。通过将查询合并到类中，我们消除了向客户公开表示选择(如`ArrayList`)的需要。这使我们可以自由地更改这些实现，而不必担心违反客户合同：

```
公共类CustomerList{
私有数组列表<Customer>Customers=new ArrayList<Customer>()；
Private SortedList<Customer>CustomersSortedBySpendingLevel=new SortedList<Customer>()；
//...
Public CustomerList findCustomersThatSpendAtLeast(金额){
返回新的CustomerList(customersSortedBySpendingLevel.elementsLargerThan(amount))；
}
}

公共类UsageExample{
公共静态无效主(String[]args){
CustomerList Customers=new CustomerList()；
//...
CustomerList CustomersOfInterest=customers.findCustomersThatSpendAtLeast(someMinimalAmount)；
//...
}
}
```

在本例中，对DRY的坚持允许我们引入另一种索引方案，其中SortedList以客户的消费水平为关键。比这个特定示例的具体细节更重要的是，跟随DRY帮助我们找到并修复了一个性能瓶颈，如果代码是湿的，这个瓶颈将更难找到。

作者：[Kirk Pepperdine](http://programmer.97things.oreilly.com/wiki/index.php/Kirk_Pepperdine)