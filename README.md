# Banking

package homework;

import java.util.Scanner;

public class BankingApplications 
{
	//scanner to take the input from the user
	Scanner sc = new Scanner(System.in);
	String Acc_No;
	String Acc_Holdername;
	String Acc_type;
	//Re_acc_no is similar as acc no used to verify while depositing withdrawal and enquiry of account
	String Re_acc_no;
	double Balance;
	
	
	//Method to display available options
	public void show()
	{
		System.out.println("\r1. Create Account");
        System.out.println("2. show Detail");
        System.out.println("3. Deposite");
        System.out.println("4. Withdraw");
        System.out.println("5. Balance Enquiry");
        System.out.println("6. Exit");
	}
	
	//Method to create a new bank account
	public void create()
	{
		System.out.println("You Should Create an Bank Acc \r");
		System.out.println("Enter Bank account No : ");
		Acc_No=sc.next();
		System.out.println("Enter bank account holder Name : ");
		Acc_Holdername=sc.next();
		System.out.println("Enter bank account type : ");
		Acc_type=sc.next();
		System.out.println("Enter the amount you want keep in bank ");
		Balance=sc.nextLong();
	}
	
	// Method to display account details
	public void showdetail ()
	{
		System.out.println("Name of account holder: " + Acc_Holdername);  
        System.out.println("Account no.: " + Acc_No);  
        System.out.println("Account type: " + Acc_type);  
        System.out.println("Balance: " + Balance);	
	}
	
	//Method to deposit money into the account
	public void deposit()
	{
		System.out.println("Re-enter your acc no for verification : ");
		Re_acc_no=sc.next();
		//here acc_no and Re_acc_no is compared so unauthorised person cannot access it
		//when ever they are equal only then u can proceed
			if(Acc_No.equals(Re_acc_no))
			{
				System.out.println("Enter the amount you want to deposit : ");
				long Deposit=sc.nextLong();
			    Balance=Deposit+Balance;
				System.out.println("Your total balance will be :  "+Balance);	
			}
			else
			{
				System.out.println("Invalid account no you can deposit the money");
			}
				
	}
	
	// Method to withdraw money from the account
	public void withdrawal ()
	{
		System.out.println("Re-enter your acc no for verification : ");
		Re_acc_no=sc.next();
		//here acc_no and Re_acc_no is compared so unauthorised person cannot access it
		//when ever they are equal only then u can proceed
			if(Acc_No.equals(Re_acc_no))
			{
			System.out.println("Enter the amount you want to withdraw : ");
			long Withdraw =sc.nextLong();
			// Check if there is sufficient balance
					if(Withdraw<=Balance)
					{
						Balance=Balance-Withdraw;
						System.out.println("Your remaning amount is : "+Balance);
					}
					else
					{
						System.out.println("You have insufficient Balance");
					}
			}
			else
			{
				System.out.println("Invalid account no you can Withdraw the money");
			}
		
	}
	
	 // Method to check the account balance 
	public void balance() 
	{
		System.out.println("Re-enter your acc no for verification : ");
		Re_acc_no=sc.next();
		//here acc_no and Re_acc_no is compared so unauthorised person cannot access it
		//when ever they are equal only then u can proceed
			if(Acc_No.equals(Re_acc_no))
			{
				System.out.println("Your Current Balance is : "+Balance);
			}
			else
			{
				System.out.println("Invalid account no you can Withdraw the money");
			}
			
		
	}
	
	
	// Method to handle user interactions and menu choices
	public void switching ()
	{
		
		int choice;
		do
		{
			Scanner sc = new Scanner(System.in);
			show();
			System.out.println("Make a choice : ");
			choice=sc.nextInt();
			switch (choice) 
			{
			case 1:
				create();
				break;
			case 2:  
				showdetail();
				break;
			case 3:
				deposit();
				break;
			case 4:
				withdrawal();
				break;
			case 5:
				balance();
				break;
			case 6:
				System.out.println("*********Thank You for Banking With us**********");
				System.out.println("**************Visit Again************");
				break;

			default:
				System.out.println("wrong Input  ");
				break;
				
			}
			
		}
		
		while(choice != 6);
		
	}
	
	
	public static void main(String[] args) 
	{
		
		BankingApplications b = new BankingApplications();
		System.out.println("*********Welcome To Banking-Application*********");
		b.switching();	
	}
}
