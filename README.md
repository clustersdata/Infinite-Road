# Infinite-Road

Infinite Road

Problem Description

甜甜从小就喜欢画图画，最近他买了一支智能画笔，由于刚刚接触，所以甜甜只会用它来画直线，于是他就在平面直角坐标系中画出如下的图形：

甜甜的好朋友蜜蜜发现上面的图还是有点规则的，于是他问甜甜：在你画的图中，我给你两个点，请你算一算连接两点的折线长度（即沿折线走的路线长度）吧。

Input

第一个数是正整数N（≤100）。代表数据的组数。

每组数据由四个非负整数组成x1，y1，x2，y2；所有的数都不会大于100。


Output

对于每组数据，输出两点(x1,y1),(x2,y2)之间的折线距离。注意输出结果精确到小数点后3位。

Sample Input

5 0 0 0 1 0 0 1 0 2 3 3 1 99 99 9 9 5 5 5 5

Sample Output

1.000 2.414 10.646 54985.047 0.000



代码：

#include <cmath>
  
#include <cstdio>
  
#include <algorithm>
  
using namespace std;

int main(void)

{

    int n, x[3], y[3];
    
    double s;
   
    scanf("%d", &n);
    
    while (n-- && scanf("%d%d%d%d", x, y, x+1, y+1))
    
    {
    
        if ((x[2] = x[0]+y[0]) > (y[2] = x[1]+y[1]))
        
        {
        
            swap(x[0], x[1]);   swap(y[0], y[1]);  swap(x[2], y[2]);
            
        }
        
        if (x[2] == y[2])
        
            printf("%.3f\n", sqrt(pow(x[0]-x[1], 2)+pow(y[0]-y[1], 2)));
            
        else
        
        {
        
            s = sqrt((double)2.0)*(x[2] + x[1] - x[0] + y[2]*(y[2]-1)/2.0 - x[2]*(x[2]+1)/2.0);
            
            for (; x[2] < y[2]; x[2]++)    s += sqrt((double)2*x[2]*x[2]+2*x[2]+1);
            
            printf("%.3f\n", s);
            
        }
        
    }
    
    return 0;
    
}

