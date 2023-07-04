# toString()
---
### toString() 메서드 
---
- `toString` 은 객체의 정보를 문자열로 형변환 해준다. 
- `Object` 클래스에서 상속받은 클래스들은 `toString()` 을 오버라이딩(재정의)하여 사용할 수 있다. 
- 자주 쓰이는 `String` 이나 `Integer` 클래스에는 이미 재정의되어 있다.
--- 
예를 들어, `Book` 이라는 클래스를 생성한다.

이때, `Book` 클래스는 따로 상속받는 클래스가 없으므로 자동으로 `Object` 를 상속받는다. 
```java
public class Book {
  int bookNumber;
  String bookTitle;

  Book (int bookNumber, String bookTitle) {
    this.bookNumber = bookNumber;
    this.bookTitle = bookTitle;
    }
  }

public class toStringEx {
  public static void main (String[] args) {
    Book book = new Book(100,"개미");

    System.out.println(book);
    System.out.println(book.toString());
    }
}

/* 출력결과
object.Book@16f65612
object.Book@16f65612
*/
```
---
`book` 을 그대로 출력한 결과와 `book.toString()` 에 참조 변수(Object형)를 넣으면 `toString()` 이 자동으로 호출된다.

    출력결과 : object.Book@16f65612
출력결과의 `@` 를 기준으로 좌측은 `클래스의 이름` 을 나타내고, 우측은 `해시코드 값` 을 나타낸다. 
- 해시코드란? : 해시 함수에 의해 자동으로 생성된 값인데 객체를 유일하게 식별할 수 있는 정수 값이다. 
---
### toString() 재정의 하기
---
`Book` 클래스에서 `toString` 메서드를 사용했을 때 해시코드 값이 아니라 사용자가 원하는 문자열을 출력하도록 메서드를 재정의해보자.
여기에서는 책제목과 책번호를 출력하도록 재정의 해 보자.
```java
public class Book {
  int bookNumber;
  String bookTitle;

  Book (int bookNumber, String bookTitle) {
    this.bookNumber = bookNumber;
    this.bookTitle = bookTitle;
    }
    
  @Override
  public String toString() {
     System.out.println(bookTitle+" "+bookNumber);
       }
    }

public class toStringEx {
  public static void main (String[] args) {
    Book book = new Book(100,"개미");

    System.out.println(book);
    System.out.println(book.toString());
    }
}

/* 출력결과
개미 100
개미 100
*/
```
`Book` 클래스에 위와 같이 오버라이딩 코드를 추가하고, 다시 테스트해보면 해시코드 대신에 책제목과 책번호가 출력된다.