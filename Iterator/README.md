# Iterator
example desine pattern of Iterator
- language
    - Java
- refer to
    - [TECHSCORE Iterator](http://www.techscore.com/tech/DesignPattern/Iterator/Iterator1.html/)



## Iteratorとは
> Iterator パターンは、要素の集まりを保有するオブジェクトの各要素に順番にアクセスする方法を提供するためのパターンです。

つまり, アクセスの仕方(昇順降順, 大文字小文字, 文字数など)はたくさんあるけど, これを独立させるらしい.

## サンプルケース
> あなたが学校の先生であることを考えてみましょう。 あなたは、ある学校の新任の先生で、あるクラスの担任を任せられました。 あなたが担任している「生徒」は５人いるものとします。

> Student クラスは、以下のように定義しましょう。

```java
public class Student{
    private String name;
    private int sex; //男の子:1  女の子:2

    public Student(String name,int sex){
        this.name = name;
        this.sex = sex;
    }
    public String getName(){
        return name;
    }
    public int getSex(){
        return sex;
    }
}
```

> 生徒は名前、性別を表すメンバ変数 name 、sexを持ち、名前を返す getName() メソッドと、性別を返す getSex() メソッドを持ちます。 これらの生徒を管理するために学校から先生に名簿が支給されます。学校から与えられる名簿は以下のように記述されています。

```java
public class StudentList{
    protected Student[] students;
    private int last = 0;

    public StudentList(){}
    public StudentList(int studentCount){
        this.students = new Student[studentCount];
    }

    public void add(Student student){
        students[last] = student;
        last++;
    }
    public Student getStudentAt(int index){
        return students[index];
    }
    public int getLastNum(){
        return last;
    }
}
```

>あなたは、学校から支給されたこの「StudentList」クラスを自由に拡張して利用することができるものとします。
>　また、この学校では、先生に対して「先生かくあるべき」という文書として、先生に求める能力を定義しています。 この第１条に以下のような条文があります。

> - 第１条　先生は、学校から与えられた名簿に自分の生徒を書き込むことができること  
- 第２条　先生は、生徒の名前を名簿の記載順に呼ぶことができること

> この条文は、Java では以下のように表現されるでしょう。

```java
public abstract class Teacher{
    protected StudentList studentList;
 
    public abstract void createStudentList();
    public abstract void callStudents();
}
```

> あなたは、まだ新任で、この能力を持っていません。そこで、あなたはこの能力を身に付ける必要があります。 さてあなたは、どのような設計を行い、「Teacher」クラスで宣言されている抽象メソッドをどのように実装するでしょう？