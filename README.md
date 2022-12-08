import java.io.File;  // Import the File class
import java.io.FileNotFoundException;  // Import this class to handle errors
import java.util.Scanner; // Import the Scanner class to read text files
import java.util.ArrayList;

public class RealEstateAnalyticProgram {

    public static void main(String[] args) {
        ReportManager.createDataObjects(ReportManager.inputTextFile());
    }
}

class RealEstateRecord{
    String HouseType;
    String Description;
    String SoldPrice;
    String StreetName;
    String StNumber;
    String NumBedrooms;
    String NumBedPlus;
    String NumBaths;
    String Basement1;
}

class ReportManager{
    public static ArrayList<String> dataLines = new ArrayList<String>();
    public static ArrayList<RealEstateRecord> realEstateDataRecords = new ArrayList<RealEstateRecord>();
   
    static String oneLine;
    static RealEstateRecord oneRecord;
   
    public static void createDataObjects(ArrayList<String>dataLines) {
        oneRecord = new RealEstateRecord();
        // 1. we will walk over the dataLines ArrayList
        // 2. we will use SUBSTRING to the line apart
        // we will pull the line apart using substring
        // each little bit of the string: we assign to a field in the RealEstateRecord OBJECT
        int positionInLine = 0;
        for (int i = 1; i<dataLines.size();i++) {
            oneLine = dataLines.get(i);
            positionInLine = oneLine.indexOf(',');
            oneRecord.HouseType = oneLine.substring(0, positionInLine);
            oneRecord.Description = oneLine.substring(positionInLine + 1, oneLine.indexOf(','));
            oneRecord.SoldPrice = oneLine.substring(0, oneLine.indexOf(','));
            oneRecord.StreetName = oneLine.substring(0, oneLine.indexOf(','));;
            oneRecord.StNumber = oneLine.substring(0, oneLine.indexOf(','));;
            oneRecord.NumBedrooms = oneLine.substring(0, oneLine.indexOf(','));;
            oneRecord.NumBedPlus = oneLine.substring(0, oneLine.indexOf(','));;
            oneRecord.NumBaths = oneLine.substring(0, oneLine.indexOf(','));;
            oneRecord.Basement1 = oneLine.substring(0, oneLine.indexOf(','));;
        }
        realEstateDataRecords.add(oneRecord);
    }
   
    public static ArrayList<String> inputTextFile(){
        try {
              File myObj = new File("C:\\realestatedata\\RealEstateData.csv");
              Scanner myReader = new Scanner(myObj);
              while (myReader.hasNextLine()) {
                String data = myReader.nextLine();
                // System.out.println(data);
                // put each line of data into an ARRAYLIST
                dataLines.add(data);
              }
              myReader.close();
            } catch (FileNotFoundException e) {
              System.out.println("An error occurred.");
              e.printStackTrace();
            }
        return dataLines;
    }
   
}
