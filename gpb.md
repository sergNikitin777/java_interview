- чем отличаются микросервисы от монолиты
+ виды памяти: heap (хранит объекты), stack (ссылка на объекты, переменные), metaspace (информация о классах)
+ зачем создан heap, почему не хватило stack (стек более быстрая памяти, за счет сдвига указателя)
- писал classloader
+ ConcurrentModificationException (скопировать коллекцию в новую и пройтись в ней iterator); решение вызвали метод iterator дальше из массива удаляем элемент и получаем данную ошибку
  List<String> stringList = new ArrayList<>();
  stringList.add("1");
  stringList.add("2");
  stringList.add("3");

  Iterator<String> stringIterator = stringList.iterator();
  stringList.remove("2");
  while (stringIterator.hasNext()) {
    System.out.println(stringIterator.next());
  }
+ iterator (перебираем коллекцию)
+ iterable (иерархия коллекций iterable потом collection
- 2 способа перебрать foreach, новый способ stream (supplier, consumer)
- дженереки (плюсы и минусы), затирание типов
- под капотом лямбда, анонимный класс это и есть лямбда
- опыт многопоточки, конфликты
- spring prototype - как работает под капотом
- @autowired поле, конструктор, setter
- @autowired поле почему не рекомендуется
- mvc - как внутри работает (через DispatcherServlet)
- @RestController и @Controller отличие
+ данные в виде xml (класс пометить @XmlRootElement и прописать @GetMapping(value = "/test", produces = MediaType.APPLICATION_XML_VALUE))
+ как spring boot понимает, что данные надо вернуть в виде json rest controller (по умолчанию в контроллере produces = MediaType.APPLICATION_JSON_VALUE
+ @Transaction; 
- 5 видов транзакции Propogation
+ @Transaction; если пометить этой аннотацией создается прокси объект
+ REQUIRED: Поддержите текущую транзакцию, создайте новую, если таковой не существует
  если в 1 метод пришла транзакция будет использовать ее при вызове 2 метода
  если в 1 метод транзакция не пришла будет создана новая
  если вызываем 2 метод все будет использована новая транзакция
  @Transaction оборачивает объект в прокси, при ошибка в 1 методе будет откат все транзакции
  @Service
  public class TestService {
    @Transactional(Propogation=Propogation.Required)
    public void calculateSmth(){
      saveSomthingInDb();
      ---------
      // some logic
      ---------
      // Error-rollback
    }
    @Transactional(Propogation=Propogation.Required_New)
    public void saveSomthingInDb() {
    }
  }
- executor service
- spring многопоточ
- spring cloud
  
  public class Application {

    public static void main(String[] args) {
        Integer x = 0;
        increment(x);
        System.out.println(x);
    }

    private static void increment(Integer x) {
        x = x + 10;
    }

}


if (obj instanceof Student) и if (getClass() == obj.getClass())





package interview;

public class Application implements A, B {
    
}

interface A {
    default void work() {}
}

interface B {
    default void work() {}
}


Stream.of("d2", "a2", "b1", "b3", "c")
    .filter(s -> {
        System.out.println("filter: " + s);
        return true;
    })
    .forEach(s -> System.out.println("forEach: " + s));
    
    // filter d2
    // foreach d2
    // filter a2
    // foreach a2
