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
#include <vector>

void ReadFile(std::string file_name, int * array);

//int n;

//array
//int seg[400000];

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

//file name
//n = length
//seg tree size
int main(int argc, char * argv[]){

    std::string fname = argv[1];
    std::string size = argv[2];
    int n = stoi(size);

    int seg[400000];
    ReadFile(fname, &seg);


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

void ReadFile(std::string file_name, std::vector<std::vector<int>> * image_data) {

	//vectors is a 2D vector list of num
	// Opens the file for reading
	std::ifstream file(file_name);

	// Create a temporary 1D Vector of doubles
	std::vector<int> new_row;

	// Creates a string to hold each line in temporarily
	std::string str;

	// Iterates over the file, storing one line at a time into `str`
	while (std::getline(file, str)) {
		// Create a stringstream object with our line of integers from the file
		std::istringstream ss(str);

		// Create a double that will hold our extracted value from the string
		int token;

		// While there are still numbers in this string, extract them as doubles
		while (ss >> token) {
			// Push these doubles into our temp vector
			new_row.push_back(token);
		}

		// The line is empty, push our completed row into our 2D vector
		(*image_data).push_back(new_row);
		new_row.clear();
	}
}
 
 ```

## How to Run 
To construct the array you start by entering a number 'N'. <br />
To begin adding values you will follow the notion "1 Index Value" <br />
1 letting the terminal know you are attempting to add / edit in the array <br />
Index being index in which youre adding or editing the value. For example in an array with a length of 3 (N = 3) to then add a value at index 1 you would type "1 1 Value"<br />
The final number is the value at that index.<br />
So the terminal call "1 1 3" means that at the index of 1 the number that occupies that space is 3.<br />
You can then edit that number by changing the final value. So "1 1 0" would change the 3 to a 0 at i = 1.

This program allows you to also find the sum of either the whole array or even segmented.
This terminal call is initated by a '2' and then indexed by start finish with the next two numbers. So to add values from the index range 0-2 you would type "2 0 2" into the terminal.<br />

