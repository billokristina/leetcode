# репозиторий для публикации моих решений задач с платформы leetcode

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

## [171. Excel Sheet Column Number](https://leetcode.com/problems/excel-sheet-column-number/submissions/1711065523/)
```c
int titleToNumber(char* columnTitle) {
    int result = 0;
    for (int i = 0; columnTitle[i] != '\0'; i++) {
        result = result * 26 + (columnTitle[i] - 'A' + 1);
    }
    return result;
}
```

## [168. Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/description/)
```c
char* convertToTitle(int columnNumber) {
    char* result = (char*)malloc(8 * sizeof(char));
    int index = 0;

    while (columnNumber > 0) {
        columnNumber--;
        int remainder = columnNumber % 26;
        result[index++] = 'A' + remainder;
        columnNumber /= 26;
    }
    result[index] = '\0';

    for (int i = 0; i < index / 2; i++) {
        char temp = result[i];
        result[i] = result[index - 1 - i];
        result[index - 1 - i] = temp;
    }

    return result;
}
```

## [268. Missing Number](https://leetcode.com/problems/missing-number/description/)
```c
int missingNumber(int* nums, int numsSize) {
    int expected_sum = numsSize * (numsSize + 1) / 2;
    
    int actual_sum = 0;
    for (int i = 0; i < numsSize; i++) {
        actual_sum += nums[i];
    }
    
    return expected_sum - actual_sum;
}
```

## [202. Happy Number]()
```c
bool isHappy(int n) {
    while (n != 1) {
        int sum = 0;
        while (n > 0) {
            int digit = n % 10;
            sum += digit * digit;
            n /= 10;
        }
        n = sum;

        if (n == 4) {
            return false;
        }
    }
    return true;
}
```

## [231. Power of Two]()
```c
bool isPowerOfTwo(int n) {
    if (n == 1)
        return true;
    long long res = 1;
    while (res < n){
        res *= 2;
        if(res == n)
            return true;
    }
    return false;
}
```

## [191. Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/description/)
```c
int hammingWeight(int n) {
    int count = 0;
    while (n != 0) {
        count += n & 1;
        n >>= 1;
    }
    return count;
}
```

## [283. Move Zeroes](https://leetcode.com/problems/move-zeroes/description/)
```c
void moveZeroes(int* nums, int numsSize) {
    int nonZeroIndex = 0;

    for (int i = 0; i < numsSize; i++) {
        if (nums[i] != 0) {
            nums[nonZeroIndex] = nums[i];
            nonZeroIndex++;
        }
    }

    for (int i = nonZeroIndex; i < numsSize; i++) {
        nums[i] = 0;
    }
}
```

## [367. Valid Perfect Square](https://leetcode.com/problems/valid-perfect-square/description/)
```c
bool isPerfectSquare(int num) {
    if (num < 1) return false;
    long left = 1, right = num;       
    while (left <= right) {
        long mid = left + (right - left) / 2;           
        long square = mid * mid;
        if (square == num) {
            return true;           
        } else if (square < num) {
            left = mid + 1;           
        } else {
            right = mid - 1;           
        }
    }
    return false;   
}
```

## [389. Find the Difference](https://leetcode.com/problems/find-the-difference/description/)
```c
char findTheDifference(char* s, char* t) {
    char result = 0;
    for (int i = 0; s[i] != '\0'; i++) {
        result ^= s[i];
    }
    for (int i = 0; t[i] != '\0'; i++) {
        result ^= t[i];
    }
    return result;
}
```

## [338. Counting Bits](https://leetcode.com/problems/counting-bits/description/)
```c
int* countBits(int n, int* returnSize) {
    int* ans = (int*)malloc((n + 1) * sizeof(int));
    *returnSize = n + 1;
    
    ans[0] = 0;
    
    for (int i = 1; i <= n; i++) {
        ans[i] = ans[i >> 1] + (i & 1);
    }
    
    return ans;
}
```

## [414. Third Maximum Number](https://leetcode.com/problems/third-maximum-number/description/)
```c
int thirdMax(int* nums, int numsSize) {
    long first = LONG_MIN, second = LONG_MIN, third = LONG_MIN;
    
    for (int i = 0; i < numsSize; i++) {
        int num = nums[i];
        
        if (num == first || num == second || num == third) {
            continue;
        }
        
        if (num > first) {
            third = second;
            second = first;
            first = num;
        } else if (num > second) {
            third = second;
            second = num;
        } else if (num > third) {
            third = num;
        }
    }
    
    if (third == LONG_MIN) {
        return first;
    } else {
        return third;
    }
}
```

## [434. Number of Segments in a String](https://leetcode.com/problems/number-of-segments-in-a-string/description/)
```c
int countSegments(char* s) {
    int count = 0;
    bool in_segment = false;      
    while (*s) {
        if (*s != ' ') {
            if (!in_segment) {
                count++;
                in_segment = true;
            }
        } else {
            in_segment = false;
        }
        s++;      
    }
    return count;
}
```

## [190. Reverse Bits](https://leetcode.com/problems/reverse-bits/description/)
```c
int reverseBits(int n) {
    int result = 0;
    for (int i = 0; i < 32; i++) {
        result <<= 1;
        result |= (n & 1);
        n >>= 1;
    }
    return result;
}
```

## [263. Ugly Number](https://leetcode.com/problems/ugly-number/description/)
```c
bool isUgly(int n) {
    if (n <= 0) {
        return false;
    }
    
    while (n % 2 == 0) {
        n /= 2;
    }
    
    while (n % 3 == 0) {
        n /= 3;
    }
    
    while (n % 5 == 0) {
        n /= 5;
    }
    
    return n == 1;
}
```

## [258. Add Digits](https://leetcode.com/problems/add-digits/description/)
```c
int addDigits(int num) {
    if (num >= 0 && num <= 9)
        return num;
    int sum = 0;
    while (num > 9)
    {
        while (num > 0)
        {
            sum += num % 10;
            num /= 10;
        }
        num = sum;
        sum = 0;
    }
    return num;
}
```

## [1. Two Sum](https://leetcode.com/problems/two-sum/description/)
```c
int* twoSum(int* nums, int numsSize, int target, int* returnSize) {
    *returnSize = 2;
    int* result = (int*)malloc(2 * sizeof(int));
    if (result == NULL) {
        return NULL;
    }

    for (int i = 0; i < numsSize - 1; i++) {
        for (int j = i + 1; j < numsSize; j++) {
            if (nums[i] + nums[j] == target) {
                result[0] = i;
                result[1] = j;
                return result;
            }
        }
    }

    free(result);
    return NULL;
}
```

