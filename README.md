
public class Awards {

    private int awardRank;
    private double gpa;
    private String awardString;
    
    
    private final String SummaCumLaude = "Graduated With Highest Distinction";
    private final String MagnaCumLaude = "Graduated With Great Distinction";
    private final String CumLaude = "Graduated With Distinction";
    //Example of class constructor 13
    public Awards(double gpa) {
        this.gpa = gpa;
        this.awardString = getAwards();
    }

    public String getAwards() {
        String returnValue;
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
        //Example of my switch statement 4
        switch (awardRank) {
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
      //This line prints the gpa award rank 19
        System.out.println(awardRank);
        return returnValue;
    }
}


public class Data {
	
	// Constant final was used (3) displayed in lines 4,5,6 
    final static String[] letterGrades = {"A+", "A", "A-", "B+", "B", "B-", "C+", "C", "C-", "D+", "D", "F"};
  //Used arrays to store values 13
    final static double[] gradeValues = {4.0, 4.0, 3.7, 3.3, 3.0, 2.7, 2.3, 2.0, 1.7, 1.3, 1.0, 0.0};
    final static int[] percentGrades = {97, 93, 90, 87, 83, 80, 77, 73, 70, 67, 65, 0};
    //Above we can aslo see the use o static variables and below static methods 20
    
    private int courseCount, creditCount = 0;
    private int courseScore[];
    private int courseCredits[];
    
    private int minScore = 100, maxScore = 0;
    

    private double gpa;
    public Data(int courseCount) {
    	// This keyword
        this.courseCount = courseCount;
        courseScore = new int[courseCount];
        courseCredits = new int[courseCount];
    }
    
    public void enteredValue(int i, int credits, int score) {
        courseCredits[i] = credits;
        creditCount += credits;
        courseScore[i] = score;
        courseCredits[i] = credits;
        minScore = Math.min(minScore, score);
        maxScore = Math.max(maxScore, score);
        gpa += (scoreToScale(score) * credits);
    }
    
    public void calculateGPA() {
        gpa = gpa / creditCount;
        System.out.println("GPA is : " + gpa);
    }
    
    public int[] getCourseScores() {
        return courseScore;
    }
    
    public int[] getCourseCredits() {
        return courseCredits;
    }
    
    public int getCourseCount() {
        return courseCount;
    }
    
    public int getCreditCount() {
        return creditCount;
    }

    public double getGPA() {
        return gpa;
    }

    public void setGPA(double gpa) {
        this.gpa = gpa;
    }
    
    private static double scoreToScale(int score) {
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
    
    public String displayAll() {
        String outString = "";
        for (int i = 0; i < courseCount; i++) {
        	//Example of conditional operator 5
            outString += "(" + (i + 1) + ") - " + courseScore[i] + "/100\t" + scoreToGrade(courseScore[i]) + "\n";
        }
        outString += "\nGPA: " + getGPA();
        outString += "\nMinimum Score: " + minScore + "\tMaximum Score: " + maxScore;
        return outString;
    }
}


 //Java fx 21
import javafx.application.Application;
import javafx.collections.FXCollections;
import javafx.event.ActionEvent;
import javafx.event.EventHandler;
import javafx.geometry.Insets;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.ComboBox;
import javafx.scene.control.Label;
import javafx.scene.control.TextField;
import javafx.scene.layout.GridPane;
import javafx.scene.layout.StackPane;
import javafx.scene.layout.TilePane;
import javafx.stage.Stage;
 // Example of inheritance throughout the project. I used the extends keyword 17
public class JavaFxGUI extends Application {
    
    private static Data studentData;
    private static Awards studentAward;
 //Created the labels, text, and buttons   
    Label firstNameLbl;
    Label lastNameLbl;
    Label majorLbl;
    Label courseCountLbl;
    Label promptLbl;
    Label creditCountLbl;
    Label currentValueLbl;
    Label summaryLbl;
    
    TextField firstNameTxt;
    TextField majorTxt;
    TextField lastNameTxt;
    
