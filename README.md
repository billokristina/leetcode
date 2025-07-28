# репозиторий для публикации моих решений задач с платформы leetcode

## содержание
 - [2235. Add Two Integers](#2235-add-two-integers)
 - [27. Remove Element](#27-remove-element)
 - [26. Remove Duplicates from Sorted Array](#26-remove-duplicates-from-sorted-array)
 - [80. Remove Duplicates from Sorted Array II](#80-remove-duplicates-from-sorted-array-ii)
 - [189. Rotate Array](#189-rotate-array)
 - [28. Find the Index of the First Occurrence in a String](#28-find-the-index-of-the-first-occurrence-in-a-string)
 - [14. Longest Common Prefix](#14-longest-common-prefix)

## [2235. Add Two Integers](https://leetcode.com/problems/add-two-integers/description/)
```
int sum(int num1, int num2) {
    return num1+num2;
}
```

## [27. Remove Element](https://leetcode.com/problems/remove-element/description/)
```
int removeElement(int* nums, int numsSize, int val) {
    int k = 0;

    for (int i = 0; i < numsSize; i++) {
        if (nums[i] != val) {
            nums[k] = nums[i];
            k++;
        }
    }

    return k;
}
```

## [26. Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/)
```
int removeDuplicates(int* nums, int numsSize) {
        if (numsSize == 0) return 0;

    int k = 1;
    
    for (int i = 1; i < numsSize; i++) {
        if (nums[i] != nums[i - 1]) {
            nums[k] = nums[i];
            k++;
        }
    }
    
    return k;
}
```

## [80. Remove Duplicates from Sorted Array II](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/description/)
```
int removeDuplicates(int* nums, int numsSize) {
        if (numsSize <= 2) {
        return numsSize;
    }

    int k = 2;

    for (int i = 2; i < numsSize; i++) {
        if (nums[i] != nums[k - 2]) {
            nums[k] = nums[i];
            k++;
        }
    }

    return k;
}
```

## [189. Rotate Array](https://leetcode.com/problems/rotate-array/description/)
```
void rotate(int* nums, int numsSize, int k) {
    k = k % numsSize;
    if (k == 0) return;

    int temp[k];
    for (int i = 0; i < k; i++) {
        temp[i] = nums[numsSize - k + i];
    }

    for (int i = numsSize - 1; i >= k; i--) {
        nums[i] = nums[i - k];
    }

    for (int i = 0; i < k; i++) {
        nums[i] = temp[i];
    }
}
```

## [28. Find the Index of the First Occurrence in a String](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/description/)
```
int strStr(char* haystack, char* needle) {
    if (*needle == '\0') {
        return 0;
    }
    
    int haystack_len = strlen(haystack);
    int needle_len = strlen(needle);
    

    if (needle_len > haystack_len) {
        return -1;
    }
    

    for (int i = 0; i <= haystack_len - needle_len; i++) {
        int j;

        for (j = 0; j < needle_len; j++) {
            if (haystack[i + j] != needle[j]) {
                break;
            }
        }

        if (j == needle_len) {
            return i;
        }
    }
    
    return -1;
}
```
## [14. Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/description/)
```
char* longestCommonPrefix(char** strs, int strsSize) {
        if (strsSize == 0) return "";
    
    char* first = strs[0];
    int prefixLen = strlen(first);

    for (int i = 1; i < strsSize; i++) {
        char* current = strs[i];
        int j = 0;

        while (j < prefixLen && current[j] != '\0' && first[j] == current[j]) {
            j++;
        }
        
      
        prefixLen = j;
        
      
        if (prefixLen == 0) break;
    }
    
    char* result = (char*)malloc(prefixLen + 1);  
    if (prefixLen > 0) {
        strncpy(result, first, prefixLen);
    }
    result[prefixLen] = '\0';  
    return result;
}
```