## [125. Valid Palindrome](https://leetcode.com/problems/valid-palindrome/description/)
```c
bool isPalindrome(char* s) {
    if (s == NULL) return false;
    
    int left = 0;
    int right = strlen(s) - 1;
    
    while (left < right) {
        while (left < right && !isalnum(s[left])) {
            left++;
        }
        while (left < right && !isalnum(s[right])) {
            right--;
        }
        
        if (tolower(s[left]) != tolower(s[right])) {
            return false;
        }
        
        left++;
        right--;
    }
    
    return true;
}
```

## [169. Majority Element](https://leetcode.com/problems/majority-element/description/)
```c
int majorityElement(int* nums, int numsSize) {
    int count = 0;
    int candidate = 0;
    
    for (int i = 0; i < numsSize; i++) {
        if (count == 0) {
            candidate = nums[i];
        }
        count += (nums[i] == candidate) ? 1 : -1;
    }
    
    return candidate;
}
```

## [242. Valid Anagram](https://leetcode.com/problems/valid-anagram/description/)
```c
bool isAnagram(char* s, char* t) {
    if (strlen(s) != strlen(t)) {
        return false;
    }

    int count[26] = {0};

    for (int i = 0; s[i] != '\0'; i++) {
        count[s[i] - 'a']++;
    }

    for (int i = 0; t[i] != '\0'; i++) {
        count[t[i] - 'a']--;
    }

    for (int i = 0; i < 26; i++) {
        if (count[i] != 0) {
            return false;
        }
    }

    return true;
}
```

## [507. Perfect Number](https://leetcode.com/problems/perfect-number/description/)
```c
bool checkPerfectNumber(int num) {
    if (num <= 1) {
        return false;
    }

    int sum = 1;
    int sqrt_num = (int)sqrt(num);

    for (int i = 2; i <= sqrt_num; i++) {
        if (num % i == 0) {
            sum += i;
            int complement = num / i;
            if (complement != i) {
                sum += complement;
            }
        }
    }

    return sum == num;
}
```

## [461. Hamming Distance](https://leetcode.com/problems/hamming-distance/description/)
```c
int hammingDistance(int x, int y) {
    int xor_result = x ^ y;
    int distance = 0;
    
    while (xor_result != 0) {
        distance += xor_result & 1;
        xor_result >>= 1;
    }
    
    return distance;
}
```

## [2264. Largest 3-Same-Digit Number in String](https://leetcode.com/problems/largest-3-same-digit-number-in-string/description/?envType=daily-question&envId=2025-08-14)
```c
char* largestGoodInteger(char* num) {
    char* result = malloc(4 * sizeof(char));
    if (result == NULL) return NULL;
    
    result[0] = '\0';
    int len = strlen(num);
    
    for (int i = 0; i <= len - 3; i++) {
        if (num[i] == num[i + 1] && num[i] == num[i + 2]) {
            if (result[0] == '\0' || num[i] > result[0]) {
                result[0] = result[1] = result[2] = num[i];
                result[3] = '\0';
            }
        }
    }
    
    return result;
}
```

## [342. Power of Four](https://leetcode.com/problems/power-of-four/description/?envType=daily-question&envId=2025-08-15)
```c
bool isPowerOfFour(int n) {
    if (n == 1)
        return true;
    long long res = 1;
    while (res <= n)
    {
        res *= 4;
        if (res == n)
            return true;
    }
    return false;
}
```

## [1323. Maximum 69 Number](https://leetcode.com/problems/maximum-69-number/description/?envType=daily-question&envId=2025-08-16)
```c
int maximum69Number (int num) {
    int temp = num;
    int pos = -1;
    int power = 1;
    
    for (int i = 0; temp > 0; i++) {
        if (temp % 10 == 6) {
            pos = i;
        }
        temp /= 10;
    }

    if (pos != -1) {
        num += 3 * (int)pow(10, pos);
    }
    
    return num;
}
```

## [121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)
```c
int maxProfit(int* prices, int pricesSize) {
    if (pricesSize <= 1) {
        return 0;
    }
    int min_price = prices[0];
    int max_profit = 0;
    for (int i = 1; i < pricesSize; i++) {
        if (prices[i] < min_price) {
            min_price = prices[i];
        } else {
            int current_profit = prices[i] - min_price;
            if (current_profit > max_profit) {
                max_profit = current_profit;
            }
        }
    }
    return max_profit;
}
```

## [278. First Bad Version](https://leetcode.com/problems/first-bad-version/description/)
```c
int firstBadVersion(int n) {
    int left = 1;
    int right = n;
    
    while (left < right) {
        int mid = left + (right - left) / 2;
        if (isBadVersion(mid)) {
            right = mid;
        } else {
            left = mid + 1;
        }
    }
    
    return left;
}
```

## [2016. Maximum Difference Between Increasing Elements](https://leetcode.com/problems/maximum-difference-between-increasing-elements/description/)
```c
int maximumDifference(int* nums, int numsSize) {
    int min_so_far = nums[0];
    int max_diff = -1;
    
    for (int j = 1; j < numsSize; j++) {
        if (nums[j] > min_so_far) {
            int current_diff = nums[j] - min_so_far;
            if (current_diff > max_diff) {
                max_diff = current_diff;
            }
        } else {
            min_so_far = nums[j];
        }
    }
    
    return max_diff;
}
```

## [1299. Replace Elements with Greatest Element on Right Side](https://leetcode.com/problems/replace-elements-with-greatest-element-on-right-side/description/)
```c
int* replaceElements(int* arr, int arrSize, int* returnSize) {
    int* result = (int*)malloc(arrSize * sizeof(int));
    
    *returnSize = arrSize;
    
    if (arrSize == 1) {
        result[0] = -1;
        return result;
    }
    
    int max_right = -1;
    
    for (int i = arrSize - 1; i >= 0; i--) {
        int current = arr[i];
        
        result[i] = max_right;
        
        if (current > max_right) {
            max_right = current;
        }
    }
    
    return result;
}
```

## [374. Guess Number Higher or Lower](https://leetcode.com/problems/guess-number-higher-or-lower/description/)
```c
int guessNumber(int n){
    int left = 1;
    int right = n;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        int result = guess(mid);
        
        if (result == 0) {
            return mid;
        } else if (result == -1) {
            right = mid - 1;
        } else {
            left = mid + 1;
        }
    }
    
    return -1;
}
```

## [326. Power of Three](https://leetcode.com/problems/power-of-three/description/)
```c
bool isPowerOfThree(int n) {
    if (n == 1)
        return true;
    long long res = 1;
    while (res < n){
        res *= 3;
        if(res == n)
            return true;
    }
    return false;
}
```

## [1903. Largest Odd Number in String](https://leetcode.com/problems/largest-odd-number-in-string/description/)
```c
char* largestOddNumber(char* num) {
    int n = strlen(num);
    
    for (int i = n - 1; i >= 0; i--) {
        if ((num[i] - '0') % 2 != 0) {
            char* result = malloc((i + 2) * sizeof(char));
            strncpy(result, num, i + 1);
            result[i + 1] = '\0';
            return result;
        }
    }
    
    return "";
}
```

