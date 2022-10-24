# Data-Analytics-portfolio

## Harsimran Sandhu - Portfolio 

#### Hey there, I am a Junior Data Analyst and here are some of the codes / project i've used to show my current skills in SQL, Tablaue, Google Data Studio and R.

## Tableau Portfolio

![Tableau BreakFix Portfolio](https://prnt.sc/on2Xj4QkNZdQ)

Please access my dashboard here - https://public.tableau.com/app/profile/dokezar/viz/BreakFixTracker/Dashboard1

I built this Dashboard for a company to keep an eye over their Break Fix Tracker for all their locations.

## Google Data Studio

![Google Data Studio Portfolio](https://i.imgur.com/rRDNxt8.png)

Access the LIVE report on Google Data Studio here - https://datastudio.google.com/s/n994QkcngPw


## SQL

TASK - Write a query to print the contest_id, hacker_id, name, and the sums of total_submissions, total_accepted_submissions, total_views, and total_unique_views for each contest sorted by contest_id. Exclude the contest from the result if all four sums are. Data is partially stored in 5 different tables, Join them and do your analysis.

```
INPUT - 

WITH stats as (
    SELECT DISTINCT challenge_id, sum(total_views) total_view, sum(total_unique_views) total_unique_view
    FROM view_stats
    GROUP BY challenge_id
),
submission as (
    SELECT DISTINCT challenge_id, sum(total_submissions) total_submission, sum(total_accepted_submissions) total_accepted_submission
    FROM submission_stats
    GROUP BY challenge_id
)

SELECT contests.contest_id, contests.hacker_id, contests.name, sum(total_submission), sum(total_accepted_submission), sum(total_view), sum(total_unique_view)
FROM Contests

JOIN Colleges
ON contests.contest_id = colleges.contest_id

JOIN Challenges
ON Challenges.college_id = Colleges.college_id

LEFT JOIN stats
ON stats.challenge_id = Challenges.challenge_id

LEFT JOIN submission
ON submission.challenge_id = Challenges.challenge_id

GROUP BY contests.contest_id, contests.hacker_id, contests.name
HAVING sum(total_submission + total_accepted_submission + total_view + total_unique_view ) > 0
ORDER BY contests.contest_id;

OUTPUT - 

845 579 Rose 1987 580 1635 566 
858 1053 Angela 703 160 1002 384 
883 1055 Frank 1121 319 1217 338 
1793 2655 Patrick 1337 360 1216 412 
2374 2765 Lisa 2733 815 3368 904 
2963 2845 Kimberly 4306 1221 3603 1184 
3584 2873 Bonnie 2492 652 3019 954 
4044 3067 Michael 1323 449 1722 528 
4249 3116 Todd 1452 376 1767 463 
4269 3256 Joe 1018 372 1766 530 
4483 3386 Earl 1911 572 1644 477 
4541 3608 Robert 1886 516 1694 504 
4601 3868 Amy 1900 639 1738 548 
4710 4255 Pamela 2752 639 2378 705 
4982 5639 Maria 2705 759 2558 711 
5913 5669 Joe 2646 790 3181 835 
5994 5713 Linda 3369 967 3048 954 
6939 6550 Melissa 2842 859 3574 1004 
7266 6947 Carol 2758 665 3044 835 
7280 7030 Paula 1963 554 886 259 
7484 7033 Marilyn 3217 934 3795 1061 
7734 7386 Jennifer 3780 1015 3637 1099 
7831 7787 Harry 3190 883 2933 1012 
7862 8029 David 1738 476 1475 472 
8812 8147 Julia 1044 302 819 266 
8825 8438 Kevin 2624 772 2187 689 
9136 8727 Paul 4205 1359 3125 954 
9613 8762 James 3438 943 3620 1046 
10568 8802 Kelly 1907 620 2577 798 
11100 8809 Robin 1929 613 1883 619 
12742 9203 Ralph 1523 413 1344 383 
12861 9644 Gloria 1596 536 2089 623 
12865 10108 Victor 2076 597 1259 418 
13503 10803 David 924 251 584 167 
13537 11390 Joyce 1381 497 1784 538 
13612 12592 Donna 1981 550 1487 465 
14502 12923 Michelle 1510 463 1830 545 
14867 13017 Stephanie 2471 676 2291 574 
15164 13256 Gerald 2570 820 2085 607 
15804 13421 Walter 1454 459 1396 476 
15891 13569 Christina 2188 710 2266 786 
16063 14287 Brandon 1804 580 1621 521 
16415 14311 Elizabeth 4535 1366 3631 1071 
18477 14440 Joseph 1320 391 1419 428 
18855 16973 Lawrence 2967 1020 3371 1011 
19097 17123 Marilyn 2956 807 2554 750 
19575 17562 Lori 2590 863 2627 760 
```

