import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class ReadFromSqlServer {
    public static void main(String[] args) {
        // Database connection parameters
        String url = "jdbc:sqlserver://your_server_address:your_port;databaseName=your_database_name";
        String username = "your_username";
        String password = "your_password";

        // SQL query to fetch data from the database
        String query = "SELECT * FROM your_table_name";

        try {
            // Load the SQL Server JDBC driver
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");

            // Create a connection to the database
            Connection connection = DriverManager.getConnection(url, username, password);

            // Create a statement to execute the query
            Statement statement = connection.createStatement();

            // Execute the query and get the result set
            ResultSet resultSet = statement.executeQuery(query);

            // Process the result set
            while (resultSet.next()) {
                // Replace "column_name" with the actual column names from your table
                int id = resultSet.getInt("column_name");
                String name = resultSet.getString("column_name");
                // Continue to retrieve other columns as needed

                // Process the data (you can print it, store it, etc.)
                System.out.println("ID: " + id + ", Name: " + name);
            }

            // Close the resources
            resultSet.close();
            statement.close();
            connection.close();
        } catch (ClassNotFoundException e) {
            System.err.println("JDBC driver not found. Make sure you have the correct JDBC driver for SQL Server in your classpath.");
        } catch (SQLException e) {
            System.err.println("An error occurred while accessing the database: " + e.getMessage());
        }
    }
}