    Button button0;
    Button button1;
    Button button2;
    Button button3;
    Button button4;
    Button button5;
    Button button6;
    Button button7;
    Button button8;
    Button button9;
    Button buttonClearCurrent;
    Button buttonClearAll;
    Button buttonAddEntry;
    Button buttonEnter;
    
    ComboBox courseCountCBox;
    ComboBox creditCountCBox;
    
    int courseCountInt, creditCountInt, creditTotalInt, pressedValueInt, currentValueInt, score, enteredCourses = 0;
    double gpa;
    String firstName, lastName, major;
    
    String incompleteDataPrompt = "Enter Name and Course Count: ";
    String courseCountPrompt = "Enter Course Count: ";
    String creditCountPrompt = "Enter Credit Count: ";
    String scorePrompt = "Enter Score for Course: ";
    String invalidScorePrompt = "Enter Score (0 - 100: ";
    
    String courseCountStr[] = {"0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "10", "11", "12"};
    String creditCountStr[] = {"0", "1", "2", "3", "4", "5", "6"};
    public static void main(String[] args) {
        launch(args);
    }
// Example of overriding 11
    @Override
    //Example of exception 10
    public void start(Stage stage) throws Exception {
        //Created the lengths and widths of the labels, buttons, and text
        int labelMinWidth = 150;
        int labelMaxWidth = 150;
        int labelMinHeight = 30;
        int labelMaxHeight = 30;
        
        int textMinWidth = 150;
        int textMaxWidth = 150;
        int textMinHeight = 50;
        int textMaxHeight = 50;
        
        int buttonMinWidth = 150;
        int buttonMaxWidth = 150;
        int buttonMinHeight = 50;
        int buttonMaxHeight = 50;
        //Created the grid pane
        GridPane gridPane = new GridPane();
        gridPane.setHgap(10);
        gridPane.setVgap(10);
        gridPane.setPadding(new Insets(10, 10, 10, 10));
        
        firstNameLbl = new Label();
        majorLbl = new Label();
        lastNameLbl = new Label();
        firstNameTxt = new TextField();
        majorTxt = new TextField();
        lastNameTxt = new TextField();
        courseCountLbl = new Label();
        creditCountLbl = new Label();
        promptLbl = new Label();
        currentValueLbl = new Label();
        
        summaryLbl = new Label();
     // Created the button functions   
        button0 = new Button();
        button1 = new Button();
        button2 = new Button();
        button3 = new Button();
        button4 = new Button();
        button5 = new Button();
        button6 = new Button();
        button7 = new Button();
        button8 = new Button();
        button9 = new Button();
        buttonClearCurrent = new Button();
        buttonClearAll = new Button();
        buttonAddEntry = new Button();
        buttonEnter = new Button();
        
        firstNameLbl.setText("First Name:");
        majorLbl.setText("Major:");
        lastNameLbl.setText("Last Name:");
        courseCountLbl.setText("Number of Courses:");
        creditCountLbl.setText("Number of Credits:");
        promptLbl.setText("");
        currentValueLbl.setText("");
        summaryLbl.setText("Summary");
        button0.setText("0");
        button1.setText("1");
        button2.setText("2");
        button3.setText("3");
        button4.setText("4");
        button5.setText("5");
        button6.setText("6");
        button7.setText("7");
        button8.setText("8");
        button9.setText("9");
        buttonClearCurrent.setText("Clear");
        buttonClearAll.setText("Reset");
        buttonAddEntry.setText("Add Course");
        buttonEnter.setText("Enter");
        
        summaryLbl.setMaxSize(Double.MAX_VALUE, Double.MAX_VALUE);
        summaryLbl.setMaxSize(Double.MAX_VALUE, Double.MAX_VALUE);
        summaryLbl.setWrapText(true);
        
        buttonAddEntry.setMaxSize(Double.MAX_VALUE, Double.MAX_VALUE);
        buttonAddEntry.setMaxSize(Double.MAX_VALUE, Double.MAX_VALUE);
        buttonAddEntry.setWrapText(true);
        
        buttonEnter.setMaxSize(Double.MAX_VALUE, Double.MAX_VALUE);
        buttonEnter.setMaxSize(Double.MAX_VALUE, Double.MAX_VALUE);
        buttonEnter.setWrapText(true);
        
        stage.setTitle(" GPA Calculator ");
        
        courseCountCBox = new ComboBox(FXCollections.observableArrayList(courseCountStr));
        courseCountCBox.getSelectionModel().select(0);
        courseCountCBox.setEditable(false);
        
        creditCountCBox = new ComboBox(FXCollections.observableArrayList(creditCountStr));
        creditCountCBox.getSelectionModel().select(0);
        creditCountCBox.setEditable(false);
        
        button0.setDisable(true);
        button1.setDisable(true);
        button2.setDisable(true);
        button3.setDisable(true);
        button4.setDisable(true);
        button5.setDisable(true);
        button6.setDisable(true);
        button7.setDisable(true);
        button8.setDisable(true);
        button9.setDisable(true);
        buttonClearCurrent.setDisable(true);
        buttonClearAll.setDisable(true);
        buttonAddEntry.setDisable(true);
        buttonEnter.setDisable(true);
        courseCountCBox.setDisable(false);
        creditCountCBox.setDisable(true);
        
        courseCountCBox.getSelectionModel().selectedItemProperty().addListener( 
            (options, oldValue, newValue) -> {
                try{
                    if (Integer.parseInt((String)newValue) < 1) {
                        return;
                    }}
                catch(Exception e) {
                    return;
                }
                Boolean canProceed = firstNameTxt.getText().length() > 0;
                canProceed = canProceed && (firstNameTxt.getText() != null);
                canProceed = canProceed && (firstNameTxt.getText().length() > 0);
                canProceed = canProceed && (majorTxt.getText() != null);
                canProceed = canProceed && (majorTxt.getText().length() > 0);
                canProceed = canProceed && (lastNameTxt.getText() != null);
                canProceed = canProceed && (lastNameTxt.getText().length() > 0);
                canProceed = canProceed && !(courseCountCBox.getSelectionModel().isEmpty());
                if(canProceed) {
                    courseCountInt = Integer.parseInt((String)newValue);
                    firstName = firstNameTxt.getText();
                    lastName = lastNameTxt.getText();
                    major = majorTxt.getText();
                    firstNameTxt.setDisable(true);
                    lastNameTxt.setDisable(true);
                    majorTxt.setDisable(true);
                    buttonClearCurrent.setDisable(false);
                    buttonClearAll.setDisable(false);
                    courseCountCBox.setDisable(true);
                    creditCountCBox.setDisable(false);
                    courseCountCBox.setStyle(null);
                    promptLbl.setText(creditCountPrompt + (enteredCourses + 1));
                    summaryLbl.setText(summaryLbl.getText() + "\nHello " + firstName + " " + lastName +
                            "\n\nWelcome to " + major + " department" +
                            "\nYou entered " + courseCountInt + " course(s)\n");
                    studentData = new Data(courseCountInt);
                }
                else {
                    courseCountCBox.getSelectionModel().select(0);
                    promptLbl.setText(incompleteDataPrompt);
                }

            }
        );
        
        creditCountCBox.getSelectionModel().selectedItemProperty().addListener( 
            (options, oldValue, newValue) -> {
                try{
                    if (Integer.parseInt((String)newValue) < 1) {
                        return;
                    }}
                catch(Exception e) {
                    return;
                }
                creditCountInt = Integer.parseInt((String)newValue);
                button0.setDisable(false);
                button1.setDisable(false);
                button2.setDisable(false);
                button3.setDisable(false);
                button4.setDisable(false);
                button5.setDisable(false);
                button6.setDisable(false);
                button7.setDisable(false);
                button8.setDisable(false);
                button9.setDisable(false);
                buttonAddEntry.setDisable(false);
                promptLbl.setText(scorePrompt + (enteredCourses + 1));
                summaryLbl.setText(summaryLbl.getText() + "\nCourse (" + (enteredCourses + 1) + ") is " + creditCountInt + " credits");
                creditCountCBox.setDisable(true);
            }
        );
        
        button0.setOnAction((ActionEvent event) -> {
            pressedValueInt = Integer.parseInt(((Button)event.getSource()).getText());
            processInputValue(pressedValueInt);
        });
        button1.setOnAction((ActionEvent event) -> {
            pressedValueInt = Integer.parseInt(((Button)event.getSource()).getText());
            processInputValue(pressedValueInt);
        });
        button2.setOnAction((ActionEvent event) -> {
            pressedValueInt = Integer.parseInt(((Button)event.getSource()).getText());
            processInputValue(pressedValueInt);
        });
        button3.setOnAction((ActionEvent event) -> {
            pressedValueInt = Integer.parseInt(((Button)event.getSource()).getText());
            processInputValue(pressedValueInt);
        });
        button4.setOnAction((ActionEvent event) -> {
            pressedValueInt = Integer.parseInt(((Button)event.getSource()).getText());
            processInputValue(pressedValueInt);
        });
        button5.setOnAction((ActionEvent event) -> {
            pressedValueInt = Integer.parseInt(((Button)event.getSource()).getText());
            processInputValue(pressedValueInt);
        });
        button6.setOnAction((ActionEvent event) -> {
            pressedValueInt = Integer.parseInt(((Button)event.getSource()).getText());
            processInputValue(pressedValueInt);
        });
        button7.setOnAction((ActionEvent event) -> {
            pressedValueInt = Integer.parseInt(((Button)event.getSource()).getText());
            processInputValue(pressedValueInt);
        });
        button8.setOnAction((ActionEvent event) -> {
            pressedValueInt = Integer.parseInt(((Button)event.getSource()).getText());
            processInputValue(pressedValueInt);
        });
        button9.setOnAction((ActionEvent event) -> {
            pressedValueInt = Integer.parseInt(((Button)event.getSource()).getText());
            processInputValue(pressedValueInt);
        });
        buttonClearCurrent.setOnAction((ActionEvent event) -> {
            promptLbl.setText("");
            currentValueLbl.setText(creditCountPrompt + (enteredCourses + 1));
            button0.setDisable(true);
            button1.setDisable(true);
            button2.setDisable(true);
            button3.setDisable(true);
            button4.setDisable(true);
            button5.setDisable(true);
            button6.setDisable(true);
            button7.setDisable(true);
            button8.setDisable(true);
            button9.setDisable(true);
            buttonAddEntry.setDisable(true);
            if (courseCountCBox.isDisabled()) {
                creditCountCBox.getSelectionModel().select(0);
                creditCountCBox.setDisable(false);
            } else {
                courseCountCBox.setDisable(false);
                firstNameTxt.setDisable(false);
                majorTxt.setDisable(false);
                lastNameTxt.setDisable(false);
                courseCountCBox.getSelectionModel().select(0);
                firstNameTxt.setText("");
                majorTxt.setText("");
                lastNameTxt.setText("");
            }
            currentValueLbl.setText("");
            creditCountInt = 0;
            creditTotalInt = 0;
            pressedValueInt = 0;
            currentValueInt = 0;
        });
        buttonClearAll.setOnAction((ActionEvent event) -> {
            buttonAddEntry.setDisable(true);
            button0.setDisable(true);
            button1.setDisable(true);
            button2.setDisable(true);
            button3.setDisable(true);
            button4.setDisable(true);
            button5.setDisable(true);
            button6.setDisable(true);
            button7.setDisable(true);
            button8.setDisable(true);
            button9.setDisable(true);
            buttonAddEntry.setDisable(true);
            buttonEnter.setDisable(true);
            
            promptLbl.setText("");
            currentValueLbl.setText("");
            firstNameTxt.setText("");
            firstNameTxt.setDisable(false);
            majorTxt.setText("");
            majorTxt.setDisable(false);
            lastNameTxt.setText("");
            lastNameTxt.setDisable(false);
            courseCountCBox.getSelectionModel().select(0);
            courseCountCBox.setDisable(false);
            creditCountCBox.setDisable(true);
            creditCountCBox.getSelectionModel().select(0);
            courseCountInt = 0;
            creditCountInt = 0;
            creditTotalInt = 0;
            pressedValueInt = 0;
            currentValueInt = 0;
            score = 0;
            enteredCourses = 0;
            firstName = "";
            major = "";
            lastName = "";
            
            summaryLbl.setText("");
            });
        
        buttonAddEntry.setOnAction((ActionEvent event) -> {
            if(currentValueInt >= 0 && currentValueInt <= 100) {
                score = currentValueInt;
                enteredCourses++;
                buttonAddEntry.setDisable(true);
                button0.setDisable(true);
                button1.setDisable(true);
                button2.setDisable(true);
                button3.setDisable(true);
                button4.setDisable(true);
                button5.setDisable(true);
                button6.setDisable(true);
                button7.setDisable(true);
                button8.setDisable(true);
                button9.setDisable(true);
                creditCountCBox.getSelectionModel().select(0);
                currentValueLbl.setText("");
                currentValueInt = 0;
                summaryLbl.setText(summaryLbl.getText() + "\nCourse (" + (enteredCourses) + ")'s score is " + score);
                if(courseCountInt > enteredCourses) {
                    creditCountCBox.setDisable(false);
                    promptLbl.setText(creditCountPrompt + (enteredCourses + 1));
                    studentData.enteredValue(enteredCourses - 1, creditCountInt, score);
                } else {
                    studentData.enteredValue(enteredCourses - 1, creditCountInt, score);
                    promptLbl.setText("Press Enter to submit");
                    buttonEnter.setDisable(false);
                }
            }
            else {
                promptLbl.setText(invalidScorePrompt);
                currentValueLbl.setText("");
                currentValueInt = 0;
            }
        });
        
        buttonEnter.setOnAction((ActionEvent event) -> {
            firstName = firstNameTxt.getText();
            major = majorTxt.getText();
            lastName = lastNameTxt.getText();
                buttonAddEntry.setDisable(true);
            button0.setDisable(true);
            button1.setDisable(true);
            button2.setDisable(true);
            button3.setDisable(true);
            button4.setDisable(true);
            button5.setDisable(true);
            button6.setDisable(true);
            button7.setDisable(true);
            button8.setDisable(true);
            button9.setDisable(true);
            buttonEnter.setDisable(true);
            studentData.calculateGPA();
            
            summaryLbl.setText("\nThis is " + firstName + " " + lastName + "'s report\n"
                    + "from " + major + " departmen:t\nYour GPA: " + studentData.getGPA() + "\n");
            summaryLbl.setText(summaryLbl.getText() + "\n" + studentData.getGPA());
            studentAward = new Awards(studentData.getGPA());
            summaryLbl.setText(summaryLbl.getText() + "\n" + studentAward.getAwards());
            summaryLbl.setText(summaryLbl.getText() + "\n" + studentData.displayAll());
            
            currentValueInt = 0;
            promptLbl.setText("");
            currentValueLbl.setText("");
            firstNameTxt.setText("");
            firstNameTxt.setDisable(false);
            majorTxt.setText("");
            majorTxt.setDisable(false);
            lastNameTxt.setText("");
            lastNameTxt.setDisable(false);
            courseCountCBox.getSelectionModel().select(0);
            courseCountCBox.setDisable(false);
            creditCountCBox.setDisable(true);
            creditCountCBox.getSelectionModel().select(0);
            courseCountInt = 0;
            creditCountInt = 0;
            creditTotalInt = 0;
            pressedValueInt = 0;
            score = 0;
            enteredCourses = 0;
        });
        
        firstNameLbl.setMaxWidth(labelMaxWidth);
        firstNameLbl.setMinWidth(labelMinWidth);
        firstNameLbl.setMaxHeight(labelMaxHeight);
        firstNameLbl.setMinHeight(labelMinHeight);
        firstNameLbl.setStyle("-fx-font-size: 1em; -fx-text-fill: #1f095c; -fx-background-color: #a2acba; -fx-border-color: #2d3745; -fx-border-width: 2px;");
        
        firstNameTxt.setMaxWidth(textMaxWidth);
        firstNameTxt.setMinWidth(textMinWidth);
        firstNameTxt.setMaxHeight(textMaxHeight);
        firstNameTxt.setMinHeight(textMinHeight);
        
        majorLbl.setMaxWidth(labelMaxWidth);
        majorLbl.setMinWidth(labelMinWidth);
        majorLbl.setMaxHeight(labelMaxHeight);
        majorLbl.setMinHeight(labelMinHeight);
        majorLbl.setStyle("-fx-font-size: 1em; -fx-text-fill: #1f095c; -fx-background-color: #a2acba; -fx-border-color: #2d3745; -fx-border-width: 2px;");
        
        majorTxt.setMaxWidth(textMaxWidth);
        majorTxt.setMinWidth(textMinWidth);
        majorTxt.setMaxHeight(textMaxHeight);
        majorTxt.setMinHeight(textMinHeight);
        
        lastNameLbl.setMaxWidth(labelMaxWidth);
        lastNameLbl.setMinWidth(labelMinWidth);
        lastNameLbl.setMaxHeight(labelMaxHeight);
        lastNameLbl.setMinHeight(labelMinHeight);
        lastNameLbl.setStyle("-fx-font-size: 1em; -fx-text-fill: #1f095c; -fx-background-color: #a2acba; -fx-border-color: #2d3745; -fx-border-width: 2px;");
        
        
        lastNameTxt.setMaxWidth(textMaxWidth);
        lastNameTxt.setMinWidth(textMinWidth);
        lastNameTxt.setMaxHeight(textMaxHeight);
        lastNameTxt.setMinHeight(textMinHeight);
        
        courseCountLbl.setMaxWidth(labelMaxWidth);
        courseCountLbl.setMinWidth(labelMinWidth);
        courseCountLbl.setMaxHeight(labelMaxHeight);
        courseCountLbl.setMinHeight(labelMinHeight);
        courseCountLbl.setStyle("-fx-font-size: 1em; -fx-text-fill: #1f095c; -fx-background-color: #a2acba; -fx-border-color: #2d3745; -fx-border-width: 2px;");
        
        creditCountLbl.setMaxWidth(labelMaxWidth);
        creditCountLbl.setMinWidth(labelMinWidth);
        creditCountLbl.setMaxHeight(labelMaxHeight);
        creditCountLbl.setMinHeight(labelMinHeight);
        creditCountLbl.setStyle("-fx-font-size: 1em; -fx-text-fill: #1f095c; -fx-background-color: #a2acba; -fx-border-color: #2d3745; -fx-border-width: 2px;");
        
        button0.setMaxWidth(buttonMaxWidth);
        button0.setMinWidth(buttonMinWidth);
        button0.setMaxHeight(buttonMaxHeight);
        button0.setMinHeight(buttonMinHeight);
        
        button1.setMaxWidth(buttonMaxWidth);
        button1.setMinWidth(buttonMinWidth);
        button1.setMaxHeight(buttonMaxHeight);
        button1.setMinHeight(buttonMinHeight);
        
        button2.setMaxWidth(buttonMaxWidth);
        button2.setMinWidth(buttonMinWidth);
        button2.setMaxHeight(buttonMaxHeight);
        button2.setMinHeight(buttonMinHeight);
        
        button3.setMaxWidth(buttonMaxWidth);
        button3.setMinWidth(buttonMinWidth);
        button3.setMaxHeight(buttonMaxHeight);
        button3.setMinHeight(buttonMinHeight);
        
        button4.setMaxWidth(buttonMaxWidth);
        button4.setMinWidth(buttonMinWidth);
        button4.setMaxHeight(buttonMaxHeight);
        button4.setMinHeight(buttonMinHeight);
        
        button5.setMaxWidth(buttonMaxWidth);
        button5.setMinWidth(buttonMinWidth);
        button5.setMaxHeight(buttonMaxHeight);
        button5.setMinHeight(buttonMinHeight);
        
        button6.setMaxWidth(buttonMaxWidth);
        button6.setMinWidth(buttonMinWidth);
        button6.setMaxHeight(buttonMaxHeight);
        button6.setMinHeight(buttonMinHeight);
        
        button7.setMaxWidth(buttonMaxWidth);
        button7.setMinWidth(buttonMinWidth);
        button7.setMaxHeight(buttonMaxHeight);
        button7.setMinHeight(buttonMinHeight);
        
        button8.setMaxWidth(buttonMaxWidth);
        button8.setMinWidth(buttonMinWidth);
        button8.setMaxHeight(buttonMaxHeight);
        button8.setMinHeight(buttonMinHeight);
        
        button9.setMaxWidth(buttonMaxWidth);
        button9.setMinWidth(buttonMinWidth);
        button9.setMaxHeight(buttonMaxHeight);
        button9.setMinHeight(buttonMinHeight);
        
       //Created button styles 
        button0.setStyle("-fx-font-size: 1em; -fx-text-fill: #1f095c; -fx-background-color: #a2acba; -fx-border-color: #2d3745; -fx-border-width: 2px;");
        button1.setStyle("-fx-font-size: 1em; -fx-text-fill: #1f095c; -fx-background-color: #a2acba; -fx-border-color: #2d3745; -fx-border-width: 2px;");
        button2.setStyle("-fx-font-size: 1em; -fx-text-fill: #1f095c; -fx-background-color: #a2acba; -fx-border-color: #2d3745; -fx-border-width: 2px;");
        button3.setStyle("-fx-font-size: 1em; -fx-text-fill: #1f095c; -fx-background-color: #a2acba; -fx-border-color: #2d3745; -fx-border-width: 2px;");
        button4.setStyle("-fx-font-size: 1em; -fx-text-fill: #1f095c; -fx-background-color: #a2acba; -fx-border-color: #2d3745; -fx-border-width: 2px;");
        button5.setStyle("-fx-font-size: 1em; -fx-text-fill: #1f095c; -fx-background-color: #a2acba; -fx-border-color: #2d3745; -fx-border-width: 2px;");
        button6.setStyle("-fx-font-size: 1em; -fx-text-fill: #1f095c; -fx-background-color: #a2acba; -fx-border-color: #2d3745; -fx-border-width: 2px;");
        button7.setStyle("-fx-font-size: 1em; -fx-text-fill: #1f095c; -fx-background-color: #a2acba; -fx-border-color: #2d3745; -fx-border-width: 2px;");
        button8.setStyle("-fx-font-size: 1em; -fx-text-fill: #1f095c; -fx-background-color: #a2acba; -fx-border-color: #2d3745; -fx-border-width: 2px;");
        button9.setStyle("-fx-font-size: 1em; -fx-text-fill: #1f095c; -fx-background-color: #a2acba; -fx-border-color: #2d3745; -fx-border-width: 2px;");
     //Created button sizes
        buttonClearCurrent.setMaxWidth(buttonMaxWidth);
        buttonClearCurrent.setMinWidth(buttonMinWidth);
        buttonClearCurrent.setMaxHeight(buttonMaxHeight);
        buttonClearCurrent.setMinHeight(buttonMinHeight);
        buttonClearCurrent.setStyle("-fx-font-size: 2em; -fx-text-fill: #0c11a8; -fx-background-color: #95bdbb; -fx-border-color: #3f6e6b; -fx-border-width: 4px;");
        
        buttonClearAll.setMaxWidth(buttonMaxWidth);
        buttonClearAll.setMinWidth(buttonMinWidth);
        buttonClearAll.setMaxHeight(buttonMaxHeight);
        buttonClearAll.setMinHeight(buttonMinHeight);
        buttonClearAll.setStyle("-fx-font-size: 2em; -fx-text-fill: #0c11a8; -fx-background-color: #f5bcc9; -fx-border-color: #f7a3b6; -fx-border-width: 4px;");
        
        buttonAddEntry.setMaxHeight(buttonMaxHeight);
        buttonAddEntry.setMinHeight(buttonMinHeight);
        buttonAddEntry.setStyle("-fx-font-size: 2em; -fx-text-fill: #0c11a8; -fx-background-color: #c6f2a2; -fx-border-color: #070f00; -fx-border-width: 4px;");
        
        buttonEnter.setMaxHeight(buttonMaxHeight);
        buttonEnter.setMinHeight(buttonMinHeight);
        buttonEnter.setStyle("-fx-font-size: 2em; -fx-text-fill: #0c11a8; -fx-background-color: #c6f2a2; -fx-border-color: #070f00; -fx-border-width: 4px;");
        
        promptLbl.setMaxWidth(labelMaxWidth);
        promptLbl.setMinWidth(labelMinWidth);
        promptLbl.setMaxHeight(labelMaxHeight);
        promptLbl.setMinHeight(labelMinHeight);
        promptLbl.setStyle("-fx-font-size: 1em; -fx-text-fill: #d40d27; -fx-background-color: #a2acba; -fx-border-color: #2d3745; -fx-border-width: 2px;");
        promptLbl.setWrapText(true);
        
        currentValueLbl.setMaxWidth(labelMaxWidth);
        currentValueLbl.setMinWidth(labelMinWidth);
        currentValueLbl.setMaxHeight(labelMaxHeight);
        currentValueLbl.setMinHeight(labelMinHeight);
        currentValueLbl.setStyle("-fx-font-size: 1.8em; -fx-text-fill: #1f095c; -fx-background-color: #a2acba; -fx-border-color: #2d3745; -fx-border-width: 2px;");
        
        gridPane.setConstraints(firstNameLbl, 0, 0);
        gridPane.setConstraints(majorLbl, 1, 0);
        gridPane.setConstraints(lastNameLbl, 2, 0);
        gridPane.setConstraints(firstNameTxt, 0, 1);
        gridPane.setConstraints(majorTxt, 1, 1);
        gridPane.setConstraints(lastNameTxt, 2, 1);
        gridPane.setConstraints(courseCountLbl, 0, 2);
        gridPane.setConstraints(promptLbl, 1, 2);
        gridPane.setConstraints(creditCountLbl, 2, 2);
        gridPane.setConstraints(courseCountCBox, 0, 3);
        gridPane.setConstraints(currentValueLbl, 1, 3);
        gridPane.setConstraints(creditCountCBox, 2, 3);
        gridPane.setConstraints(button1, 0, 4);
        gridPane.setConstraints(button2, 1, 4);
        gridPane.setConstraints(button3, 2, 4);
        gridPane.setConstraints(button4, 0, 5);
        gridPane.setConstraints(button5, 1, 5);
        gridPane.setConstraints(button6, 2, 5);
        gridPane.setConstraints(button7, 0, 6);
        gridPane.setConstraints(button8, 1, 6);
        gridPane.setConstraints(button9, 2, 6);
        gridPane.setConstraints(button0, 1, 7);
        gridPane.setConstraints(buttonClearCurrent, 0, 7);
        gridPane.setConstraints(buttonClearAll, 2, 7);
        
        gridPane.getChildren().addAll(firstNameLbl, majorLbl, lastNameLbl,
                firstNameTxt, majorTxt, lastNameTxt,
                courseCountLbl, creditCountLbl, currentValueLbl,
                courseCountCBox, promptLbl, creditCountCBox,
                button1, button2, button3,
                button4, button5, button6,
                button7, button8, button9,
                buttonClearCurrent, button0, buttonClearAll);
        gridPane.add(buttonAddEntry, 0, 8, 3, 1);
        gridPane.add(buttonEnter, 0, 9, 3, 1);
        gridPane.add(summaryLbl, 0, 10, 3, 8);

        Scene scene = new Scene(gridPane, 490, 1000);
        
        stage.setScene(scene);
  
        stage.show();
        
    }
    
    private void processInputValue(int valueEntry) {
        currentValueInt = currentValueInt * 10;
        currentValueInt += valueEntry;
        currentValueLbl.setText("" + currentValueInt);
    }
}
