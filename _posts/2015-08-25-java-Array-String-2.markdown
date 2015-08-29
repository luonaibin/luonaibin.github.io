---
layout:     post
title:      "剑指offer-Java实现(21--40)"
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

