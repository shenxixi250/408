  
3.[数组中重复的数字](#1)  
4.[二维数组中的查找](#2)  
5.[替换空格](#3)  
6.[从尾到头打印链表](#4)  
7.[重建二叉树](#5)  
8.[二叉树的下一个结点](#6)  
9.[用两个栈实现队列](#7)  
10.1[斐波那契数列](#8)  
10.2[矩形覆盖](#9)  
10.3[跳台阶](#10)  
10.4[变态跳台阶](#11)  
11.[旋转数组的最小数字](#12)  
12.[矩阵中的路径](#13)  
13.[机器人的运动范围](#14)  
14.[剪绳子](#15)  
15.[二进制中 1 的个数](#16)  
16.[数值的整数次方](#17)  
17.[打印从 1 到最大的 n 位数](#18)  
18.1[在O(1) 时间内删除链表节点](#19)  
18.2[删除链表中重复的结点](#20)  
19.[正则表达式匹配](#21)  
20.[表示数值的字符串](#22)  
21.[调整数组顺序使奇数位于偶数前面](#23)  
22.[链表中倒数第 K 个结点](#24)  
23.[链表中环的入口结点](#25)  
24.[反转链表](#26)  
25.[合并两个排序的链表](#27)  
26.[树的子结构](#28)  
27.[二叉树的镜像](#29)  
28.[对称的二叉树](#30)  
29.[顺时针打印矩阵](#31)  
30.[包含 min 函数的栈](#32)  
31.[栈的压入、弹出序列](#33)  
32.1[从上往下打印二叉树](#34)  
32.2[把二叉树打印成多行](#35)  
32.3[按之字形顺序打印二叉树](#36)  
33.[二叉搜索树的后序遍历序列](#37)  
34.[二叉树中和为某一值的路径](#38)  
35.[复杂链表的复制](#39)  
36.[二叉搜索树与双向链表](#40)  
37.[序列化二叉树](#41)  
38.[字符串的排列](#42)  
39.[数组中出现次数超过一半的数字](#43)  
40.[最小的 K 个数](#44)  
41.1[数据流中的中位数](#45)  
41.2[字符流中第一个不重复的字符](#46)  
42.[连续子数组的最大和](#47)  
43.[从 1 到 n 整数中 1 出现的次数](#48)  
44.[数字序列中的某一位数字](#49)  
45.[把数组排成最小的数](#50)  
46.[把数字翻译成字符串](#51)  
47.[礼物的最大价值](#52)  
48.[最长不含重复字符的子字符串](#53)  
49.[丑数](#54)  
50.[第一个只出现一次的字符位置](#55)  
51.[数组中的逆序对](#56)  
52.[两个链表的第一个公共结点](#57)  
53.[数字在排序数组中出现的次数](#58)  
54.[二叉查找树的第 K 个结点](#59)  
55.1[二叉树的深度](#60)  
55.2[平衡二叉树](#61)  
56.[数组中只出现一次的数字](#62)  
57.1[和为 S 的两个数字](#63)  
57.2[和为 S 的连续正数序列](#64)  
58.1[翻转单词顺序列](#65)  
58.2[左旋转字符串](#66)  
59.[滑动窗口的最大值](#67)  
60.[n 个骰子的点数](#68)  
61.[扑克牌顺子](#69)  
62.[圆圈中最后剩下的数](#70)  
63.[股票的最大利润](#71)  
64.[求 1+2+3+...+n](#72)  
65.[不用加减乘除做加法](#73)  
66.[构建乘积数组](#74)  
67.[把字符串转换成整数](#75)  
68.[树中两个节点的最低公共祖先](#76)  
  
  
  
<A name="1"> 数组中重复的数字 </A>   

在一个长度为 n 的数组里的所有数字都在 0 到 n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字是重复的，也不知道每个数字重复几次。请找出数组中任意一个重复的数字。

```
Input:
{2, 3, 1, 0, 2, 5}

Output:
2
```
解法

<A name="2"> 二维数组中的查找 </A>   
题目描述
给定一个二维数组，其每一行从左到右递增排序，从上到下也是递增排序。给定一个数，判断这个数是否在该二维数组中。

Consider the following matrix:
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]

Given target = 5, return true.
Given target = 20, return false.


结题思路
```

该二维数组中的一个数，小于它的数一定在其左边，大于它的数一定在其下边。
因此，从右上角开始查找，就可以根据 target 和当前元素的大小关系来缩小查找区间
，当前元素的查找区间为左下角的所有元素。

标准解答
public boolean Find(int target, int[][] matrix) {
    if (matrix == null || matrix.length == 0 || matrix[0].length == 0)
        return false;
    int rows = matrix.length, cols = matrix[0].length;
    int r = 0, c = cols - 1; // 从右上角开始
    while (r <= rows - 1 && c >= 0) {
        if (target == matrix[r][c])
            return true;
        else if (target > matrix[r][c])
            r++;
        else
            c--;
    }
    return false;
}
```
需要学习的地方就是  matrix.length表示行  matrix[0].length表示数组的列

```
public class Find {
    public static void main(String[] args) {


    int[][] a= new int[][]{
            {1, 4, 7, 11, 15},
            {2, 5, 8, 12, 19},
            {3, 6, 9, 16, 22},
            {10, 13, 14, 17, 24},
            {19, 21, 23, 26, 30}
    };
    Boolean i=find(a,5,5);
    System.out.println(i);
}
    public static boolean find(int a[][],int m,int n)
    {
        Scanner sc = new Scanner(System.in);
        int i = sc.nextInt();
        int p=1;
        int q=0;
        for (int j = 0; j <m+n-1 ; j++) {
            if(i>a[q][m-p])
            {
                if (q>=m-1)
                    return false;
                else
                    q++;
            }
            if(i<a[q][m-p])
            {
                if(p>=n-1)
                    return false;
                else
                    p++;

            }
            if(i==a[q][m-p])
            {return true;}
        }
        return false;
    }
}
```


<A name="3"> 替换空格 </A>   

替换空格

将一个字符串中的空格替换成 "%20"。

Input:
"A B"

Output:
"A%20B"

1.  在字符串尾部填充任意字符，使得字符串的长度等于替换之后的长度。因为一个空格要替换成三个字符（%20），所以当遍历到一个空格时，需要在尾部填充两个任意字符。

2. 令 P1 指向字符串原来的末尾位置，P2 指向字符串现在的末尾位置。P1 和 P2 从后向前遍历，当 P1 遍历到一个空格时，就需要令 P2 指向的位置依次填充 02%（注意是逆序的），否则就填充上 P1 指向字符的值。从后向前遍是为了在改变 P2 所指向的内容时，不会影响到 P1 遍历原来字符串的内容。

3. 当 P2 遇到 P1 时（P2 <= P1），或者遍历结束（P1 < 0），退出。

![](<++>) <++>

```
public class paix {
	public static void main(String[] args) {
		StringBuffer sb= new StringBuffer("a 1 i o u");
		String st=fangfa(sb);
		System.out.println(st+"");
		System.out.println(fangfa(sb));
	}
	public static String fangfa(StringBuffer Sb)
	{
		int j;
		int i=0;
		char [] c =Sb.toString().toCharArray();
		for(char a: c)
			if (a == ' ')
				i++;
		//Sb.append(2*i);
		char [] b= new char[Sb.length()+2*i];
		for (int d=c.length-1;d>=0;d--)
		{
			if(c[d]==' ') {
				j=2*i-1;
				b[d + j] = '2';
				b[d + j-1] = '1';
				b[d + j+1] = '3';
				i=i-1;
			}
			else
			{
				b[d+i+i]=c[d];
			}
		}
		System.out.println(b);
		return b.toString();

	}


}
```
要学习的地方就是 这个i的处理 老是出问题 然后就是
System.out.print(str)显示的居然是 str的地址值  我炸  
System.out.print(str+"")就可以显示具体值了
```
public String replaceSpace(StringBuffer str) {
    int P1 = str.length() - 1;
    for (int i = 0; i <= P1; i++)
        if (str.charAt(i) == ' ')
            str.append("  ");

    int P2 = str.length() - 1;
    while (P1 >= 0 && P2 > P1) {
        char c = str.charAt(P1--);
        if (c == ' ') {
            str.setCharAt(P2--, '0');
            str.setCharAt(P2--, '2');
            str.setCharAt(P2--, '%');
        } else {
            str.setCharAt(P2--, c);
        }
    }
    return str.toString();
}
```
这里仅仅使用了一个StringBuffer就解决了问题 值得学习学习
是通过P1 P2 来进行位置的调换   实在是好方法啊

<A name="4"> 从尾到头打印链表 </A>   
典型的对栈使用的考察


使用头插法也可以解决这个问题 


使用递归
```

import java.util.ArrayList;
import java.util.Stack;

/**
 * 剑指offer面试题5：从尾到头打印链表
 * 输入一个链表的头结点，从尾到头打印出每个结点的值
 * 解决方案一：首先遍历链表的节点后打印，典型的“后进先出”，可以使用栈来实现这种顺序。
 * 解决方案二：栈的本质就是递归，直接使用递归的方式，打印一个节点的时候先打印它后面的节点，再打印该节点自身，实现反向打印
 * 解决方案三：遍历链表，把链表中的元素复制到ArrayList中，然后逆序打印ArrayList中的元素
 * 解决方案四：前三种解决方案本身属于在打印链表的时候不修改链表本身结构，
 * 在允许修改链表结构的情况下可以把链表中的节点指针反转过来，改变链表方向，然后重新遍历打印改变方向后的链表
 * @author GL
 *
 */
public class link {

    public static void main(String[] args) {
        ListNode node1=new ListNode(1);
        ListNode node2=new ListNode(2);
        ListNode node3=new ListNode(3);
        ListNode node4=new ListNode(4);
        ListNode node5=null;
        ListNode node6=new ListNode(6);
        ListNode node7=new ListNode();
        node1.next=node2;
        node2.next=node3;
        node3.next=node4;


        printListFromTailToHead(node1);
        printList(node1);//这个是我修改的只是会显示的代码
        ArrayList<Integer>  fin= new ArrayList<Integer>();
        fin = printListFromTailTo(node1);//这个是一个会返回一个数组的代码
        System.out.println(fin);


       // printListFromTailToHead(node5);
       // printListFromTailToHead(node6);
       // printListFromTailToHead(node7);
       // //使用栈实现逆序打印链表
     printListFromTailToHeadByStack(node1);
       // //使用递归实现逆序打印链表
       // printListFromTailToHead(node1);
      //使用递归反转实现逆序打印
     printListFromTailToHeadByReverseList(node1);
      //使用ArrayList逆序打印链表
     printListFromTailToHeadByArrayList(node1);
    }

    /*
     * 方案一：通过使用栈结构，遍历链表，把先遍历的节点的值推入栈中，遍历结束后通过弹出栈内元素实现逆序打印
     */
    public static void printListFromTailToHeadByStack(ListNode node){
        Stack<Integer> stack=new Stack<Integer>();
        while(node!=null){
            stack.push(node.val);
            node=node.next;
        }
        while(!stack.isEmpty()){
            System.out.print(stack.pop()+",");
        }
    }


    /*
     * 方案二：递归法逆序打印链表
     */
    public static ArrayList<Integer> printListFromTailTo(ListNode listNode) {
        ArrayList<Integer> ret = new ArrayList<>();
        if (listNode != null) {
            ret.addAll(printListFromTailTo(listNode.next));
            ret.add(listNode.val);
        }
        return ret;
    }
    public static void printListFromTailToHead(ListNode node){
        if(node!=null){
            if(node.next!=null){
                printListFromTailToHead(node.next);
            }
            System.out.print(node.val+",");
        }
        else
            System.out.println("输入的链表为空");
    }

    public static void printList(ListNode listNode) {
        ArrayList<Integer> ret = new ArrayList<>();
        if (listNode != null) {
            printList(listNode.next);
            //ret.add(listNode.val);
            System.out.println(listNode.val);
        }
    }
    /*
     * 方案三：使用ArrayList逆序打印链表
     */
    public static void    printListFromTailToHeadByArrayList(ListNode node){
        if(node==null)
            System.out.print("输入链表为null");
        ArrayList<Integer> arrayList=new ArrayList<Integer>();
        while(node!=null){
            arrayList.add(node.val);
            node=node.next;
        }
        for(int i=arrayList.size()-1;i>=0;i--){
            System.out.print(arrayList.get(i)+",");
        }
    }


    /*
     * 方案四：递归反转链表，后遍历打印
     */
    public static void printListFromTailToHeadByReverseList(ListNode node){
        ListNode reversedNode=reverse(node);
        while(reversedNode!=null){
            System.out.print(reversedNode.val+",");
            reversedNode=reversedNode.next;
        }

    }
    //递归反转
    private static ListNode reverse(ListNode head){
        if(head.next==null)
            return head;
        ListNode reversedListNode=reverse(head.next);
        head.next.next=head;
        head.next=null;
        return reversedListNode;
    }

}
class ListNode{
    int val;
    ListNode next=null;
    public ListNode(){

    }
    public ListNode(int value){
        this.val=value;
    }
}
```

<++>
<A name="5"> 重建二叉树 </A>   

<A name="6"> 二叉树的下一个结点 </A> 

<A name="7"> 用两个栈实现队列 </A>   

<A name="8"> 斐波那契数列 </A>   

<A name="9"> 矩形覆盖 </A>   

<A name="10"> 跳台阶 </A>   

<A name="11"> 变态跳台阶 </A>   
<A name="12"> 旋转数组的最小数字 </A>   
<A name="13"> 矩阵中的路径 </A>   
<A name="14"> 机器人的运动范围 </A>   
<A name="15"> 剪绳子 </A>   
<A name="16"> 二进制中 1 的个数 </A>   
<A name="17"> 数值的整数次方 </A>   
<A name="18"> 打印从 1 到最大的 n 位数 </A>   
<A name="19"> 在O(1) 时间内删除链表节点 </A>   
<A name="20"> 删除链表中重复的结点 </A>   
<A name="21"> 正则表达式匹配 </A>   
<A name="22"> 表示数值的字符串 </A>   
<A name="23"> 调整数组顺序使奇数位于偶数前面 </A>   
<A name="24"> 链表中倒数第 K 个结点 </A>   
<A name="25"> 链表中环的入口结点 </A>   
<A name="26"> 反转链表 </A>   
<A name="27"> 合并两个排序的链表 </A>   
<A name="28"> 树的子结构 </A>   
<A name="29"> 二叉树的镜像 </A>   
<A name="30"> 对称的二叉树 </A>   
<A name="31"> 顺时针打印矩阵 </A>   
<A name="32"> 包含 min 函数的栈 </A>   
<A name="33"> 栈的压入、弹出序列 </A>   
<A name="34"> 从上往下打印二叉树 </A>   
<A name="35"> 把二叉树打印成多行 </A>   
<A name="36"> 按之字形顺序打印二叉树 </A>   
<A name="37"> 二叉搜索树的后序遍历序列 </A>   
<A name="38"> 二叉树中和为某一值的路径 </A>   
<A name="39"> 复杂链表的复制 </A>   
<A name="40"> 二叉搜索树与双向链表 </A>   
<A name="41"> 序列化二叉树 </A>   
<A name="42"> 字符串的排列 </A>   
<A name="43"> 数组中出现次数超过一半的数字 </A>   
<A name="44"> 最小的 K 个数 </A>   
<A name="45"> 数据流中的中位数 </A>   
<A name="46"> 字符流中第一个不重复的字符 </A>   
<A name="47"> 连续子数组的最大和 </A>   
<A name="48"> 从 1 到 n 整数中 1 出现的次数 </A>   
<A name="49"> 数字序列中的某一位数字 </A>   
<A name="50"> 把数组排成最小的数 </A>   
<A name="51"> 把数字翻译成字符串 </A>   
<A name="52"> 礼物的最大价值 </A>   
<A name="53"> 最长不含重复字符的子字符串 </A>   
<A name="54"> 丑数 </A>   
<A name="55"> 第一个只出现一次的字符位置 </A>   
<A name="56"> 数组中的逆序对 </A>   
<A name="57"> 两个链表的第一个公共结点 </A>   
<A name="58"> 数字在排序数组中出现的次数 </A>   
<A name="59"> 二叉查找树的第 K 个结点 </A>   
<A name="60"> 二叉树的深度 </A>   
<A name="61"> 平衡二叉树 </A>   
<A name="62"> 数组中只出现一次的数字 </A>   
<A name="63"> 和为 S 的两个数字 </A>   
<A name="64"> 和为 S 的连续正数序列 </A>   
<A name="65"> 翻转单词顺序列 </A>   
<A name="66"> 左旋转字符串 </A>   
<A name="67"> 滑动窗口的最大值 </A>   
<A name="68"> n 个骰子的点数 </A>   
<A name="69"> 扑克牌顺子 </A>   
<A name="70"> 圆圈中最后剩下的数 </A>   
<A name="71"> 股票的最大利润 </A>   
<A name="72"> 求 1+2+3+...+n </A>   
<A name="73"> 不用加减乘除做加法 </A>   
<A name="74"> 构建乘积数组 </A>   
<A name="75"> 把字符串转换成整数 </A>   
<A name="76"> 树中两个节点的最低公共祖先 </A>   
  
  
  
