import java.util.Scanner;

public class PriorityNonPreemptive {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input number of processes
        System.out.print("Enter number of processes: ");
        int n = sc.nextInt();

        int[] at = new int[n];   // Arrival Time
        int[] bt = new int[n];   // Burst Time
        int[] pr = new int[n];   // Priority (lower = higher)
        int[] ct = new int[n];   // Completion Time
        int[] tat = new int[n];  // Turnaround Time
        int[] wt = new int[n];   // Waiting Time
        boolean[] done = new boolean[n]; // To mark completed processes

        // Read inputs
        for (int i = 0; i < n; i++) {
            System.out.println("\nProcess " + (i + 1));
            System.out.print("Arrival Time : ");
            at[i] = sc.nextInt();
            System.out.print("Burst Time   : ");
            bt[i] = sc.nextInt();
            System.out.print("Priority (lower = higher): ");
            pr[i] = sc.nextInt();
        }

        int time = 0;       // Current system time
        int completed = 0;  // Number of completed processes

        // Loop until all processes are done
        while (completed < n) {
            int idx = -1;
            int bestPriority = Integer.MAX_VALUE;

            // Find process with highest priority that has arrived and not done
            for (int i = 0; i < n; i++) {
                if (!done[i] && at[i] <= time) {
                    if (pr[i] < bestPriority) {
                        bestPriority = pr[i];
                        idx = i;
                    } else if (pr[i] == bestPriority && at[i] < at[idx]) {
                        // If same priority, choose the one that arrived earlier
                        idx = i;
                    }
                }
            }

            if (idx != -1) {
                // Execute the selected process
                time += bt[idx];
                ct[idx] = time;
                tat[idx] = ct[idx] - at[idx];
                wt[idx] = tat[idx] - bt[idx];
                done[idx] = true;
                completed++;
            } else {
                // If no process arrived yet, move time forward
                time++;
            }
        }

        // Display result in aligned table
        System.out.println();
        System.out.printf("%-8s %5s %5s %9s %6s %6s %6s%n",
                "Process", "AT", "BT", "Priority", "CT", "TAT", "WT");
        System.out.println("----------------------------------------------------------");

        double sumTAT = 0, sumWT = 0;
        for (int i = 0; i < n; i++) {
            System.out.printf("%-8s %5d %5d %9d %6d %6d %6d%n",
                    "P" + (i + 1), at[i], bt[i], pr[i], ct[i], tat[i], wt[i]);
            sumTAT += tat[i];
            sumWT += wt[i];
        }

        System.out.println("----------------------------------------------------------");
        System.out.printf("Average Turnaround Time: %.2f%n", sumTAT / n);
        System.out.printf("Average Waiting Time   : %.2f%n", sumWT / n);

        sc.close();
    }
}
