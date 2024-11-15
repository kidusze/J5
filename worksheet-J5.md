1. A GUI relies on the operating system to handle processes like clicking with a mouse. It also implements a java swing class that enables information hiding, encapsulation, and idea of abstract and inheritance.

2. WindowListener is an interface that defines methods for handling window events in a GUI, while WindowAdapter is a concrete class that implements this interface with empty method implementations, allowing developers to override only the necessary methods.

3. The program creates a GUI with a JFrame that uses a BorderLayout. The window is 400x400 pixels with the title "Quiz J4-2". The left half of the window (West) contains a panel named primes, which is also laid out using BorderLayout. This panel has Button "2" in the East, Button "3" in the West, and Button "5" in the North. The right half of the window (East) contains a panel named composites, also using BorderLayout, with Button "4" in the North and Button "6" in the Center. Button "1" is placed in the Center region of the main JFrame. The result is a layout where the left panel shows Buttons "2", "3", and "5", the right panel shows Buttons "4" and "6", and Button "1" is centered in the middle of the window, dividing the two panels.

4.
```java
public class HelloGoodbyeEx2 {
    public static void main(String args[]) {
        JFrame f = new JFrame();
        f.setTitle("Hello/Goodbye Ex1");
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);


        JLabel label = new JLabel("Hello");
        JButton button = new JButton("Click me!");

        // Counter to track the number of times the button has been clicked
        final int[] clickCount = {0};

        // Using an anonymous class for the button action listener
        button.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                clickCount[0]++; // Increment the click counter

                // Update label text between "Hello" and "Goodbye"
                if (label.getText().equals("Hello")) {
                    label.setText("Goodbye");
                } else {
                    label.setText("Hello");
                }

                // Update the button's label to show the number of clicks
                button.setText("Clicked " + clickCount[0] + " times");
            }
        });
        
        f.add(button, BorderLayout.SOUTH);
        f.add(label, BorderLayout.NORTH);

        f.pack();
        f.setVisible(true);
    }
}
```
5.
```java

public class RedPillBluePill extends JFrame {
  JLabel label;

  public RedPillBluePill() {
      this.setSize(300, 300);
      this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

      JPanel panel = new JPanel(new BorderLayout());        
      JButton red = new JButton("red");
      JButton blue = new JButton("blue");
      panel.add(red, BorderLayout.EAST);
      panel.add(blue, BorderLayout.WEST);
      label =new JLabel("click a button");
      this.add(label, BorderLayout.NORTH);
      this.add(panel, BorderLayout.SOUTH);


      red.addActionListener((e) -> {
            if (l.getText().equals("RED")) {
                l.setText("BLUE");
            }else {
                l.setText("RED");
            }
        });
      blue.addActionListener((e) -> {
            if (l.getText().equals("BLUE")) {
                l.setText("RED");
            }else {
                l.setText("BLUE");
            }
       });
    }
}
```
6. We can use a lambda expression with ActionListener because it has a single abstract method. However, WindowListener cannot be used with a lambda because it has multiple abstract methods, requiring either an anonymous class or a WindowAdapter to handle them.

7.
```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class PinEntry extends JFrame {
    private JTextField display;  // to show the entered PIN
    private String pin = "";  // stores the PIN being entered as a string

    public PinEntry() {
        super();

        // Setup display
        display = new JTextField(10);
        display.setEditable(false); // the display cannot be edited directly

        // Create panel for the buttons
        JPanel buttonPanel = new JPanel(new GridLayout(3, 3, 5, 5)); // 3x3 grid for buttons
        String[] buttons = {
            "1", "2", "3", 
            "4", "5", "6", 
            "7", "8", "9", 
            "<", "0"
        };

        // Add buttons to the panel
        for (String label : buttons) {
            JButton button = new JButton(label);
            button.addActionListener(new ButtonClickListener());
            buttonPanel.add(button);
        }

        // Layout setup
        JPanel mainPanel = new JPanel(new BorderLayout());
        mainPanel.add(display, BorderLayout.NORTH);
        mainPanel.add(buttonPanel, BorderLayout.CENTER);

        this.add(mainPanel);
        this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        this.pack();
    }

    // Inner class to handle button click events
    private class ButtonClickListener implements ActionListener {
        public void actionPerformed(ActionEvent e) {
            String command = e.getActionCommand();
            
            if (command.equals("<")) {
                // Backspace functionality: Remove the last character from pin if there is one
                if (pin.length() > 0) {
                    pin = pin.substring(0, pin.length() - 1);
                }
            } else if (pin.length() < 6) {
                // Only allow entering 6 digits
                pin += command;
            }

            // Update the display based on the current PIN length
            if (pin.equals("202113")) {
                display.setText("YOU MAY ENTER!");
            } else {
                // Show the PIN as typed with the same length, replace digits with asterisks (*)
                StringBuilder displayText = new StringBuilder();
                for (int i = 0; i < pin.length(); i++) {
                    displayText.append("*");
                }
                display.setText(displayText.toString());
            }
        }
    }

    public static void main(String[] args) {
        PinEntry pinEntry = new PinEntry();
        pinEntry.setVisible(true);
    }
}
```
