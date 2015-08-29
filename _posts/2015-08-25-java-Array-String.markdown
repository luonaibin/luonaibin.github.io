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
**题目描述**输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有的奇数位于数组的前半部分，所有的偶数位于位于数组的后半部分，并保证奇数和奇数，偶数和偶数之间的相对位置不变。

		import java.util.LinkedList;
		import java.util.Queue;
		public class Solution {
			public  void reOrderArray(int[] array) {
				Queue<Integer> odd_queue = new LinkedList<>();// 奇数列
				Queue<Integer> even_queue = new LinkedList<>();// 偶数列
				for (int i = 0; i < array.length; i++) {
					if (isOdd(array[i])) {
						odd_queue.add(array[i]);
					} else {
						even_queue.add(array[i]);
					}
				}
				int i = 0;
				while (!odd_queue.isEmpty()) {
					array[i++] = odd_queue.poll();
				}
				while (!even_queue.isEmpty()) {
					array[i++] = even_queue.poll();
				}
			}
		 
			public  boolean isOdd(int x) {// 判断是否是奇数
				if (x % 2 == 1) {
					return true;
				} else {
					return false;
				}
			}
		}


### 十四、 链表中倒数第k个结点
**题目描述**输入一个链表，输出该链表中倒数第k个结点。

		/*
		public class ListNode {
			int val;
			ListNode next = null;
		 
			ListNode(int val) {
				this.val = val;
			}
		}
		*/
		public class Solution {
			public ListNode FindKthToTail(ListNode head,int k) {
				if(head==null || k==0){
					return null;
				}
				ListNode p=head;
				ListNode q=head;
				while(k-->1){
					q=q.next;
					if(q==null){
						return null;
					}
				}
				while(q.next!=null){
					q=q.next;
					p=p.next;
				}
				return p;
			}
		}

### 十五、 反转链表
**题目描述**输入一个链表，反转链表后，输出链表的所有元素。

		/*public class ListNode {
			int val;
			ListNode next = null;
		 
			ListNode(int val) {
				this.val = val;
			}
		}*/
		public class Solution {
			public ListNode ReverseList(ListNode head) {
		if(head==null){
					return null;
				}
				ListNode p1=head;
				ListNode p2=p1.next;
				ListNode p3;
				while(p2!=null){
					p3=p2.next;
					p2.next=p1;
					p1=p2;
					p2=p3;
				}
				head.next=null;
				head=p1;
				return head;
			}
		}

### 十六、 合并两个排序的链表
**题目描述**输入两个单调递增的链表，输出两个链表合成后的链表，当然我们需要合成后的链表满足单调不减规则。

		/*
		public class ListNode {
			int val;
			ListNode next = null;
		 
			ListNode(int val) {
				this.val = val;
			}
		}
		*/
		public class Solution {
			public ListNode Merge(ListNode list1,ListNode list2) {
				if (list1 == null) {
					return list2;
				} else if (list2 == null) {
					return list1;
				}
		 
				ListNode p = null;
				if (list1.val < list2.val) {
					p = list1;
					p.next = Merge(list1.next, list2);
				} else {
					p = list2;
					p.next = Merge(list1, list2.next);
				}
				return p;
			}
		}

### 十七、 树的子结构
**题目描述**


### 十八、 二叉树的镜像
**题目描述**
操作给定的二叉树，将其变换为源二叉树的镜像。 
输入描述:
二叉树的镜像定义：源二叉树 
    	    8
    	   /  \
    	  6   10
    	 / \  / \
    	5  7 9 11
    	镜像二叉树
    	    8
    	   /  \
    	  10   6
    	 / \  / \
    	11 9 7  5
		
		
			/*
		public class TreeNode {
			int val = 0;
			TreeNode left = null;
			TreeNode right = null;
		 
			public TreeNode(int val) {
				this.val = val;
		 
			}
		 
		}
		*/
		public class Solution {
			public void Mirror(TreeNode root) {
				if (null == root) {
					return;
				}
				if (null == root.left && null == root.right) {
					return;
				}
				TreeNode leftTmp = root.left;
				root.left = root.right;
				root.right = leftTmp;
				Mirror(root.left);
				Mirror(root.right);
			}
		}	

