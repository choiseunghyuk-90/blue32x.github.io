코딜리티 Lesson 1
---
```
static int solution(int N) {
		int val = 0;
		boolean flag = false;
		boolean end  = false;
		int tmp=0;
		while(N!= 1)
		{
			if(N%2==1 && flag == false)
			{
				flag=true;
			}
			else if (N%2==0 && flag ==true)
			{
				val++;
			}
			else if((N/2!=1 &&(N%2==1))  && flag == true )
			{
				tmp=val;
				if(tmp != 0)
				  val=0;
			}
			else if(N%2==1 && flag == true)
			{
				if(tmp <val)
				{
					tmp=val;
				}
				flag=false;
			}
			
			N/=2;
		}
		if(tmp <val)
		{
			tmp=val;
		}
		
		
		return tmp;
	}
```
