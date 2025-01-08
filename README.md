#include <stdlib.h>

/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* twoSum(int* nums, int numsSize, int target, int* returnSize) {
    int* result = (int*)malloc(2 * sizeof(int));
    *returnSize = 2;
    
    for (int i = 0; i < numsSize; i++) {
        for (int j = i + 1; j < numsSize; j++) {
            if (nums[i] + nums[j] == target) {
                result[0] = i;
                result[1] = j;
                return result;
            }
        }
    }
    
    result[0] = 0;
    result[1] = 1;
    return result;
}

bool isPalindrome(int x) {

     double rev=0, rem, orignal=x;
    
    
        while(x>0)
        {
            rem = x % 10;
            rev = rev * 10 + rem;
            x/=10;
        }

        if(rev == orignal)
            return true;
        
         else
       return false;
    
}

int DecimalNumericalPlace(char roman_np_value)
    {
        switch(roman_np_value)
        {
            case 'M':
            return 1000;
            break;

             case 'D':
            return 500;
            break;

            case 'C':
            return 100;
            break;

             case 'L':
            return 50;
            break;

             case 'X':
            return 10;
            break;

             case 'V':
            return 5;
            break;

            case 'I':
            return 1;
            break;
            default :
            return -1;
        }
    }
int romanToInt(char * s)
{
    int len=strlen(s);
    int sum=0;
   for(int i=0;s[i]!='\0';i++){
       if(DecimalNumericalPlace(s[i]) < DecimalNumericalPlace(s[i+1])){
       sum = sum-DecimalNumericalPlace(s[i]);
   }
   else{
   sum+=DecimalNumericalPlace(s[i]);
   }
   }
    return sum;
}

#include <stdio.h>
#include <stdlib.h>

char* longestCommonPrefix(char** strs, int strsSize) {
    int i = 0;
    int j = 0;
    int k = 0;
    char* w = malloc(sizeof(char) * 200); // Allocating space for the result
    if (w == NULL) return NULL; // Check for memory allocation failure
    w[0] = '\0'; // Initialize the result string

    char* ptr = strs[0]; // Reference to the first string
    while (ptr[j] != '\0') { // Iterate through characters of the first string
        for (i = 1; i < strsSize; i++) {
            if (strs[i][j] != ptr[j]) { // Check for mismatch
                w[k] = '\0'; // Null terminate the string
                return w; // Return the common prefix found so far
            }
        }
        w[k++] = ptr[j]; // Add the matching character to the result
        j++; // Move to the next character
    }

    w[k] = '\0'; // Null terminate the final result
    return w; // Return the common prefix
}

bool isValid(char *s) {

    char *q=s;
    
    for (char *p=s; *p; p++) 
        switch(*p) {
            case '(': *q++ = ')'; continue;
            case '{': *q++ = '}'; continue;
            case '[': *q++ = ']'; continue;
            default: if (q==s || *p != *--q) return false;
        }
    
    return q==s;
}

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
void insert (struct ListNode** head,int num){
    struct ListNode* new = (struct ListNode*)malloc(sizeof(struct ListNode));
    new->val = num;
    new->next = NULL;

    if(*head == NULL){
        *head = new;
    }else{
        struct ListNode* temp = *head;
        while(temp->next != NULL){
            temp =temp->next;
        }
        temp->next = new;
    }
}

struct ListNode* mergeTwoLists(struct ListNode* list1, struct ListNode* list2) {
    struct ListNode* head = NULL;
    while(list1 != NULL && list2 != NULL){
        if(list1->val < list2->val){
            insert(&head,list1->val);
            list1 = list1->next;
        }else{
            insert(&head,list2->val);
            list2 = list2->next;
        }
    }
    while(list1 != NULL){
        insert(&head,list1->val);
        list1 = list1->next;
    }
    while(list2 != NULL){
        insert(&head,list2->val);
        list2 = list2->next;
    }

    return head;
}

