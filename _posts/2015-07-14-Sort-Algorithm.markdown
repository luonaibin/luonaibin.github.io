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
# 插入排序
## 直接插入排序
**基本思想**<p>每次将一个待排序的记录，按其关键字大小插入到前面已经排序号的子序列中，直到全部记录插入完成。</p>

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
    			for (int j = i; (j 0) && (a[j] < a[j - 1]); j--) {
    				int temp = a[j];
    				a[j] = a[j - 1];
    				a[j - 1] = temp;
    			}
    		}
    	}


## 希尔排序
**基本思想**<p>先将待排序表分割成若干形如L[i,i+d,i=2d......i+kd]的子表，分别进行插入排序，当整个表中的元素基本有序时，在对全体记录进行一次直接插入排序。</p>

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


# 交换排序
## 冒泡排序

## 快速排序
# 选择排序
## 简单选择排序
## 堆排序
# 归并排序
## 二路归并排序
## 多路归并排序 