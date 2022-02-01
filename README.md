# RPROGRAM7.B
#Poisson fit and goodness of fit
x<-c(0,1,2,3,4)
f<-c(211,90,19,5,0)
fx<-f*x
sumfx<-sum(f*x)
print(sumfx)
sumf<-sum(f)
print(sumf)
s<-length(x)-1
p=sumfx/sumf
print(p)
pr<-dpois(0:4,lambda=p)
pr<-round(pr,digits=5)
fee<-(pr*sumf)
fe<-round(fee,digits=0)
mydata<- data.frame(x,f,fx,pr,fee,fe)
print(mydata)
sums<-list(NA,sum(f),sum(f*x),NA,NA,sum(fe))
mydata<-rbind(mydata,sums)
print(mydata,row.names=FALSE)
result<-chisq.test(f,p=pr,rescale.p=TRUE)
print(result)
tablevalue<-qchisq(.95, df=s)
print(tablevalue)
OUTPUT:
 #Poisson fit and goodness of fit
> x<-c(0,1,2,3,4)
> f<-c(211,90,19,5,0)
> fx<-f*x
> sumfx<-sum(f*x)
> print(sumfx)
[1] 143
> sumf<-sum(f)
> print(sumf)
[1] 325
> s<-length(x)-1
> p=sumfx/sumf
> print(p)
[1] 0.44
> pr<-dpois(0:4,lambda=p)
> pr<-round(pr,digits=5)
> fee<-(pr*sumf)
> fe<-round(fee,digits=0)
> mydata<- data.frame(x,f,fx,pr,fee,fe)
> print(mydata)
  x   f fx      pr       fee  fe
1 0 211  0 0.64404 209.31300 209
2 1  90 90 0.28338  92.09850  92
3 2  19 38 0.06234  20.26050  20
4 3   5 15 0.00914   2.97050   3
5 4   0  0 0.00101   0.32825   0
> sums<-list(NA,sum(f),sum(f*x),NA,NA,sum(fe))
> mydata<-rbind(mydata,sums)
> print(mydata,row.names=FALSE)
  x   f  fx      pr       fee  fe
  0 211   0 0.64404 209.31300 209
  1  90  90 0.28338  92.09850  92
  2  19  38 0.06234  20.26050  20
  3   5  15 0.00914   2.97050   3
  4   0   0 0.00101   0.32825   0
 NA 325 143      NA        NA 324
> result<-chisq.test(f,p=pr,rescale.p=TRUE)
Warning message:
In chisq.test(f, p = pr, rescale.p = TRUE) :
  Chi-squared approximation may be incorrect
> print(result)

	Chi-squared test for given probabilities

data:  f
X-squared = 1.8545, df = 4, p-value = 0.7625

> tablevalue<-qchisq(.95, df=s)
> print(tablevalue)
[1] 9.487729
> 
