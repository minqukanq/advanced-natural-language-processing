## N-gram Language Models



## Sparsity problems

Language Model은 통계기반으로 만들어지기 때문에 Co-occurrence Matrix 중간에 count가 0인 값을 갖게 됨. 확률이 0인 zero probability 문제가 발생하여 Language Model을 범용적으로 사용하기 힘듦.

이러한 문제들을 해결하기 위해 Smoothing 기법을 적용 함.

![image-20210309170759363](C:\Users\mingukang\AppData\Roaming\Typora\typora-user-images\image-20210309170759363.png)



### 1.  Add-one smoothing

Zero count를 없애기 위해 상수를 더해주어 Zero probability 문제를 해결하고자 함.

N-gram의 모든 count에 대해 1을 더해줌.

가장 기초적인 방법으로 다른 method들의 baseline 역활을 함.

![image-20210309170918861](C:\Users\mingukang\AppData\Roaming\Typora\typora-user-images\image-20210309170918861.png)



### 2. Back off and Interpolation

* #### Back off

  tri-gram 사용이 우수할 수 있지만, statistics가 부족해 zero probability 문제가 발생할 수 있음.

  그러한 상황에는 tri-gram 대신 bi-gram을 사용. 즉, Higher-order (Higher n gram)에서 zero count 일 시 n-1 gram 값을 사용.

![image-20210309173930246](C:\Users\mingukang\AppData\Roaming\Typora\typora-user-images\image-20210309173930246.png)

* #### Interpolation

  여러 order n-gram 값을 linear combination하여 사용. uni-gram부터 tri-gram까지 interpolation 하는 경우의 확률은 아래와 같음.

![image-20210309174615292](C:\Users\mingukang\AppData\Roaming\Typora\typora-user-images\image-20210309174615292.png)

​		각 n-gram 값의 람다는 held-out corpus 로부터 찾아내면 됨.

​		또한, 아래와 같이 람다를 단어의 함수로 만들어 Context 정보를 적용할 수 있음.

![image-20210309174841793](C:\Users\mingukang\AppData\Roaming\Typora\typora-user-images\image-20210309174841793.png)

