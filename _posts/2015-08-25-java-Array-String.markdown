---
layout:     post
title:      "剑指offer-Java实现"
date:       2015-08-28
---

<style type="text/css">
p{
	text-indent: 2em;
}
.post img {
  margin-bottom: 0rem;
}
</style>

--------

### 一、二维数组中的查找

**题目描述**
在一个二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。
	
	/**
			 * Java二维数组中的查找
			 * 
			 * @param array
			 * @param target
			 */
		public class Solution {
			public boolean Find(int [][] array,int target) {
				int m = array.length;
				int n = array[0].length;
				for (int i = 0; i < m; i++) {
					for (int j = 0; j < n; j++) {
						if(array[i][j]==target){
							return true;
						}
					}
				}
				return false;
			}
		}
	
	
### 二、替换空格
**题目描述**
请实现一个函数，将一个字符串中的空格替换成“%20”。例如，当字符串为We Are Happy.则经过替换之后的字符串为We%20Are%20Happy。

		public class Solution {
			public String replaceSpace(StringBuffer str) {
				char[] ch=str.toString().toCharArray();
				String s="";
				for(int i=0;i<ch.length;i++){
					if(ch[i]==' '){
						s+="%20";
					}else{
						s+=ch[i];
					}
				}
				return s;
			}
		}

### 三、从尾到头打印链表
**题目描述**
输入一个链表，从尾到头打印链表每个节点的值。

		/**
		*    public class ListNode {
		*        int val;
		*        ListNode next = null;
		*
		*        ListNode(int val) {
		*            this.val = val;
		*        }
		*    }
		*
		*/
		import java.util.ArrayList;
		import java.util.Iterator;
		import java.util.Stack;
		public class Solution {
			public ArrayList<Integer> printListFromTailToHead(ListNode listNode) {
				Stack<Integer> stack = new Stack();
				ArrayList<Integer> alist = new ArrayList();
				if (listNode == null) {
					return alist;
				}
				ListNode p = listNode;
				while (p != null) {
					stack.push(p.val);
					p = p.next;
				}
				Iterator<Integer> it = stack.iterator();
				while (it.hasNext()) {
					alist.add(stack.pop());
				}
				return alist;
			}
		}

### 四、重建二叉树
**题目描述**



### 五、用两个栈实现队列
**题目描述**
用两个栈来实现一个队列，完成队列的Push和Pop操作。 队列中的元素为int类型。

		import java.util.Stack;
		import java.util.Iterator;
		 
		public class Solution {
			Stack<Integer> stack1 = new Stack<Integer>();
			Stack<Integer> stack2 = new Stack<Integer>();
			 
			public void push(int node) {   
					stack1.push(node);
				 
			}
		 
			public int pop() {
				Iterator<Integer> it1=stack1.iterator();
				//Iterator<Integer> it2=stack2.iterator();
				if (!stack2.isEmpty()) {
					return stack2.pop();
				}else {
					if (!stack1.isEmpty()) {
						while(it1.hasNext()){
							stack2.push(stack1.pop());
						}
						return stack2.pop();
					}else {
						return -1;
					}
				}
			}
		}
### 六、旋转数组的最小数字
**题目描述**
把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个非递减序列的一个旋转，输出旋转数组的最小元素。例如数组{3,4,5,1,2}为{1,2,3,4,5}的一个旋转，该数组的最小值为1。

		import java.util.ArrayList;
		public class Solution {
			public int minNumberInRotateArray(int [] array) {
				if(array == null || array.length==0){
					return 0;
				}
				int min = array[0];
				for(int i=1;i<array.length;i++){
					if(array[i]<min){
						min=array[i];
					}
				}
				return min;
			}
		}

### 七、斐波那契数列
**题目描述**
大家都知道斐波那契数列，现在要求输入一个整数n，请你输出斐波那契数列的第n项。

		public class Solution {
			public int Fibonacci(int n) {
				int[] dp=new int[3];
				dp[0]=0;   
				dp[1]=1;
				dp[2]=1;
				if(n<2){
					return dp[n];
				}
				for(int i=2;i<=n;i++){
					dp[2]=dp[0]+dp[1];
					dp[0]=dp[1];
					dp[1]=dp[2];
				}
				return dp[2];
			}
		}

### 八、 跳台阶
**题目描述**
一只青蛙一次可以跳上1级台阶，也可以跳上2级。求该青蛙跳上一个n级的台阶总共有多少种跳法。

		public class Solution {
			public int JumpFloor(int target) {
				int[] dp=new int[3];
				dp[0]=0;
				dp[1]=1;
				dp[2]=2;
				if(target<=2){
					return dp[target];
				}
				for(int i=3;i<=target;i++){
					dp[0]=dp[1]+dp[2];
					dp[1]=dp[2];
					dp[2]=dp[0];
					System.out.println("dp[2]"+dp[2]);
				}
				return dp[2];
			}
		}

