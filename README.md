# Data-Analytics-portfolio

## Harsimran Sandhu - Portfolio 

#### Hey there, I am a Junior Data Analyst and here are some of the codes / project i've used to show my current skills in SQL, Tablaue, abd R.

## SQL

TASK - Write a query to print the contest_id, hacker_id, name, and the sums of total_submissions, total_accepted_submissions, total_views, and total_unique_views for each contest sorted by contest_id. Exclude the contest from the result if all four sums are. Data is partially stored in 5 different tables, Join them and do your analysis.

INPUT - 

`SELECT contests.contest_id, contests.hacker_id, contests.name, sum(total_submissions) ts, sum(total_accepted_submissions) tas, sum(total_views) tv, sum(total_unique_views) tuv
FROM Contests
JOIN Colleges
ON Colleges.contest_id = Contests.contest_id
JOIN Challenges
ON Challenges.college_id = Colleges.college_id
LEFT JOIN View_stats
ON view_stats.challenge_id = Challenges.challenge_id
LEFT JOIN submission_stats
ON submission_stats.challenge_id = challenges.challenge_id
GROUP BY contests.contest_id,contests.hacker_id,contests.name
HAVING sum(total_submissions + total_accepted_submissions + total_views + total_unique_views ) > 0
ORDER BY contests.contest_id; `

OUTPUT - 

`845 579 Rose 3301 1029 2747 957 
858 1053 Angela 1953 448 1740 636 
883 1055 Frank 2689 734 2153 667 
1793 2655 Patrick 2666 742 2269 769 
2374 2765 Lisa 6373 1947 7933 2154 
2963 2845 Kimberly 9471 2630 7528 2516 
3584 2873 Bonnie 6841 1720 6424 2051 
4044 3067 Michael 2859 1059 3188 970 
4249 3116 Todd 2418 616 2146 600 
4269 3256 Joe 3115 1042 3363 1004 
4483 3386 Earl 3988 1026 3355 911 
4541 3608 Robert 3670 1010 3532 975 
4601 3868 Amy 3991 1427 4500 1367 
4710 4255 Pamela 4402 1039 3979 1140 
4982 5639 Maria 5188 1394 4877 1359 
5913 5669 Joe 4518 1415 5827 1510 
5994 5713 Linda 6928 1928 6151 1879 
6939 6550 Melissa 6490 1917 7375 2082 
7266 6947 Carol 5969 1452 5449 1647 
7280 7030 Paula 3754 1135 2636 858 
7484 7033 Marilyn 7588 2216 8142 2210 
7734 7386 Jennifer 8214 2207 8853 2529 
7831 7787 Harry 7223 1805 6007 2074 
7862 8029 David 2748 813 2864 903 
8812 8147 Julia 1916 494 1865 572 
8825 8438 Kevin 5541 1671 5495 1627 
9136 8727 Paul 8279 2886 8131 2459 
9613 8762 James 8137 2217 8478 2539 
10568 8802 Kelly 5363 1826 6165 1886 
11100 8809 Robin 3701 1216 3847 1271 
12742 9203 Ralph 3443 866 3399 972 
12861 9644 Gloria 2947 964 2981 977 
12865 10108 Victor 3364 966 2365 852 
13503 10803 David 1109 314 963 259 
13537 11390 Joyce 3079 1133 3592 1115 
13612 12592 Donna 3698 1045 3501 1016 
14502 12923 Michelle 3673 1148 3158 1066 
14867 13017 Stephanie 4609 1351 5189 1187 
15164 13256 Gerald 4772 1603 4942 1487 
15804 13421 Walter 3317 1046 3546 1080 
15891 13569 Christina 4779 1570 4180 1531 
16063 14287 Brandon 4839 1535 5161 1674 
16415 14311 Elizabeth 9793 2856 9736 2924 
18477 14440 Joseph 2213 728 2352 777 
18855 16973 Lawrence 7693 2397 7966 2527 
19097 17123 Marilyn 7020 2134 6420 1890 
19575 17562 Lori 5222 1625 5692 1695 `
