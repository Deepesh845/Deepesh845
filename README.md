import java.io.BufferedWriter;
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Scanner;

public class BirthdayWishLink {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter the birthday person's name:");
        String name = scanner.nextLine();

        System.out.println("Enter the birthday person's age:");
        int age = scanner.nextInt();
        scanner.nextLine(); // Consume newline left-over

        System.out.println("Enter the photo album title:");
        String albumTitle = scanner.nextLine();

        System.out.println("Enter the number of photos in the album:");
        int numPhotos = scanner.nextInt();
        scanner.nextLine(); // Consume newline left-over

        String[] photoUrls = new String[numPhotos];
        for (int i = 0; i < numPhotos; i++) {
            System.out.println("Enter the URL of photo " + (i + 1) + ":");
            photoUrls[i] = scanner.nextLine();
        }

        createHtmlFile(name, age, albumTitle, photoUrls);
    }

    private static void createHtmlFile(String name, int age, String albumTitle, String[] photoUrls) {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter("birthday_wish.html"))) {
            writer.write("<html>\n");
            writer.write("<head>\n");
            writer.write("<title>Happy Birthday " + name + "!</title>\n");
            writer.write("</head>\n");
            writer.write("<body>\n");
            writer.write("<h1>Happy Birthday " + name + "!</h1>\n");
            writer.write("<p>May this year bring you joy, happiness, and success!</p>\n");
            writer.write("<p>Wishing you a wonderful year ahead! You're now " + age + " years young!</p>\n");
            writer.write("<h2>" + albumTitle + "</h2>\n");
            writer.write("<div class='photo-album'>\n");
            for (String photoUrl : photoUrls) {
                writer.write("<img src='" + photoUrl + "' alt='Photo' width='200' height='150'>\n");
            }
            writer.write("</div>\n");
            writer.write("</body>\n");
            writer.write("</html>\n");
            System.out.println("HTML file created successfully!");
        } catch (IOException e) {
            System.out.println("Error creating HTML file: " + e.getMessage());
        }
    }
}
```

This program will create an HTML file named `birthday_wish.html` with a link for birthday wishes and a photo album. The photo album will contain the specified number of photos, each with a specified URL.

To run this program, simply compile it and run the resulting Java class file. Follow the prompts to enter the birthday person's name, age, photo album title, and photo URLs. The program will then create the HTML file.