### 十九、 顺时针打印矩阵

### 二十、 包含min函数的栈

### 二十一、栈的压入、弹出序列

### 二十二、从上往下打印二叉树
**题目描述**从上往下打印出二叉树的每个节点，同层节点从左至右打印。

		/*
		public class TreeNode {
			int val = 0;
			TreeNode left = null;
			TreeNode right = null;
		 
			public TreeNode(int val) {
				this.val = val;
		 
			}
		 
		}*/
		import java.util.ArrayList;
		import java.util.LinkedList;
		import java.util.Queue;
		 
		public class Solution {
			public ArrayList<Integer> PrintFromTopToBottom(TreeNode root) {
				ArrayList<Integer> alist = new ArrayList<>();
				Queue<TreeNode> queue = new LinkedList<>();
				if (root == null) {
					return alist;
				}
				queue.add(root);
				//alist.add(root.val);
				while (!queue.isEmpty()) {
					TreeNode pNode = queue.peek();
					queue.poll();
					alist.add(pNode.val);
					if (pNode.left != null) {
						queue.add(pNode.left);
					}
					if (pNode.right != null) {
						queue.add(pNode.right);
					}
				}
				return alist;
			}
		}

### 二十三、 二叉搜索树的后序遍历序列

### 二十四、 二叉树中和为某一值的路径

### 二十五、 复杂链表的复制

### 二十六、 二叉搜索树与双向链表

### 二十七、 字符串的排列

### 二十八、 数组中出现次数超过一半的数字
**题目描述**
数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。例如输入一个长度为9的数组{1,2,3,2,2,2,5,4,2}。由于数字2在数组中出现了5次，超过数组长度的一半，因此输出2。

		import java.util.Arrays;
		public class Solution {
			public int MoreThanHalfNum_Solution(int [] array) {
				if(array.length==0 || array==null){
					return 0;
				}
				int count = 0;
		 
				Arrays.sort(array);
				int axis = array[array.length >> 1];
				
				count = 0;
				for (int i = 0; i < array.length; i++) {
					if (axis == array[i]) {
						count++;
					}
				}
				if (count > array.length / 2) {
					return axis;
				}
				return 0;
				 
			}
		}

### 二十九、 最小的K个数
**题目描述**
输入n个整数，找出其中最小的K个数。例如输入4,5,1,6,2,7,3,8这8个数字，则最小的4个数字是1,2,3,4,。

		import java.util.ArrayList;
		public class Solution {
			public ArrayList<Integer> GetLeastNumbers_Solution(int [] input, int k) {
				ArrayList<Integer> alist=new ArrayList();
				 if(k>input.length || k==0){
					return alist;
				}
				int[] kint=new int[k];
				 
				for(int i=0;i<k;i++){
					kint[i]=input[i];
				}
				int mk;
				int mindex;
				for(int j=k;j<input.length;j++){
					mk=max(kint);
					mindex=max_i(kint);
					if(mk>input[j]){
						kint[mindex]=input[j];
					}
				}
				
				for(int a:kint){
					alist.add(a);
				}
				return alist;
			}
			 
			 
			public static int max(int[] array){
				int m=array[0];
				for(int i=1;i<array.length;i++){
					if(array[i]>m){
						m=array[i];
					}
				}
				return m;
			}
			public static int max_i(int[] array){
				int m=array[0];
				int index=0;
				for(int i=1;i<array.length;i++){
					if(array[i]>m){
					   index=i;
					}
				}
				return index;
			}
		}

### 三十、 连续子数组的最大和
**题目描述**

