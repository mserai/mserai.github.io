---
layout: project
type: project
image: images/JAVA.png
title: Java
permalink: projects/java
date: 2016
labels:
  - Java
  - CSV
summary: program I wrote in 211 involving csv files, read ins, and manipulation of data.
---

After several assignments in 211, we tied the section together by combining code from the previous assignments. There is a lot of functionality behind these concepts, and I enjoyed glueing them together. I learned how to read in from files, store them in data structures, manipulate them, and finally output them.   

<hr>
<hr>

<pre>
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;
/**
* Write a super class and subclass, store data from a file into an array, and change the data with methods.
*
* @author Serai, Mike
* @assignment ICS 211 Assignment 10
* @date 2/17/2016
*/
public class SeraiMike10 {
   public static void main(String[] args) {
      // Determines if a commandline argument was entered
      if (args.length != 1) {
         System.out.println("Please enter exactly 1 commandline argument.");
         System.exit(1);
      }
      // Create a constant
      final Integer SIZE = 10;
      // Create an array of islands of the pacific objects
      IslandsOfThePacificTwoMore islandsArray[] = new IslandsOfThePacificTwoMore[SIZE];
          
      // Print the array with null values
      System.out.println("The Islands of the Pacific before initializing elements:" + "\n");
      System.out.println("Index  Element");
         for (int i = 0; i < SIZE; i++){
            System.out.printf("%d" + "      "+"%-10s\n", i, islandsArray[i]);
         }//for
      // Begin reading from the file entered
      System.out.println("\n" + "Connect to: " + args[0] + "\n");
         int size = 0;
         File file = new File(args[0]);
         Scanner fileConnect = null;
         // Connect with the file
         try {
            fileConnect = new Scanner(file);
         }
         catch (FileNotFoundException exception) {
            // Catch if file is not found
            System.out.print("File not found for: " + args[0]);
         }     
         // If the file is found
         if(fileConnect != null) {
            // Store the headers of the file
            String firstLineOfFile = fileConnect.nextLine();
            // Loop through the remaining lines of the file
            while (fileConnect.hasNextLine()) {
               // Store a line in the file
               String line = fileConnect.nextLine();
               // Seperate the line with commas
               Scanner lineInput = new Scanner(line).useDelimiter(",");
               //Store each section of the line that is seperated by commas
               String islandName = lineInput.next();
               String islandPopulation = lineInput.next();
               String islandArea1 = lineInput.next();
               String islandCapital = lineInput.next();
               String islandElevation1 = lineInput.next();
               // Convert the String to a Double
               Double islandArea = .0;
               try {
               islandArea = Double.parseDouble(islandArea1);
               }
               // Confirm the line stored is a double with try/catch
               catch (NumberFormatException exception) {
                  System.out.println("not a double");
               }
               // Convert the String to a Double
               Double islandElevation = .0;
               try {
               islandElevation = Double.parseDouble(islandElevation1);
               }
               // Confirm the line stored is a double with try/catch
               catch (NumberFormatException exception) {
                  System.out.println("not a double");
               }  
               // Initialize the array with an element
               islandsArray[size] = new IslandsOfThePacificTwoMore(islandName, islandPopulation,
                                        islandArea, islandCapital, islandElevation);
                     size ++;
            }
               // Print the Array with the values from the file
               System.out.println("The Islands of the Pacific after initializing elements:" + "\n");
                  System.out.println("Index Name of the Island    Population            Area              Capital          Elevation" +
                                  "\n");
                     for (int i = 0; i < SIZE; i++){
                     // Use toString to print
                     System.out.printf("%d" + "     "+"%-10s \n", i, islandsArray[i].toString());
                     }
         // Declare variables used in get/set methods
         String islandName = "blank";
         String islandPopulation = "blank";
         Double islandArea = 0.0;
         String islandCapital = "blank";
         Double islandElevation = 0.0;
            // Utilize Get, Set and upperName methods to change the data
            for (int i = 0; i < SIZE; i++) {
               islandName = islandsArray[i].getName();
               islandsArray[i].setName(islandName);
               islandsArray[i].upperName();
            }
            // Utilize Get, Set and noPop methods to change the data
            for (int i = 0; i < SIZE; i++) {
               islandPopulation = islandsArray[i].getPop();
               islandsArray[i].setPop(islandPopulation);
               islandsArray[i].noPop();
            }
            // Utilize Get, Set and kiloArea methods to change the data
            for (int i = 0; i < SIZE; i++) {
               islandArea = islandsArray[i].getArea();
               islandsArray[i].setArea(islandArea);
               islandsArray[i].kiloArea();
            }
            // Utilize Get, Set and upperCapital methods to change the data
            for (int i = 0; i < SIZE; i ++) {
               islandCapital = islandsArray[i].getCapital();
               islandsArray[i].setCapital(islandCapital);
               islandsArray[i].upperCapital();
            }
            // Utilize Get, Set and kiloElevation methods to change the data
            for (int i = 0; i < SIZE; i ++) {
               islandElevation = islandsArray[i].getElevation();
               islandsArray[i].setElevation(islandElevation);
               islandsArray[i].kiloElevation();
            }     
         // Print the Array with the changed values 
         System.out.println("The Islands of the Pacific after changing the elements:" + "\n");
         System.out.println("Index Name of the Island    Population          Area(km)            Capital        Elevation(km)" +
                                  "\n");
                     for (int i = 0; i < SIZE; i++){
                     // Use toString to print
                     System.out.printf("%d" + "     "+"%-10s \n", i, islandsArray[i].toString());
                     }                    
         }// if               
   }// Main
}// Class

