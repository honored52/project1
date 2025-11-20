  import javax.swing.*;
  import java.awt.*;
  import java.awt.event.*;

  public class Main {
      private int puncte = 0; // contor pentru răspunsuri corecte
      private int intrebareCurenta = 0; // indicele întrebării curente

    private String[] intrebari = {
            "2+2 este 5?:",
            "Capitala Franței este Paris?:",
            "Luna este mai aproape de soare?:",
            "Joe Biden este președintele Rusiei?",
            "Donald Trump este președintele SUA?"
    };

    private String[] raspunsuriCorecte = {
            "fals",
            "adevărat",
            "adevărat",
            "fals",
            "adevărat"
    };

    public void createAndShowGUI() {
        JFrame frame = new JFrame("Test de Adevărat sau Fals");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(600, 300);
        frame.setLayout(new BorderLayout());

        // Panou pentru întrebări
        JLabel questionLabel = new JLabel(intrebari[intrebareCurenta], SwingConstants.CENTER);
        questionLabel.setFont(new Font("Arial", Font.BOLD, 16));
        frame.add(questionLabel, BorderLayout.NORTH);

        // Panou pentru butoane Adevărat/Fals
        JPanel buttonPanel = new JPanel();
        JButton adevaratButton = new JButton("Adevărat");
        JButton falsButton = new JButton("Fals");
        buttonPanel.add(adevaratButton);
        buttonPanel.add(falsButton);
        frame.add(buttonPanel, BorderLayout.CENTER);

        // Panou pentru scor
        JLabel scoreLabel = new JLabel("Puncte: " + puncte, SwingConstants.CENTER);
        scoreLabel.setFont(new Font("Arial", Font.PLAIN, 16));
        frame.add(scoreLabel, BorderLayout.SOUTH);

        ActionListener answerListener = e -> {
            String alegere = e.getActionCommand().toLowerCase();
            boolean corect = false;

            switch (intrebareCurenta) {
                case 0: // 2+2
                    corect = alegere.equals("fals");
                    break;
                case 1: // Capitala Franței
                    corect = alegere.equals("adevărat");
                    break;
                case 2: // Mai aproape de soare
                    corect = alegere.equals("adevărat"); // luna e corect
                    break;
                case 3: // Președintele Rusiei
                    corect = alegere.equals("fals"); // Putin
                    break;
                case 4: // Președintele SUA
                    corect = alegere.equals("adevărat"); // Donald
                    break;
            }

            if (corect) {
                puncte++;
            }

            intrebareCurenta++;
            if (intrebareCurenta < intrebari.length) {
                questionLabel.setText(intrebari[intrebareCurenta]);
            } else {
                questionLabel.setText("Test finalizat! Ai obținut " + puncte + " puncte.");
                adevaratButton.setEnabled(false);
                falsButton.setEnabled(false);
            }

            scoreLabel.setText("Puncte: " + puncte);
        };

        adevaratButton.addActionListener(answerListener);
        falsButton.addActionListener(answerListener);

        frame.setVisible(true);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            new Main().createAndShowGUI();
        });
    }
}
