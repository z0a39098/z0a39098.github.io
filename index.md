# Senior Protfolio
## By Zain Alimam

### Projects
###### Hotel Reservations GUI

```markdown
import javax.swing.JFrame;
import javax.swing.JButton;
import javax.swing.JLabel; //only component that is used to not collect data
import java.awt.BorderLayout;
import java.awt.GridLayout;
import javax.swing.JTextField;
import javax.swing.JTextArea;
import javax.swing.JPanel;
import javax.swing.JComboBox; //dropbox
import javax.swing.JCheckBox;
import javax.swing.JRadioButton;
import javax.swing.ButtonGroup;
import javax.swing.ImageIcon;
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;
import javax.swing.JOptionPane;

public class Hotel extends JFrame implements ActionListener{
  private JLabel firstName, lastName, checkIn, checkOut, roomLabel, guestLabel, rateLabel, roomType, commentLabel,
    street, city, zip, phone, billing, state, visaLabel, masterLabel, amexLabel, disLabel, cardNum, exp;
  private JTextField firstNameText, lastNameText, inText, outText, streetText, cityText, zipText, phoneText, cardText, 
    expText;
  private JPanel north, south, west, center, east;
  private JButton submit, cancel;
  private JComboBox roomNum, guestNum, stateBox;
  private ButtonGroup sRate, cards;
  private JRadioButton none, aaa, senior, gov, visa, master, amex, discover;
  private JCheckBox studio, family, standard, suite;
  private JTextArea commentArea;
  private ImageIcon visaIcon, masterIcon, amexIcon, disIcon;
  public Hotel() {
   super("Hotel Reservation System");
   
   //North Panel
   firstName = new JLabel("Enter First Name:");
   firstNameText = new JTextField(5);
   lastName = new JLabel("Enter Last Name:");
   lastNameText = new JTextField(5);
   north = new JPanel();
   north.add(firstName);
   north.add(firstNameText);
   north.add(lastName);
   north.add(lastNameText);
   add(north, BorderLayout.NORTH);
   
   //South Panel
   submit = new JButton("Submit" );
   submit.addActionListener(this);
   cancel = new JButton("Cancel");
   cancel.addActionListener(this);
   south = new JPanel();
   south.add(submit);
   south.add(cancel);
   add(south, BorderLayout.SOUTH);
   
   
   //West Panel
   checkIn = new JLabel("Check in Date (MM/DD/YY)");
   inText = new JTextField(5);
   checkOut = new JLabel("Check out Date (MM/DD/YY)");
   outText = new JTextField(5);
   ////
   roomLabel = new JLabel("No. of Rooms");
   String roomList [] = {"1", "2", "3", "4-9", "10-25", "26+"};
   roomNum = new JComboBox(roomList);
   guestLabel = new JLabel("Guests/Rooms");
   String guestList [] = {"1", "2", "3", "4", "5", "6"};
   guestNum = new JComboBox(guestList);
   ////
    rateLabel = new JLabel("SPECIAL RATES");
    none = new JRadioButton("None");
    aaa = new JRadioButton("AAA/CAA");
    senior = new JRadioButton("Senior Discount");
    gov = new JRadioButton("Government & Military");
    sRate = new ButtonGroup();
    sRate.add(none);
    sRate.add(aaa);
    sRate.add(senior);
    sRate.add(gov);
    ////
    roomType = new JLabel("Room Type");
    studio = new JCheckBox("Studio");
    standard = new JCheckBox("Standard");
    family = new JCheckBox("Family");
    suite = new JCheckBox("Suite");
    ////
    commentLabel = new JLabel ("Special Requests");
   commentArea = new JTextArea(5,10);
   ////
   west = new JPanel();
   west.setLayout(new GridLayout(20,2));
   west.add(checkIn);
   west.add(inText);
   west.add(checkOut);
   west.add(outText);
   west.add(roomLabel);
   west.add(roomNum);
   west.add(guestLabel);
   west.add(guestNum);
   west.add(rateLabel);
   west.add(none);
   west.add(aaa);
   west.add(senior);
   west.add(gov);
   west.add(roomType);
   west.add(studio);
   west.add(standard);
   west.add(family);
   west.add(suite);
   west.add(commentLabel);
   west.add(commentArea);
   add(west, BorderLayout.WEST);
   
   //Center Panel
   billing = new JLabel ("Billing Address: ");
   street = new JLabel("Street:");
   streetText = new JTextField(10);
   city = new JLabel("City:");
   cityText = new JTextField(10);
   ////
   state = new JLabel("State: ");
   String stateList [] = {" ", "DC", "VA", "MD"};
   stateBox = new JComboBox(stateList);
   ////
   zip = new JLabel("Zipcode:");
   zipText = new JTextField(10);
   phone = new JLabel("Phone Number:");
   phoneText = new JTextField(10);
   center = new JPanel();
   center.setLayout(new GridLayout(16,0));
   center.add(billing);
   center.add(street);
   center.add(streetText);
   center.add(city);
   center.add(cityText);
   center.add(state);
   center.add(stateBox);
   center.add(zip);
   center.add(zipText);
   center.add(phone);
   center.add(phoneText);
   add(center, BorderLayout.CENTER);
   
   //East Panel
    visa = new JRadioButton("");
    visaIcon = new ImageIcon("visa.gif");
    visaLabel = new JLabel(visaIcon);
    master = new JRadioButton("");
    masterIcon = new ImageIcon("master.gif");
    masterLabel = new JLabel(masterIcon);
    amex = new JRadioButton("");
    amexIcon = new ImageIcon("amex.gif");
    amexLabel = new JLabel(amexIcon);
    discover = new JRadioButton("");
    disIcon = new ImageIcon("discover.gif");
    disLabel = new JLabel(disIcon);
    cards = new ButtonGroup();
    cards.add(visa);
    cards.add(master);
    cards.add(amex);
    cards.add(discover);
    ////
   cardNum = new JLabel("Credit Card Number: ");
   cardText = new JTextField(16);
   exp = new JLabel("Experation Date: ");
   expText = new JTextField(5);
    
    east = new JPanel();
    east.setLayout(new GridLayout(16,20));
    east.add(visa);
    east.add(visaLabel);
    east.add(master);
    east.add(masterLabel);
    east.add(amex);
    east.add(amexLabel);
    east.add(discover);
    east.add(disLabel);
    east.add(cardNum);
    east.add(cardText);
    east.add(exp);
    east.add(expText);
    add(east, BorderLayout.EAST);
   
    
    
    setSize(800, 1000);
    setVisible(true);
    setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE); 
  }
  public void actionPerformed(ActionEvent event) {
    if(event.getSource() == submit){
      String fName = firstNameText.getText();
      String lName = lastNameText.getText();
      String inDate = inText.getText();
      String outDate = outText.getText();
      String room = roomNum.getSelectedItem().toString();
      String guest = guestNum.getSelectedItem().toString();
      String rate = "";
      String sInfo = streetText.getText();
      String cInfo = cityText.getText();
      String stateInfo = stateBox.getSelectedItem().toString();
      String zInfo = zipText.getText();
      String pInfo = phoneText.getText();
      String cNum = cardText.getText();
      String expInfo = expText.getText();
      
      if(none.isSelected()){
        
        rate = "None";
      } else if(aaa.isSelected()){
        
       rate = "AAA/CAA";
      } else if(senior.isSelected()){
        
        rate = "Senior Discount";
      } else if(gov.isSelected()){
        
        rate = "Government & military";
      }
      
      String studioType = "No";
      if(studio.isSelected()){
        studioType = "Yes";
      }
      String stndType = "No";
      if(standard.isSelected()){
        stndType = "Yes";
      }
      String fType = "No";
      if(family.isSelected()){
        fType = "Yes";
      }
      String suiteType = "No";
      if(suite.isSelected()){
        suiteType = "Yes";
      }
      String comment = commentArea.getText();
      
      String cardTypes = "";
      if(visa.isSelected()){
        
        cardTypes = "Visa Card";
      } else if(master.isSelected()){
        
       cardTypes = "Master Card";
      } else if(amex.isSelected()){
        
        cardTypes = "Amex Card";
      } else if(discover.isSelected()){
        
        cardTypes = "Discover Card";
      }
      
      
      
      String output = "First Name: " + fName + "\nLast Name: " + lName + "\nCheck In Date: " + inDate + 
       "\nCheck Out Date: "  + outDate + "\nNo. of Rooms: " + room + "\nGuest/Room: " + guest + 
        "\nSpecial Rates: " + rate + "\nRoom Type: \nStudio: " + studioType + "\n Standard: " + stndType + "\nFamily: " + fType
        + "\nSuite: " + suiteType + "\nSpecial Requests:\n" + comment + "\nBilling Address:\n" + sInfo +"\n" + cInfo + 
        ", " + stateInfo + " " + zInfo + "\nPhone Number: " + pInfo + "\nCard Type: " + cardTypes + "\nCredit Card Number: "
        + cNum + "\nExperation Date: " + expInfo;
      JOptionPane.showMessageDialog(null, output);
      
      
    } else if (event.getSource() == cancel){
      
      //i kept those in order of to show which is which
      firstNameText.setText("");
      lastNameText.setText("");
      inText.setText("");
      outText.setText("");  
      roomNum.setSelectedIndex(0);
      guestNum.setSelectedIndex(0);
      sRate.clearSelection();
      studio.setSelected(false);
      standard.setSelected(false);
      family.setSelected(false);
      suite.setSelected(false);
      commentArea.setText("");
      streetText.setText("");
      cityText.setText("");
      stateBox.setSelectedIndex(0);
      zipText.setText("");
      phoneText.setText("");
      cards.clearSelection();
      cardText.setText("");
      expText.setText("");
    }
  
  
  
  
  }
  
  public static void main(String [] args) {
    Hotel app = new Hotel();
  }
}

```
[Hotel Reservations Gui](file:///C:/Users/zaina/Desktop/Assignments/Hotel%20Reservations%20GUI.pdf)

