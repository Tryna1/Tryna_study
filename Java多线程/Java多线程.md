## 创建线程的三种方法

* 继承Thread类
* 实现Runnable接口
* 实现Callable接口

### 继承Thread类

* 自定义线程类继承Thread类
* 重写run()方法
* 创建线程对象，调用start()方法启动线程

```java
public class Main extends Thread{

    @Override
    public void run() {
        for (int i = 0; i < 20; i++) {
            System.out.println("我在看代码" + i);
        }
    }

    public static void main(String[] args) {

        Main main = new Main();

        main.start();

        for (int i = 0; i < 20; i++) {
            System.out.println("我在学习多线程" + i);
        }

    }

}
```

### 实现Runnable接口


* 使该类实现Runnable接口
* 重写run()方法
* 创建实现类对象，通过Thread类调用

```java
public class Main implements Runnable{

    @Override
    public void run() {
        for (int i = 0; i < 20; i++) {
            System.out.println("我在看代码" + i);
        }
    }

    public static void main(String[] args) {

        final Main main = new Main();

        new Thread(main).start();

        for (int i = 0; i < 20; i++) {
            System.out.println("我在学习多线程" + i);
        }

    }

}
```

### 继承Thread类和实现Runnable接口的区别

* 继承Thread类不建议使用：避免OOP单继承局限性
* 实现Runnable接口推荐使用：避免单继承局限性，灵活方便，方便同一个对象被多个线程使用。