## [693. Binary Number with Alternating Bits](https://leetcode.com/problems/binary-number-with-alternating-bits/description/)
```c
bool hasAlternatingBits(int n) {
    int prev = n & 1;
    n >>= 1;
    
    while (n > 0) {
        int current = n & 1;
        
        if (current == prev) {
            return false;
        }
        
        prev = current;
        n >>= 1;
    }
    
    return true;
}
```

## [2460. Apply Operations to an Array](https://leetcode.com/problems/apply-operations-to-an-array/description/)
```c
int* applyOperations(int* nums, int numsSize, int* returnSize) {
    for (int i = 0; i < numsSize - 1; i++) {
        if (nums[i] == nums[i + 1]) {
            nums[i] *= 2;
            nums[i + 1] = 0;
        }
    }
    
    int* result = (int*)malloc(numsSize * sizeof(int));
    *returnSize = numsSize;
    
    int index = 0;
    for (int i = 0; i < numsSize; i++) {
        if (nums[i] != 0) {
            result[index++] = nums[i];
        }
    }
    
    while (index < numsSize) {
        result[index++] = 0;
    }
    
    return result;
}
```

## [28. Find the Index of the First Occurrence in a String](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/description/)
```c
int strStr(char* haystack, char* needle) {
    int len1 = strlen(haystack);
    int len2 = strlen(needle);

    if (len2 > len1 || len2 == 0)
        return -1;

    for (int i = 0; i <= len1 - len2; i++)
    {
        if (haystack[i] == needle[0])
        {
            int j;
            for (j = 1; j < len2; j++)
            {
                if (haystack[i + j] != needle[j])
                    break;
            }
            if (j == len2)
                return i;
        }
    }
    return -1;
}
```

## [459. Repeated Substring Pattern](https://leetcode.com/problems/repeated-substring-pattern/description/)
```c
bool repeatedSubstringPattern(char* s) {
    int n = strlen(s);
    for (int i = 1; i <= n / 2; i++) {
        if (n % i != 0) continue;
        
        bool valid = true;
        for (int j = i; j < n; j++) {
            if (s[j] != s[j % i]) {
                valid = false;
                break;
            }
        }
        if (valid) {
            return true;
        }
    }
    return false;
}
```

## [2351. First Letter to Appear Twice](https://leetcode.com/problems/first-letter-to-appear-twice/description/)
```c
char repeatedCharacter(char* s) {
    int len = strlen(s);
    int mas[26] = {0};
    int min_sec_ind = len;
    for (int i = 0; i < len; i++)
    {
        if (mas[s[i] - 'a'] == 0)
            mas[s[i] - 'a'] = 1;
        else
        {
            if (i < min_sec_ind)
                return s[i];
        }
    }
    return s[1];
}
```

## [1160. Find Words That Can Be Formed by Characters](https://leetcode.com/problems/find-words-that-can-be-formed-by-characters/description/)
```c
int countCharacters(char** words, int wordsSize, char* chars) {
    int total_length = 0;
    int char_count[26] = {0};
    
    for (int i = 0; chars[i] != '\0'; i++) {
        char_count[chars[i] - 'a']++;
    }
    
    for (int i = 0; i < wordsSize; i++) {
        char* word = words[i];
        int word_len = strlen(word);
        int temp_count[26];
        int is_good = 1;
        
        memcpy(temp_count, char_count, sizeof(char_count));
        
        for (int j = 0; j < word_len; j++) {
            int index = word[j] - 'a';
            
            if (temp_count[index] <= 0) {
                is_good = 0;
                break;
            }
            
            temp_count[index]--;
        }
        
        if (is_good) {
            total_length += word_len;
        }
    }
    
    return total_length;
}
```

## [345. Reverse Vowels of a String](https://leetcode.com/problems/reverse-vowels-of-a-string/description/)
```c
bool isVowel(char c) {
    return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u' ||
           c == 'A' || c == 'E' || c == 'I' || c == 'O' || c == 'U';
}

char* reverseVowels(char* s) {
    int left = 0;
    int right = strlen(s) - 1;
    
    while (left < right) {
        while (left < right && !isVowel(s[left])) left++;
        while (left < right && !isVowel(s[right])) right--;
        
        if (left < right) {
            char temp = s[left];
            s[left++] = s[right];
            s[right--] = temp;
        }
    }
    
    return s;
}
```

## [3065. Minimum Operations to Exceed Threshold Value I](https://leetcode.com/problems/minimum-operations-to-exceed-threshold-value-i/description/)
```c
int minOperations(int* nums, int numsSize, int k) {
    int res = 0;
    for (int i = 0; i<numsSize; i++){
        if (nums[i]<k) res++;
    }
    return res;
}
```

## [2843. Count Symmetric Integers](https://leetcode.com/problems/count-symmetric-integers/description/)
```c
int countSymmetricIntegers(int low, int high) {
    int count = 0;
    for (int num = low; num <= high; num++) {
        int temp = num;
        int digits = 0;
        while (temp != 0) {
            digits++;
            temp /= 10;
        }
        if (digits % 2 != 0) {
            continue;
        }
        int firstHalfSum = 0;
        int secondHalfSum = 0;
        temp = num;
        for (int i = 0; i < digits / 2; i++) {
            secondHalfSum += temp % 10;
            temp /= 10;
        }
        for (int i = 0; i < digits / 2; i++) {
            firstHalfSum += temp % 10;
            temp /= 10;
        }
        if (firstHalfSum == secondHalfSum) {
            count++;
        }
    }
    return count;
}
```

## [977. Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/description/)
```c
int* sortedSquares(int* nums, int numsSize, int* returnSize) {
    *returnSize = numsSize;
    int* result = (int*)malloc(numsSize * sizeof(int));
    if (result == NULL) return NULL;
    
    int left = 0;
    int right = numsSize - 1;
    int index = numsSize - 1;
    
    while (left <= right) {
        int left_sq = nums[left] * nums[left];
        int right_sq = nums[right] * nums[right];
        
        if (left_sq >= right_sq) {
            result[index--] = left_sq;
            left++;
        } else {
            result[index--] = right_sq;
            right--;
        }
    }
    
    return result;
}
```

## [2525. Categorize Box According to Criteria](https://leetcode.com/problems/categorize-box-according-to-criteria/description/)
```c
char* categorizeBox(int length, int width, int height, int mass) {
    bool isBulky = false;
    
    if (length >= 10000 || width >= 10000 || height >= 10000) {
        isBulky = true;
    }
    else {
        long long volume = (long long)length * width * height;
        if (volume >= 1000000000) {
            isBulky = true;
        }
    }
    
    bool isHeavy = (mass >= 100);
    
    if (isBulky && isHeavy) {
        return "Both";
    } else if (!isBulky && !isHeavy) {
        return "Neither";
    } else if (isBulky && !isHeavy) {
        return "Bulky";
    } else {
        return "Heavy";
    }
}
```

