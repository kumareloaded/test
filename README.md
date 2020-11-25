package com.sample.programs;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

public class DevTestIntegration {
	
	/*def formTeam(d, t, q):
	    ans = []
	    maxSize = max(q)
	    hMap = {i: 0 for i in range(0, maxSize+1)}
	    res = []
	    helper(res, d, t, d, t, maxSize, "", hMap)
	    for size in q:
	        ans.append(hMap[size])
	    return ans

	def helper(res, d, t, maxD, maxT, size, currPerm, hMap):
	    if size >= len(currPerm):
	        hMap[len(currPerm)] += 1
	    if size == len(currPerm):
	        res.append(currPerm)
	    else:
	        if currPerm == "" or d > 1:
	            helper(res, d - 1, maxT, maxD, maxT, size, currPerm+'D', hMap)
	        if currPerm == "" or t > 1:
	            helper(res, maxD, t - 1, maxD, maxT, size, currPerm + 'T', hMap)*/
	
	public static void main(String[] args) {
		long startTime = System.currentTimeMillis();
		System.out.println(formTeam(19,47,Arrays.asList(new Integer[] {
				29, 124, 77, 10, 28, 101, 78, 93, 15, 7, 106, 40, 65, 118, 98, 127, 53, 27, 83, 94, 34, 
				110, 70, 38, 5, 35, 61, 51, 72, 22, 81, 108, 67, 80, 18, 99, 63, 95, 23, 3, 88, 26, 75, 
				31, 2, 71, 9, 42, 114, 91, 66, 105, 112, 33, 20, 92, 85, 30, 62, 89, 16, 24, 1, 84,
				32/*
					 * , 123, 100, 57, 13, 90, 122, 73, 39, 116, 25, 37, 64, 113, 86, 8, 69, 87, 41,
					 * 59, 125, 79, 44, 126, 58, 48, 4, 47, 119, 36, 49, 111, 121, 52, 115, 56, 74,
					 * 43, 107
					 */})));
		long endTime = System.currentTimeMillis();
		System.out.println(endTime-startTime);
	}
	
	public static List<Integer> formTeam(int d, int t, List<Integer> q) {
		List<Integer> resultList = new ArrayList<>();
		
		int maxSize = Collections.max(q);
		
		Map<Integer, Integer> hMap = new HashMap<>();
		
		for(int i=0; i<=maxSize; i++) {
			hMap.put(i, 0);
		}
		
		List<String> results = new ArrayList<>();
		
		helper(results, d, t, d, t, maxSize, "", hMap);
		
		for(int size : q) {
			resultList.add(hMap.get(size));
		}
        
        return resultList;
    }

	private static void helper(List<String> results, int d, int t, int maxD, int maxT, int size, String currPerm,
			Map<Integer, Integer> hMap) {
		if (size >= (currPerm).length()) {
			hMap.put(currPerm.length(), hMap.get(currPerm.length())+1);
		}
	        
	    if (size == (currPerm).length())
	    	results.add(currPerm);
	    else {
	    	if (currPerm == "" || d > 1)
	            helper(results, d - 1, maxT, maxD, maxT, size, currPerm+'D', hMap);
	        if (currPerm == "" || t > 1)
	            helper(results, maxD, t - 1, maxD, maxT, size, currPerm + 'T', hMap);
	    }
	        
	}

}
