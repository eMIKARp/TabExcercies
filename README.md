# TabExcercies
A piece of code that creates few tabs and a posibility for a user to create more

    package zakladki;

    import javax.swing.*;
    import java.awt.*;
    import java.awt.event.*;

    public class Main extends JFrame {
    
    private JTabbedPane zakladki = new JTabbedPane();
    private JPanel panelTworzenia = new JPanel();

    public Main()
    {
        initComponets();
    }
    
    public void initComponets()
    {
        this.setTitle("Zakładki");
        this.setBounds(300,300,300,200);
        
        JPanel panel = new JPanel();
        panel.add(new JButton("TO jest taki button"));
        
        this.getContentPane().add(zakladki);
        
        zakladki.addTab("Tab 1", new JLabel("To jest pierwsza zakładka"));
        zakladki.addTab("Tab 2", panel);
        zakladki.addTab("Tab 3", panelTworzenia);
        
        zakladki.setMnemonicAt(0, KeyEvent.VK_T);
        zakladki.setMnemonicAt(1, KeyEvent.VK_A);
        zakladki.setMnemonicAt(2, KeyEvent.VK_B);
        
        zakladki.setTabLayoutPolicy(JTabbedPane.WRAP_TAB_LAYOUT);
        
        
        panelTworzenia.add(new JLabel("Stwórz nowy pliku o nazwie: "));
        final JTextField nazwaNowejZakladki = new JTextField(7);
        panelTworzenia.add(nazwaNowejZakladki);
        JButton stworzZakladke = new JButton("Stwórz zakładkę");
        panelTworzenia.add(stworzZakladke);
        stworzZakladke.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) 
            { 
            JPanel panelTekstowy = new JPanel();
            panelTekstowy.setLayout(new GridLayout(1,1));
            JTextArea obszarTekstowy = new JTextArea();
            panelTekstowy.add(new JScrollPane(obszarTekstowy));
            zakladki.addTab(nazwaNowejZakladki.getText()+".txt",panelTekstowy);    
            zakladki.setSelectedIndex(zakladki.getComponentCount()-1);
            
            zakladki.addKeyListener(new KeyAdapter() {
                
                public void keyPressed(KeyEvent e) {

                    
                    
                }
                
                int indeksZakladki = zakladki.getSelectedIndex();
                String tytulZakladki = zakladki.getTitleAt(indeksZakladki);
                boolean flagaZapisu = true;
                
            });
                
            }
        });
        
        
        this.setDefaultCloseOperation(JFrame.DISPOSE_ON_CLOSE);
    }
    
    public static void main(String[] args) {
       new Main().setVisible(true);
    }
    
    }