## [3158. Find the XOR of Numbers Which Appear Twice](https://leetcode.com/problems/find-the-xor-of-numbers-which-appear-twice/description/)
```c
int duplicateNumbersXOR(int* nums, int numsSize) {
    int counter[50] = {0};
    int result = 0;
    for (int i = 0; i < numsSize; i++)
    {
        counter[nums[i] - 1]++;
        if (counter[nums[i] - 1] > 1)
            result ^= nums[i];
    }
    return result;
}
```

## [2194. Cells in a Range on an Excel Sheet](https://leetcode.com/problems/cells-in-a-range-on-an-excel-sheet/description/)
```c
char** cellsInRange(char* s, int* returnSize) {
    // Парсим входную строку
    char start_col = s[0];  // Первый столбец (например, 'K')
    char start_row = s[1];  // Первая строка (например, '1')
    char end_col = s[3];    // Конечный столбец (например, 'L')
    char end_row = s[4];    // Конечная строка (например, '2')
    
    // Преобразуем символы строк в числа
    int start_row_num = start_row - '0';
    int end_row_num = end_row - '0';
    
    // Вычисляем количество столбцов и строк
    int num_cols = end_col - start_col + 1;
    int num_rows = end_row_num - start_row_num + 1;
    
    // Общее количество ячеек
    int total_cells = num_cols * num_rows;
    *returnSize = total_cells;
    
    // Выделяем память для массива строк
    char** result = (char**)malloc(total_cells * sizeof(char*));
    
    int index = 0;
    
    // Проходим по всем столбцам от начального до конечного
    for (char col = start_col; col <= end_col; col++) {
        // Проходим по всем строкам от начальной до конечной
        for (char row_char = start_row; row_char <= end_row; row_char++) {
            // Выделяем память для каждой ячейки (3 символа: буква + цифра + нуль-терминатор)
            result[index] = (char*)malloc(3 * sizeof(char));
            
            // Формируем строку ячейки
            result[index][0] = col;      // Столбец (буква)
            result[index][1] = row_char; // Строка (цифра)
            result[index][2] = '\0';     // Конец строки
            
            index++;
        }
    }
    
    return result;   
}
```

## [3471. Find the Largest Almost Missing Integer](https://leetcode.com/problems/find-the-largest-almost-missing-integer/description/)
```c
int largestInteger(int* nums, int numsSize, int k) {
    // Создаем массив для подсчета количества подмассивов для каждого числа
    // Поскольку числа в диапазоне [0, 50], нам нужно 51 элемент
    int count[51] = {0}; // Инициализируем все элементы нулями
    
    // Проходим по всем возможным подмассивам длины k
    for (int i = 0; i <= numsSize - k; i++) {
        // Создаем временный массив для отслеживания уникальных чисел в текущем подмассиве
        bool seen[51] = {false};
        
        // Проходим по элементам текущего подмассива
        for (int j = i; j < i + k; j++) {
            int num = nums[j];
            // Если число еще не встречалось в этом подмассиве
            if (!seen[num]) {
                seen[num] = true; // Помечаем как встреченное
                count[num]++;     // Увеличиваем счетчик для этого числа
            }
        }
    }
    
    // Ищем наибольшее число, которое встречается ровно в одном подмассиве
    int result = -1;
    for (int num = 0; num <= 50; num++) {
        if (count[num] == 1) {
            if (num > result) {
                result = num;
            }
        }
    }
    
    return result;
}
```

## [1945. Sum of Digits of String After Convert](https://leetcode.com/problems/sum-of-digits-of-string-after-convert/description/)
```c
int getLucky(char* s, int k) {
    // Шаг 1: Преобразование букв в их числовые значения
    int numStr[1000]; // Буфер для числовых значений
    int numStrLength = 0;
    
    // Проходим по каждой букве в строке
    for (int i = 0; s[i] != '\0'; i++) {
        int letterValue = s[i] - 'a' + 1; // 'a' -> 1, 'b' -> 2, ..., 'z' -> 26
        
        // Разбиваем двузначные числа на отдельные цифры
        if (letterValue >= 10) {
            numStr[numStrLength++] = letterValue / 10; // Первая цифра
            numStr[numStrLength++] = letterValue % 10; // Вторая цифра
        } else {
            numStr[numStrLength++] = letterValue; // Однозначное число
        }
    }
    
    // Шаг 2: Вычисляем начальную сумму цифр
    long long currentValue = 0;
    for (int i = 0; i < numStrLength; i++) {
        currentValue += numStr[i];
    }
    
    // Шаг 3: Повторяем операцию суммирования цифр k-1 раз
    // (первое суммирование уже сделано выше)
    for (int transform = 1; transform < k; transform++) {
        long long newValue = 0;
        
        // Суммируем цифры текущего числа
        while (currentValue > 0) {
            newValue += currentValue % 10; // Берем последнюю цифру
            currentValue /= 10;           // Убираем последнюю цифру
        }
        
        currentValue = newValue;
    }
    
    return (int)currentValue;
}
```

## [2520. Count the Digits That Divide a Number](https://leetcode.com/problems/count-the-digits-that-divide-a-number/description/)
```c
int countDigits(int num) {
    int count = 0;
    int tmp = num;
    while (tmp > 0)
    {
        if (num % (tmp % 10) == 0)
            count++;
        tmp /= 10;
    }
    return count;
}
```

## [762. Prime Number of Set Bits in Binary Representation](https://leetcode.com/problems/prime-number-of-set-bits-in-binary-representation/description/)
```c
// Функция для подсчета количества единичных битов в числе
int countSetBits(int n) {
    int count = 0;
    while (n) {
        count += n & 1;  // Проверяем младший бит
        n >>= 1;         // Сдвигаем число вправо
    }
    return count;
}

// Функция проверки, является ли число простым
bool isPrime(int n) {
    if (n <= 1) return false;    // 0 и 1 не простые
    if (n == 2) return true;     // 2 - простое
    if (n % 2 == 0) return false; // Четные числа больше 2 не простые
    
    // Проверяем делители до квадратного корня из n
    for (int i = 3; i * i <= n; i += 2) {
        if (n % i == 0) {
            return false;
        }
    }
    return true;
}

int countPrimeSetBits(int left, int right) {
    int count = 0;
    
    // Проходим по всем числам в диапазоне [left, right]
    for (int num = left; num <= right; num++) {
        // Подсчитываем количество единичных битов
        int setBits = countSetBits(num);
        
        // Проверяем, является ли это количество простым числом
        if (isPrime(setBits)) {
            count++;
        }
    }
    
    return count;
}
```

