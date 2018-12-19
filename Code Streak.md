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


`
#include <bits/stdc++.h> --
using namespace std; <br>
class codeStreak { <br>
    int *results; <br>
    long int len; <br>
    long int ones; <br>
    public : <br>
        codeStreak(long int s){ <br>
            results = new int[s]();<br>
            len = s;<br>
            ones = 0;<br>
        }<br>
        void insert(int pos, int res) {<br>
            if(res){<br>
                results[pos-1] = 1;<br>
            }<br>
        }<br>
        int countOne(){<br>
            for(long int i = 0; i < len; i++) {<br>
                if(results[i])<br>
                    ones++;<br>
            }<br>
            return ones;<br>
        }<br>
};<br>
main() {<br>
    int t;<br>
    cin >> t;<br>
    int n,p,r;<br>
    int *res = new int[t];<br>
    for(int test = 0; test < t; test++) {<br>
        //logic<br>
        cin >> n;<br>
        codeStreak c(n);<br>
        for(int i = 0; i < n; i++) {<br>
            cin >> p;<br>
            cin >> r;<br>
            c.insert(p,r);<br>
        }<br>
        res[test] = c.countOne();<br>
    }<br>
    sort(res, res+t);<br>
    for(int i = 0; i < t; i++) {<br>
        cout << res[i] << endl;<br>
    }<br>
}<br>
`
