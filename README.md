package pack;



public class Awards { // We created the Customer DB class and included the getCustomer method which allows for the acceptance of the customer

    private int awardRank;
    private double gpa;
    private String awardString;
    
    
    private final String SummaCumLaude = "Graduated With Highest Distinction";
    private final String MagnaCumLaude = "Graduated With Great Distinction";
    private final String CumLaude = "Graduated With Distinction";
    
    public Awards(double gpa) { // Created method for awards
        this.gpa = gpa; // Here we used the this method (17)
        this.awardString = getAwards();
    }

    public String getAwards() {
        String returnValue;
        //We created these if else statements as a method to return what gpa reward they are eligable for based on the number value the program runs. (10)
        if (gpa >= 3.5 && gpa < 3.7) {
            returnValue = "You have qualified for the Cum Laude reward";
            awardRank = 3;
        } else if (gpa > 3.7 && gpa < 3.9) {
            returnValue = "You have qaulified for the Magna Cum Laude reward";
            awardRank = 2;
        } else if (gpa >= 3.9 && gpa <= 4.0) {
            returnValue = "You have qaulified for the Summa Cum Laude reward";
            awardRank = 1;
        } else {
            returnValue = "";
            awardRank = 4;
        }
        
        switch (awardRank) {  //We used a switch statement here to help print the award rank (4)
            case 1: {
                returnValue = SummaCumLaude + "\n\t" + returnValue;
                break;
            }
            case 2: {
                returnValue = MagnaCumLaude + "\n\t"  + returnValue;
                break;
            }
            case 3: {
                returnValue = CumLaude + "\n\t"  + returnValue;
                break;
            }
            case 4: {
                returnValue = "";
                break;
            }
            default: {
                returnValue = "";
                break;
            }
        }
        return returnValue;
    }
}


package pack;


import java.util.Scanner; //Here is where we imported a scanner (1)
// We added multiple classes which are awards,data and test

public class Data {
    // Here we used an array for the letter grades, grade values and percents (11)
    
    // Constant final was used (3) displayed in lines 12,14,16 are different variables we used (3)
   
    final static String[] letterGrades = {"A+", "A", "A-", "B+", "B", "B-", "C+", "C", "C-", "D+", "D", "F"};
    // Double array for grade values
    final static double[] gradeValues = {4.0, 4.0, 3.7, 3.3, 3.0, 2.7, 2.3, 2.0, 1.7, 1.3, 1.0, 0.0};
    // Int aaray for percentage grades
    final static int[] percentGrades = {97, 93, 90, 87, 83, 80, 77, 73, 70, 67, 65, 0};
    
    
    private int courseCount, creditCount = 0; // Example of three variables we used Course Count, course score, course credits 2
    private int courseScore[];
    private int courseCredits[];
    
    private int minScore = 0, maxScore = 100;
    

    private double gpa;

    public Data(Scanner scan) { // Here is where we used a constructor it helped intialized the new created object (14)
        System.out.print("Please enter the total number of courses you have completed so far: ");
        courseCount = scan.nextInt();
        
        courseScore = new int[courseCount];
        courseCredits = new int[courseCount];
        
        for(int i = 0; i < courseScore.length; i++) {  // Used a for loop to help us keep reprinting the number of 
            System.out.println("Please score  points out of (?/100) for course [" + (i+1) +"] out of [" + courseCount + "]");
            courseScore[i] = scan.nextInt();
            System.out.println("Please number of credits for course [" + (i+1) +"] out of [" + courseCount + "]");
            courseCredits[i] = scan.nextInt();
            creditCount += courseCredits[i];
            // Using Math class min and max from the Standard Java Library (15)
            minScore = Math.min(minScore, courseScore[i]); // We used a math class method in 42 and 43(7)
            maxScore = Math.max(maxScore, courseScore[i]);
            gpa += (scoreToScale(courseScore[i]) * courseCredits[i]);
        }
        gpa = gpa / creditCount;
    }

    public double getGPA() {
        return gpa;
    }

    public void setGPA(double gpa) {
        this.gpa = gpa; // Here we used the this method (17)
    }
    //Here we used a method passing argument by values(9) and here you can also see examples of returning values from methods line 57 -110(10)
    private static double scoreToScale(int score) { // If else statement where used to return the gpa value
        if(score >= percentGrades[0])
            return gradeValues[0];
        else if(score >= percentGrades[1])
            return gradeValues[1];
        else if(score >= percentGrades[2])
            return gradeValues[2];
        else if(score >= percentGrades[3])
            return gradeValues[3];
        else if(score >= percentGrades[4])
            return gradeValues[4];
        else if(score >= percentGrades[5])
            return gradeValues[5];
        else if(score >= percentGrades[6])
            return gradeValues[6];
        else if(score >= percentGrades[7])
            return gradeValues[7];
        else if(score >= percentGrades[8])
            return gradeValues[8];
        else if(score >= percentGrades[9])
            return gradeValues[9];
        else if(score >= percentGrades[10])
            return gradeValues[10];
        else if(score >= percentGrades[11])
            return gradeValues[11];
        return 0.0;
    }
    
    private static String scoreToGrade(int score) {
        if(score >= percentGrades[0])
            return letterGrades[0];
        else if(score >= percentGrades[1])
            return letterGrades[1];
        else if(score >= percentGrades[2])
            return letterGrades[2];
        else if(score >= percentGrades[3])
            return letterGrades[3];
        else if(score >= percentGrades[4])
            return letterGrades[4];
        else if(score >= percentGrades[5])
            return letterGrades[5];
        else if(score >= percentGrades[6])
            return letterGrades[6];
        else if(score >= percentGrades[7])
            return letterGrades[7];
        else if(score >= percentGrades[8])
            return letterGrades[8];
        else if(score >= percentGrades[9])
            return letterGrades[9];
        else if(score >= percentGrades[10])
            return letterGrades[10];
        else if(score >= percentGrades[11])
            return letterGrades[11];
        return "Invalid score";
    }
    
    public void displayAll() {
        String outString = "";
        for (int i = 0; i < courseCount; i++) { // conditional operators(5) and arithmetical operators (6)
            outString += "(" + (i + 1) + ") - " + courseScore[i] + "/100\t" + scoreToGrade(courseScore[i]) + "\n";
        }
        System.out.println(outString);
        System.out.println("Minimum Score: " + minScore + "\tMaximum Score: " + maxScore);
    }
}
			 



package pack;

import java.util.Scanner;

public class Test { // Here is an example
    // We used objects of the Data and Award classes within the Test class, like student data line 24 (13)
    private static Data studentData;
    private static Awards studentAward;
    
    private static String firstName, lastName, major;
    private static double gpa = 0;
    
    public static void main(String args[]) {
        System.out.println("Welcome to the CU GPA Calculator!");

        Scanner input = new Scanner(System.in); // Used a scanner to ask students basic required questions
        System.out.print("Enter your first name: ");
        firstName = input.nextLine();
        System.out.print("Enter your last name: ");
        lastName = input.nextLine();
        System.out.print("Enter your major: ");
        major = input.nextLine();

        studentData = new Data(input);
        studentAward = new Awards(studentData.getGPA());
        
        System.out.printf("Your GPA is: %.1f\n\n", + studentData.getGPA());
        System.out.println(studentAward.getAwards());
        System.out.println("\n=\n");
        System.out.println("Here's the summary:");
        studentData.displayAll();

    }
}
