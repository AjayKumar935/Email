# Sending the email  via Java

## code

``` java
import java.net.Authenticator;
import java.net.PasswordAuthentication;
import java.util.Properties;
import javax.mail.Message;
import javax.mail.MessagingException;
import javax.mail.Session;
import javax.mail.Transport;
import javax.mail.internet.AddressException;
import javax.mail.internet.InternetAddress;
import javax.mail.internet.MimeMessage;
import javax.mail.*;

public class mailTest {

	public static void main(String[] args) {
		StringBuilder sb1=new StringBuilder();
		String sender="ajay.a@doppiogroup.com";
		String password="@@Dolly1234";
		String receiver="ajaycse2024@gmail.com";
		String host="smtp.gmail.com";
		Properties properties=System.getProperties();
		properties.setProperty("mail.smtp.host", host);
		properties.put("mail.smtp.starttls.enable", "true");
		properties.put("mail.smtp.port", "587");
	    properties.put("mail.smtp.auth", "true");
	    String msg=sb1.toString("Hii");
	    
	    
//	    Session session=Session.getDefaultInstance(properties,
//	            new Authenticator() {
//            protected PasswordAuthentication getPasswordAuthentication() {
//                return new PasswordAuthentication(sender,password);
//            }
//        });
	    
	    Session session = Session.getDefaultInstance(properties, new javax.mail.Authenticator() {
	    	protected javax.mail.PasswordAuthentication getPasswordAuthentication () {
	    		return new javax.mail.PasswordAuthentication(sender, password);
	    	}
 		});
	    
	    
	    
		session.setDebug(true);
		session.setDebug(true);
		try {
			MimeMessage message=new MimeMessage(session);
			message.setFrom(new InternetAddress(sender));
			 message.addRecipient(Message.RecipientType.TO, new InternetAddress(receiver));
			
			message.setText(msg);
			 Transport.send(message);
			
		} catch (AddressException e) {
			e.printStackTrace();
		} catch (MessagingException e) {
			
			e.printStackTrace();
		}
	}
}

```
