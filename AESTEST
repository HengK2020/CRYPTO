
import javax.crypto.Cipher;
import javax.crypto.KeyGenerator;
import javax.crypto.SecretKey;
import java.util.Scanner;
import java.util.Base64;

public class AESTEST {
	
	private static final String UNICODE_FORMAT = "UTF-8";
	
	public static void main(String[]args) {
																	//Displays message and prompts user to enter in message
		Scanner sc = new Scanner(System.in);
		System.out.println("Enter message to encrypt:");
		String text = sc.nextLine();
		sc.close();
		try
		{
																	//Created variable for cipher and SecretKey then generates AES
			SecretKey key = generateKey("AES");
			Cipher ci;
			ci = Cipher.getInstance("AES");
																	//Takes the input from text and encrypts with AES variables above from the method encryptString
			byte[] encryptedData = encryptString(text,key,ci);
																	//The encrypted data is passed through as a string
			String encryptedString = new String(encryptedData);
																	//Formatted the UTF-8 into base64 string into variable then printed out
			String enc = Base64.getEncoder().encodeToString(encryptedString.getBytes(UNICODE_FORMAT));
			System.out.println(enc);
			
																	//Takes in the encrypted String with the cipher and SecretKey and created a new string variable then printed
			String decrypted = decryptString(encryptedData,key,ci);
			System.out.println(decrypted);
		}
		catch(Exception k)
		{
		
		}
	
	}
	
	public static SecretKey generateKey(String encryptionType)
	{
		try
		{
																	//Generates a secret key
			KeyGenerator keyGenerator = KeyGenerator.getInstance(encryptionType);
			SecretKey myKey = keyGenerator.generateKey();
			return myKey;
		}
		catch(Exception k)
		{
			return null;
		}
	}
	
	public static byte[] encryptString(String dataToEncrypt, SecretKey myKey, Cipher cipher)
	{
		try
		{
																	//Takes the user inputed message and encrypts with UTF-8 then stores into textEncrypted
			byte[] text = dataToEncrypt.getBytes(UNICODE_FORMAT);
			cipher.init(Cipher.ENCRYPT_MODE,  myKey);
			byte[] textEncrypted = cipher.doFinal(text);
			
			return textEncrypted;
		}
		catch(Exception k)
		{
			return null;
		}
	}
	
	public static String decryptString(byte[] dataToDecrypt, SecretKey myKey, Cipher cipher)
	{
		try
		{
																	//Takes in the textEncrypted and decrypts it using the secret key generated then stores into results
			cipher.init(Cipher.DECRYPT_MODE, myKey);
			byte[] textDecrypted = cipher.doFinal(dataToDecrypt);
			String result = new String(textDecrypted);
			
			return result;
		}
		catch(Exception k)
		{
			System.out.println(k);
			return null;
		}
	}
}
