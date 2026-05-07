import java.util.Scanner;

public class FCFS_Scheduling {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input number of processes
        System.out.print("Enter number of processes: ");
        int n = sc.nextInt();

        int[] pid = new int[n];
        int[] at  = new int[n]; // Arrival Time
        int[] bt  = new int[n]; // Burst Time
        int[] ct  = new int[n]; // Completion Time
        int[] tat = new int[n]; // Turnaround Time
        int[] wt  = new int[n]; // Waiting Time

        // Read arrival time and burst time for each process
        for (int i = 0; i < n; i++) {
            pid[i] = i + 1;
            System.out.print("Enter Arrival Time for Process " + pid[i] + ": ");
            at[i] = sc.nextInt();
            System.out.print("Enter Burst Time for Process " + pid[i] + ": ");
            bt[i] = sc.nextInt();
        }

        // Sort processes by arrival time (simple bubble sort for clarity)
        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                if (at[j] > at[j + 1]) {
                    // swap arrival
                    int tmp = at[j]; at[j] = at[j + 1]; at[j + 1] = tmp;
                    // swap burst
                    tmp = bt[j]; bt[j] = bt[j + 1]; bt[j + 1] = tmp;
                    // swap pid
                    tmp = pid[j]; pid[j] = pid[j + 1]; pid[j + 1] = tmp;
                }
            }
        }

        // Calculate completion times
        if (n > 0) {
            ct[0] = at[0] + bt[0]; // first process completes at its arrival + burst
            for (int i = 1; i < n; i++) {
                // if CPU is idle until this process arrives
                if (at[i] > ct[i - 1]) {
                    ct[i] = at[i] + bt[i];
                } else {
                    ct[i] = ct[i - 1] + bt[i];
                }
            }
        }

        // Calculate TAT and WT
        for (int i = 0; i < n; i++) {
            tat[i] = ct[i] - at[i];   // Turnaround = Completion - Arrival
            wt[i]  = tat[i] - bt[i];  // Waiting = Turnaround - Burst
        }

        // Print header with fixed column widths so columns align
        System.out.println();
        System.out.printf("%-8s %5s %5s %6s %6s %6s%n",
                          "Process", "AT", "BT", "CT", "TAT", "WT");
        System.out.println("------------------------------------------------");

        // Print each process row with same formatting
        for (int i = 0; i < n; i++) {
            System.out.printf("%-8s %5d %5d %6d %6d %6d%n",
                              "P" + pid[i], at[i], bt[i], ct[i], tat[i], wt[i]);
        }

        // Calculate and print averages
        double sumTAT = 0, sumWT = 0;
        for (int i = 0; i < n; i++) {
            sumTAT += tat[i];
            sumWT  += wt[i];
        }
        double avgTAT = (n == 0) ? 0 : sumTAT / n;
        double avgWT  = (n == 0) ? 0 : sumWT / n;

        System.out.println("------------------------------------------------");
        System.out.printf("Average Turnaround Time: %.2f%n", avgTAT);
        System.out.printf("Average Waiting Time   : %.2f%n", avgWT);

        sc.close();
    }
}