HZ偶尔会拿些专业问题来忽悠那些非计算机专业的同学。今天测试组开完会后,他又发话了:在古老的一维模式识别中,常常需要计算连续子向量的最大和,当向量全为正数的时候,问题很好解决。但是,如果向量中包含负数,是否应该包含某个负数,并期望旁边的正数会弥补它呢？例如:{6,-3,-2,7,-15,1,2,2},连续子向量的最大和为8(从第0个开始,到第3个为止)。你会不会被他忽悠住？

		public class Solution {
			public int FindGreatestSumOfSubArray(int[] array) {
				if (array.length == 0 || array==null) {
					return 0;
				}
				int maxSum = array[0];
				int thisSum = array[0];
				for (int i = 1; i < array.length; i++) {
		 
					thisSum = thisSum + array[i];
					if (thisSum > maxSum) {
						maxSum = thisSum;
					} else if (thisSum < 0) {
						thisSum = 0;
					}
				}
				return maxSum;
			}
		}


### 三十一、 整数中1出现的次数（从1到n整数中1出现的次数）
**题目描述**

求出1~13的整数中1出现的次数,并算出100~1300的整数中1出现的次数？为此他特别数了一下1~13中包含1的数字有1、10、11、12、13因此共出现6次,但是对于后面问题他就没辙了。ACMer希望你们帮帮他,并把问题更加普遍化,可以很快的求出任意非负整数区间中1出现的次数。

		public class Solution {
			public int NumberOf1Between1AndN_Solution(int n) {
				int num = 0;
				for (int i = 1; i <= n; i++) {
					int j=i;
					while(j>0){
						if(j%10==1){
							num++;
						}
						j=j/10;
					}
				}
				return num;
			}
		}

### 三十二、 把数组排成最小的数
**题目描述**

输入一个正整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。例如输入数组{3，32，321}，则打印出这三个数字能排成的最小数字为321323。

		import java.util.ArrayList;
		import java.util.Collections;
		import java.util.Comparator;
		 
		public class Solution {
			public String PrintMinNumber(int [] numbers) {
				if (numbers == null) {
					return null;
				}
				ArrayList<String> list = new ArrayList<>();
				for (int i = 0; i < numbers.length; i++) {
					list.add(String.valueOf(numbers[i]));
				}
				Collections.sort(list, new Comparator<String>() {
					public int compare(String str1, String str2) {
						String s1 = str1 + str2;
						String s2 = str2 + str1;
						return s1.compareTo(s2);
					}
				});
				StringBuilder sb = new StringBuilder();
				for (String s : list) {
					sb.append(s);
				}
				return sb.toString();
			}
		}

### 三十三、 丑数

### 三十四、 第一个只出现一次的字符
**题目描述**

在一个字符串(1<=字符串长度<=10000，全部由字母组成)中找到第一个只出现一次的字符的位置。若为空串，返回-1

		public class Solution {
			public int FirstNotRepeatingChar(String str) {
				if (str.length() == 0 || str == null) {
					return -1;
				}
				int[] book = new int[26];
				char c = 'A';
				if (str.charAt(0) >= 'a') {
					c = 'a';
				}
				for (int i = 0; i < str.length(); i++) {
					book[str.charAt(i) - c]++;
				}
				for (int i = 0; i < str.length(); i++) {
					if (book[str.charAt(i)-c] == 1) {
						return i;
					}
				}
				return -1;
			}
		}

### 三十五、 数组中的逆序对

### 三十六、 两个链表的第一个公共结点

### 三十七、 数字在排序数组中出现的次数
**题目描述**
统计一个数字在排序数组中出现的次数。

		public class Solution {
			public int GetNumberOfK(int [] array , int k) {
				int count=0;
				for(int i=0;i<array.length;i++){
					if(array[i]==k){
						count++;
					}
				}
				return count;
			}
		}


### 三十八、 二叉树的深度
**题目描述**
输入一棵二叉树，求该树的深度。从根结点到叶结点依次经过的结点（含根、叶结点）形成树的一条路径，最长路径的长度为树的深度。

		/*public class TreeNode {
			int val = 0;
			TreeNode left = null;
			TreeNode right = null;
		 
			public TreeNode(int val) {
				this.val = val;
		 
			}
		 
		}*/
		public class Solution {
			public int TreeDepth(TreeNode root) {
				if(root==null)
					return 0;
				if(root.left==null && root.right==null){
					return 1;
				}
				int leftDepth=TreeDepth(root.left);
				int rightDepth=TreeDepth(root.right);
				return (leftDepth>rightDepth ? leftDepth:rightDepth)+1;
			}
		}

