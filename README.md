//# SimpleBank
//A simple bank program is a basic computer application designed to perform fundamental banking operations. It typically allows users to create accounts, make deposits, withdrawals, and check balances. 


import java.util.Scanner;

public class Banko {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        boolean display = true;
        boolean hasAccount = false;
        String name = "";
        String info = "";
        double initial = 0;

        while (display) {
            System.out.println();
            System.out.println("  *WELCOME TO PHILIPPINE BANK*");
            System.out.println("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~");
            System.out.println("| [1] New Account              |");
            System.out.println("| [2] Transaction              |");
            System.out.println("| [3] Exit                     |");
            System.out.println("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~");
            System.out.print("Select Option: ");

            try {
                int choice = in.nextInt();
                in.nextLine();

                switch (choice) {
                    case 1:
                        System.out.println();
                        System.out.print("Enter your full name: ");
                        name = in.nextLine();
                        System.out.println();
                        System.out.print("Course/Year/Section: ");
                        info = in.nextLine();

                        boolean invalidDeposit = true;

                        while (invalidDeposit) {
                            System.out.println();
                            System.out.print("Enter initial deposit: ");
                            if (in.hasNextDouble()) {
                                initial = in.nextDouble();
                                in.nextLine();
                                invalidDeposit = false;
                                hasAccount = true;
                                System.out.println("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~");
                                System.out.println("Successfully Registered!");
                                System.out.println("Initial Balance: " + initial);
                                System.out.println("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~");
                                System.out.println();
                                            System.out.print("Proceed to Menu? ('Y' for yes 'N' for no):");
                                            char menu = in.next().charAt(0);
                                                 if (menu == 'Y' || menu == 'y'){
                                                 display = true;
                                             }
                                        else if (menu == 'N' || menu == 'n'){
                                            System.out.println("Thank you for trusting Philippine Bank!");
                                            display = false;
                                        }
                            } else {
                                in.nextLine();
                                System.out.println("Invalid Input. Enter a number.");
                            }
                        }
                        break;

                    case 2:
                        if (!hasAccount) {
                            System.out.println("You must create an account first.");
                        } else {
                            System.out.println();
                            System.out.println("Account Name: " + name);
                            System.out.println("----------------------------------");
                            System.out.println("[1] Deposit");
                            System.out.println("[2] Withdraw");
                            System.out.println("[3] Check Account Balance");
                            System.out.println("----------------------------------");
                            System.out.print("Select option: ");
                            int dpw = in.nextInt();
                            in.nextLine();

                            switch (dpw) {
                                case 1:
                                    double depositAmount;
                                    System.out.println();
                                    System.out.println("Student Name: " + name);
                                    System.out.println("Account Balance: " + initial);
                                    System.out.println();
                                    System.out.print("Enter amount to deposit: ");
                                    if (in.hasNextDouble()) {
                                        depositAmount = in.nextDouble();
                                        in.nextLine();
                                        initial += depositAmount;
                                        System.out.println("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~");
                                        System.out.println("You successfully added " + depositAmount + " to your account.");
                                        System.out.println("Total Account Balance: " + initial);
                                        System.out.println("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~");
                                        System.out.println();
                                            System.out.print("Proceed to Menu? ('Y' for yes 'N' for no):");
                                            char menu = in.next().charAt(0);
                                                 if (menu == 'Y' || menu == 'y'){
                                                 display = true;
                                             }
                                        else if (menu == 'N' || menu == 'n'){
                                            System.out.println("Thank you for trusting Philippine Bank!");
                                            display = false;
                                        }
                                    } else {
                                        in.nextLine();
                                        System.out.println("Invalid amount. Please try again.");
                                    }
                                    break;

                                case 2:
                                    double withdrawAmount;
                                    System.out.println();
                                    System.out.println("Account Balance: " + initial);
                                    System.out.print("Enter amount to withdraw: ");
                                    if (in.hasNextDouble()) {
                                        withdrawAmount = in.nextDouble();
                                        in.nextLine();
                                        if (withdrawAmount <= initial) {
                                            initial -= withdrawAmount;
                                            System.out.println("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~");
                                            System.out.println("You successfully withdrew " + withdrawAmount + " from your account.");
                                            System.out.println("Total Account Balance: " + initial);
                                            System.out.println("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~");

                                            System.out.println();
                                            System.out.print("Proceed to Menu? ('Y' for yes 'N' for no):");
                                            char menu = in.next().charAt(0);
                                                 if (menu == 'Y' || menu == 'y'){
                                                 display = true;
                                             }
                                        else if (menu == 'N' || menu == 'n'){
                                            System.out.println("Thank you for trusting Philippine Bank!");
                                            display = false;
                                        }
                                        } else {
                                            System.out.println();
                                            System.out.println("Insufficient funds. Please try again.");
                                        }
                                    } else {
                                        in.nextLine();
                                        System.out.println();
                                        System.out.println("Invalid amount. Please try again.");
                                    }
                                    break;

                                case 3:
                                    System.out.println();
                                    System.out.println("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~");
                                    System.out.println("Account Name: " + name);
                                    System.out.println("Student Information: " + info);
                                    System.out.println("Account Balance: " + initial);
                                    System.out.println("~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~");
                                    
                                    System.out.println();
                                    System.out.print("Proceed to Menu? ('Y' for yes 'N' for no):");
                                    char menu = in.next().charAt(0);
                                        if (menu == 'Y' || menu == 'y'){
                                            display = true;
                                        }
                                        else if (menu == 'N' || menu == 'n'){
                                            System.out.println("Thank you for trusting Philippine Bank!");
                                            display = false;
                                        }
                                    break;

                                default:
                                    System.out.println("Invalid option. Please try again.");
                                    break;
                            }
                        }
                        break;

                    case 3:
                        display = false;
                        System.out.println("Thank you for trusting Philippine Bank!");
                        break;

                    default:
                        System.out.println("Invalid option. Please try again.");
                        break;
                }
            } catch (Exception e) {
                in.nextLine(); 
                System.out.println();
                System.out.println("Invalid input. Please try again.");
            }
        }
    }
}
