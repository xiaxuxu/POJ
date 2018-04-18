### DNA Sorting
Time Limit: 1000MS		Memory Limit: 10000K
Total Submissions: 107188		Accepted: 42930
Description

One measure of "unsortedness" in a sequence is the number of pairs of entries that are out of order with respect to each other. 
For instance, in the letter sequence "DAABEC", this measure is 5, 
since D is greater than four letters to its right and E is greater than one letter to its right. 
This measure is called the number of inversions in the sequence. The sequence "AACEDGG'' has only one inversion (E and D)---it is nearly sorted---while the sequence ``ZWQM'' has 6 inversions (it is as unsorted as can be---exactly the reverse of sorted). 

You are responsible for cataloguing a sequence of DNA strings (sequences containing only the four letters A, C, G, and T). However, you want to catalog them, not in alphabetical order, but rather in order of "sortedness'', from "most sorted'' to "least sorted''. All the strings are of the same length. 
Input

The first line contains two integers: a positive integer n (0 < n <= 50) giving the length of the strings; and a positive integer m (0 < m <= 100) giving the number of strings. These are followed by m lines, each containing a string of length n.
Output

Output the list of input strings, arranged from "most sorted" to "least sorted". Since two strings can be equally sorted, then output them according to the orginal order.
Sample Input

10 6
AACATGAAGG
TTTTGGCCAA
TTTGGCCAAA
GATCAGATTT
CCCGGGGGGA
ATCGATGCAT
Sample Output

CCCGGGGGGA
AACATGAAGG
GATCAGATTT
ATCGATGCAT
TTTTGGCCAA
TTTGGCCAAA

我的代码
```C++
#include<iostream>
#include<vector>
#include<stdio.h>
#include<algorithm>
using namespace std;
typedef struct {
    char a[50];
    int count;
}dna;
bool compare(const dna &node1, const dna &node2)  {  
        return node1.count < node2.count;  
        
    }  
int main(){
    int l,m;
    char a[50];
    vector<dna>ddarray;
    cin>>l>>m;
    for(int i=0;i<m;i++){
        dna d1;
        d1.count=0;
        scanf("%s",d1.a);
        for(int j=0;j<l;j++){
            int k;
            for(k=j+1;k<l;k++){if((d1.a[k]-'0')<(d1.a[j]-'0')) d1.count++; }
        }
        
        ddarray.push_back(d1);
    }
    
    sort(ddarray.begin(),ddarray.end(),compare);
    for(int i=0;i<m;i++){
        printf("%s\n",ddarray[i].a);
    }
    
    return 0;
    
}
```
