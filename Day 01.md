
# algorithm

## Methodology to decide which algo is better.
1) Time complexity
2) Space complexity

# Complxity -> concept (problem statement)
## Time complexity : (kaise?) ( input -> increase, output ka rate???)
1) Big O notation -> upper bound -> worst case
2) Omega notation -> lower bound -> best case
3) Theta notation -> tight bound -> average case

## space complexity : 
1) in place algorithm (without extra space)
2) out of place algorithm

## Observations
1) While comparing time complexity using any of the notations always use larger values as input.
2) Reason for ignoring smaller order variables/ values.

f(n) = 3n^3+ 2n + 5; => O(n^3)
h(n) = 2n + 8; => 

g(n) = n^2 + 1;

n =5; time=15 sec 
n= 10; time= 25 sec

arr[5] = {3,0,1,4,2}
sort 
1) temp[5] 
2) arr (in place) O(1) -> constant time (best solution)

# Arrays
## Time complexicity for baseic operations:
1) Insertion -> O(n)
2) Deletion -> O(n)
3) Search -> O(n)

## Q1) arr => 0, 1 , sort 
method 1;
//using count sort . 
//time complexity= O(n)
//space complexity = O(1)
public static void sortBinaryArray(){
    int count0 = 0;
    for(int i=0;i<arr.length();i++){
        if(arr[i]==0)
        count0++;
    }
    for(int i=0;i<arr.length;i++){
        if(i<count0)
            arr[i]=0;
        else
            arr[i]=1;
    }
}

ex => arr = {0,1,1,2,1,0,0,2,1};

## method2 -> 2 pointer method 
int start = 0;
int last = arr.length;
while(start<last){
    if(arr[start]==0){
        start++;
    }
    if(arr[start]==1){
        swap(arr[start],arr[last]);
        last--;
    }
}

start =0
mid = length-2;
last = length -1;

## 3 pointer
while(start<=mid && start<last)
arr = {0,1,1,2,1,0,0,2,1};
{0,1,1,2,1,0,0,2,1}
{0,2,1,2,1,0,0,1,1}
{0,0,0,1,1,1,1,2,2}

## Q2) arr containg upto n numbers , only some specific value is missing ,n-1;
missing number = ?

1 -> count sort ( time complex -> O(n)), space o(n);
2 -> sum time-> O(n) , space -> O(1)

public static int findMissing(int[] input, int size){
    int temp[] = new int[size];
    Arrays.fill(temp, 0);
    int requiredIndex=0;
    for(int i=0;i<size;i++){
        temp[input[i]]++;
    }
    for(int i=0;i<size;i++){
        if(temp[i]!=1)
        requiredIndex = i;
    }
    return requiredIndex;
}

## Q3) Find duplicates in an array

M1)  
1) sort input arr -> O(nlogn)
2) find 

M2) O(n) , space -> O(n)

ex -> {10000000000, 3,5,2,6,6,7}
hashMap -> containsKey() ->O(1)


public static int findDuplicateNumber(){
    HashSet<Integer> set = new HashSet();
    for(int i=0;i<arr.length;i++){
        set.add(arr[i]);
    }
    int arrSum=0;
    for(int i=0;i<arr.length;i++){
        arrSum += arr[i];
    }
    int setSum=0;
    for(int i=0;i<set.size();i++){
        setSum += set.get(i);
    }
    return arrSum - setSum;
}

public static int refractoredFindDuplicateNumber(){
    HashSet<Integer> set = new HashSet();
    for(int i=0;i<arr.length;i++){
        int beforeAdd = set.size();
        set.add(arr[i]);
        if(set.size()==beforeAdd)
            return arr[i];
    }
    return -1;
}

# Wrap up:
1) Count sort 
2) 2 pointer arrays 
3) 3 pointer arrays
