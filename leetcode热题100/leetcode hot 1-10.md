# 49

![](<leetcode hot 1-10_md_files/ae6a3d30-bcb3-11ee-b120-bbdd045c73c5_20240127093040.jpeg?v=1\&type=image\&token=V1%3Au9wnVqAcsS_xvsSM8qSgHXBTj3uXgcxhFwhpk5kzHJA>)

```C++
class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        unordered_map<string,vector<string>> h;
        for(auto str:strs){
           string nstr=str;
           sort(nstr.begin(),nstr.end());
           h[nstr].push_back(str);
        }
        vector<vector<string>> res;
       for(auto x:h){res.push_back(x.second);}
      return res;

    }
};
```





# 438

```C
class Solution {
public:
    vector<int> findAnagrams(string s, string p) {
        vector<int> v;
               for(int i=0;i<s.size();i++){
                string  nstr=s.substr(i,p.size());  --->string.substr(开始位置，长度)
                sort(nstr.begin(),nstr.end());
                
                if(nstr==p)  v.push_back(i);


               }
               return v;
    }
};
```

