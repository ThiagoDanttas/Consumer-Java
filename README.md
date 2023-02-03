# Consumer - Java

---

[Documenta��o Consumer\<T>](https://docs.oracle.com/javase/10/docs/api/java/util/function/Consumer.html)


~~~~java
public interface Consumer<T> {
    void accept (T t);
}
~~~~

### Vers�es de implementa��o Predicate:

� Implementa��o da interface <br>
~~~~java
public class PriceUpdate implements Consumer<Product> {
    
    @Override
    public void accept(Product p) {
        return p.setPrice(p.getPrice * 1.1);
    }
}
~~~~
� Reference method com m�todo est�tico<br>
� Reference method com m�todo n�o est�tico<br>
~~~~java

public class Program {

	public static void main(String[] args) {

		List<Product> list = new ArrayList<>();

		list.add(new Product("Tv", 900.00));
		list.add(new Product("Mouse", 50.00));
		list.add(new Product("Tablet", 350.50));
		list.add(new Product("HD Case", 80.90));
        
		list.forEach(Product::staticPriceUpdate); // <-- Observa��o
        list.forEach(System.out::println);
	}
}
~~~~
� Express�o lambda declarada<br>

~~~~java

public class Program {

	public static void main(String[] args) {

		List<Product> list = new ArrayList<>();

		list.add(new Product("Tv", 900.00));
		list.add(new Product("Mouse", 50.00));
		list.add(new Product("Tablet", 350.50));
		list.add(new Product("HD Case", 80.90));

                double factor = 1.1; // Permite a utiliza��o de vari�veis
        
		Consumer<Product> cons = p -> {
                    p.setPrice(p.getPrice() * factor);
               };

		list.forEach(cons); // <-- Observa��o
        list.forEach(System.out::println);
        
	}
}
~~~~

� Express�o lambda inline

~~~~java

public class Program {

	public static void main(String[] args) {

		List<Product> list = new ArrayList<>();

		list.add(new Product("Tv", 900.00));
		list.add(new Product("Mouse", 50.00));
		list.add(new Product("Tablet", 350.50));
		list.add(new Product("HD Case", 80.90));
        
                double factor = 1.1; // Permite a utiliza��o de vari�veis
                
                Consumer<Product> cons = p -> p.setPrice(p.getPrice() * factor);
		list.forEach(cons); // <-- Observa��o
                list.forEach(System.out::println);
        
		}
	}
}
~~~~