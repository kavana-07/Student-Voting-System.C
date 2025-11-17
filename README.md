#include <stdio.h> 
#include <string.h> 
 
#define MAX_CANDIDATES 3 
#define MAX_VOTERS 100 
 
// Structure to hold candidate details 
struct Candidate { 
    char name[50]; 
    int votes; 
}; 
 
int main() { 
    struct Candidate candidates[MAX_CANDIDATES]; 
    int totalVoters, choice; 
 
    // Initialize candidate names and votes 
    strcpy(candidates[0].name, "Anil"); 
    strcpy(candidates[1].name, "Bhuvi"); 
    strcpy(candidates[2].name, "Samay"); 
 
    for (int i = 0; i < MAX_CANDIDATES; i++) { 
        candidates[i].votes = 0; 
    } 
 
    printf("Enter the number of voters: "); 
    scanf("%d", &totalVoters); 
 
    for (int i = 0; i < totalVoters; i++) { 
        printf("\nVoter %d, please cast your vote:\n", i + 1); 
        for (int j = 0; j < MAX_CANDIDATES; j++) { 
            printf("%d. %s\n", j + 1, candidates[j].name); 
        } 
 
        printf("Enter your choice (1-%d): ", MAX_CANDIDATES); 
        scanf("%d", &choice); 
 
        if (choice >= 1 && choice <= MAX_CANDIDATES) { 
            candidates[choice - 1].votes++; 
            printf("Vote recorded for %s.\n", candidates[choice - 1].name); 
        } else { 
            printf("Invalid choice! Vote not recorded.\n"); 
        } 
    } 
 
    // Display results 
    printf("\n--- Voting Results ---\n"); 
    for (int i = 0; i < MAX_CANDIDATES; i++) { 
        printf("%s: %d votes\n", candidates[i].name, candidates[i].votes); 
    } 
 
    // Determine the winner 
    int maxVotes = candidates[0].votes; 
    int winnerIndex = 0; 
    for (int i = 1; i < MAX_CANDIDATES; i++) { 
        if (candidates[i].votes > maxVotes) { 
            maxVotes = candidates[i].votes; 
            winnerIndex = i; 
        } 
    } 
 
    // Check for tie 
    int tie = 0; 
    for (int i = 0; i < MAX_CANDIDATES; i++) { 
        if (i != winnerIndex && candidates[i].votes == maxVotes) { 
            tie = 1; 
            break; 
        } 
    } 
 
    if (tie) { 
        printf("Result: It's a tie!\n"); 
    } else { 
        printf("Winner: %s\n", candidates[winnerIndex].name); 
    } 
 
    return 0; 
} 
