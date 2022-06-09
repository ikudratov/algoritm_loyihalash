## Mutagenezga asoslangan genetik algoritm

```bash
import numpy as np
import matplotlib.pyplot as plt
import openpyxl as xl
import pandas as pd
import random
import math

N=100
Gmax=2000
all_max=0
pm=0.02
pc=0.7
def f(x1,x2):
    return 21.5+x1*math.sin(4*math.pi*x1)+x2*math.sin(20*math.pi*x2)

A=[]
for i in range(0,N):
	A.append([random.uniform(-3, 12.1),random.uniform(4.1, 5.8)])


fitness=[]
for i in range(0,N):
	fitness.append(f(A[i][0],A[i][1]))
fit=np.array(fitness)
ans = sum(fit)
Max_now=max(fit)
if Max_now>all_max: 
	all_max=Max_now
s=0
for i in range(0,N):
	s=fit[i]/ans+s
	fit[i]=s
A2=[]
for i in range(0,N):
	n=random.uniform(0, 1)
	which=np.where(fit >n )[0][0]
	A2.append(A[which])

mating=np.random.rand(N)
select=np.where(mating<=pc)
i=0
while i<len(select[0]):
	digit= random.randint(0, 1)
	if i+1<len(select[0]):
		A2[select[0][i]][digit:],A2[select[0][i+1]][digit:]=A2[select[0][i+1]][digit:],A2[select[0][i]][digit:]  #exchange
	i=i+2

for a in A2:
	variation=np.random.rand(2)
	if variation[0]<=pm:
		a[0]=random.uniform(-3, 12.1)
	if variation[1]<=pm:
		a[1]=random.uniform(4.1, 5.8)

print(A2)
```

# Natijani ko'rish
```bash
# python3 index.py
```