#错失多态的机会

多态是面向对象的基本思想之一。这个词来自希腊语，意思是许多(*多)形式(*变形*)。在编程环境中，多态是指特定类对象或方法的多种形式。但是，多态并不是简单的替代实现。小心使用，多态可以创建微小的本地化执行上下文，使我们无需冗长的If-Then-Else*块即可工作。身处一个环境中可以让我们直接做正确的事情，而在那个环境之外则迫使我们重建它，这样我们才能做正确的事情。通过谨慎地使用替代实现，我们可以捕获上下文，从而帮助我们生成更少、更具可读性的代码。最好用一些代码来演示这一点，例如以下(不切实际地)简单的购物车：

```
公共类ShoppingCart{
Private ArrayList<Item>Cart=new ArrayList<Item>()；
Public void Add(Item Item){cart.add(Item)；}
公共项takNext(){Return cart.Remove(0)；}
公共布尔值isEmpty(){返回cart.isEmpty()；}
}
```

假设我们的网店提供可以下载的商品和需要发货的商品。让我们构建另一个支持这些操作的对象：

```
公共班级发货{
公共布尔发货(Item Item，SurfaceAddress地址){...}
公共布尔发货(项目、电子邮件地址){...}
}
```

当客户完成结账后，我们需要发货：

```
而(！cart.isEmpty()){
Shipping.ship(cart.takeNext()，？)；
}
```

*？*参数不是什么新奇的猫王运算符，它是在问我应该用电子邮件还是蜗牛邮寄物品？回答这个问题所需的背景不再存在。我们可以在布尔型或枚举型中捕获发货方法，然后使用*If-Then-Else*来填充缺失的参数。另一种解决方案是创建两个都扩展Item的类。让我们将它们称为DownloadableItem和SurfaceItem。现在让我们编写一些代码。我将把Item提升为支持单个方法Ship的接口。要运送购物车中的内容，我们将调用`item.ship(Shipper)`。类`DownloadableItem`和`SurfaceItem`都会实现Ship。

```
公共类DownloadableItem实现项{
公共布尔船(船运托运人){
Shipper.ship(this，Customer.getEmailAddress())；
}
}

公共类SurfaceItem实现了项{
公共布尔船(船运托运人){
Shiper.ship(this，Customer.getSurfaceAddress())；
}
}
```

在本例中，我们已将处理`Shipping`的责任委托给每个项目。因为每件物品都知道如何最好地运送，这种安排允许我们继续进行，而不需要*IF-THEN-ELSE*。该代码还演示了两种模式的使用，这两种模式经常很好地结合在一起：命令和双重调度。这些模式的有效使用依赖于对多态的谨慎使用。当发生这种情况时，我们代码中的*If-Then-Else*块的数量将会减少。

虽然在某些情况下，使用*If-Then-Else*而不是多态要实用得多，但更常见的情况是，多态的编码风格会产生更小、更易读、更不脆弱的代码库。错失的机会数是代码中*IF-THEN-ELSE*语句的简单计数。

作者：[Kirk Pepperdine](http://programmer.97things.oreilly.com/wiki/index.php/Kirk_Pepperdine)
