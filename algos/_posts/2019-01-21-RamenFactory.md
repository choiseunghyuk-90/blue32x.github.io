---
layout: post
title: RamenFactory
categories:
    - algos
---

코딜리티 Lesson 2
--- 
1. 문제
---
라면 공장에서는 하루에 밀가루를 1톤씩 사용합니다. 원래 밀가루를 공급받던 공장의 고장으로 앞으로 k일 이후에야 밀가루를 공급받을 수 있기 때문에 해외 공장에서 밀가루를 수입해야 합니다.

해외 공장에서는 향후 밀가루를 공급할 수 있는 날짜와 수량을 알려주었고, 라면 공장에서는 운송비를 줄이기 위해 최소한의 횟수로 밀가루를 공급받고 싶습니다.

현재 공장에 남아있는 밀가루 수량 stock, 밀가루 공급 일정(dates)과 해당 시점에 공급 가능한 밀가루 수량(supplies), 원래 공장으로부터 공급받을 수 있는 시점 k가 주어질 때, 밀가루가 떨어지지 않고 공장을 운영하기 위해서 최소한 몇 번 해외 공장으로부터 밀가루를 공급받아야 하는지를 return 하도록 solution 함수를 완성하세요.


2. 문제해석
---
초기 문제를 읽고  dates의 for문을 돌면서 공급일인지 검증하고 밀가루의 수량을 감소시키면서 0이 되었을 경우는 무조건 공급.
0이 아닐 경우공급일을 제외한나머지 공급일들의 수량의 합이 남은 밀가루 수량보다 크면 공급하지 않는다는 로직을 세워지만.
문제해결을 위해 참고한 블로그의 내용을 본 후 느낀 것은 내가 문제를 풀 때 너무 어렵게 접근한다는 것을 알았다.
      


3.문제해결
---
문제 해결 못함 출처에 적힌 블로그의 풀이와 소스를 참고함.
출처: https://dreamhollic.tistory.com/entry/Programmers-19-라면공장-JAVA [Only_One_Engineer]

```
		 if(A.length ==0)
		 {
			 return A;
		 }
		 
		 int[] B=A.clone();
		 
		 while((K--) != 0)
		 {
			 int shiftedNum=0;
			 shiftedNum=A[A.length-1];
			 for(int i=0; i<A.length-1; i++)
			 {
				 A[i+1]=B[i];
			 }
			 A[0]=shiftedNum;
			 B=A.clone();
		 }
		 
		 return A;
	    }
```