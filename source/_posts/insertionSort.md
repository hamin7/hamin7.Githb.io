---
title: Insertion Sort란?
author: Hamin
date: 2020-10-18 21:44:22
tags: [Insertion Sort, Sort, Algorithm]
categories:
- [Algorithm, Sort]
thumbnail: /gallery/algorithm.png
---

삽입 정렬이란 선택한 요소에 알맞은 위치에 삽입하는 작업을 반복하여 정렬하는 알고리즘이다.
자료 배열의 모든 요소를 앞에서부터 차례대로 선택하고
이미 정렬된 배열 부분과 비교 후 알맞은 위치를 찾아 삽입함으로써 정렬을 완성하는 알고리즘이다.

<!--more-->

## 동작 방식

{% asset_img InsertionSort.jpg %}

Key값을 정렬된 배열 부분과 비교하여 알맞은 위치에 삽입.
삽입 전, x는 정렬되지 않은 부분의 첫 번째 요소로 선택된 키 값이다.

{% asset_img InsertPosition1.jpg %}

삽입 후, 삽입 된 부분에서 x거 들어갈 알맞은 위치에 삽입하게 된다.

{% asset_img InsertPosition2.jpg %}

정렬되지 않은 항목 중 첫 번째 항목이 다음 key 값으로 지정된다.

## 특징

1. 장점
- 간단한 구현
- 같은 값 사이에는 상대적 위치 변화가 없음
- Stable한 정렬임
- 주어진 자료공간 이외의 공간을 사용하지 않음

2. 단점
- 입력 데이터 배열의 길이가 길어질수록 비효율적
- 역으로 정렬되어 있는 입력 값에 대해서 최악의 성능을 보임 (모든 입력값에 대해 삽입이 필요)

## 시간복잡도

{% asset_img InsertionSort_Psudo.jpg %}

T(n) = c1n + c2(n-1) + c4(n-1) + c5(n(n+1)/2-1) + c6(n(n-1)/2) + c7(n(n-1)/2) + c8(n-1)

T(n) = O(n^2)

## 예제 코드

~~~java
import java.util.Scanner;
// 단순 삽입 정렬

class InsertionSort {
	// 단순 삽입 정렬
	static void insertionSort(int[] a, int n) {
		for (int i = 1; i < n; i++) {
			int j;
			int tmp = a[i];
			for (j = i; j > 0 && a[j - 1] > tmp; j--)
				a[j] = a[j - 1];
			a[j] = tmp;
		}
	}

	public static void main(String[] args) {
		Scanner stdIn = new Scanner(System.in);

		System.out.println("단순 삽입 정렬");
		System.out.print("요솟수：");
		int nx = stdIn.nextInt();
		int[] x = new int[nx];

		for (int i = 0; i < nx; i++) {
			System.out.print("x[" + i + "]：");
			x[i] = stdIn.nextInt();
		}

		insertionSort(x, nx);				// 배열 x를 단순 삽입 정렬

		System.out.println("오름차순으로 정렬했습니다.");
		for (int i = 0; i < nx; i++)
			System.out.println("x[" + i + "]＝" + x[i]);
	}
}
~~~