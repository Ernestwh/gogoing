# 树结构

    /**
     * Definition for a binary tree node.
     * public class TreeNode {
     *     int val;
     *     TreeNode left;
     *     TreeNode right;
     *     TreeNode(int x) { val = x; }
     * }
     */

# 

    /**
     * Definition for singly-linked list.
     * public class ListNode {
     *     int val;
     *     ListNode next;
     *     ListNode(int x) {
     *         val = x;
     *         next = null;
     *     }
     * }
     */
# 排序算法：
![image.png](https://cdn.nlark.com/yuque/0/2021/png/21808628/1629600227133-f0cb2388-a856-477f-b1b5-0b456452b297.png#clientId=u1f519363-7956-4&from=paste&height=398&id=ub8cc286c&margin=%5Bobject%20Object%5D&name=image.png&originHeight=474&originWidth=720&originalType=url&ratio=1&size=129533&status=done&style=none&taskId=u50708fc3-902d-4ee1-ba8f-c1618e47c40&width=604)
计数排序：
适合数量巨大，可能数组都存不下，但是数值区间范围有限的情形，可以在线性时间排序。
**一是需要排序的元素必须是整数，二是排序元素的取值要在一定范围内，并且比较集中。**
计数排序不能解决的double类型排序问题
**比如取值范围在 200-300之间，那就可以申请100（平移范围）大小的数组，将值读入数组再计数，再取出**
桶排序：
数据量巨大或者计数排序不能解决的double类型非int排序问题数值区间范围。
适合区间排序，比如，打分0-100分，每10分为一个等级，需要快速确定所有人的分数等级。
划分多个范围相同的区间，每个子区间内自排序（选择合适的比较算法（最快nlogn）），最后合并。
极限情况下，划分桶大小等于数值范围大小。
 	特点是：每个区间代表一个桶，按照元素大小放入对应的桶中，
基数排序：
基数排序(Radix Sort)是[桶排序](http://www.cnblogs.com/skywang12345/p/3602737.html)的扩展，它的基本思想是：将整数按位数切割成不同的数字，然后按每个位数分别比较，从低位到最高位收集。 
	具体做法是：将所有待比较数值统一为同样的数位长度，数位较短的数前面补零。然后，从最低位开始，依次进行一次排序（按区间收集采用桶排序，比如整数的时候范围在0-9，分10个桶）。这样从最低位排序一直到最高位排序完成以后, 数列就变成一个有序序列。
# 常用的位运算
n &(n-1) 去掉n的最右（低）一位1
n & (-n)==n 判断是否是2的x次幂
n&1 判断奇偶

# String、StringBuilder常用api方法：
## String:
Int length();
获取字符串长度
boolean isEmpty() 
          当且仅当 length() 为 0 时返回 true。 
int length() 
          返回此字符串的长度。
char charAt(int index) 
          返回指定索引处的 char 值。
String trim() 
返回字符串的副本，忽略前导空白和尾部空白。
String substring(int beginIndex, int endIndex) 
返回一个新字符串，它是此字符串的一个子字符串。
## String 比较
compareTo
public int compareTo(String anotherString)
按字典顺序比较两个字符串。该比较基于字符串中各个字符的 Unicode 值。按字典顺序将此 String 对象表示的字符序列与参数字符串所表示的字符序列进行比较。如果按字典顺序此 String 对象位于参数字符串之前，则比较结果为一个负整数。如果按字典顺序此 String 对象位于参数字符串之后，则比较结果为一个正整数。如果这两个字符串相等，则结果为 0；compareTo 只在方法 equals(Object) 返回 true 时才返回 0。
即对应位置字符不相等时，返回对应两个字符串位置的差值。this-another
## StringBuilder:
StringBuilder可以使用string的所有方法，也可以使用自己的特定方法
append('a') 插入字符、字符串
delete(int start, int end); 删除字符串 左闭右开
deleteCharAt(int index)；删除指定位置
insert(int offset, String str)； 可以插入各种类型的数据到字符串
insert(int offset, boolean b)；
insert(int offset, int i)；
reverse();//反转字符串

# 判断int数字越界
## BigInter的使用

	public void testBasic() {
		BigInteger a = new BigInteger("13");
		BigInteger b = new BigInteger("4");
		int n = 3;

		//1.加
		BigInteger bigNum1 = a.add(b);			//17
		//2.减
		BigInteger bigNum2 = a.subtract(b);		//9
		//3.乘
		BigInteger bigNum3 = a.multiply(b);		//52
		//4.除
		BigInteger bigNum4 = a.divide(b);		//3
		//5.取模(需 b > 0，否则出现异常：ArithmeticException("BigInteger: modulus not positive"))
		BigInteger bigNum5 = a.mod(b);			//1
		//6.求余
		BigInteger bigNum6 = a.remainder(b);	//1
		//7.平方(需 n >= 0，否则出现异常：ArithmeticException("Negative exponent"))
		BigInteger bigNum7 = a.pow(n);			//2197
		//8.取绝对值
		BigInteger bigNum8 = a.abs();			//13
		//9.取相反数
		BigInteger bigNum9 = a.negate();		//-13
	}
add()，subtract()，multiply()，divide()，mod()，remainder()，pow()，abs()，negate()；
compareTo()返回一个int型数据：1 大于； 0 等于； -1 小于；
max()，min()：分别返回大的（小的）那个BigInteger数据；
//比较大小:compareTo(),max(),min()
	
	@Test
	public void testCompare() {
		BigInteger bigNum1 = new BigInteger("52");
		BigInteger bigNum2 = new BigInteger("27");

		//1.compareTo()：返回一个int型数据（1 大于； 0 等于； -1 小于）
		int num = bigNum1.compareTo(bigNum2);			//1

		//2.max()：直接返回大的那个数，类型为BigInteger
		//	原理：return (compareTo(val) > 0 ? this : val);
		BigInteger compareMax = bigNum1.max(bigNum2);	//52

		//3.min()：直接返回小的那个数，类型为BigInteger
		//	原理：return (compareTo(val) < 0 ? this : val);
		BigInteger compareMin = bigNum1.min(bigNum2);	//27
	}
## 2.用long或者BigInteger来存结果
再去和Integer.MAX_VALUE判断即可。
最后使用(int)ans;强制类型转换
## 3. 通过数字来判断
如果ans是正数大于最大值/10，那么无论在后面添加什么值必定越界。
如果ans是正数等于最大值/10，后面添加的值大于最大值%10也会越界
如果ans是负数，ans小于最小值/10，那么无论后面添加什么值必越界
如果ans是负数，ans等于最小值/10，如果后面添加的值小于最小值%10也会越界

    if(flag==1&&(ans>(Integer.MAX_VALUE/10)||(ans==Integer.MAX_VALUE/10&&add>=Integer.MAX_VALUE%10))){
        ans=Integer.MAX_VALUE;
        break;
    }else if(flag==-1&&(-1*ans<(Integer.MIN_VALUE/10)||(-1*ans==Integer.MIN_VALUE/10&&-1*add<=Integer.MIN_VALUE%10))){
        ans=Integer.MIN_VALUE;
        break;
    }
# 复制List
List<Integer>  list2=new ArrayList<>(list);
# 取中值操作
int m=low+(high-low)/2;防止越界！
# 输入输出

一直输入，hasnext接收数据：
import java.util.*;
public class Main{
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        while (sc.hasNext()) { 
        //操作
        }
    }
}
//接收输入一个值 
import java.util.Scanner;
public class Main{
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n=sc.nextInt();
        while(n>0) {
 //操作
            n--;
        }
    }
}
// a c bb 一直输入
sc.nextLine() 接收从上一次回车到现在为止输入的字符，
如 aa bb cc会读取到 aa bb cc包括空格的字符串
sc.next() 接收字符串遇到空格或者回车结束，
如 aa bb cc只会先读取到aa，再读bb，cc
读一个浮点数：double t = sc.nextDouble();
读一个字符串：String s = sc.next();
读一整行： String s = sc.nextLine();
如果先next，然后使用nextline
以aa bb cc，会先next读取到aa结束，再从aa后面读取到最后，其中包括aa后面的空格。
两个next的话会先读取aa，bb以空格为分隔读取（不包括最后一个空格）
　next()不会吸取字符前/后的空格/Tab键，只吸取字符，开始吸取字符（字符前后不算）直到遇到空格/Tab键/回车截止吸取；
　nextLine()吸取字符前后的空格/Tab键，回车键截止。

