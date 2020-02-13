# 最长回文子串

## 回文串

回文串是正读和反读都相同的字符串

例如，"a"，"aba"，"abba"是回文串，而"abc"不是回文串。

### 判断回文串

回文串是一个对称串，因此判断回文串只需从首尾比较对称位置是否相等即可。

例题：

[leetcode-125. 验证回文串](https://leetcode-cn.com/problems/valid-palindrome/)

```.c
for(i=0,j=cvec.size()-1;i<j;i++,j--){
    if(cvec[i]!=cvec[j]){
        flag=false;
    }
}
flag=true;
```

### 求解最长回文子串

目的：寻找目标字符串中，所有连续子串中，是回文串且长度最长的子串长度，或者求回文子串个数。

用途：算法题、面试题中经常出现，但是并不清楚具体的用途。

### 暴力

枚举所有子串，判断是否回文串。

复杂度：$O(n^3)$

### 枚举中心

考虑暴力方法，我们发现其中有很多重复计算，比如，判断字符串str[i...j]是否为回文串，我们需要判断str[i+1...j-1]是否为回文串，而枚举到位置i+1时，我们会重复判断一次str[i+1...j-1]是否为回文串。

考虑枚举以每个位置为中心的最长回文串，枚举位置i，str[i-l,...,i,...,i+l]不是回文串，那么就不用再判断子串str[i-(l+1),...,i,...,i+(l+1)]，而如果str[i-l,...,i,...,i+l]时回文串，判断子串str[i-(l+1),...,i,...,i+(l+1)]是否为回文串，只需要判断str[i-(l+1)]是否等于str[i+(l+1)]。

复杂度：$O(n^2)$

例题：

统计回文子串个数

[leetcode-647. 回文子串](https://leetcode-cn.com/problems/palindromic-substrings/)

```.c
int n=s.length();
int ans=0;
for(int i=0;i<n;i++) {
    for(int j=0;j<n;j++) {
        if(i-j>=0&&i+j<n&&s[i-j]==s[i+j]) {
            ans++;
        } else {
            break;
        }
    }
}
for(int i=0;i<n-1;i++) {
    for(int j=0;j<n;j++) {
        if(i-j>=0&&i+j+1<n&&s[i-j]==s[i+j+1]) {
            ans++;
        } else {
            break;
        }
    }
}
return ans;
```

### 技巧
如上，求取回文子串需要分两种情况，一种回文串长度为奇数只有一个中心元素，一种是回文串长度为偶数，有两个中心元素。

在每个字符中间增加一个'#'，这样奇回文串，仍然是奇回文串，如"aba"->"#a#b#a#"，偶回文串，转化为了奇回文串，如"aa"->"#a#a#"，而原回文串的长度$n$，和新回文串长度$n'$，满足$n=\lfloor \frac{n}{2} \rfloor$

### 终极算法

虽然从中间位置枚举回文串，能够避免很多暴力枚举过程中的重复计算，但是通过回文串的性质，我们可以利用之前的中间结果，进一步提升算法效率。

假设对于每个位置i，以它为中心的最长回文串为，［i-f[i],...,i,...,i+f[i]]

例如，当前枚举到位置i+1，我们要求解f[i+1]，我们定义$right=\max\limits_{j=0}^i {j+f[j]}$，对应回文串中心定义为center，此时其实已经有了[i+1,right]这个之间的字符串信息，$f[i+1]>=min(0,right-(i+1),f[2*center-(i+1)])$，并且，如果right-(i+1)>f[2*center-(i+1)]，则f[i+1]=f[2*center-(i+1)]。

复杂度：$O(n)$。由于每次枚举，只有三种情况，f[i+1]<=right-(i+1)都是O(1)复杂度，而f[i+1]>right-(i+1)会更新right，最终right<=n，累计总操作数小于n。

例题：

[hiho-1032 : 最长回文子串](http://hihocoder.com/problemset/problem/1032)

```.c
center=0;
right=0;
A[t]='$';
for(i=1;i<t;i++)
{
    f[i]=0;
    if(i<right)
    {
        f[i]=min(right-i,f[2*center-i]);
    }
    while(A[i+f[i]+1]==A[i-f[i]-1])
        f[i]++;
    if(right<i+f[i])
    {
        right=i+f[i];
        center=i;
    }
    ans=max(ans,f[i]);
}
```