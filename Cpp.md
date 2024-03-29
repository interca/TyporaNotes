#  Cpp

## 注意事项

>从一个容器取出另一个容器，最好用&
>
>比如set s=&map[index]
>
>int &a = f(i)
>
>可以取出值 并且可以改变a来改变f(i)
>
>c++  vectorPush一个vector是值Push
>
>最好用depue

**+= 比较快**

```cpp
const int N=1010;
class Solution {
public:
    int a[(int)4e5][26];
    int index=0;
    int sum[(int)4e5];
    vector<int> sumPrefixScores(vector<string>& words) {
        int n=words.size();
         for(int i=0;i<n;i++){
             insert(words[i]);
         }
         vector<int>v(n);
         for(int i=0;i<n;i++){
             v[i]=query(words[i]);
         }
         return v;
    }
    
    int  query(string s){
        int count=0;
        int q=0;
        for(int i=0;i<s.size();i++){
            int k=s[i]-'a';
            if(a[q][k]==0)break;
            q=a[q][k];
            count+=sum[q];
        }
        return count;
    }

    void insert(string s){
        int q=0;
        for(int i=0;i<s.size();i++){
           int k=s[i]-'a';
           if(a[q][k]==0)a[q][k]=++index;
           q=a[q][k];
           sum[q]++;
        }
    }
};··
```



## 一、头文件

//解决爆栈，手动加栈，必须放在头文件之前
#pragma comment(linker,"/STACK:1024000000,1024000000") 

//万能头文件，部分比赛中可能不让用
#include <bits/stdc++.h> //C++

//STL专用，使用了哪种数据结构，就要用到哪种头文件
#include <map> //C++
#include <vector> //C++
#include <set> //C++

//C++必备头文件，cin、cout及其相关函数在这里
#include <isotream> //C++

//strlen()、strcat()等字符串操作函数在这里
#include <cstring> //C++
#include <string.h> //C语言

//min()、max()等在这里
#include <cstdlib> //C++
#include <stdlib.h> //C语言

//scanf()、printf()以及和它们长得像的函数在这里
#include <cstdio> //C++
#include <stdio.h> //C语言

//sort()在这里
#include <algorithm>> //C++

//log()、sin()、pow()等数学运算的函数在这里
#include <cmath>> //C++
#include <math.h> //C语言





## 二、stl基础

![微信截图_20220825162003](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220825162003.png)



### 1、基本构成

![微信截图_20220825162753](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220825162753.png)

![微信截图_20220825163309](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220825163309.png)



### 2、for循环

![微信截图_20220825164835](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220825164835.png)



### 3、基本容器

![微信截图_20220825165313](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220825165313.png)

![微信截图_20220825165650](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220825165650.png)

![微信截图_20220825165925](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220825165925.png)

![微信截图_20220825173019](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220825173019.png)

![微信截图_20220825174628](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220825174628.png)

![微信截图_20220825174657](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220825174657.png)

![微信截图_20220825174810](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220825174810.png)



## 三、详细

### 1、map

遍历：

for(auto t:map)

t.first  ->key

t.second ->value



2、查询元素

m.count(x)  如果为0就是不存在



3、排序

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220919002108.png)





### 2、pair<int,int> 

定义键值对，在搜索时候经常用





### 3、set

c++中的set是默认排序的

同时set,begin取出头元素的指针

如果要用值加上*(set.begin())

尾元素 end()

删除 :  s.erase(index)值  不是下表



### 4、字符串

#### 读取

char a[10];

sacnf("%s",a+1);

从第一个位置开始读入，方便操作



#### 包含

一个字符串是否包含另一个字符串

(s + s).find(goal) != string::npos;  包含

或者  s.find(w)== 0  是包括查找w在s中的位置

#### 字符串和整数转换

to_string(num);

stoi(string）

stoll(string)

此函数将在函数调用中作为参数提供的字符串转换为long long int。它解析str并将其内容解释为指定基数的整数，并将其作为long long int类型的值返回。

#### 排序

```
 string s(str.rbegin(),str.rend());  降序
```





#### 删除

s.erase(a,b)从a开始 删除b个元素



#### 截取

substr(size_type _Off = 0,size_type _Count = npos)
一种构造string的方法
形式 ： s.substr(pos, len)
返回值： string，包含s中从pos开始的len个字符的拷贝（pos的默认值是0，len的默认值是s.size() - pos，即不加参数会默认拷贝整个s）
异常 ：若pos的值超过了string的大小，则substr函数会抛出一个out_of_range异常；若pos+n的值超过了string的大小，则substr会调整n的值，只拷贝到string的末尾



### 插入

s.insert(a,s2)  在s的a位置前插入s2字符串







### **6、堆**

 //定义小顶堆  priority_queue<int,vector<int>,greater<int>>heap;

结构体：

大顶堆

```cpp
#include<iostream>
#include<cstring>
#include<algorithm>
#include<vector>
#include<cmath>
#include<map>
#include<queue>
using namespace std;
typedef struct Edge
{
    int a,b,w;
     bool operator< (const  Edge &W)const
    {
        return w > W.w;
    }
}e;
int main(){
  priority_queue<e,vector<e>>heap;
  
  return 0;
}
```









### 7、vector

####  7.1排序

rbegin()   rend()从大到小

```cpp
sort默认排序从小到大，使用greater<int>()

        #include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

        int main() {
        int a[] = {8,6,2,9,3,5,4,1,7,10};
        vector<int> arr(a, a+5);
        sort(arr.begin(),arr.end(),greater<int>());
        for(int i = 0; i <arr.size(); ++i){
        cout <<arr[i] << " ";
        }
        return 0 ;
        }

        方法二：自定义函数
        #include <iostream>
         #include <vector>
         #include <algorithm>
         using namespace std;

        bool cmp_max(int x,int y){
              return x > y;
        }

        int main() {
        int a[] = {8,6,2,9,3,5,4,1,7,10};
        vector<int> arr(a, a+5);
        sort(arr.begin(),arr.end(),cmp_max);
        for(int i = 0; i <arr.size(); ++i){
             cout <<arr[i] << " ";
        }
        return 0 ;
        }
```



#### 7.2 二维

 vector<vector<int>>a(m,vector<int>(n));



#### 7.3 插入

插入某个位置

v.insert(v.begin()+数字，插入数字)

插入前面后面

push_back        push_front    



#### 7.4删除

pop_back   pop_front

begin()     end()  

删除

 v.erase(v.begin()+1);   删除第几个元素

v.erase(v.begin()+1,v.begin()+2)  左闭右开

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220919224727.png)



