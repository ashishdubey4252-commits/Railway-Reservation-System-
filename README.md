import java.util.*;

class Train {
    int trainNo;
    String trainName, source, destination;
    int seats;

    Train(int trainNo, String trainName, String source, String destination, int seats) {
        this.trainNo = trainNo;
        this.trainName = trainName;
        this.source = source;
        this.destination = destination;
        this.seats = seats;
    }
}

public class RailwayReservationSystem {
    static Scanner sc = new Scanner(System.in);
    static ArrayList<Train> trains = new ArrayList<>();

    public static void main(String[] args) {
        trains.add(new Train(101, "Express A", "Delhi", "Mumbai", 50));
        trains.add(new Train(102, "Express B", "Chennai", "Bangalore", 40));

        while (true) {
            System.out.println("\n--- Railway Reservation System ---");
            System.out.println("1. View Trains");
            System.out.println("2. Book Ticket");
            System.out.println("3. Cancel Ticket");
            System.out.println("4. Exit");
            System.out.print("Enter choice: ");
            int choice = sc.nextInt();

            switch (choice) {
                case 1:
                    viewTrains();
                    break;
                case 2:
                    bookTicket();
                    break;
                case 3:
                    cancelTicket();
                    break;
                case 4:
                    System.out.println("Thank You!");
                    System.exit(0);
                default:
                    System.out.println("Invalid choice");
            }
        }
    }

    static void viewTrains() {
        for (Train t : trains) {
            System.out.println(t.trainNo + " " + t.trainName + " " + t.source + " -> " + t.destination + " Seats: " + t.seats);
        }
    }

    static void bookTicket() {
        System.out.print("Enter Train Number: ");
        int no = sc.nextInt();
        for (Train t : trains) {
            if (t.trainNo == no && t.seats > 0) {
                t.seats--;
                System.out.println("Ticket Booked Successfully!");
                return;
            }
        }
        System.out.println("No seats available or invalid train");
    }

    static void cancelTicket() {
        System.out.print("Enter Train Number: ");
        int no = sc.nextInt();
        for (Train t : trains) {
            if (t.trainNo == no) {
                t.seats++;
                System.out.println("Ticket Cancelled Successfully!");
                return;
            }
        }
        System.out.println("Invalid train number");
    }
}




