## Code Streak
### *Result* : *Draw* (codearina)

## Problem 


Roy is working on HackerEarth Profile. Right now he is working on User Statistics.
One of the statistics data (Code Streak) is as follows:

Given the User Activity Data, find the maximum number of continuous correct solutions submitted by any user.
Seems easy eh? Here's the catch! In order to maximize this number a user could have submitted a correct answer to the same problem which he has already solved. Now such cases cannot be tolerated. (See test case for clarification). 
Also in all the continuous correct submissions multiple correct submissions to same problem should be counted only once.

User Activity Data will be as follows:
Total number of submissions by the user - N
For each submission its Submission ID - S and Result - R (Solved or Unsolved) will be given.
Solved is represented by integer 1 and Unsolved by 0.

Input:
First line contains integer T - number of test cases. T test cases follow. First line of each test case will contain N. Next N lines each will contain two space separated integers S and R.

Ouput:
For each test case output in a single line the required answer.

Constraints:
1 <= T <= 1000
1 <= N <= 1000000 (106)
1 <= S <= 1000000 (106)
0 <= R <= 1

Note: Sum of N over all the test cases in each file does not exceed 1000000 (106)

SAMPLE INPUT 
3
6
1 0
2 1
3 1
4 1
5 1
6 0
5
1 1
2 0
3 1
1 1
2 1
4
1 1
2 1
2 1
3 1
SAMPLE OUTPUT 
4
2
3
Explanation
In first test case, submissions from second to fifth are all correct and all are unique. None of the questions were solved before. So answer is 4.

In second tests case, longest range of correct submission is third to fifth i.e answer should be 3. But fourth submission should not counted since it has already been solved once. Hence the answer is 2.

Third test case is quite obvious now.


`#include <bits/stdc++.h>

using namespace std; 
class codeStreak { 
    int *results; 
    long int len; 
    long int ones; 
    public : 
        codeStreak(long int s){ 
            results = new int[s]();
            len = s;
            ones = 0;
        }
        void insert(int pos, int res) {
            if(res){
                results[pos-1] = 1;
            }
        }
        int countOne(){
            for(long int i = 0; i < len; i++) {
                if(results[i])
                    ones++;
            }
            return ones;
        }
};
main() {
    int t;
    cin >> t;
    int n,p,r;
    int *res = new int[t];
    for(int test = 0; test < t; test++) {
        //logic
        cin >> n;
        codeStreak c(n);
        for(int i = 0; i < n; i++) {
            cin >> p;
            cin >> r;
            c.insert(p,r);
        }
        res[test] = c.countOne();
    }
    sort(res, res+t);
    for(int i = 0; i < t; i++) {
        cout << res[i] << endl;
    }
}`