### 三十九、 平衡二叉树
**题目描述**

输入一棵二叉树，判断该二叉树是否是平衡二叉树。

		/*
		public class TreeNode {
			int val = 0;
			TreeNode left = null;
			TreeNode right = null;
		 
			public TreeNode(int val) {
				this.val = val;
		 
			}
		 
		}
		*/
		public class Solution {
			public boolean IsBalanced_Solution(TreeNode root) {
				if(root == null){
					return true;
				}
				if(getHeight(root) == -1){
					return false;
				}
				return true;
			}
			 
			public static int getHeight(TreeNode root){
				if(root == null){
					return 0;
				}
				int leftNum = getHeight(root.left);
				int rightNum = getHeight(root.right);
				if(leftNum == -1 || rightNum == -1){
					return -1;
				}
				if(Math.abs(leftNum - rightNum) > 1){
					return -1;
				}
				return ((leftNum > rightNum)? leftNum  : rightNum)+1;
			}
		}

### 四十、 数组中只出现一次的数字
**题目描述**

一个整型数组里除了两个数字之外，其他的数字都出现了两次。请写程序找出这两个只出现一次的数字。

		//num1,num2分别为长度为1的数组。传出参数
		//将num1[0],num2[0]设置为返回结果
		public class Solution {
			public void FindNumsAppearOnce(int [] array,int num1[] , int num2[]) {
				if(array==null || array.length<2){
					return;
				}
				int resultExclusiveOR = 0;
				for(int i=0;i<array.length;i++){
					resultExclusiveOR ^= array[i];
				}
				int index=FindFirstBitIs1(resultExclusiveOR);
				num1[0]=0;
				num2[0]=0;
				for(int j=0;j<array.length;j++){
					if(IsBit1(array[j],index)){
						num1[0]^=array[j];
					}else{
						num2[0]^=array[j];
					}
				}
			}
			 
			public static int FindFirstBitIs1(int num){
				int indexBit=0;
				while((num&1)==0){
					num=num>>1;
					indexBit++;
				}
				return indexBit;
			}
			 
			public static boolean IsBit1(int num,int indexBit){
				num=num>>indexBit;
				return (num & 1)==1;
			}
					   
		}

### 四十一、 和为S的连续正数序列

### 四十二、 和为S的两个数字
**题目描述**

输入一个递增排序的数组和一个数字S，在数组中查找两个数，是的他们的和正好是S，如果有多对数字的和等于S，输出两个数的乘积最小的。 
输出描述:
对应每个测试案例，输出两个数，小的先输出。

		import java.util.ArrayList;
		public class Solution {
			public ArrayList<Integer> FindNumbersWithSum(int [] array,int sum) {
				ArrayList<Integer> list=new ArrayList<>();
				int len=array.length;
				int i=0;
				int j=len-1;
				int product=0;
				int min=sum*sum;
				for(;i<j;){
					if(array[i]+array[j]>sum){
						j--;
					}else if (array[i]+array[j]<sum) {
						i++;
					}else {
		//              list.clear();
						product=array[i]*array[j];
						if(min>product){
							min=product;
							list.add(array[i]);
							list.add(array[j]);
						}
						i++;
					}
				}
				return list;
			}
		}

### 四十三、 左旋转字符串
**题目描述**

汇编语言中有一种移位指令叫做循环左移（ROL），现在有个简单的任务，就是用字符串模拟这个指令的运算结果。对于一个给定的字符序列S，请你把其循环左移K位后的序列输出。例如，字符序列S=”abcXYZdef”,要求输出循环左移3位后的结果，即“XYZdefabc”。是不是很简单？OK，搞定它！

		public class Solution {
			public String LeftRotateString(String str,int n) {
				if(str==null || str.length()<n){
					return "";
				}
				char[] ch=str.toCharArray();
				while (n > 0) {
					rotate(ch);
					n--;
				}
				return String.valueOf(ch);
			}
			public  void rotate(char[] ch) {
		//      char[] ch = str.toCharArray();
				char c = ch[0];
				for (int i = 1; i < ch.length; i++) {
					ch[i - 1] = ch[i];
				}
				ch[ch.length - 1] = c;
			}
		}

