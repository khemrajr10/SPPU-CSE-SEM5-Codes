import java.util.Scanner;

public class SJF_Preemptive {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number of processes: ");
        int n = sc.nextInt();

        int[] bt = new int[n];
        int[] at = new int[n];
        int[] ct = new int[n];
        int[] wt = new int[n];
        int[] tat = new int[n];
        int[] remaining = new int[n];
        int[] finish = new int[n];

        System.out.println("Enter Arrival Time for each process:");
        for (int i = 0; i < n; i++) {
            System.out.print("P[" + (i + 1) + "]: ");
            at[i] = sc.nextInt();
        }

        System.out.println("Enter Burst Time for each process:");
        for (int i = 0; i < n; i++) {
            System.out.print("P[" + (i + 1) + "]: ");
            bt[i] = sc.nextInt();
            remaining[i] = bt[i];
            finish[i] = 0;
        }

        int time = 0, completed = 0, min, c;
        while (completed != n) {
            min = Integer.MAX_VALUE;
            c = n;
            for (int i = 0; i < n; i++) {
                if (at[i] <= time && finish[i] == 0 && remaining[i] < min && remaining[i] > 0) {
                    min = remaining[i];
                    c = i;
                }
            }
            if (c == n) {
                time++;
            } else {
                remaining[c]--;
                time++;
                if (remaining[c] == 0) {
                    ct[c] = time;
                    finish[c] = 1;
                    completed++;
                }
            }
        }

        float totalWT = 0, totalTAT = 0;
        for (int i = 0; i < n; i++) {
            tat[i] = ct[i] - at[i];
            wt[i] = tat[i] - bt[i];
            totalWT += wt[i];
            totalTAT += tat[i];
        }

        System.out.println("\nProcess\tAT\tBT\tWT\tTAT");
        for (int i = 0; i < n; i++) {
            System.out.println("P[" + (i + 1) + "]\t" + at[i] + "\t" + bt[i] + "\t" + wt[i] + "\t" + tat[i]);
        }

        System.out.println("\nAverage Waiting Time: " + (totalWT / n));
        System.out.println("Average Turnaround Time: " + (totalTAT / n));
    }
}