int removeDuplicates(int* nums, int numsSize) {
    if (numsSize == 0) return 0;

    int index = 1; 

    for (int i = 1; i < numsSize; i++) {
        if (nums[i] != nums[index - 1]) { 
            nums[index++] = nums[i];  
        }
    }

    return index;
}

int removeElement(int* nums, int numsSize, int val) {
    if(numsSize==0){
        return 0;
    }
    int j=0;
    for(int i=0;i<numsSize;i++){
        if(nums[i]!=val){
            nums[j++]=nums[i];
        }
    }
    return j;
}

int strStr(char* haystack, char* needle) {
  int count = 0;
  int ptr = 0;
  int n_len = strlen(needle);
  int h_len = strlen(haystack);
  for(int i = 0; i < h_len; i++){
    ptr = i;
    for(int j = 0; j < n_len; j++){
      if(haystack[i] == needle[j]){
        count++;
        i++;
      }
      else{
        count = 0;
      }
    }
    if(count == n_len){
      return ptr;
    }
    count = 0;
    i = ptr;
  }
  return -1;
}

int searchInsert(int* nums, int numsSize, int target) 
{   
    int counter = 0;
    for(int i = 0; i < numsSize; i++)
    {
        if (nums[i] == target) return i;
        if(nums[i] <= target)
        {
            counter++; //to count the index where we would put the target
        }
    }
    return counter;
}

int lengthOfLastWord(char* s) {
    int count=0;
    while((*s)!='\0'){
        if(((*s)==' ')&& ((*(s+1))!=' ')&&((*(s+1))!='\0'))
         count=0;
        else{
         if(*s!=' ')
         count++;
        }
        s++;
    }
    return count;
    
}

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* addTwoNumbers(struct ListNode* l1, struct ListNode* l2) {
    struct ListNode* listHead = (struct ListNode*)malloc(sizeof(struct ListNode));
    struct ListNode* listTail = listHead;
    listTail->val = 0;

    
    while (true) {
        int val = (l1 ? l1->val: 0) + (l2 ? l2->val: 0) + listTail->val;

        listTail->val = val % 10;
        
        l1 = l1 ? l1->next : NULL;
        l2 = l2 ? l2->next : NULL;
        
        if (l1 || l2 || val/10) {
            listTail->next = (struct ListNode*)malloc(sizeof(struct ListNode));
            listTail->next->val = val/10;
            listTail = listTail->next;
            
        }
        else {
            listTail->next = NULL;
            return listHead;
        }
    }
}

int* plusOne(int* digits, int digitsSize, int* returnSize)
{
    int *res = malloc(sizeof(int) * 100);
    int cf = 1;
    
    for (int i = digitsSize - 1; i >= 0; i--) {
        if (digits[i] + cf > 9) {
            digits[i] = (digits[i] + cf) % 10;
        } else {
            digits[i] = digits[i] + cf;
            cf = 0;
            break;
        }
    }
    
    if (cf)
        res[0] = 1;
    
    for (int i = cf, j = 0; j < digitsSize; i++, j++)
        res[i] = digits[j];

        char * addBinary(char * a, char * b){
    int sizeA = strlen(a);
    int sizeB = strlen(b);
    int sizeOutput = (sizeA > sizeB ? sizeA : sizeB) + 1;
    char * output = (char *)malloc(sizeOutput + 1);
    int sum = 0;
    
    output[sizeOutput] = '\0';
    
    while(sizeA > 0 || sizeB > 0 || sum > 0) {
        
        if(sizeA > 0) {
            sum += a[--sizeA] - '0';
        }
        if(sizeB > 0) {
            sum += b[--sizeB] - '0';
        }
        output[--sizeOutput] = sum % 2 + '0';
        sum /= 2;
    }
    return output + sizeOutput;   
}
    
    *returnSize = digitsSize + cf;
    return res;
}

int mySqrt(int x) {
  return sqrt(x);  
}

int climbStairs(int n) {
    long long int prv1 = 1;
    long long int prv2 = 1;

    for (int i = 0; i < n; i++) {
        long long int tmp = prv1;
        prv1 = prv1 + prv2;
        prv2 = tmp;
    }

    return (int)prv2;
}

