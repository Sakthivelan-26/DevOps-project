
package com.example.todo;

import java.util.*;
public class App 
{
    static String[] seats = new String[11]; // Seat 1 to 10 (0 unused)

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int choice;

        // Initialize all seats as empty
        for (int i = 1; i <= 10; i++) {
            seats[i] = "Empty";
        }

        do {
            System.out.println("\n=== Online Bus Reservation System ===");
            System.out.println("1. View Seats");
            System.out.println("2. Reserve Seat");
            System.out.println("3. Cancel Reservation");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            choice = sc.nextInt();
            sc.nextLine(); // Clear newline

            switch (choice) {
                case 1:
                    viewSeats();
                    break;
                case 2:
                    reserveSeat(sc);
                    break;
                case 3:
                    cancelSeat(sc);
                    break;
                case 4:
                    System.out.println("Thank you for using the system!");
                    break;
                default:
                    System.out.println("Invalid choice. Try again.");
            }
        } while (choice != 4);

        sc.close();
    }

    static void viewSeats() {
        System.out.println("\n--- Seat Status ---");
        for (int i = 1; i <= 10; i++) {
            System.out.println("Seat " + i + ": " + seats[i]);
        }
    }

    static void reserveSeat(Scanner sc) {
        System.out.print("Enter seat number to reserve (1-10): ");
        int seat = sc.nextInt();
        sc.nextLine(); // Clear newline

        if (seat < 1 || seat > 10) {
            System.out.println("Invalid seat number.");
        } else if (!seats[seat].equals("Empty")) {
            System.out.println("Seat already reserved by " + seats[seat]);
        } else {
            System.out.print("Enter passenger name: ");
            String name = sc.nextLine();
            seats[seat] = name;
            System.out.println("Seat " + seat + " reserved successfully for " + name + ".");
        }
    }

    static void cancelSeat(Scanner sc) {
        System.out.print("Enter seat number to cancel (1-10): ");
        int seat = sc.nextInt();
        sc.nextLine(); // Clear newline

        if (seat < 1 || seat > 10) {
            System.out.println("Invalid seat number.");
        } else if (seats[seat].equals("Empty")) {
            System.out.println("Seat is already empty.");
        } else {
            System.out.println("Reservation for " + seats[seat] + " cancelled.");
            seats[seat] = "Empty";
        }
    }
}