## [3146. Permutation Difference between Two Strings](https://leetcode.com/problems/permutation-difference-between-two-strings/description/)
```c
int findPermutationDifference(char* s, char* t) {
    int diff = 0;
    int s_index[26] = {0}; // Массив для хранения индексов символов в строке s
    
    // Заполняем массив индексами из строки s
    for (int i = 0; s[i] != '\0'; i++) {
        s_index[s[i] - 'a'] = i; // Сохраняем индекс для каждого символа
    }
    
    // Проходим по строке t и вычисляем разницу
    for (int i = 0; t[i] != '\0'; i++) {
        char c = t[i];
        int s_pos = s_index[c - 'a']; // Получаем позицию символа в s
        diff += abs(s_pos - i); // Суммируем абсолютную разницу
    }
    
    return diff;
}
```

## [2859. Sum of Values at Indices With K Set Bits](https://leetcode.com/problems/sum-of-values-at-indices-with-k-set-bits/description/)
```c
int count_bits(int n) {
    int count = 0;
    while (n) {
        count += n & 1;
        n >>= 1;
    }
    return count;
}

int sumIndicesWithKSetBits(int *nums, int numsSize, int k)
{
    int result = 0;
    for (int i = 0; i < numsSize; i++)
    {
        if (count_bits(i) == k)
            result += nums[i];
    }
    return result;
}
```

## [2733. Neither Minimum nor Maximum](https://leetcode.com/problems/neither-minimum-nor-maximum/description/)
```c
int findNonMinOrMax(int* nums, int numsSize) {
    // Если в массиве меньше 3 элементов, невозможно найти число,
    // которое не является ни минимумом, ни максимумом
    if (numsSize < 3) {
        return -1;
    }
    
    int min = nums[0];
    int max = nums[0];
    
    // Находим минимальное и максимальное значения
    for (int i = 1; i < numsSize; i++) {
        if (nums[i] < min) {
            min = nums[i];
        }
        if (nums[i] > max) {
            max = nums[i];
        }
    }
    
    // Ищем любое число, которое не является ни минимумом, ни максимумом
    for (int i = 0; i < numsSize; i++) {
        if (nums[i] != min && nums[i] != max) {
            return nums[i];
        }
    }
    
    // На всякий случай возвращаем -1 (хотя теоретически сюда не должны дойти)
    return -1;
}
```

## [2119. A Number After a Double Reversal](https://leetcode.com/problems/a-number-after-a-double-reversal/description/)
```c
int reverseNumber(int num)
{
    int result = 0;
    while (num > 0)
    {
        result = result * 10 + num % 10;
        num /= 10;
    }
    return result;
}

bool isSameAfterReversals(int num)
{
    if (num == 0)
        return true;
    if (num % 10 == 0)
        return false;

    int revers1 = reverseNumber(num);
    int revers2 = reverseNumber(revers1);
    if (revers2 == num)
        return true;
    return false;
}
```

## [2160. Minimum Sum of Four Digit Number After Splitting Digits](https://leetcode.com/problems/minimum-sum-of-four-digit-number-after-splitting-digits/description/)
```c
int minimumSum(int num) {
    int arr[4] = {num % 10, (num / 10) % 10, (num / 100) % 10, num / 1000};
    for (int i = 0; i < 4; i++)
    {
        for (int j = i + 1; j < 4; j++)
        {
            if (arr[j] < arr[i])
            {
                int tmp = arr[i];
                arr[i] = arr[j];
                arr[j] = tmp;
            }
        }
    }
    int new1 = arr[0] * 10 + arr[2];
    int new2 = arr[1] * 10 + arr[3];

    return new1 + new2;
}
```

## [1935. Maximum Number of Words You Can Type](https://leetcode.com/problems/maximum-number-of-words-you-can-type/description/?envType=daily-question&envId=2025-09-15)
```c
int canBeTypedWords(char* text, char* brokenLetters) {
    char alphabet[26] = {0};
    int count = 0;
    int len_text = strlen(text);
    int len_broken = strlen(brokenLetters);
    for (int i = 0; i < len_broken; i++)
    {
        alphabet[brokenLetters[i] - 'a'] = 1;
    }
    for (int i = 0; i < len_text && text[i] != '\0'; i++)
    {
        int good = 1;
        while (text[i] != ' ' && i < len_text)
        {
            if (alphabet[text[i] - 'a'])
            {
                good = 0;
            }
            i++;
        }
        if (good)
            count++;
    }
    return count;
}
```

## [3498. Reverse Degree of a String](https://leetcode.com/problems/reverse-degree-of-a-string/description/)
```c
int reverseDegree(char *s)
{
    int len = strlen(s);
    int sum = 0;
    for (int i = 0; i < len; i++)
    {
        sum += (i + 1) * (26 - (s[i] - 'a'));
    }
    return sum;
}
```

## [2255. Count Prefixes of a Given String](https://leetcode.com/problems/count-prefixes-of-a-given-string/description/)
```c
int countPrefixes(char** words, int wordsSize, char* s) {
    int result = 0;
    for (int i = 0; i < wordsSize; i++)
    {
        if (!strncmp(words[i], s, strlen(words[i])))
            result++;
    }
    return result;
}
```

## [2465. Number of Distinct Averages](https://leetcode.com/problems/number-of-distinct-averages/description/)
```c
void bubbleSort(int arr[], int n)
{
    int i, j;
    int swapped;
    for (i = 0; i < n - 1; i++)
    {
        swapped = 0;
        for (j = 0; j < n - i - 1; j++)
        {
            if (arr[j] > arr[j + 1])
            {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
                swapped = 1;
            }
        }
        if (swapped == 0)
            break;
    }
}

int distinctAverages(int *nums, int numsSize)
{
    int result = 0;
    
    bubbleSort(nums, numsSize);
    
    int min_index = 0;
    int max_index = numsSize - 1;

    double *mid_nums = (double *)malloc((numsSize / 2) * sizeof(double));
    if (mid_nums == NULL)
        return -1;

    int i = 0;
    while (min_index < max_index)
    {
        mid_nums[i++] = (nums[min_index++] + nums[max_index--]) / 2.0;
    }

    for (int j = 0; j < i; j++)
    {
        if (mid_nums[j] == -1.0) continue;
        for (int k = j + 1; k < i; k++)
        {
            if (mid_nums[j] == mid_nums[k])
                mid_nums[k] = -1.0;
        }
    }

    for (int j = 0; j < i; j++)
    {
        if (mid_nums[j] != -1.0)
            result++;
    }

    free(mid_nums);
    return result;
}
```

## [2169. Count Operations to Obtain Zero](https://leetcode.com/problems/count-operations-to-obtain-zero/description/)
```c
int countOperations(int num1, int num2) {
    int count = 0;
    while (num1 && num2)
    {
        if (num1 > num2)
            num1 -= num2;
        else
            num2 -= num1;
        count++;
    }
    return count;
}
```

