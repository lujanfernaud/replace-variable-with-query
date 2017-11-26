# Upcase Refactoring Trail

## Replace Variable with Query

Refactoring exercise using the [Replace Temp with Query](https://www.refactoring.com/catalog/replaceTempWithQuery.html) refactoring for the [Upcase Refactoring Trail](https://thoughtbot.com/upcase/refactoring).

### Replace Temp with Query

> Extract the expression into a method. Replace all references to the temp with the expression. The new method can then be used in other methods. -- Martin Fowler

#### Before

```ruby
class Tipper
  ...

  def total
    tax_amount      = amount * TAX
    discount_amount = amount * (discount_percentage / 100.0)
    tip_amount      = amount * (tip_percentage / 100.0)

    amount + tax_amount - discount_amount + tip_amount
  end
end
```

#### After

```ruby
class Tipper
  ...

  def total
    amount + tax_amount - discount_amount + tip_amount
  end

  private

  def tax_amount
    amount * TAX
  end

  def discount_amount
    amount * (discount_percentage / 100.0)
  end

  def tip_amount
    amount * (tip_percentage / 100.0)
  end
end
```

### Additional Resources

- [Ruby Patterns: Query Method](http://reinh.com/blog/2008/07/17/ruby-patterns-query-method.html) by [Rein Henrichs](http://reinh.com/)
