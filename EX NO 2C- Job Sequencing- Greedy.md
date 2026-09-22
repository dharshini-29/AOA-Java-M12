
# EX 2C Job Sequencing using Greedy Approach
## AIM

To write a Java program using the **Greedy Approach** to schedule jobs before their deadlines and maximize the total profit.

## ALGORITHM

1. Start.
2. Read the number of jobs `n`.
3. Read the **job ID, deadline, and profit** for each job.
4. Sort the jobs in **descending order of profit**.
5. Find the maximum deadline.
6. Create time slots to schedule the jobs.
7. For each job, find a free slot from its deadline backwards.
8. If a free slot is found, schedule the job and add its profit.
9. Count the scheduled jobs.
10. Print the number of jobs and total profit.
11. Stop.

## Program:
```
/*
Developed by: K Vijay
Register Number:  212223040236
*/
import java.util.*;

public class JobScheduling {

    static class Job {
        int id, deadline, profit;

        Job(int id, int deadline, int profit) {
            this.id = id;
            this.deadline = deadline;
            this.profit = profit;
        }
    }

    public static int[] jobScheduling(Job[] jobs, int n) {
        Arrays.sort(jobs, (a, b) -> b.profit - a.profit);

        int maxDeadline = 0;
        for (Job job : jobs) {
            maxDeadline = Math.max(maxDeadline, job.deadline);
        }

        boolean[] slot = new boolean[maxDeadline + 1];
        int totalProfit = 0;
        int countJobs = 0;

        for (Job job : jobs) {
            for (int j = job.deadline; j > 0; j--) {
                if (!slot[j]) {
                    slot[j] = true;
                    totalProfit += job.profit;
                    countJobs++;
                    break;
                }
            }
        }

        return new int[]{countJobs, totalProfit};
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        Job[] jobs = new Job[n];

        for (int i = 0; i < n; i++) {
            int id = sc.nextInt();
            int deadline = sc.nextInt();
            int profit = sc.nextInt();
            jobs[i] = new Job(id, deadline, profit);
        }

        int[] result = jobScheduling(jobs, n);
        System.out.println(result[0] + " " + result[1]);
    }
}

```

## Output:

<img width="821" height="551" alt="image" src="https://github.com/user-attachments/assets/e59960d0-7182-4f2a-bead-6f588a1329ba" />


## Result:
The program successfully implemented and the expected output is verified.