## [2529. Maximum Count of Positive Integer and Negative Integer](https://leetcode.com/problems/maximum-count-of-positive-integer-and-negative-integer/description/)
```c
int maximumCount(int* nums, int numsSize) {
    int pos = 0;
    int neg = 0;
    for (int i = 0; i < numsSize; i++)
    {
        if (nums[i] < 0)
            neg++;
        if (nums[i] > 0)
            pos++;
    }
    return pos > neg ? pos : neg;
}
```

## [744. Find Smallest Letter Greater Than Target](https://leetcode.com/problems/find-smallest-letter-greater-than-target/description/)
```c
char nextGreatestLetter(char* letters, int lettersSize, char target) {
    for (int i = 0; i < lettersSize; i++)
    {
        if (letters[i] > target)
            return letters[i];
    }
    return letters[0];
}
```

## [3178. Find the Child Who Has the Ball After K Seconds](https://leetcode.com/problems/find-the-child-who-has-the-ball-after-k-seconds/description/)
```c
int numberOfChild(int n, int k) {
    int pos = 0;      // начальная позиция мяча — ребенок 0
    int direction = 1; // направление передачи, 1 — вправо, -1 — влево

    for (int i = 0; i < k; i++) {
        pos += direction;

        // меняем направление, если мяч у одного из концов очереди
        if (pos == 0 || pos == n - 1) {
            direction = -direction;
        }
    }

    return pos;
}
```

## [2595. Number of Even and Odd Bits](https://leetcode.com/problems/number-of-even-and-odd-bits/description/)
```c
int* evenOddBit(int n, int* returnSize) {
    // Выделяем память для результата
    int* arr = (int*)malloc(2 * sizeof(int));
    arr[0] = 0; // even - четные индексы
    arr[1] = 0; // odd - нечетные индексы
    
    int index = 0;
    while(n > 0) {
        if(index % 2 == 0)
            arr[0] += n & 1;  // Четные индексы
        else
            arr[1] += n & 1;  // Нечетные индексы
        
        index++;
        n = n >> 1;  // Сдвиг вправо
    }
    
    *returnSize = 2;  // Устанавливаем размер возвращаемого массива
    return arr;
}
```

## [2224. Minimum Number of Operations to Convert Time](https://leetcode.com/problems/minimum-number-of-operations-to-convert-time/description/)
```c
int convertTime(char* current, char* correct) {
    int count = 0;
    int min_cu = ((current[0] - '0') * 10 + (current[1] - '0')) * 60 + ((current[3] - '0') * 10 + (current[4] - '0'));
    int min_co = ((correct[0] - '0') * 10 + (correct[1] - '0')) * 60 + ((correct[3] - '0') * 10 + (correct[4] - '0'));
    int diff = 0;
    if (min_co >= min_cu)
        diff = min_co - min_cu;
    else
        diff = (24 * 60 - min_cu) + min_co;
    count += diff / 60;
    diff %= 60;

    count += diff / 15;
    diff %= 15;

    count += diff / 5;
    diff %= 5;

    count += diff;
    return count;
}
```

## [724. Find Pivot Index](https://leetcode.com/problems/find-pivot-index/description/)
```c
int pivotIndex(int* nums, int numsSize) {
    int total = 0;
    int left_sum = 0;
    
    // Считаем сумму всех элементов массива
    for (int i = 0; i < numsSize; i++) {
        total += nums[i];
    }

    // Проходим по массиву и проверяем условие опорного индекса
    for (int i = 0; i < numsSize; i++) {
        // Сумма справа равна: total - left_sum - nums[i]
        if (left_sum == total - left_sum - nums[i])
            return i;
        left_sum += nums[i];
    }
    return -1;
}
```

## [2855. Minimum Right Shifts to Sort the Array](https://leetcode.com/problems/minimum-right-shifts-to-sort-the-array/description/)
```c
int minimumRightShifts(int* nums, int numsSize) {
    int count = 0;
    int pivot = -1;

    // Поиск разрыва: где последовательность перестаёт быть возрастающей
    for (int i = 0; i + 1 < numsSize; i++) {
        if (nums[i] > nums[i + 1]) {
            count++;
            pivot = i;
        }
    }

    // Если разрывов нет, массив уже отсортирован
    if (count == 0)
        return 0;

    // Если разрывов больше одного, отсортировать сдвигами невозможно
    // Или если последний элемент больше первого (нарушает цикл сортировки)
    if (count > 1 || nums[numsSize - 1] > nums[0])
        return -1;

    // Если разрыв один, вернуть количество нужных сдвигов
    return numsSize - 1 - pivot;
}
```

## [1422. Maximum Score After Splitting a String](https://leetcode.com/problems/maximum-score-after-splitting-a-string/description/)
```c
int maxScore(char* s) {
    int len = strlen(s);
    int max_score = 0;
    
    // Проходим по всем возможным точкам разделения
    // от первого символа до предпоследнего
    for (int i = 1; i < len; i++) {
        int zeros_left = 0;
        int ones_right = 0;
        
        // Считаем нули в левой части (от 0 до i-1)
        for (int j = 0; j < i; j++) {
            if (s[j] == '0') {
                zeros_left++;
            }
        }
        
        // Считаем единицы в правой части (от i до конца)
        for (int j = i; j < len; j++) {
            if (s[j] == '1') {
                ones_right++;
            }
        }
        
        // Обновляем максимальный балл
        int current_score = zeros_left + ones_right;
        if (current_score > max_score) {
            max_score = current_score;
        }
    }
    
    return max_score;
}
```

## [2605. Form Smallest Number From Two Digit Arrays](https://leetcode.com/problems/form-smallest-number-from-two-digit-arrays/description/)
```c
int minNumber(int* nums1, int nums1Size, int* nums2, int nums2Size) {
     int min1 = 10;
    int min2 = 10;
    int common_min = 10;
    int digits[10] = {0};
    
    for (int i = 0; i < nums1Size; i++) {
        if (nums1[i] < min1) min1 = nums1[i];
        digits[nums1[i]] = 1;
    }
    
    for (int i = 0; i < nums2Size; i++) {
        if (nums2[i] < min2) min2 = nums2[i];
        if (digits[nums2[i]] && nums2[i] < common_min) {
            common_min = nums2[i];
        }
    }
    
    if (common_min != 10) return common_min;
    
    return (min1 < min2) ? (min1 * 10 + min2) : (min2 * 10 + min1);
}
```

## [2357. Make Array Zero by Subtracting Equal Amounts]()
```c
int minimumOperations(int* nums, int numsSize) {
    // Создаем массив для отслеживания уникальных ненулевых чисел
    int count[101] = {0}; // так как числа от 0 до 100
    
    // Подсчитываем уникальные ненулевые числа
    for (int i = 0; i < numsSize; i++) {
        if (nums[i] > 0) {
            count[nums[i]] = 1;
        }
    }
    
    // Считаем количество уникальных ненулевых чисел
    int uniqueCount = 0;
    for (int i = 1; i <= 100; i++) {
        if (count[i] == 1) {
            uniqueCount++;
        }
    }
    
    return uniqueCount;
}
```