import java.util.*;
import java.util.Scanner;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        while(sc.hasNext()) {

            String[] strs = sc.nextLine().split(" ");
         //操作
        }
    }
}
## 字符转数字
        char c='8';
        int num='8'-'0';
        System.out.println(num);
		#  8
## 数字转字符
//1.先转字符串再转字符
Int num=9;
String s=String.valueOf(num);
Char c=s.charAt(i);
2.强制类型转换
Char c=(char)(num+'0')
## 字符数组转字符串
char[] data = {‘a’, ‘b’, ‘c’};
String str = new String(data);
String s =String.valueOf(char[] ch)
## 字符串转为字符数组
String string1 = “abcdefghijk” ;
char [] strArr1 = string1.toCharArray(); //注意返回值是char数组
String string = “abc,def,ghi”;
## 字符串字符串数组互转
String [] strArr= string.split(“,”); //注意分隔符是需要转译
字符串转数字
## Integer.valueOf()
int i = Integer.parseInt(String);
int i = Integer.valueOf(String);
## 数字转字符串
1.) String s = String.valueOf(i);
2.) String s = Integer.toString(i);
3.) String s = "" + i;

# 二维数组排序
使用以下方法，必须处理相等情况否则会报错java.lang.IllegalArgumentException: Comparison method violates its general contract!
Arrays.sort(intervals,(o1,o2)->{
if(o1[0]>o2[0]) return 1;
else if(o1[0]<o2[0]) return -1;
else return 0;
});
o1代表后面的元素，o2代表当前元素
# Set遍历方式：
**for** (String i : set) 
# MAP常用方法：
## computeIfAbsent(xxx,key->1)
hashmap.computeIfAbsent(K key, Function remappingFunction)
hashmap.computeIfAbsent("a", key -> 280)
如果map中键值a存在直接返回a的value，a不存在则会添加到map中并设置value为280
如果 key 对应的 value 不存在，则使用获取 remappingFunction 重新计算后的值，并保存为该 key 的 value，否则返回map已有key的 value。
## Map.getOrDefault(“a”,1);
| [getOrDefault()](https://www.runoob.com/java/java-hashmap-getordefault.html) | 获取指定 key 对应对 value，如果找不到 key ，则返回设置的默认值 |
| --- | --- |

## 遍历的几种方式：
| [entrySet()](https://www.runoob.com/java/java-hashmap-entryset.html) | 返回 hashMap 中所有映射项的集合集合视图。 |
| --- | --- |
| [keySet](https://www.runoob.com/java/java-hashmap-keyset.html)() | 返回 hashMap 中所有 key 组成的集合视图。 |
| [values()](https://www.runoob.com/java/java-hashmap-values.html) | 返回 hashMap 中存在的所有 value 值。 |

1.
for(Map.Entry<String, String> entry:map.entrySet()){  
  System.out.println(entry.getKey()+"--->"+entry.getValue());  
}
2.
    for (String key : map.keySet()) {
        String value = map.get(key);
}
3.
Iterator it = tempMap.keySet().iterator();
while (it.hasNext()) {
	String key = it.next();
String value = map.get(key);
}
4.
Iterator<Entry<String, String>> iterator = map.entrySet().iterator();
    while (iterator.hasNext()) {
        String key = iterator.next().getKey();
        String value = iterator.next().getValue();
    }
# 用优先队列做堆

PriorityQueue()
          使用默认的初始容量（11）创建一个 PriorityQueue，并根据其自然顺序对元素进行排序。
PriorityQueue(Collection<? extends E> c)
          创建包含指定 collection 中元素的 PriorityQueue。
PriorityQueue(int initialCapacity)
          使用指定的初始容量创建一个 PriorityQueue，并根据其自然顺序对元素进行排序。
PriorityQueue(int initialCapacity, Comparator<? super E> comparator)
          使用指定的初始容量创建一个 PriorityQueue，并根据指定的比较器对元素进行排序。
PriorityQueue(PriorityQueue<? extends E> c)
          创建包含指定优先级队列元素的 PriorityQueue。
PriorityQueue(SortedSet<? extends E> c)
          创建包含指定有序 set 元素的 PriorityQueue。

PriorityQueue<Map.Entry<Integer, Integer>> que=new PriorityQueue<>((o1,o2)->o1.getValue()>o2.getValue()?1:-1);//升序排列，队列前面是较小的值，小顶堆改成-1:1是降序
O2代表当前元素，O1是后一个的元素，如果o2<o1就是升序 为1， 否则 o2>o1降序为-1
PriorityQueue的常用方法有：poll(),offer(Object),size(),peek()等。

- 　　插入方法（offer()、poll()、remove() 、add() 方法）时间复杂度为O(log(n)) ；
- 　　remove(Object) 和 contains(Object) 时间复杂度为O(n)；
- 　　检索方法（peek、element 和 size）时间复杂度为常量。

# 栈的主要操作
Stack<Integer> s= new Stack<>();
void push(int data)：将data（数据）插入栈
int pop()：删除并返回最后一个插入栈的
栈的辅助操作
int top()：返回最后一个插入栈的元素，但不删除
int size()：返回存储在栈中的元素的个数
int isEmpty()：判断栈中是否有元素
int isStackFull()：判断栈中是否满元素
判断是否为空 stk.isEmpty();
入栈stk.push();
出栈stk.pop();
显示栈顶头元素，但不移除stk.peek();

# 双端队列

Deque<Integer> que =new LinkedList<>();

|  | 第一个元素 (头部) |  | 最后一个元素 (尾部) |  |
| --- | --- | --- | --- | --- |
|  | 抛出异常 | 特殊值 | 抛出异常 | 特殊值 |
| 插入 | addFirst(e) | offerFirst(e) | addLast(e) | offerLast(e) |
| 删除 | removeFirst() | pollFirst() | removeLast() | pollLast() |
| 检查 | getFirst() | peekFirst() | getLast() | peekLast() |


支持队列和栈的所有操作offer,pool,peek,push,pop，且头部（数组的前面）作为出栈、出队的方向。队列是往数组尾部插入，而栈是只在头部入、出。
可以直接转化为数组list= new ArrayList<>(Deque);
# 队列主要操作
Queue<TreeNode> q = new LinkedList<TreeNode>();
用这个对象调用函数
判断是否为空 q.isEmpty();
添加元素q.offer();
删除元素q.poll();
显示队列头元素但不移除q.peek();

# Arrays 常用方法
## 排序
Arrays.sort()
## 填充
Arrays.fill(Object[] array,Object object)
## 逆序
**Collections.reverse()**