emplace_back()

该函数是 [C++](http://c.biancheng.net/cplus/) 11 新增加的，其功能和 push_back() 相同，都是在 vector 容器的尾部添加一个元素。









### 8、比较器

比较器就行了

和java一样

```cPP
class Solution {

    public:
    static bool cmp(vector<int>v1,vector<int>v2){
        if(v1[0]!=v2[0])return v1[0]>v2[0];
        return v1[1]<v2[1];
    }
    vector<vector<int>> reconstructQueue(vector<vector<int>>& people) {
        sort(people.begin(),people.end(),cmp);
        vector<vector<int>>v;
        for(auto&t:people){
            v.insert(v.begin()+t[1],t);
        }
        return v;
    }
};
```





看代码是什么内容 比较器套上一些结构

```c++
  struct node{
       bool operator()(ListNode* x, ListNode* y) const {
        return x->val > y->val;
      }
  };
    ListNode* mergeKLists(vector<ListNode*>& lists) {
       priority_queue<ListNode*,vector<ListNode*>,node>heap;
       return NULL;
    }
```



或者这样子

```c++
auto compare = [](ListNode* x, ListNode* y) {
    return x->val > y->val;
};
std::priority_queue<ListNode*, std::vector<ListNode*>, decltype(compare)> heap(compare);

```





二维数组排序

```cpp
sort(nums1.rbegin(),nums1.rend());
    sort(v.begin(),v.end(),[&](vector<int>&h1,vector<int>&h2){
    return h1[0]>h2[0];
}
```



简介代码自定义比较器

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220919002841.png)





结构体排序

```cpp
struct Edge
{
    int a,b,w;

     bool operator< (const Edge &W)const
    {
        return w < W.w;
    }
}edges[N];
```



Java的

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220919003241.png)



### 9、常用函数

 **memset(st, false, sizeof st);**

初始化



**earse**

前面的文章中提到过如何向容器中添加元素，这里介绍一个如何删除容器中元素的函数，包括顺序容器和关联容器。

就是这个erase函数，基本用法如下：

c.erase( p)------------------------------从c中删除迭代器p指定的元素，p必须指向c中的一个真实元素，不能等于c.end()

c.erase(b,e)----------------------------从c中删除迭代器对b和e所表示的范围中的元素，返回e

具体用法如下：

vector<string> e = {"a","b","c","d","e","f","g"};
e.erase("c");        //删除字符串“c”
auto it = e.end()-1;  //.end()指向末尾的后一个元素，因此需要-1，指向末尾元素    
e.erase(it);           //删除末尾元素“e”
auto it2 = e.begin()+1;
auto it3 = e.end()-2;
e.erase(it2,it3);    //删除it2到it3之间的元素



字符串里面是指定开始位置和长度



**reverse(a.begin(),a.end)  反转函数**









  **next_permutation(v.begin(),v.end());**

全排列函数







### 10、multiset

>multiset是有序的，begin返回第一个元素，end返回集合尾部之后的位置，rbegin返回集合最后一个位置

```cpp
class Solution {
public:
    long long continuousSubarrays(vector<int>& nums) {
        long long ans = 0;
        multiset<int> s;
        int left = 0, n = nums.size();
        for (int right = 0; right < n; right++) {
            s.insert(nums[right]);
            while (*s.rbegin() - *s.begin() > 2)
                s.erase(s.find(nums[left++]));
            ans += right - left + 1;
        }
        return ans;
    }
};
```



>可以用lower_bond找出大于等于某个数的第一个元素，
>upper是大于
>*pre是上一个元素 可以找出小于等于某个数的最大元素

```cpp
class Solution {
public:
    int minAbsoluteDifference(vector<int>& nums, int x) {
        if (x == 0) return 0;
        int n = nums.size();
        multiset<int> ms;
        for (int i = x; i < n; i++) ms.insert(nums[i]);

        int ans = 1e9;
        for (int i = 0; i < n; i++) {
            // 用 multiset.lower_bound 找出两个目标整数
            auto it = ms.lower_bound(nums[i]);
            if (it != ms.end()) ans = min(ans, *it - nums[i]);
            if (it != ms.begin()) ans = min(ans, nums[i] - *prev(it));
            // 滑动窗口向右移动一格
            if (i + x < n) ms.erase(ms.find(nums[i + x]));
            if (i + 1 - x >= 0) ms.insert(nums[i + 1 - x]);
        }
        return ans;

    }
};
```