## [1869. Longer Contiguous Segments of Ones than Zeros](https://leetcode.com/problems/longer-contiguous-segments-of-ones-than-zeros/description/)
```c
bool checkZeroOnes(char* s) {
    int max_ones = 0;  // Максимальная длина отрезка из единиц
    int max_zeros = 0; // Максимальная длина отрезка из нулей
    int current_ones = 0;  // Текущая длина отрезка из единиц
    int current_zeros = 0; // Текущая длина отрезка из нулей
    
    // Проходим по всем символам строки
    for (int i = 0; s[i] != '\0'; i++) {
        if (s[i] == '1') {
            // Если текущий символ '1', увеличиваем счетчик единиц
            current_ones++;
            current_zeros = 0; // Сбрасываем счетчик нулей
            
            // Обновляем максимум для единиц
            if (current_ones > max_ones) {
                max_ones = current_ones;
            }
        } else { // s[i] == '0'
            // Если текущий символ '0', увеличиваем счетчик нулей
            current_zeros++;
            current_ones = 0; // Сбрасываем счетчик единиц
            
            // Обновляем максимум для нулей
            if (current_zeros > max_zeros) {
                max_zeros = current_zeros;
            }
        }
    }
    
    // Проверяем условие: максимальный отрезок единиц СТРОГО больше максимального отрезка нулей
    return max_ones > max_zeros;
}
```

## [1304. Find N Unique Integers Sum up to Zero](https://leetcode.com/problems/find-n-unique-integers-sum-up-to-zero/)
```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* sumZero(int n, int* returnSize) {
    // Выделяем память для результата
    int* result = (int*)malloc(n * sizeof(int));
    *returnSize = n;
    
    // Если n нечетное, добавляем 0 и заполняем симметричными парами
    if (n % 2 == 1) {
        result[n - 1] = 0;  // Последний элемент = 0
        for (int i = 0; i < n - 1; i += 2) {
            result[i] = i + 1;        // Положительное число
            result[i + 1] = -(i + 1); // Отрицательное число
        }
    } 
    // Если n четное, заполняем только симметричными парами
    else {
        for (int i = 0; i < n; i += 2) {
            result[i] = i + 1;        // Положительное число
            result[i + 1] = -(i + 1); // Отрицательное число
        }
    }
    
    return result;
}
```

## [3105. Longest Strictly Increasing or Strictly Decreasing Subarray](https://leetcode.com/problems/longest-strictly-increasing-or-strictly-decreasing-subarray/description/)
```c
int longestMonotonicSubarray(int* nums, int numsSize) {
    if (numsSize == 0) return 0;
    if (numsSize == 1) return 1;
    
    int max_len = 1; // Минимальная длина подмассива всегда 1
    
    // Проверяем все возможные подмассивы
    for (int start = 0; start < numsSize; start++) {
        // Проверяем строго возрастающие подмассивы
        int inc_len = 1;
        for (int end = start + 1; end < numsSize; end++) {
            if (nums[end] > nums[end - 1]) {
                inc_len++;
            } else {
                break;
            }
        }
        if (inc_len > max_len) {
            max_len = inc_len;
        }
        
        // Проверяем строго убывающие подмассивы
        int dec_len = 1;
        for (int end = start + 1; end < numsSize; end++) {
            if (nums[end] < nums[end - 1]) {
                dec_len++;
            } else {
                break;
            }
        }
        if (dec_len > max_len) {
            max_len = dec_len;
        }
    }
    
    return max_len;
}
```

## [485. Max Consecutive Ones](https://leetcode.com/problems/max-consecutive-ones/description/)
```c
int findMaxConsecutiveOnes(int* nums, int numsSize) {
    int res = 0;
    int len = 0;

    for (int i = 0; i < numsSize; i++) {
        if (nums[i]) {
            len++;
        } else {
            len = 0;
        }
        
        if (len > res) {
            res = len;
        }
    }
    return res;
}
```

## [704. Binary Search](https://leetcode.com/problems/binary-search/description/)
```c
int search(int* nums, int numsSize, int target) {
    int left = 0;
    int right = numsSize - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        
        if (nums[mid] == target) {
            return mid;  // Нашли target, возвращаем индекс
        }
        else if (nums[mid] < target) {
            left = mid + 1;  // Искомый элемент в правой половине
        }
        else {
            right = mid - 1;  // Искомый элемент в левой половине
        }
    }
    
    return -1;  // Элемент не найден
}
```

## [1725. Number Of Rectangles That Can Form The Largest Square](https://leetcode.com/problems/number-of-rectangles-that-can-form-the-largest-square/description/)
```c
int countGoodRectangles(int** rectangles, int rectanglesSize, int* rectanglesColSize){
    int maxLen = 0;  // Максимальная длина квадрата
    int count = 0;   // Счетчик прямоугольников, дающих квадрат максимальной длины
    
    // Проходим по всем прямоугольникам
    for (int i = 0; i < rectanglesSize; i++) {
        // Для каждого прямоугольника находим максимально возможную сторону квадрата
        // Это минимум из длины и ширины
        int currentLen = (rectangles[i][0] < rectangles[i][1]) ? rectangles[i][0] : rectangles[i][1];
        
        // Если нашли квадрат больше текущего максимума
        if (currentLen > maxLen) {
            maxLen = currentLen;  // Обновляем максимум
            count = 1;            // Начинаем новый счетчик
        }
        // Если нашли квадрат равный текущему максимуму
        else if (currentLen == maxLen) {
            count++;  // Увеличиваем счетчик
        }
    }
    
    return count;
}
```

## [1742. Maximum Number of Balls in a Box](https://leetcode.com/problems/maximum-number-of-balls-in-a-box/description/)
```c
#include <stdlib.h>

// Функция для вычисления суммы цифр числа
int digitSum(int num) {
    int sum = 0;
    while (num > 0) {
        sum += num % 10;  // Добавляем последнюю цифру
        num /= 10;        // Убираем последнюю цифру
    }
    return sum;
}

int countBalls(int lowLimit, int highLimit) {
    // Максимальная возможная сумма цифр для highLimit = 100000
    // 99999 -> 9+9+9+9+9 = 45, но для надежности возьмем запас
    int maxBox = 46; // Максимальный номер коробки
    
    // Создаем массив для подсчета мячей в коробках
    int* boxes = (int*)calloc(maxBox + 1, sizeof(int));
    
    // Проходим по всем мячам
    for (int ball = lowLimit; ball <= highLimit; ball++) {
        int boxNum = digitSum(ball);  // Вычисляем номер коробки
        boxes[boxNum]++;              // Увеличиваем счетчик коробки
    }
    
    // Находим коробку с максимальным количеством мячей
    int maxBalls = 0;
    for (int i = 1; i <= maxBox; i++) {
        if (boxes[i] > maxBalls) {
            maxBalls = boxes[i];
        }
    }
    
    free(boxes);  // Освобождаем память
    return maxBalls;
}
```

