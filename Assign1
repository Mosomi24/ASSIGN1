import java.util.Scanner;

class Car {
    private String model;
    private String make;
    private boolean isAvailable;
    private double rentalFee;

    public Car(String model, String make, double rentalFee) {
        this.model = model;
        this.make = make;
        this.isAvailable = true;
        this.rentalFee = rentalFee;
    }

    public String getModel() {
        return model;
    }

    public String getMake() {
        return make;
    }

    public boolean isAvailable() {
        return isAvailable;
    }

    public void setAvailable(boolean available) {
        isAvailable = available;
    }

    public double getRentalFee() {
        return rentalFee;
    }

    public void displayInfo() {
        System.out.println("Car: " + make + " " + model + " | Available: " + isAvailable + " | Rental Fee: " + rentalFee + " Shillings");
    }
}

class Customer {
    private String name;
    private int id;

    public Customer(String name, int id) {
        this.name = name;
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public int getId() {
        return id;
    }
}

class RentalAgency {
    private Car[] cars;
    private int carCount;

    public RentalAgency(int size) {
        cars = new Car[size];
        carCount = 0;
    }

    public void addCar(Car car) {
        if (carCount < cars.length) {
            cars[carCount] = car;
            carCount++;
        } else {
            System.out.println("No more space to add new cars.");
        }
    }

    public boolean rentCar(Customer customer, String model) {
        for (int i = 0; i < carCount; i++) {
            if (cars[i].getModel().equals(model) && cars[i].isAvailable()) {
                cars[i].setAvailable(false);
                System.out.println(customer.getName() + " rented " + model + " for " + cars[i].getRentalFee() + " Shillings");
                return true;
            }
        }
        System.out.println("Car not available for rent.");
        return false;
    }

    public void returnCar(String model) {
        for (int i = 0; i < carCount; i++) {
            if (cars[i].getModel().equals(model) && !cars[i].isAvailable()) {
                cars[i].setAvailable(true);
                System.out.println(model + " has been returned.");
                return;
            }
        }
        System.out.println("Car not found or already available.");
    }

    public void displayAvailableCars() {
        System.out.println("Available cars:");
        for (int i = 0; i < carCount; i++) {
            if (cars[i].isAvailable()) {
                cars[i].displayInfo();
            }
        }
    }
}

public class Main {
    public static void main(String[] args) {
        RentalAgency agency = new RentalAgency(5);

        Car car1 = new Car("Model S", "Tesla", 15000.0);
        Car car2 = new Car("Civic", "Honda", 7500.0);

        agency.addCar(car1);
        agency.addCar(car2);

        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter your name: ");
        String customerName = scanner.nextLine();
        Customer customer1 = new Customer(customerName, 101);

        agency.displayAvailableCars();
        
        System.out.print("Enter the model of the car you want to rent: ");
        String selectedModel = scanner.nextLine();

        boolean rented = agency.rentCar(customer1, selectedModel);
        if (!rented) {
            System.out.println("Rental failed.");
        }

        agency.displayAvailableCars();

        System.out.print("Enter the model of the car you want to return: ");
        String returnModel = scanner.nextLine();
        agency.returnCar(returnModel);
        agency.displayAvailableCars();

        scanner.close();
    }
}
