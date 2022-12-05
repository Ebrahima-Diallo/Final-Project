# Final-Project
Final Project for CSC212
# Group Members:  <br />
 &nbsp; Juliana Nguyen <br />
 &nbsp; Alyssa Krouson <br />
 &nbsp; Jake Javier <br />
 &nbsp; Ebrahima Diallo <br />
 


## Code Completed
 ```
#include <iostream>
#include <cmath>

int n;

//array
int seg[400000];

//curr is to keep track of which node were at 
//start and end is to keep track what range we're on
//value is the value being inserted
void insert(int curr, int start, int end, int index, int value){
    
    //base case that makes it so nothing will happen if index is not in range, the one that the index is not in is discarded
    if (index > end || index < start){
        return;
    }
    
    if (start == end){
        seg[curr] = value;
        return;
    }
    
    //left insert between start to mid point
    insert(2*curr + 1, start, (start + end)/2, index, value);
    //right insert between mid point to end
    insert(2*curr + 2, (start + end)/2 + 1, end, index, value);
    
    seg[curr] = seg[2*curr + 1] + seg[2*curr + 2];
}

//helper function
void insert(int index, int value){
    //always starting at the root which is 0
    insert(0, 0, n-1, index, value);
}

int sum(int curr, int start, int end, int ql, int qr){
    
    if (ql > end || qr < start){
        return 0;
    }
    
    if (start >= ql && end <= qr){
        return seg[curr];
    }
    
    return sum(2*curr + 1, start, (start + end)/2, ql, qr) + sum(2*curr + 2, (start + end)/2 + 1, end, ql, qr);
    
}

//helper function
int sum(int ql, int qr){
    return sum(0, 0, n-1, ql, qr);
}
    
int main(){
    
    //int n;
    std::cin >> n;
    
    while(true){

        int x;
        std::cin >> x;
        
        if (x == 1){
            
            int index, val;
            std::cin >> index >> val;
            
            insert(index, val);
        }
        else{
            int ql, qr;
            std::cin >> ql >> qr;
        
        std::cout << sum(ql, qr);
           // a = sum(ql, qr);
           // std::cout << a;
        }
    }
}
 
 ```