## [1624. Largest Substring Between Two Equal Characters](https://leetcode.com/problems/largest-substring-between-two-equal-characters/description/)
```c
int maxLengthBetweenEqualCharacters(char* s) {
    // Массив для хранения первого вхождения каждого символа
    int first_occurrence[26];
    
    // Инициализируем массив значением -1 (символ еще не встречался)
    for (int i = 0; i < 26; i++) {
        first_occurrence[i] = -1;
    }
    
    int max_length = -1;
    int i = 0;
    
    // Проходим по строке
    while (s[i] != '\0') {
        int char_index = s[i] - 'a';  // Преобразуем символ в индекс (0-25)
        
        if (first_occurrence[char_index] == -1) {
            // Первое вхождение символа - сохраняем позицию
            first_occurrence[char_index] = i;
        } else {
            // Символ уже встречался - вычисляем длину подстроки между ними
            int length = i - first_occurrence[char_index] - 1;
            
            // Обновляем максимальную длину
            if (length > max_length) {
                max_length = length;
            }
        }
        
        i++;
    }
    
    return max_length;
}
```

## [1880. Check if Word Equals Summation of Two Words](https://leetcode.com/problems/check-if-word-equals-summation-of-two-words/description/)
```c
bool isSumEqual(char* firstWord, char* secondWord, char* targetWord) {
    // Функция для преобразования слова в числовое значение
    int wordToNumber(char* word) {
        int result = 0;
        // Проходим по каждому символу слова
        for (int i = 0; word[i] != '\0'; i++) {
            // Преобразуем букву в цифру: 'a'->0, 'b'->1, ..., 'j'->9
            int digit = word[i] - 'a';
            // Добавляем цифру к результату (умножаем текущий результат на 10)
            result = result * 10 + digit;
        }
        return result;
    }
    
    // Преобразуем все три слова в числа
    int num1 = wordToNumber(firstWord);
    int num2 = wordToNumber(secondWord);
    int numTarget = wordToNumber(targetWord);
    
    // Проверяем равенство суммы и целевого числа
    return (num1 + num2) == numTarget;
}
```

## [1317. Convert Integer to the Sum of Two No-Zero Integers](https://leetcode.com/problems/convert-integer-to-the-sum-of-two-no-zero-integers/description/)
```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
// Вспомогательная функция для проверки отсутствия нулей в числе
int containsNoZero(int num) {
    while (num > 0) {
        int digit = num % 10;  // Получаем последнюю цифру
        if (digit == 0) {
            return 0;  // Найден ноль - число не подходит
        }
        num /= 10;  // Убираем последнюю цифру
    }
    return 1;  // Нулей не найдено
}

int* getNoZeroIntegers(int n, int* returnSize) {
    // Выделяем память для результата (массив из 2 элементов)
    int* result = (int*)malloc(2 * sizeof(int));
    *returnSize = 2;
    
    // Перебираем возможные значения a от 1 до n-1
    for (int a = 1; a < n; a++) {
        int b = n - a;
        
        // Проверяем, что оба числа не содержат нулей
        if (containsNoZero(a) && containsNoZero(b)) {
            result[0] = a;
            result[1] = b;
            return result;
        }
    }
    
    // Если не нашли пару (по условию всегда должна быть)
    result[0] = 1;
    result[1] = n - 1;
    return result;
}
```

## [557. Reverse Words in a String III](https://leetcode.com/problems/reverse-words-in-a-string-iii/description/)
```c
char* reverseWords(char* s) {
    int length = strlen(s);
    char* result = (char*)malloc(length + 1);
    strcpy(result, s);
    
    int start = 0;
    
    for (int i = 0; i <= length; i++) {
        // Если нашли пробел или конец строки - разворачиваем слово
        if (result[i] == ' ' || result[i] == '\0') {
            int end = i - 1;
            
            // Разворачиваем слово от start до end
            while (start < end) {
                char temp = result[start];
                result[start] = result[end];
                result[end] = temp;
                start++;
                end--;
            }
            
            // Переходим к началу следующего слова
            start = i + 1;
        }
    }
    
    return result;
}
```

## [1779. Find Nearest Point That Has the Same X or Y Coordinate](https://leetcode.com/problems/find-nearest-point-that-has-the-same-x-or-y-coordinate/description/)
```c
int nearestValidPoint(int x, int y, int** points, int pointsSize, int* pointsColSize) {
    int min_distance = INT_MAX;  // Инициализируем минимальное расстояние максимальным значением
    int best_index = -1;         // Изначально индекс -1 (если не найдем валидных точек)
    
    // Проходим по всем точкам в массиве
    for (int i = 0; i < pointsSize; i++) {
        int a = points[i][0];  // x-координата текущей точки
        int b = points[i][1];  // y-координата текущей точки
        
        // Проверяем, является ли точка валидной
        // Точка валидна, если ее x совпадает с нашим x ИЛИ ее y совпадает с нашим y
        if (a == x || b == y) {
            // Вычисляем манхэттенское расстояние
            int distance = abs(x - a) + abs(y - b);
            
            // Если нашли точку с меньшим расстоянием, обновляем минимум
            if (distance < min_distance) {
                min_distance = distance;
                best_index = i;
            }
            // Если расстояние равно текущему минимуму, выбираем точку с меньшим индексом
            else if (distance == min_distance) {
                if (i < best_index) {
                    best_index = i;
                }
            }
        }
    }
    
    return best_index;  // Возвращаем индекс лучшей точки или -1 если не нашли
}
```

## [1556. Thousand Separator](https://leetcode.com/problems/thousand-separator/description/)
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char* thousandSeparator(int n) {
    // Обрабатываем случай n = 0
    if (n == 0) {
        char* result = (char*)malloc(2 * sizeof(char));
        strcpy(result, "0");
        return result;
    }
    
    // Преобразуем число в строку без разделителей
    char temp[20]; // Максимальная длина для int (2^31-1 = 2147483647)
    sprintf(temp, "%d", n);
    int len = strlen(temp);
    
    // Вычисляем длину результирующей строки
    // Количество точек = (len - 1) / 3
    int dots = (len - 1) / 3;
    int result_len = len + dots;
    
    // Выделяем память для результата
    char* result = (char*)malloc((result_len + 1) * sizeof(char));
    result[result_len] = '\0'; // Завершающий нуль-символ
    
    int result_index = result_len - 1;
    int count = 0;
    
    // Заполняем строку с конца, добавляя точки каждые 3 цифры
    for (int i = len - 1; i >= 0; i--) {
        result[result_index--] = temp[i];
        count++;
        
        // Добавляем точку после каждых 3 цифр, кроме последней группы
        if (count % 3 == 0 && i > 0) {
            result[result_index--] = '.';
        }
    }
    
    return result;
}
```