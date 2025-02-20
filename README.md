# Leetcode-1980

# C++ (2^N)
class Solution {
public:
    string ans;
    void func(string a,map<string,int>mp,int n)
    {
        if(ans.length())return;
        if(a.length()==n)
        {
            if(!mp[a])
            ans=a;
            return ;
        }
        for(int i=0;i<2;i++)
        {
            a+=char(i+48);
            func(a,mp,n);
            a.pop_back();
        }
        return;
    }
    string findDifferentBinaryString(vector<string>& nums) {
       int n=nums.size();
       string a="";
       map<string,int>mp;
       for(int i=0;i<n;i++)
       {
        mp[nums[i]]=1;
       }
       func(a,mp,n);
       return ans;
    }
};

# C++ (N)

class Solution {
public:
    string findDifferentBinaryString(vector<string>& nums) {
       int n=nums.size();
       string a="";
       for(int i=0;i<n;i++)
       {
         a+=(nums[i][i]=='0'?"1":"0");
       }
       return a;
    }
};

# Python

class Solution:
    def __init__(self):
        self.ans = ""

    def func(self, a, mp, n):
        if self.ans:
            return
        if len(a) == n:
            if a not in mp:
                self.ans = a
            return
        
        for i in range(2):
            self.func(a + str(i), mp, n)

    def findDifferentBinaryString(self, nums):
        n = len(nums)
        mp = set(nums)  # Using set for efficient lookup
        self.ans = ""
        self.func("", mp, n)
        return self.ans

# Java

import java.util.HashSet;
import java.util.Set;

class Solution {
    private String ans = "";

    private void func(String a, Set<String> mp, int n) {
        if (!ans.isEmpty()) return;
        if (a.length() == n) {
            if (!mp.contains(a)) {
                ans = a;
            }
            return;
        }
        for (int i = 0; i < 2; i++) {
            func(a + i, mp, n);
        }
    }

    public String findDifferentBinaryString(String[] nums) {
        int n = nums.length;
        Set<String> mp = new HashSet<>();
        for (String num : nums) {
            mp.add(num);
        }
        ans = "";
        func("", mp, n);
        return ans;
    }
}
