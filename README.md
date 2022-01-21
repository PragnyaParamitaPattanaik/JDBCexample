# JDBCexample
student information
package Jdbc;
import java.io.BufferedReader;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
import java.sql.*;


public class Jdbcexample {
	static final String DB_URL = "jdbc:h2:tcp://localhost/~/test";
	   static final String USER = "Sa";
	   static final String PASS = "";
	   static final String QUERY = "SELECT * FROM STUDENT1";
	

	public static void main(String[] args) throws ClassNotFoundException,SQLException, IOException
	{
		File file=new File("C:\\Users\\pragn\\OneDrive\\Desktop\\STUDENT1.txt");
        try(BufferedReader BufferedReader = new BufferedReader(new FileReader(file))) {
       	    String line = BufferedReader.readLine();
       	    while(line != null) {
       	        System.out.println(line);
       	        line = BufferedReader.readLine();
       	    }
       	} catch (FileNotFoundException e) 
        {
		  
			      // Open a connection
			      try(Connection conn = DriverManager.getConnection(DB_URL, USER, PASS);
			         Statement stmt = conn.createStatement();
			         ResultSet rs = stmt.executeQuery(QUERY);
			      ) {		      
			         while(rs.next()){
			            //Display values
			            System.out.print(" ROLLNUMBER: " + rs.getInt("ROLLNUMBER"));
			            
			            System.out.print("NAME: " + rs.getString("NAME"));			            
			            
			            	            
			            System.out.println("SUBJECT: " + rs.getString("SUBJECT"));
			            
			            System.out.print("AGE: " + rs.getInt("AGE"));
			            
			         }
			      } catch (SQLException e1) {
			         e1.printStackTrace();
			      }
			          
			      } 
			   }
}
