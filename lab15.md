###  字符版本贪吃蛇游戏设计及算法 或创新玩法
##### 在上周，本人完成了字符版本的贪吃蛇。借助这篇博客，我再来理清一下设计的思路。
	在这次的字符版本的贪吃蛇中，c代码包含了三个头文件
	1.<stdio.h> 标准输入输出文件 在这次设计中 主要运用了printf ()和 getchar()
	2.<stdlib.h>C标准函数库的头文件，声明了数值与字符串转换函数, 伪随机数生成函数, 动态内存分配函数, 进程控制函数等公共函数。在这次的设计中 ，使用到了srand 和 rand 来随机生成食物
	3.<time.h> 是C标准函数库中获取时间与日期、对时间与日期数据操作及格式化的头文件。

设计的主要内容是四个函数 ，分别是   
		
		1.void snakeMove(int，int) // 蛇的移动
		2.void put_money(void)//放置食物
		3.void output(void)//移动图形块
		4.void gameover(void)//判断游戏是否结束

接下来，我们逐一分析设计每个函数时需要思考的几个关键点
### snakeMove(int x, int y)
蛇的位置由坐标来决定 ，坐标我们使用数组来实现  
我们使用到了 system("cls") 这是用来清屏的  
函数的两个参数设计来是移动蛇的位置的 
		
		//根据食入的数据让蛇移动  
				        
		switch(CH)  
        {  
            case 'a':  
                snakeMove(0,-1);  
                break;  
            case 'w':  
                snakeMove(-1,0);  
                break;  
            case 's':  
                snakeMove(1,0);  
                break;  
            case 'd':  
                snakeMove(0,1);  
                break;  
        }  
      
 
 考虑的几种情况
 1.保留蛇最后一块的位置
 2.重新计算蛇整个身体的位置
 3.当头出现的位置由食物时
 4.若没有食物，就将蛇的最后一个位置变成空格


### void output(void) 
这是一个实现打印图案的函数 没有什么可讲的 
利用双重循环打印出二维数组

### void put_money(void)
这里运用到了rand随机函数来放置食物  
同时我们设置了变量flag来表明食物的状态 
		
	void put_money(void)  
		{  
    //随机产生食物  
	    while(flag)  
	    {  
	        moneyX=rand()%10+1;  
	        moneyY=rand()%10+1;  
        
	        if(map[moneyX][moneyY]==' ')  
	        {  
	            flag=0;  
	        }  
        }  
    
	    map[moneyX][moneyY]=SNAKE_FOOD;  
		}  



### int gameover(void)
判断游戏是否结束的几个标志
1.如果蛇的长度达到20 ，结束游戏
2.如果蛇撞到墙游戏结束
3.如果蛇撞到自己游戏结束  
这里设置了变量flag1来标记游戏的状态

	int gameover(void)  
	{  
    int flag1=0, i;  
    
    //如果蛇的长度达到20，结束  
    if(snakeLength==20)  
    {  
        flag1=1;  
    }  
    
    //如果，蛇撞到墙，游戏结束  
    if(snakeX[0]==0||snakeX[0]==12||snakeY[0]==0||snakeY[0]==12)  
    {  
        flag1=1;  
    }  
    
    //如果蛇撞到自己，游戏结束  
    for(i=1;i<snakeLength;i++)  
    {  
        if(snakeX[0]==snakeX[i]&&snakeY[0]==snakeY[i])  
        {  
            flag1=1;  
        }  
    }  
    
    //打印游戏结束  
    if(flag1)  
    {  
        printf("Game over!!\n");  
        printf("Good Game!!\n");  
        printf("亲爱的玩家，您还想再来一局吗？\n");  
        return 1;  
    }  
    
    return 0;  
	}  
### 可能的创新玩法
1.增加游戏难度  
我