/**
 * IslandsOfThePacific superclass stores and displays the data for each object
 *
 * @author Serai, Mike
 * @date 2/18/2016
 */
class IslandsOfThePacific {
   // Data Fields
   protected String name;
   protected String population;
   protected Double area;
   public static final Double DCONVERT = 2.58999;
   /**
    * The Constructor initializes the data fields
    *
    * @param islandName is the name of the island
    * @param islandPopulation is the string of integers representing the island's population
    * @param islandArea is the double representing the island's area
    */
   public IslandsOfThePacific (String islandName, String islandPopulation, Double islandArea) {
      name = islandName;
      population = islandPopulation;
      area = islandArea;
   }
   /**
    * Gets the Island Name
    *
    * @return the Island Name
    */
   public String getName () {
      return name;
   }
   /**
    * Gets the Island Population
    *
    * @return the Island Population
    */
   public String getPop () {
      return population;
   }
   /**
    * Gets the Island Area
    *
    * @return the Island Area
    */
   public Double getArea () {
      return area;
   }
   /**
    * Sets the Island Name
    *
    * @param islandName is the Island's name
    */
   public void setName (String islandName) {
      name = islandName;
   }
   /**
    * Sets the Island Population
    *
    * @param islandPopulation is the Island's population
    */
   public void setPop (String islandPopulation) {
      population = islandPopulation;
   }
   /**
    * Sets the Island Area
    *
    * @param islandArea is the Island's area
    */
   public void setArea (Double islandArea) {
      area = islandArea;
   }
    /**
    * Changes the Island's name to uppercase
    **/
   public void upperName () {
      name = name.toUpperCase();
   }
   /**
    * Changes the Island's population to 0
    */
   public void noPop () {
      population = "0";
   }
   /**
    * Converts the Island's area to kilometers
    */
   public void kiloArea () {
      area = area * DCONVERT;
   }
   /**
    * The toString() method returns a String with the three data fields
    *
    * @return the output of the initialized array
    */
   public String toString(){
      String output = String.format("%-10s %19s %18.2f\n", name, population, area);
      return output;
   }
}// Class
/**
 * A subclass of IslandsOfThePacific
 *
 * @author Serai, Mike
 * @date 2/18/2016
 */
class IslandsOfThePacificTwoMore extends IslandsOfThePacific {
   // Data Fields
   private String capital;
   private Double elevation;
   /**
    * The Constructor initializes the data fields
    *
    * @param islandName is the name of the island
    * @param islandPopulation is the string of integers representing the island's population
    * @param islandArea is the double representing the island's area
    * @param islandCapital is the name of the capital of the island
    * @param islandElevation is the max elevation of the island
    */
   public IslandsOfThePacificTwoMore (String islandName, String islandPopulation, Double islandArea,
                                       String islandCapital, Double islandElevation) {
      // Utilize super to initialize the variables from IslandsOfThePacific
      super (islandName, islandPopulation, islandArea);
      capital = islandCapital;
      elevation = islandElevation;
   }// Constructor
   /**
    * Gets the Island Capital
    *
    * @return the Island Capital
    */
   public String getCapital () {
      return capital;
   }
   /**
    * Gets the Island Elevation
    *
    * @return the Island Elevation
    */
   public Double getElevation () {
      return elevation;
   }
   /**
    * Sets the Island Capital
    *
    * @param islandCapital is the Island's Capital
    */
   public void setCapital (String islandCapital) {
      capital = islandCapital;
   }
   /**
    * Sets the Island Elevation
    *
    * @param islandElevation is the Island's elevation
    */
   public void setElevation (Double islandElevation) {
      elevation = islandElevation;
   }
   /**
    * Changes the Island's Capital to uppercase
    **/          
   public void upperCapital () {
      capital = capital.toUpperCase ();
   }
   /**
    * Converts the Island's elevation to kilometers
    */ 
   public void kiloElevation () {
      elevation = elevation * DCONVERT;
   } 
   /**
    * The toString() method returns a String with the five data fields
    *
    * @return the output of the initialized array
    */
   public String toString(){
      String output = String.format("%-10s %19s %18.2f %19s % 18.2f\n", name, population, area, capital, elevation);
      return output;
   }// toString
}// Class
</pre>

<hr>
<hr>