struct ListNode* deleteDuplicates(struct ListNode* head){
    struct ListNode* curr = head;

    while(curr != NULL && curr->next != NULL){
        if(curr->val == curr->next->val)
            curr->next = curr->next->next;
        else
            curr = curr->next;
    }

    return head;
}

void merge(int* nums1, int nums1Size, int m, int* nums2, int nums2Size, int n) {
    int p1=m-1;
    int p2=n-1;
    int p=m+n-1;
    while(p1>=0 && p2>=0){
        if(nums1[p1]>nums2[p2])
            nums1[p--]=nums1[p1--];
        else
        nums1[p--]=nums2[p2--];
    }
    while(p2>=0)
     nums1[p--]=nums2[p2--];
}

int i=0;
int arr[101]={0};
void inorder(struct TreeNode* s)
{
    if(s!=NULL)
    {
        inorder(s->left);
        arr[i++]=s->val;
        inorder(s->right);
    }
}
int* inorderTraversal(struct TreeNode* root, int* returnSize){
    inorder(root);
    int* ans=malloc(i*sizeof(int));
    for(int j=0;j<i;j++) ans[j]=arr[j];
    *(returnSize)=i;
    i=0;
    return ans;
}

bool isSameTree(struct TreeNode* p, struct TreeNode* q){
    return (p == NULL || q == NULL) ? p == NULL && q == NULL : p->val == q->val && isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
}
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */

bool parallel_traverse(struct TreeNode* a, struct TreeNode* b)
{
    if (a == NULL && b == NULL)
        return true;
 
    if (a == NULL || b == NULL)
        return false;

    if (a->val != b->val)
        return false;
    
    return parallel_traverse(a->left, b->right) && parallel_traverse(a->right, b->left);
}

bool isSymmetric(struct TreeNode* root)
{
    if (root == NULL)
        return true;
    return parallel_traverse(root->left, root->right);
}

int maxArea(int* arr, int N){
    int max = 0, i = 0, j = N - 1;
    while(j > i){
        int test = arr[i];
        if(test > arr[j]) test = arr[j];
        test *= (j - i);
        if(max < test) max = test;
        if(arr[i] < arr[j]) i++ ;
        else j--;
    }
    return max;
}

int maxDepth(struct TreeNode* root){
    if (!root)
        return 0;
    int left_depth= maxDepth(root->left);
    int right_depth= maxDepth(root->right);
    if(left_depth > right_depth)
        return left_depth +1;
    else
        return right_depth +1;
    
}

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */
struct TreeNode* sortedArrayToBST(int* nums, int numsSize) {
    struct TreeNode* t;
    if (numsSize == 0) {
        return 0;
    }
    int mid = numsSize / 2;
    t = (struct TreeNode*)malloc(sizeof(struct TreeNode));
    t->val = nums[mid];
    t->left=sortedArrayToBST(nums,mid);
    t->right=sortedArrayToBST(nums+mid+1,numsSize-mid-1);
    return t;
}

int minDepth(struct TreeNode* root){
    if (!root) return 0;
    
    if (!root->left && !root->right) return 1;
    
    if(!root->left) return minDepth(root->right)+1;
    
    if(!root->right) return minDepth(root->left)+1;
    
    return minDepth(root->left) > minDepth(root->right) ? minDepth(root->right)+1 : minDepth(root->left)+1;
}

/* Definition for a binary tree node.                   */
/* struct TreeNode {                                    */
/*     int val;                                         */
/*     struct TreeNode *left;                           */
/*     struct TreeNode *right;                          */
/* };                                                   */
int depth(struct TreeNode *root);

bool isBalanced(struct TreeNode *root) {
    if (root == NULL)
        return true;
        
    return isBalanced(root->left) && 
           isBalanced(root->right) &&
           !(abs(depth(root->left) - depth(root->right)) > 1);
}

int depth(struct TreeNode *root) {
    if (root == NULL)
        return 0;
        
    return fmax(depth(root->left), depth(root->right)) + 1;
}

