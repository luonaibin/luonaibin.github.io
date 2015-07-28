---
layout: post
title:  "排序算法"
date:   2015-07-14
---
<style type="text/css">
p{
	text-indent: 2em;
}
.post img {
  margin-bottom: 0rem;
}
</style>

<p class="intro">
	<span class="dropcap">排</span>序算法，重新排列表中的元素，使表中的元素满足按关键字递增或递减排列的过程。
</p>
## 一、插入排序
### 1.1 直接插入排序
**基本思想**每次将一个待排序的记录，按其关键字大小插入到前面已经排序号的子序列中，直到全部记录插入完成。

    	/**
    	 * Java插入排序算法
    	 * 
    	 * @param a
    	 */
    	public static void insertSort1(int[] a) {
    		int i, j;
    		for (i = 1; i < a.length; i++) {
    			if (a[i - 1] a[i]) {
    				int temp = a[i];
    
    				for (j = i - 1; j >= 0 && a[j] temp; j--) {
    					a[j + 1] = a[j];
    				}
    				a[j + 1] = temp;
    			}
    		}
    	}
    
    	public static void insertSort2(int[] a) {
    		for (int i = 1; i < a.length; i++) {
    			for (int j = i; (j>0) && (a[j] < a[j - 1]); j--) {
    				int temp = a[j];
    				a[j] = a[j - 1];
    				a[j - 1] = temp;
    			}
    		}
    	}


### 1.2 希尔排序
**基本思想**
先将待排序表分割成若干形如L[i,i+d,i=2d......i+kd]的子表，分别进行插入排序，当整个表中的元素基本有序时，在对全体记录进行一次直接插入排序。

    	public static void shellSort(int[] a) {
    		int len = a.length;
    		for (int d = len / 2; d >= 1; d = d / 2) {
    			for (int i = d; i < len; i = i + d) {
    				if (a[i] < a[i - d]) {
    					int t = a[i];
    					int j;
    					for (j = i - d; j >= 0 && t < a[j]; j = j - d) {
    						a[j + d] = a[j];
    					}
    					a[j + d] = t;
    				}
    			}
    		}
    	}


## 二、交换排序
### 2.1 冒泡排序
**基本思想**假设待排序表长n，从后往前(从前往后)两两比较相邻元素的值，若为逆序（即A[i-1]>A[i]），则交换它们，直到序列比较完。

	/**
	 * Java的冒泡排序算法 小数下沉
	 * 
	 * @param a
	 */
	public static void bubbleSort1(int[] a) {
		for (int i = 0; i < a.length; i++) {
			for (int j = a.length - 1; j > 0; j--) {
				if (a[j] < a[j - 1]) {
					int temp = a[j];
					a[j] = a[j - 1];
					a[j - 1] = temp;
				}
			}
			System.out.println(a[i]);
		}
	}

	/**
	 * Java冒泡排序 大数上冒
	 * 
	 * @param a
	 */
	public static void bubbleSort2(int[] a) {
		for (int i = a.length - 1; i > 0; i--) {
			for (int j = 0; j < i; j++) {
				if (a[j] > a[j + 1]) {
					int temp = a[j];
					a[j] = a[j + 1];
					a[j + 1] = temp;
				}
			}
		}
	}


    void BubbleSort(int[] A,int n){//另一种写法
    	boolean flag;
    	for(int i=0;i<n-1;i++){
    		flag=false;
    		for(int j=n-1;j>i;j--){
    			if(A[j-1]>A[j]){
    				swap(A[j-1],A[j]);
    				flag=true;
    			}	
    		}
    		if(flag==false){
    			returnl;
    		}	}
    }


##2.2 快速排序
**基本思想**首先选择一个轴值（即比较的基准），将待排序记录分割成独立的两部分，左侧记录的关键码均小于或等于轴值，右侧记录的关键码均大于等于轴值，然后分别对这两部分重复上述过程直到整个序列有序。

    	    public static int Partition(int[] a,int left,int right){
    		int pivot = a[left];
    		while(left<right){
    			while(left<right && pivot<=a[right]){
    				right--;
    			}
    			a[left]=a[right];
    			while(left<right && pivot>=a[left]){
    				left++;
    			}
    			a[right]=a[left];
    		}
    		a[left]=pivot;
    		return left;
    	}
    
    
    	public static void quickSort(int[] a,int start,int end){
    		if (start<end) {
    			int mid = Partition(a,start,end);
    			quickSort(a,start,mid-1);
    			quickSort(a,mid+1,end);
    		}
    	}



## 三、选择排序
### 3.1 简单选择排序
**基本思想**每一趟（例如第i趟）在后面n-i+1个待排序元素中选取关键字最小的元素，作为有序子序列的第i个元素，直到第n-1趟做完，待排序元素只剩下1个，就不用再选了。
>     	public static void selectSort(int[] a, int n) {
>     		int min;
>     		for (int i = 0; i < n - 1; i++) {
>     			min = i;
>     			for (int j = i + 1; j < n; j++) {
>     				if (a[j] < a[min]) {
>     					min = j;
>     				}
>     			}
>     			if (min != i) {
>     				int t = a[i];
>     				a[i] = a[min];
>     				a[min] = t;
>     			}
>     		}
>     	}
> 

### 3.2 堆排序
## 四、归并排序
### 4.1 二路归并排序
### 4.2 多路归并排序 