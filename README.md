# test_technique_ncq
Algo 1:
import numpy as np
from numpy import zeros,array

def solution( N,A):
    V=zeros(N)
    for i in range(np.size(A)):
        if((A[i]>=1 )and(A[i]<=N)):
            V[A[i]-1]+=1
             
        elif (A[i]== N+1):
            max=0
            for j in range(N):
                if V[j]>max:
                    max=V[j]
            for i in range(N):
                V[i]=max
    return V
Algo2:
import numpy as np
from numpy import array
def getmax(a):
    for i in range (np.size(a)-1):
        max=a[0]
        if(a[i]>max):
            max=a[i]
    return max
def buildtab(n,p):
    tab=array(n+1)
    q=1
    r=1
    tab[0]=1
    tab[1]=1
    index=3
    while(index<=n+1):
        t=r
        r=(r+q)%(2**p)
        q=t
        tab[index-1]=r
        index+=1
    
    return tab
def solution(A,B):
    result=array(np.size(A))
    n=getmax(A)
    p=getmax(B)
    cach=buildtab(n,p)
    for i in range (np.size(A)-1):
        result[i] = tab[A[i]] % (2** B[i])
    return result
Algo 3:
from numpy import array
import numpy as np
def solution(A):
    n=np.size(A)
    if(n==0):
        return 0
    max=A[0]
    sum=0
    for i in range(0,n-1):
        value=abs(A[i])
        sum+=value
        if(max<value):
            max=value
        A[i]=value
    count=array(max+1)
    for i in A:
        count[i]+=1
    total=array(sum+1)
    for i in range(0,sum):
        total[i]=-1
    for i in range (0,max):
        for j in range (0,sum):
            if (total[j]>=0):
                total[j]=count[i]
            elif((total[j-i]>=0) and(j-i)>=0 ):
                total[j]=total[j-i]-1
    return total
                
