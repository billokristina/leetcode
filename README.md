# репозиторий для публикации моих решений задач с платформы leetcode

## содержание
 - [2235. Add Two Integers](#2235-add-two-integers)
 - [27. Remove Element](#27-remove-element)
 - [26. Remove Duplicates from Sorted Array](#26-remove-duplicates-from-sorted-array)
 - [80. Remove Duplicates from Sorted Array II](#80-remove-duplicates-from-sorted-array-ii)
 - [189. Rotate Array](#189-rotate-array)
 - [28. Find the Index of the First Occurrence in a String](#28-find-the-index-of-the-first-occurrence-in-a-string)
 - [14. Longest Common Prefix](#14-longest-common-prefix)
 - [58. Length of Last Word](#58-length-of-last-word)
 - [387. First Unique Character in a String](#387-first-unique-character-in-a-string)
 - [383. Ransom Note](#383-ransom-note)
 - [344. Reverse String](#344-reverse-string)
 - [151. Reverse Words in a String](#151-reverse-words-in-a-string)
 - [2769. Find the Maximum Achievable Number](#2769-find-the-maximum-achievable-number)
 - [2798. Number of Employees Who Met the Target](#2798-number-of-employees-who-met-the-target)
 - [9. Palindrome Number](#9-palindrome-number)
 - [3136. Valid Word](#3136-valid-word)
 - [35. Search Insert Position](#35-search-insert-position)
 - [66. Plus One](#66-plus-one)
 - [69. Sqrt(x)](#69-sqrtx)
 - [88. Merge Sorted Array](#88-merge-sorted-array)
 - [1672. Richest Customer Wealth](#1672-richest-customer-wealth)
 - [412. Fizz Buzz](#412-fizz-buzz)
 - [136. Single Number](#136-single-number)

## [2235. Add Two Integers](https://leetcode.com/problems/add-two-integers/description/)
```c
int sum(int num1, int num2) {
    return num1+num2;
}
```

## [27. Remove Element](https://leetcode.com/problems/remove-element/description/)
```c
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
```c
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
```c
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
```c
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
```c
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
```c
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

## [58. Length of Last Word](https://leetcode.com/problems/length-of-last-word/description/)
```c
int lengthOfLastWord(char* s) {
    int length = 0;
    int i = strlen(s) - 1;
    
    while (i >= 0 && s[i] == ' ') {
        i--;
    }

    while (i >= 0 && s[i] != ' ') {
        length++;
        i--;
    }
    
    return length;
}
```

## [387. First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/description/)
```c
int firstUniqChar(char* s) {
    int count[26] = {0};
    
    for (int i = 0; s[i] != '\0'; i++) {
        count[s[i] - 'a']++;
    }

    for (int i = 0; s[i] != '\0'; i++) {
        if (count[s[i] - 'a'] == 1) {
            return i;
        }
    }
    
    return -1;
}
```

## [383. Ransom Note](https://leetcode.com/problems/ransom-note/description/)
```c
bool canConstruct(char* ransomNote, char* magazine) {
    int alph[26]= {0};
    int len1 = strlen(ransomNote);
    int len2 = strlen(magazine);

    if(len1>len2)
        return false;
    
    for (int i = 0; i<len2; i++){
        alph[magazine[i]-97]++;
    }
    for (int i = 0; i<len1; i++){
        alph[ransomNote[i]-97]--;
        if (alph[ransomNote[i]-97]<0){
            return false;
        }
    }
    return true;
}
```

## [344. Reverse String](https://leetcode.com/problems/reverse-string/description/)
```c
void reverseString(char* s, int sSize) {
    int left = 0;
    int right = sSize - 1;
    
    while (left < right) {
        char temp = s[left];
        s[left] = s[right];
        s[right] = temp;
        
        left++;
        right--;
    }
}
```

## [151. Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/description/)
```c
char* reverseWords(char* s) {
    int len = strlen(s);
    if (len == 0) return s;
    
    char** words = (char**)malloc(len * sizeof(char*));
    int word_count = 0;
    
    int i = 0;
    while (i < len) {
        while (i < len && s[i] == ' ') i++;
        
        if (i >= len) break;
        
        int start = i;

        while (i < len && s[i] != ' ') i++;
        
        int word_len = i - start;
        words[word_count] = (char*)malloc((word_len + 1) * sizeof(char));
        strncpy(words[word_count], s + start, word_len);
        words[word_count][word_len] = '\0';
        word_count++;
    }
    
    if (word_count == 0) {
        free(words);
        char* result = (char*)malloc(1 * sizeof(char));
        result[0] = '\0';
        return result;
    }
    
    int total_len = 0;
    for (int i = 0; i < word_count; i++) {
        total_len += strlen(words[i]);
        if (i < word_count - 1) total_len += 1;
    }
    
    char* result = (char*)malloc((total_len + 1) * sizeof(char));
    int pos = 0;
    
    for (int i = word_count - 1; i >= 0; i--) {
        int word_len = strlen(words[i]);
        strncpy(result + pos, words[i], word_len);
        pos += word_len;
        if (i > 0) {
            result[pos] = ' ';
            pos++;
        }
    }
    result[pos] = '\0';
    
    for (int i = 0; i < word_count; i++) {
        free(words[i]);
    }
    free(words);
    
    return result;
}
```

## [2769. Find the Maximum Achievable Number](https://leetcode.com/problems/find-the-maximum-achievable-number/description/)
```c
int theMaximumAchievableX(int num, int t) {
    return num + 2 * t;
}
```

## [2798. Number of Employees Who Met the Target](https://leetcode.com/problems/number-of-employees-who-met-the-target/description/)
```c
int numberOfEmployeesWhoMetTarget(int* hours, int hoursSize, int target) {
    int count = 0;
    for (int i = 0; i < hoursSize; i++) {
        if (hours[i] >= target) {
            count++;
        }
    }
    return count;
}
```

## [9. Palindrome Number](https://leetcode.com/problems/palindrome-number/description/)
```c
bool isPalindrome(int x) {
    if (x < 0) {
        return false;
    }
    
    if (x != 0 && x % 10 == 0) {
        return false;
    }
    
    int reversed = 0;
    int original = x;
    
    while (x > reversed) {
        reversed = reversed * 10 + x % 10;
        x /= 10;
    }
    
    return x == reversed || x == reversed / 10;
}
```

## [3136. Valid Word](https://leetcode.com/problems/valid-word/description/)
```c
bool isValid(char* word) {
    int length = 0;
    bool has_vowel = false;
    bool has_consonant = false;
    bool has_valid_chars = true;

    for (int i = 0; word[i] != '\0'; i++) {
        char c = word[i];
        length++;

        if (!(isdigit(c) || isalpha(c))) {
            has_valid_chars = false;
        }

        if (isalpha(c)) {
            char lower_c = tolower(c);
            if (lower_c == 'a' || lower_c == 'e' || lower_c == 'i' || lower_c == 'o' || lower_c == 'u') {
                has_vowel = true;
            } else {
                has_consonant = true;
            }
        }
    }

    if (length >= 3 && has_vowel && has_consonant && has_valid_chars) {
        return true;
    } else {
        return false;
    }
}
```

## [35. Search Insert Position](https://leetcode.com/problems/search-insert-position/description/)
```c
int searchInsert(int* nums, int numsSize, int target) {
    int left = 0;
    int right = numsSize - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        
        if (nums[mid] == target) {
            return mid;
        } else if (nums[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return left;
}
```

## [66. Plus One](https://leetcode.com/problems/plus-one/)
```c
int* plusOne(int* digits, int digitsSize, int* returnSize) {
    for (int i = digitsSize - 1; i >= 0; i--) {
        if (digits[i] < 9) {
            digits[i]++;
            *returnSize = digitsSize;
            int* result = malloc(digitsSize * sizeof(int));
            memcpy(result, digits, digitsSize * sizeof(int));
            return result;
        }
        digits[i] = 0;
    }
    
    *returnSize = digitsSize + 1;
    int* result = malloc((digitsSize + 1) * sizeof(int));
    result[0] = 1;
    for (int i = 1; i < digitsSize + 1; i++) {
        result[i] = 0;
    }
    return result;
}
```

## [69. Sqrt(x)](https://leetcode.com/problems/sqrtx/description/)
```c
int mySqrt(int x) {
    if (x == 0)
        return x;
    for (long long i = 0; i <= x; i++)
    {
        if ((i * i) > x)
            return i - 1;
        if ((i * i) == x)
            return i;
    }
    return x;
}
```

## [88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)
```c
void merge(int* nums1, int nums1Size, int m, int* nums2, int nums2Size, int n) {
    int i = m - 1;
    int j = n - 1;
    int k = m + n - 1;

    while (i >= 0 && j >= 0) {
        if (nums1[i] > nums2[j]) {
            nums1[k--] = nums1[i--];
        } else {
            nums1[k--] = nums2[j--];
        }
    }

    while (j >= 0) {
        nums1[k--] = nums2[j--];
    }
}
```

## [1672. Richest Customer Wealth](https://leetcode.com/problems/richest-customer-wealth/description/)
```c
int maximumWealth(int** accounts, int accountsSize, int* accountsColSize) {
    int max = -1;
    for (int i = 0; i < accountsSize; i++)
    {
        int sum = 0;
        for (int j = 0; j < accountsColSize[i]; j++)
        {
            sum += accounts[i][j];
        }
        if (sum > max)
            max = sum;
    }
    return max;
}
```

## [412. Fizz Buzz](https://leetcode.com/problems/fizz-buzz/description/)
```c
char** fizzBuzz(int n, int* returnSize) {
    char** answer = (char**)malloc(n * sizeof(char*));
    *returnSize = n;

    for (int i = 1; i <= n; i++) {
        if (i % 3 == 0 && i % 5 == 0) {
            answer[i - 1] = strdup("FizzBuzz");
        } else if (i % 3 == 0) {
            answer[i - 1] = strdup("Fizz");
        } else if (i % 5 == 0) {
            answer[i - 1] = strdup("Buzz");
        } else {
            answer[i - 1] = (char*)malloc(12 * sizeof(char));
            sprintf(answer[i - 1], "%d", i);
        }
    }

    return answer;
}
```

## [136. Single Number](https://leetcode.com/problems/single-number/description/)
```c
int singleNumber(int* nums, int numsSize) {
    int result = 0;
    for (int i = 0; i < numsSize; i++)
    {
        result ^= nums[i];
    }
    return result;
}
```