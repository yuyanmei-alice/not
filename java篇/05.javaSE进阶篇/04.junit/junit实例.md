
定义一个计算机类，里面提供加法和减法的方法

```
public class Calator {
    /**
     * @param a  传入第一个相加数
     * @param b  传入第二个相加数
     * @return 返回a+b的和
     * 
     */
    public int add(int a,int b){
        
        return a+b;
    }

    /**
     * @param a  传入第一个被减数
     * @param b  传入第二个减数
     * @return 返回a-b的和
     *
     */
    public int divid(int a,int b){
        return a -b;
    }
}

```

通过junit来测试这个方法
