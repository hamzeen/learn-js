```java
package com.hamzeen;

import java.util.ArrayList;
import java.util.HashMap;
import java.util.HashSet;
import java.util.List;
import java.util.Map;
import java.util.Set;

/**
 * Given a string s, and a const k, return all substrings of length k such that there are k-1 distinct characters in each substring.
 * All possible substrings of length k from the given string are [awag, wagl, aglk]. And only "awag" has k-1 distinct characters.
 * Question URL: https://leetcode.com/discuss/interview-question/783947/amazon-oa-sde-1-aug-2020
 */
public class UniqueSubstrings {
	static List<String> solve(String str, int k) {

	        int low = 0;
	        int high = 0;
	        Map<Character, Integer> map = new HashMap<>();
	        Set<String> ans = new HashSet<>();
	        while (high < str.length()) {
	            char sh = str.charAt(high);
	            map.put(sh, map.getOrDefault(sh, 0) + 1);

	            if (high + 1 - low == k) {

	                if (map.size() == k-1) {
	                    ans.add(str.substring(low, high+1));
	                }
	                map.put(str.charAt(low), map.getOrDefault(str.charAt(low), 0) - 1);

	                if (map.get(str.charAt(low)) <= 0) {
	                    map.remove(str.charAt(low));
	                }
	                low++;
	            }
	            high++;
	        }
	        return new ArrayList<String>(ans);
	}

	// Driver Program
	public static void main(String[] args) {
		System.out.println(solve("awaglk", 4)); // 'awag'
		
	}
}

```
