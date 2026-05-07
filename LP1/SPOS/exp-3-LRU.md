import java.util.Scanner;

class LRU {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);

        System.out.println("LRU Page Replacement Algorithm");

        // Step 1: Input number of frames
        System.out.print("Enter number of frames: ");
        int f = sc.nextInt();
        int frame[] = new int[f];

        // Initialize frames as empty (-1)
        for (int i = 0; i < f; i++)
            frame[i] = -1;

        // Step 2: Input number of pages
        System.out.print("Enter number of pages: ");
        int n = sc.nextInt();
        int pages[] = new int[n];

        System.out.println("Enter the page numbers:");
        for (int i = 0; i < n; i++)
            pages[i] = sc.nextInt();

        int pageFaults = 0;

        // Step 3: Process each page
        for (int i = 0; i < n; i++) {
            int page = pages[i];
            boolean found = false;

            // Check if page is already present in frames
            for (int j = 0; j < f; j++) {
                if (frame[j] == page) {
                    found = true;
                    break;
                }
            }

            // Step 4: If not found, page fault occurs
            if (!found) {
                int empty = -1;

                // Check for an empty frame
                for (int j = 0; j < f; j++) {
                    if (frame[j] == -1) {
                        empty = j;
                        break;
                    }
                }

                // If empty frame found, place the page there
                if (empty != -1) {
                    frame[empty] = page;
                } else {
                    // Find least recently used page
                    int leastIndex = 0;
                    int lastUse = i;

                    for (int j = 0; j < f; j++) {
                        int k;
                        for (k = i - 1; k >= 0; k--) {
                            if (frame[j] == pages[k])
                                break;
                        }
                        if (k < lastUse) {
                            lastUse = k;
                            leastIndex = j;
                        }
                    }

                    frame[leastIndex] = page; // Replace LRU page
                }

                pageFaults++;
            }

            // Step 5: Display current frames
            System.out.print("Frames: ");
            for (int j = 0; j < f; j++)
                System.out.print(frame[j] + " ");
            System.out.println();
        }

        System.out.println("Total Page Faults: " + pageFaults);
    }
}
