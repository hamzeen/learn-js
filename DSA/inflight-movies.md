```java
package com.hamzeen;

import java.util.Arrays;
import java.util.HashMap;

// https://www.geeksforgeeks.org/amazon-interview-experience-sde-2-10/
// https://leetcode.com/discuss/interview-question/313719/Amazon-or-Online-Assessment-2019-or-Movies-on-Flight
// Sort + Two pointer solution
// Time: O(nlogn)
// Space: O(1)
public class InFlightMovies {

	static void merge(int arr[], int beg, int mid, int end)  {  

		int l = mid - beg + 1;  
		int r = end - mid;  

		int[] LeftArray = new int [l];  
		int[] RightArray = new int [r];  

		for (int i=0; i<l; ++i)  
			LeftArray[i] = arr[beg + i];  

		for (int j=0; j<r; ++j)  
			RightArray[j] = arr[mid + 1+ j];  


		int i = 0, j = 0;  
		int k = beg;  
		while (i<l&&j<r)  
		{  
			if (LeftArray[i] <= RightArray[j])  
			{  
				arr[k] = LeftArray[i];  
				i++;  
			}  
			else  
			{  
				arr[k] = RightArray[j];  
				j++;  
			}  
			k++;  
		}  
		while (i<l)  {  
			arr[k] = LeftArray[i];  
			i++;  
			k++;  
		}  

		while (j<r)  {  
			arr[k] = RightArray[j];  
			j++;  
			k++;  
		}  
	}

	public static void sort(int arr[], int beg, int end) {
		if (beg < end) {
			int mid = (beg + end) / 2;
			sort(arr, beg, mid);
			sort(arr, mid + 1, end);
			merge(arr, beg, mid, end);
		}
	}
	
    public static int[] findMovies(int[] list, int duration) {
        HashMap<Integer, Integer> mapByLength = new HashMap<>(list.length);
        int[] aryResult = new int[] {-1, -1};
        
        for (int i = 0; i < list.length; i++) {
        	mapByLength.put(list[i], i);
        }
        sort(list, 0, list.length-1);

        int l = 0, r = list.length -1;
        int max = 0;
        while (l < r) {

        	if(list[l] + list[r] > duration) {
                r--;
            } else {

            	if (list[l] + list[r] > max) {
                	max = list[l] + list[r];
                	int idxLeft = mapByLength.get(list[l]);
                	int idxRight = mapByLength.get(list[r]);

                	if (idxLeft > idxRight) {
                		aryResult[0] = idxRight;
                		aryResult[1] = idxLeft;
                	} else {
                		aryResult[0] = idxLeft;
                		aryResult[1] = idxRight;
                	}
                }
                l++;
            }
        }
        return aryResult;
    }

	public static void main(String args[])  {
        System.out.println(Arrays.toString(findMovies(new int[]{90, 85, 75, 60, 120, 150, 125}, 250)));
        System.out.println(Arrays.toString(findMovies(new int[]{1, 10, 25, 35, 60}, 90)));
        System.out.println(Arrays.toString(findMovies(new int[]{27, 1, 10, 39, 12, 76}, 77)));
        System.out.println(Arrays.toString(findMovies(new int[]{10, 1, 39, 76}, 77)));
        System.out.println(Arrays.toString(findMovies(new int[]{27, 1, 10, 39, 12, 52, 32, 67, 76}, 77)));
	}
}
```