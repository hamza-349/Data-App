# Data-App
package com.practce.practicetask2;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class MainActivity extends AppCompatActivity {

        setContentView(R.layout.activity_main);
    }
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

    public class NoteApplication {

        private static final String FILE_NAME = "name.txt";

        public static void main(String[] args) {
            List<String> name = new ArrayList<>();
            loadNameFromFile(name);


            Scanner scanner = new Scanner(System.in);
            String input;

            while (true) {
                System.out.print("Enter your name: ");
                input = scanner.nextLine();

                if (input.equalsIgnoreCase("exit")) {
                    break;
                }

                name.add(input);
                saveNotesToFile(name);
            }

            scanner.close();
        }

        private static void loadNameFromFile(List<String> name) {
            try (BufferedReader reader = new BufferedReader(new FileReader(FILE_NAME))) {
                String line;
                while ((line = reader.readLine()) != null) {
                    name.add(line);
                }
            } catch (IOException e) {
                // Ignore if the file doesn't exist or cannot be read.
            }
        }

        private static void saveNotesToFile(List<String> name) {
            try (BufferedWriter writer = new BufferedWriter(new FileWriter(FILE_NAME))) {
                for (String note : name)
                {
                    writer.write(note);
                    writer.newLine();
                }
            } catch (IOException e) {
                System.err.println("Error saving notes: " + e.getMessage());
            }
        }
    }

}