### 九、 变态跳台阶
**题目描述**
一只青蛙一次可以跳上1级台阶，也可以跳上2级……它也可以跳上n级。求该青蛙跳上一个n级的台阶总共有多少种跳法。


		public class Solution {
			public int JumpFloorII(int target) {
				int[] fib=new int[target+1];
				fib[0]=0;
				fib[1]=1;
				for(int i=2;i<=target;i++){
					fib[i]=2*fib[i-1];
				}
				return fib[target];
			}
		}

### 十、 矩形覆盖
**题目描述**我们可以用2*1的小矩形横着或者竖着去覆盖更大的矩形。请问用n个2*1的小矩形无重叠地覆盖一个2*n的大矩形，总共有多少种方法？

		public class Solution {
			public int RectCover(int target) {
				int[] fib=new int[target+1];
				fib[0]=1;
				fib[1]=1;
			   // fib[2]=2;
				for(int i=2;i<=target;i++){
					fib[i]=fib[i-1]+fib[i-2];
				}
				return fib[target];
			}
		}


### 十一、 二进制中1的个数
**题目描述**输入一个整数，输出该数二进制表示中1的个数。其中负数用补码表示。

		class Solution {
		public:
			 int  NumberOf1(int n) {
				 int count = 0;
				 while(n){         
					 n = n & (n-1);
					 count++;
				 }
				 return count;
			 }
		};

### 十二、 数值的整数次方
**题目描述**给定一个double类型的浮点数base和int类型的整数exponent。求base的exponent次方。

		class Solution {
		public:
			double Power(double base, int exponent) {
				if(base==0 && exponent!=0){
					return 0;
				}
				if(exponent<0){
					return 1/Pow(base,-exponent);
				}else{
					return Pow(base, exponent);
				}
			}
			 
			double Pow(double x, int n){
				if(n==0){
					return 1.0;
				}
				double v=Pow(x,n/2);
				if(n%2==0){
					return v*v;
				}else{
					return v*v*x;
				}
			}
		};


### 十三、 调整数组顺序使其奇数位于偶数前面
**题目描述**


### 十四、 链表中倒数第k个结点
**题目描述**


### 十五、 反转链表
**题目描述**


### 十六、 合并两个排序的链表
**题目描述**


### 十七、 树的子结构
**题目描述**


### 十八、 二叉树的镜像
**题目描述**


### 十九、 顺时针打印矩阵

### 二十、 包含min函数的栈

### 二十一、栈的压入、弹出序列

### 二十二、从上往下打印二叉树

### 二十三、 二叉搜索树的后序遍历序列

### 二十四、 二叉树中和为某一值的路径

### 二十五、 复杂链表的复制

### 二十六、 二叉搜索树与双向链表

### 二十七、 字符串的排列

### 二十八、 数组中出现次数超过一半的数字

### 二十九、 最小的K个数

### 三十、 连续子数组的最大和

### 三十一、 整数中1出现的次数（从1到n整数中1出现的次数）

### 三十二、 把数组排成最小的数

### 三十三、 丑数

### 三十四、 第一个只出现一次的字符

### 三十五、 数组中的逆序对

### 三十六、 两个链表的第一个公共结点

### 三十七、 数字在排序数组中出现的次数

### 三十八、 二叉树的深度

### 三十九、 平衡二叉树

### 四十、 数组中只出现一次的数字

### 四十一、 和为S的连续正数序列

### 四十二、 和为S的两个数字

### 四十三、 左旋转字符串

### 四十四、 翻转单词顺序列

### 四十五、 扑克牌顺子

### 四十六、 孩子们的游戏(圆圈中最后剩下的数)

### 四十七、 求1+2+3+...+n

### 四十八、 不用加减乘除做加法

### 四十九、 把字符串转换成整数

### 五十、 数组中重复的数字

### 五十一、 构建乘积数组

### 五十二、 正则表达式匹配

### 五十三、 表示数值的字符串

### 五十四、 字符流中第一个不重复的字符

### 五十五、 链表中环的入口结点

### 五十六、 删除链表中重复的结点

### 五十七、 二叉树的下一个结点

### 五十八、 对称的二叉树

### 五十九、 按之字形顺序打印二叉树
 
### 六十、 把二叉树打印成多行

### 六十一、 序列化二叉树

### 六十二、 二叉搜索树的第k个结点

### 六十三、 数据流中的中位数

### 六十四、 滑动窗口的最大值

### 六十五、 矩阵中的路径

### 六十六、 机器人的运动范围







