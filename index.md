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
###### Quantum Resistance Cryptography
```markdown

AI: Quantum Resistant Cryptography

Zain Alimam

NOVA Community College



Author’s Note
Zain Alimam, Information System AS degree from NOVA Community College.
Zain Alimam is Transferring to Marymount University to finish a bachelor’s degree in Cyber Security.
Correspondence concerning this article should be addressed to Zain
Alimam, NOVA Community College, 21200 Campus Dr, Sterling, VA 20164.
Contact: zea28@email.vccs.edu

Table of Contents

1.	Abstract………………………………………………… .pg.3
2.	Major Problems with AI Functionality………………… p.g.4
3.	Counter Measures for AI Malfunction…………….……. Pg.5
4.	How Could AI help in Securing Information………….....pg.7
5.	Summary…………………………………………………pg.8
6.	References………………………………………………. Pg.9


Abstract
In a world full of technological advancement, Society relies on technology more than ever.  But with all the Artificial Intelligence (AI) being developed comes risks, which include hackers. Massive sets of sensitive information are being protected by AI systems using Quantum Cryptography. Unlike traditional encryption, quantum communication systems are recognized for offering the potential of virtually indestructible encryption. According to Science Daily, “Now, new research on this topic is shaking up the long-held notion that quantum communications are 100 percent protected. Researchers have recently demonstrated that quantum encryption may be susceptible to hacking” (Optical Society, 2013).  If a program is created to infiltrate the cryptography, then massive amounts of classified information could fall into the wrong hands. The amount of damage would be catastrophic. In order to prevent such events, we need to produce a security system to oversee quantum computers that backs up the defense system to stop and prevent hackers from obtaining unlawful information. This paper analyzes possible defense mechanisms for AIs through Quantum Cryptography. 


Major Problems with AI Functionality
	As society advances and improves, so does the technology used every day. Now, people are becoming more and more dependent on technology that they would not be able to survive without. However, just because we rely on Artificial Intelligence every day doesn’t make it flawless; at the end of the day AI is just a pile of algorithms that were developed by humans. Even when it comes to AI technology, it would not be able to process information that was not implemented in its algorithms. Granados (2018) states, “More and more courts are using an AI product called COMPAS to predicts whether persons convicted of crimes will offend again, and judges are relying on it in handing out sentences. But a thorough study by a third party of actual outcomes over time revealed that COMPAS was heavily infected with racial bias.” Technology is amazing in all aspects, but can it really be trusted with something as serious as “handing out sentences” for criminals?  COMPAS can only perceive calculations that we installed in its hard drive. If you provided the AI with the criminal records from 50 years ago until now, it will run a mathematical equation to figure out whether the accused is guilty or not. The main issue in this situation is that records from 50 years ago would not provide accurate or fair trials in a lot of cases; in return when the AI runs the algorithms, it will not get a fair or unbiased answer. In 2016, Russian scientists managed to create an AI system to develop an online beauty contest with woman from all around the world. When they announced the winners, 97% of the participants were light skinned. When the scientists analyzed their process, it showed that only a small proportion of dark-skinned models were found in data, thus the program concluded that dark-skinned models were an aberration and dismissed their data completely (Granados, 2018).  When it comes to technology and machines, they cannot tell the difference between right and wrong; Humans program them to their concepts of right and wrong; machines cannot learn or adapt to their surroundings. As far as modern technology goes, humans have not been able to create such technology to be able to behave with free will.
Counter Measures for AI Malfunctions
	When new technology is introduced whether it be smartphones, cars, computers etc.  it has to pass many safety procedures to allow proof of its reliability to the consumers. This does not exclude AI systems. In fact, AIs need a lot more safety procedures because most AI are programmed to do multiple complex functions that would take a regular computer twice -or even thrice – as long to process or implement. But that also means that AI could become an even bigger threat to society if something were to go wrong with it. That’s where quantum cryptography can come in to play. In “Artificial Intelligence: The Challenges to Keep it Safe” Conn (2017) states:
Artificial intelligence is designed so that it can learn from interactions with its surroundings and alter its behavior accordingly, which could provide incredible benefits to humanity. Because AI can address so many problems more effectively than people, it has huge potential to improve health and wellbeing for everyone. But it’s not hard to imagine how this technology could go awry. And we don’t need to achieve superintelligence for this to become a problem.
By applying quantum cryptography to AI Systems or even regular technology, the Security will improve by an astounding margin. Data will be encrypted and scrambled due to quantum cryptography and only with the right “Key” or “Keys” would someone be able to access the data. Now, that does not mean that quantum cryptography cannot be hacked because everything has its pattern no matter how random it is. However, it does live up to expectations as far as advanced technology goes. There isn’t that many ways to hack technology, but one of the most common is uploading a virus. A paragraph in “Introductions to Computer Applications” book states:
Vaccines or Antivirus software is a computer program that detects, prevents, and takes action to disarm or remove malicious software programs, such as viruses and worms. New viruses, worms, and other threats are created by cyber terrorists and discovered 
every day. Updating antivirus software is periodically mandatory. (pg.22)

Viruses can do many different things such as erasing the hard drives, copying data, Corrupting data which can cause technology to malfunction etc. some viruses are untraceable until it does whatever it was programmed to do. Having encryptions will stop majority of viruses in AI systems, but there are some viruses made to attack quantum encryptions. If that’s the case, multiple firewalls and antivirus programs - no matter the size - should be implemented in the algorithms which should provide enough time to for the virus/viruses to be detected and take care of any threat. According to FitzGerald in his book Business data communications and networking “A firewall is a router or special-purpose device that examines packets flowing in and out of a network and restricts access to the organization’s network”. (pg.307) Implementing an idea like that will help secure AI encryptions from cyber-attacks and counter attack which could help prevent the hacker from attacking again. Cyber-attacks happen more often than people would thing. Matter of fact, Cyber-attacks happen every second and they never stop. One small malfunction could cause a power outage and that opens doors for hackers to launch an attack that could cause a national crisis. For example, if the government data base goes awry even for a second; someone could have hacked the system took sensitive information and leaked it to other nations. this could lead to an all-out war between countries. Which is Technology need to create more efficient ways to secure data in AI Systems.
How Could AI help in Securing Information
	Protecting data is one of the biggest issues that most programmers face when creating system or other technologies. Encrypting data so that systems are secure takes time and a lot of hard work to accomplish, but in the end, it will be worth the time and effort. Using quantum cryptography enhances the security system majorly especially when programmers and developers include it in newer technology such as computers and AI Systems. Having an AI system built for only protecting against hackers and viruses will make life easier and safer for data. If an AI developed with the right set of algorithms and was encrypted with quantum mechanics, then it can defend against ant cyber-attack coming its way. According to an article on FutureofLife.com:
This research program comes as a sequel to our AI Safety grants competition in 2015, where generous donations from Elon Musk and the Open Philanthropy Project funded 37 researchers to begin various projects to help ensure that artificial intelligence remains safe and beneficial. Now, three years later, our grant winners have produced over 45 scientific publications and a host of conference events, which you can also read about below. 
The research on AI safety was going on a slow pace before Elon Musk. Once he got involved in 2017-18, the amount of funds almost doubled in comparison to 2015. That allowed for resources to be provided for the research, which will help drastically in advancing security in AI systems. 


Summary
Creating an AI system with Quantum encryptions will help better technology and create a safer inner-web safety for people to use every day. Now, there will always be a risk when it comes to concepts and new technology; that’s why people need counter measure to every aspect when something new comes into play.


References
The Optical Society. (2013, May 28). Just how secure is quantum cryptography?.    
ScienceDaily. Retrieved March 22, 2019 from www.sciencedaily.com/releases/2013/05/130528122435.htm

Granados, L. (2018, September-October). Artificial Stupidity: Computers aren't 
bigoted--they're just based on cold calculations, right? The Humanist, 78(5)
, 6+. Retrieved from http://link.galegroup.com.eznvcc.vccs.edu:2048/apps/doc/A552253195/OVIC?u=viva2_vccs&sid=OVIC&xid=0140f2c6

Conn, A. (2017). Artificial Intelligence: The Challenge to Keep it Safe.
Retrieved from https://futureoflife.org/2017/09/21/safety-principle/?cn-reloaded=1

Future of Life. (2018). AI Safety Research. Retrieved from https://futureoflife.org/ai-safety-research/

Tamil, N. (2007). Introductions to Computer Applications and concepts. India: AgriMoon.


FitzGerald, J. & Dennis, A. (2017). Business Data Communications and Networking. New Jersy: Wiley.

```