### 四十四、 翻转单词顺序列
**题目描述**

JOBDU最近来了一个新员工Fish，每天早晨总是会拿着一本英文杂志，写些句子在本子上。同事Cat对Fish写的内容颇感兴趣，有一天他向Fish借来翻看，但却读不懂它的意思。例如，“student. a am I”。后来才意识到，这家伙原来把句子单词的顺序翻转了，正确的句子应该是“I am a student.”。Cat对一一的翻转这些单词顺序可不在行，你能帮助他么？

		public class Solution {
			public String ReverseSentence(String str) {
				if(str == null || str == "" || str.length() == 0)
					return str;
				String[] s=str.split(" ");
				if(s.length <= 1)
					return str;
				int i=0;
				int j=s.length-1;
				while(i<j){
					String st=s[i];
					s[i++]=s[j];
					s[j--]=st;
				}
				StringBuffer sb=new StringBuffer();
				for(int k=0;k<s.length-1;k++){
					sb.append(s[k]+" ");
				}
				sb.append(s[s.length-1]);
				return sb.toString();
			}
		}

### 四十五、 扑克牌顺子

### 四十六、 孩子们的游戏(圆圈中最后剩下的数)

### 四十七、 求1+2+3+...+n
**题目描述**
求1+2+3+...+n，要求不能使用乘除法、for、while、if、else、switch、case等关键字及条件判断语句（A?B:C）。

		public class Solution {
			public int Sum_Solution(int n) {
				return (1+n)*n/2;
			}
		}

### 四十八、 不用加减乘除做加法
**题目描述**

写一个函数，求两个整数之和，要求在函数体内不得使用+、-、*、/四则运算符号。

		public class Solution {
			public int Add(int a,int b) {
				if(b==0)
					return a;
				int sum,carry;
				sum=a^b;
				carry=(a&b)<<1;
				return Add(sum,carry);
			}
		}

### 四十九、 把字符串转换成整数
**题目描述**
将一个字符串转换成一个整数，要求不能使用字符串转换整数的库函数。

		public class Solution {
			public int StrToInt(String str) {
				if (str.length() == 0) {
					return 0;
				}
				boolean flag = true;
				long num = 0;
				if (str != null) {
					char[] cstr = str.toCharArray();
					int i = 0;
					if (cstr[i] == '+') {
						i++;
					} else if (cstr[i] == '-') {
						i++;
						flag = false;
					}
					while (i < str.length() && cstr[i] != '\0') {
						if (cstr[i] >= '0' && cstr[i] <= '9') {
							num = num * 10 + (cstr[i] - '0');
		 
							i++;
						} else {
							num = 0;
							break;
						}
					}
					if (!flag) {
						num = 0 - num;
					}
					if (num > Integer.MAX_VALUE) {
						return 0;
					}
					if (num < Integer.MIN_VALUE) {
						return 0;
					}
				}
				return (int)num;
			}
		}

### 五十、 数组中重复的数字

### 五十一、 构建乘积数组
**题目描述**
给定一个数组A[0,1,...,n-1],请构建一个数组B[0,1,...,n-1],其中B中的元素B[i]=A[0]*A[1]*...*A[i-1]*A[i+1]*...*A[n-1]。不能使用除法。

		import java.util.ArrayList;
		public class Solution {
			int[] multiply(int[] A) {
				int n = A.length;
				int[] left = new int[n];
				int[] right = new int[n];
				left[0] = 1;
				right[n - 1] = 1;
				int[] result = new int[n];
				for (int i = 0; i < n - 1; ++i) {
					left[i + 1] = left[i] * A[i];
					right[n - 2 - i] = right[n - 1 - i] * A[n - 1 - i];
				}
				for (int i = 0; i < n; i++) {
					result[i] = left[i] * right[i];
				}
				return result;
			}
		}

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







