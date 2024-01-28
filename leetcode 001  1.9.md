1# a+b\=k

```C++
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map <int,int> h;
        for(int i=0;i<nums.size();i++){
            int r=target-nums[i];
               if(h.count(r))  return{i,h[r]};   key:nums[i]--->value:i
               h[nums[i]]=i;
        }
        return {};
    }
```

vector\<int> arr(2);--->vector定义

unordered\_map\<string, int> h; --->哈希表定义

cout(r) --->哈希表中有这种key便为true

#### 7.5 unordered\_map查找操作

find(key); //查找键key是否存在,若存在，返回该键的元素的迭代器；/若不存在，返回map.end();

count(keyElem); //返回容器中==key==为keyElem的对组个数 【1或0】。





2# 链表转加法  --->模拟加法运算

```
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        auto dummy = new ListNode(-1), cur = dummy;
        int t = 0;
        while (l1 || l2 || t) {   ---》二者又不为空 或者还有进位未处理
            if (l1) t += l1->val, l1 = l1->next;
            if (l2) t += l2->val, l2 = l2->next;
            cur = cur->next = new ListNode(t % 10);
            t /= 10;   ----->t是向高位的进位
        }
        return dummy->next;
    }

```

new动态申请空间

//变量 int\* p \= new int(5);   //注意申请简单变量，也必须使用指针形式

delete p;              //释放空间

&#x20;p\= NULL;              //让指针指向空指针，杜绝野地址&#x20;

//一维数组 int\* p \= new int\[5];

delete \[]p;            //释放空间,记住与变量不同&#x20;

p\= NULL;&#x20;

//二维数组
int (\*pl)\[4]              //必须点明列大小
pl \= new int\[3]\[4];

delete \[]pl; pl \= NULL; &#x20;





3# 最长不重复字符**子串/最长重复字符**子串

    最长重复子串 AcWing 771
        int key=0,max=0;
    for(int i=0,j=0;str[i];i++){
        while(str[i]==str[j]&&str[j]){j++;} --->j指针i后向后
         if(j-i>max){max=j-i;key=i;}
        i=j-1;
    }
    cout<<str[key]<<" "<<max<<endl;


    最长不重复子串 leetcode 3
            
            unordered_map <char,int> h;
            int res=0;
           for(int i=0,j=0;i<s.size();i++){
               h[s[i]]++;
               while(h[s[i]]>1){ ------>前面若有和s【i】相同的 j向后直到没有为止
                        h[s[j++]]--;}; ------>j指针i前向后
               int r=i-j+1;
               res=max(res,r);
           }
           return res;

5# 最长回文串

![](day1_md_files/527d9b70-aef8-11ee-800b-fdd4454286b2_20240109220645.jpeg?v=1\&type=image\&token=V1%3AgNz8Si2uBJvkIKTgOGrLn4bliPMUWxuqwh-8XfStFOk)





7# 整数反转

![](day1_md_files/f4114900-aef8-11ee-800b-fdd4454286b2_20240109221116.jpeg?v=1\&type=image\&token=V1%3AgfMhc4Brm8wd7HoKc9Q8kfojXQnyOAYxVql-4YVkDrE)

用long long会溢出如何在计算中判断溢出？

如何取出一个整数的每一位？





9#  回文数

```C++
方案一：
        long long t=0;
         int a=x;
         while(x) t=x%10+t*10,x/=10;
         if(t==a&&a>=0) return true;
         else return false;

方案二：转化为字符串 反转后返回

bool isPalindrome(int x) {
        if (x < 0) return 0;
        string s = to_string(x);
        return s == string(s.rbegin(), s.rend());
    }
```

==atoi（string.c\_str()）; stoi（string）；== 字符串转化为整数，返回一个整数-----》去掉了负号

**to\_string(int x)     整数转化为字符串**--->返回一个string不改变x

string(s.rbegin(), s.rend());--->返回一个string

s \= string(s.rbegin(), s.rend());  ---》逆序遍历从尾到头遍历字符串 --》相当于反转并输出字符串
