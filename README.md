import java.awt.*;
import java.awt.event.*;

public class VehicleServiceAWT extends Frame implements ActionListener {

    Label lUser, lPass, lMsg;
    TextField tUser, tPass;
    Button bLogin;

    Label lGreet, lVehicle, lVno, lOwner, lService, lDate, lCost;
    TextField tVno, tOwner, tDate, tCost;
    Choice cVehicle, cService;
    Button bSubmit, bClear, bExit;
    TextArea ta;

    String loggedUser = "";

    Color bgColor = new Color(30, 30, 30);
    Color fieldColor = new Color(60, 60, 60);
    Color textColor = Color.WHITE;

    VehicleServiceAWT() {

        setTitle("Vehicle Service Record Management System");
        setSize(650, 700);
        setLayout(null);
        setBackground(bgColor);

        Font f = new Font("Arial", Font.BOLD, 12);

        lUser = new Label("Username:");
        lUser.setBounds(220, 140, 100, 20);
        lUser.setForeground(textColor);
        add(lUser);

        tUser = new TextField();
        tUser.setBounds(330, 140, 140, 22);
        tUser.setBackground(fieldColor);
        tUser.setForeground(Color.WHITE);
        add(tUser);

        lPass = new Label("Password:");
        lPass.setBounds(220, 180, 100, 20);
        lPass.setForeground(textColor);
        add(lPass);

        tPass = new TextField();
        tPass.setEchoChar('*');
        tPass.setBounds(330, 180, 140, 22);
        tPass.setBackground(fieldColor);
        tPass.setForeground(Color.WHITE);
        add(tPass);

        bLogin = new Button("LOGIN");
        bLogin.setBounds(300, 230, 80, 30);
        bLogin.setBackground(new Color(0, 153, 76));
        bLogin.setForeground(Color.WHITE);
        bLogin.setFont(f);
        add(bLogin);

        lMsg = new Label("");
        lMsg.setBounds(220, 270, 300, 20);
        lMsg.setForeground(Color.RED);
        add(lMsg);

        bLogin.addActionListener(this);

        addWindowListener(new WindowAdapter() {
            public void windowClosing(WindowEvent e) {
                dispose();
            }
        });

        setVisible(true);
    }

    void openServiceScreen() {

        removeAll();
        repaint();
        setBackground(bgColor);

        Font f = new Font("Arial", Font.BOLD, 12);

        lGreet = new Label("Hello " + loggedUser);
        lGreet.setBounds(260, 40, 250, 20);
        lGreet.setForeground(Color.GREEN);
        add(lGreet);

        lVehicle = new Label("Vehicle Type:");
        lVehicle.setBounds(80, 90, 120, 20);
        lVehicle.setForeground(textColor);
        add(lVehicle);

        cVehicle = new Choice();

        if (loggedUser.equals("Ankit")) {
            cVehicle.add("Scorpio S11");
            cVehicle.add("Bolero");
            cVehicle.add("RE Standard 350");
            cVehicle.add("Fortuner");
            cVehicle.add("Tata Truck");
        } else {
            cVehicle.add("Honda Amaze");
            cVehicle.add("Classic 350");
            cVehicle.add("Tata Trolley");
            cVehicle.add("Dumper");
        }

        cVehicle.setBounds(230, 90, 260, 22);
        cVehicle.setBackground(fieldColor);
        cVehicle.setForeground(Color.WHITE);
        add(cVehicle);

        lVno = new Label("Vehicle No:");
        lVno.setBounds(80, 130, 120, 20);
        lVno.setForeground(textColor);
        add(lVno);

        tVno = new TextField();
        tVno.setBounds(230, 130, 260, 22);
        tVno.setBackground(fieldColor);
        tVno.setForeground(Color.WHITE);
        add(tVno);

        lOwner = new Label("Owner Name:");
        lOwner.setBounds(80, 170, 120, 20);
        lOwner.setForeground(textColor);
        add(lOwner);

        tOwner = new TextField();
        tOwner.setBounds(230, 170, 260, 22);
        tOwner.setBackground(fieldColor);
        tOwner.setForeground(Color.WHITE);
        add(tOwner);

        lService = new Label("Service Type:");
        lService.setBounds(80, 210, 120, 20);
        lService.setForeground(textColor);
        add(lService);

        cService = new Choice();
        cService.add("General Service");
        cService.add("Oil Change");
        cService.add("Engine Repair");
        cService.add("Full Service");
        cService.setBounds(230, 210, 260, 22);
        cService.setBackground(fieldColor);
        cService.setForeground(Color.WHITE);
        add(cService);

        lDate = new Label("Service Date:");
        lDate.setBounds(80, 250, 120, 20);
        lDate.setForeground(textColor);
        add(lDate);

        tDate = new TextField();
        tDate.setBounds(230, 250, 260, 22);
        tDate.setBackground(fieldColor);
        tDate.setForeground(Color.WHITE);
        add(tDate);

        lCost = new Label("Cost:");
        lCost.setBounds(80, 290, 120, 20);
        lCost.setForeground(textColor);
        add(lCost);

        tCost = new TextField();
        tCost.setBounds(230, 290, 260, 22);
        tCost.setBackground(fieldColor);
        tCost.setForeground(Color.WHITE);
        add(tCost);

        bSubmit = new Button("SUBMIT");
        bSubmit.setBounds(120, 340, 90, 30);
        bSubmit.setBackground(new Color(0, 153, 76));
        bSubmit.setForeground(Color.WHITE);
        add(bSubmit);

        bClear = new Button("CLEAR");
        bClear.setBounds(270, 340, 90, 30);
        bClear.setBackground(new Color(255, 153, 51));
        add(bClear);

        bExit = new Button("EXIT");
        bExit.setBounds(420, 340, 90, 30);
        bExit.setBackground(new Color(204, 0, 0));
        bExit.setForeground(Color.WHITE);
        add(bExit);

        ta = new TextArea();
        ta.setBounds(80, 390, 480, 220);
        ta.setBackground(new Color(50, 50, 50));
        ta.setForeground(Color.WHITE);
        add(ta);

        bSubmit.addActionListener(this);
        bClear.addActionListener(this);
        bExit.addActionListener(this);

        setVisible(true);
    }

    public void actionPerformed(ActionEvent e) {

        if (e.getSource() == bLogin) {

            if (tUser.getText().equals("Abhiram") && tPass.getText().equals("Abhiram008")) {
                loggedUser = "Abhiram";
                openServiceScreen();
            }
            else if (tUser.getText().equals("Ankit") && tPass.getText().equals("Ankit008")) {
                loggedUser = "Ankit";
                openServiceScreen();
            }
            else {
                lMsg.setText("Invalid Login Details");
            }
        }

        if (e.getSource() == bSubmit) {
            ta.setText(
                "User: " + loggedUser + "\n" +
                "Vehicle: " + cVehicle.getSelectedItem() + "\n" +
                "Vehicle No: " + tVno.getText() + "\n" +
                "Owner: " + tOwner.getText() + "\n" +
                "Service: " + cService.getSelectedItem() + "\n" +
                "Date: " + tDate.getText() + "\n" +
                "Cost: " + tCost.getText()
            );
        }

        if (e.getSource() == bClear) {
            tVno.setText("");
            tOwner.setText("");
            tDate.setText("");
            tCost.setText("");
            ta.setText("");
        }

        if (e.getSource() == bExit) {
            dispose();
        }
    }

    public static void main(String[] args) {
        new VehicleServiceAWT();
    }
}
