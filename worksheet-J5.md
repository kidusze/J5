1. A GUI relies on the operating system to handle processes like clicking with a mouse. It also implements a java swing class that enables information hiding, encapsulation, and idea of abstract and inheritance.

2. WindowListener is an interface that defines methods for handling window events in a GUI, while WindowAdapter is a concrete class that implements this interface with empty method implementations, allowing developers to override only the necessary methods.

3. The program creates a GUI with a JFrame that uses a BorderLayout. The window is 400x400 pixels with the title "Quiz J4-2". The left half of the window (West) contains a panel named primes, which is also laid out using BorderLayout. This panel has Button "2" in the East, Button "3" in the West, and Button "5" in the North. The right half of the window (East) contains a panel named composites, also using BorderLayout, with Button "4" in the North and Button "6" in the Center. Button "1" is placed in the Center region of the main JFrame. The result is a layout where the left panel shows Buttons "2", "3", and "5", the right panel shows Buttons "4" and "6", and Button "1" is centered in the middle of the window, dividing the two panels.

4.FAF
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
