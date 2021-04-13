1. clarification

什么是字母异位词,是否考虑大小写?

2. possible solution.

* 暴力,sort,sorted_str 相等? O(NlongN)

* Hash map-> 来统计每个字母的频次 

3. Code

```java
public boolean isAnagram(String s, String t) {
    if (s.length() != t.length()) {
        return false;
    }
    int[] count = new int[26];
    for (int i = 0; i < s.length(); i++) {
        count[s.charAt(i) - 'a']++;
        count[t.charAt(i) - 'a']--;
    }
    for (int i : count) {
        if (i != 0) {
            return false;
        }
    }
    return true;
}
```



同类题

https://leetcode.com/problems/group-anagrams/

```
public List<List<String>> groupAnagrams(String[] strs) {
    if(strs == null || strs.length ==0 ) return new ArrayList<>();
    Map<String,List<String>> map  = new HashMap<>();
    for (String s : strs) {
        char[] ca = s.toCharArray();
        Arrays.sort(ca);
        String keyStr = String.valueOf(ca);
        if(!map.containsKey(keyStr)) map.put(keyStr,new ArrayList<String>());
        map.get(keyStr).add(s);
    }
    return new ArrayList<>(map.values());
}

Instead of sorting, we can also build the key string in this way. Thanks @davidluoyes for pointing this out.

    public List<List<String>> groupAnagrams(String[] strs) {
        if (strs == null || strs.length == 0) return new ArrayList<>();
        Map<String, List<String>> map = new HashMap<>();
        for (String s : strs) {
            char[] ca = new char[26];
            for (char c : s.toCharArray()) ca[c - 'a']++;
            String keyStr = String.valueOf(ca);
            if (!map.containsKey(keyStr)) map.put(keyStr, new ArrayList<>());
            map.get(keyStr).add(s);
        }
        return new ArrayList<>(map.values());
    }
```

