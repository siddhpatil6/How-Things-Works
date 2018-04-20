# How-Things-Works
Here we will get to know how technology works of different apps and Sites

How Video and Voice Calling Works? <br>
https://blog.mindorks.com/how-voice-and-video-call-works-b0896aa0a630


# How AES Encryption Works?

* AES comprises three block ciphers: AES-128, AES-192 and AES-256. Each cipher encrypts and decrypts data in blocks of 128 bits using cryptographic keys of 128-, 192- and 256-bits, respectively. The Rijndael cipher was designed to accept additional block sizes and key lengths, but for AES, those functions were not adopted.

## AES encryption block cipher
Symmetric (also known as secret-key) ciphers use the same key for encrypting and decrypting, so the sender and the receiver must both know -- and use -- the same secret key. All key lengths are deemed sufficient to protect classified information up to the "Secret" level with "Top Secret" information requiring either 192- or 256-bit key lengths. There are 10 rounds for 128-bit keys, 12 rounds for 192-bit keys and 14 rounds for 256-bit keys -- a round consists of several processing steps that include substitution, transposition and mixing of the input plaintext and transform it into the final output of ciphertext.

* The AES encryption algorithm defines a number of transformations that are to be performed on data stored in an array. The first step of the cipher is to put the data into an array; after which the cipher transformations are repeated over a number of encryption rounds. The number of rounds is determined by the key length, with 10 rounds for 128-bit keys, 12 rounds for 192-bit keys and 14 rounds for 256-bit keys.

* The first transformation in the AES encryption cipher is substitution of data using a substitution table; the second transformation shifts data rows, the third mixes columns. The last transformation is a simple exclusive or (XOR) operation performed on each column using a different part of the encryption key -- longer keys need more rounds to complete.

```
public static SecretKey generateKey() 
    throws NoSuchAlgorithmException, InvalidKeySpecException 
{ 
    return secret = new SecretKeySpec(password.getBytes(), "AES"); 
}

public static byte[] encryptMsg(String message, SecretKey secret)
    throws NoSuchAlgorithmException, NoSuchPaddingException, InvalidKeyException, InvalidParameterSpecException, IllegalBlockSizeException, BadPaddingException, UnsupportedEncodingException 
{ 
   /* Encrypt the message. */
   Cipher cipher = null; 
   cipher = Cipher.getInstance("AES/ECB/PKCS5Padding");
   cipher.init(Cipher.ENCRYPT_MODE, secret); 
   byte[] cipherText = cipher.doFinal(message.getBytes("UTF-8")); 
   return cipherText; 
}

public static String decryptMsg(byte[] cipherText, SecretKey secret) 
    throws NoSuchPaddingException, NoSuchAlgorithmException, InvalidParameterSpecException, InvalidAlgorithmParameterException, InvalidKeyException, BadPaddingException, IllegalBlockSizeException, UnsupportedEncodingException 
{
    /* Decrypt the message, given derived encContentValues and initialization vector. */
    Cipher cipher = null;
    cipher = Cipher.getInstance("AES/ECB/PKCS5Padding");
    cipher.init(Cipher.DECRYPT_MODE, secret); 
    String decryptString = new String(cipher.doFinal(cipherText), "UTF-8");
    return decryptString; 
}
```

# How SHA1 Works?
https://deadhacker.com/2006/02/21/sha-1-illustrated/
<br>
I googled “SHA1 illustrated” and found this article: SHA-1 Illustrated.

Abstract from the referenced article:

The following simplifies the specification of SHA-1 in an easy to digest form. First we will cover the general structure of the algorithm. Detail of the expansion and compression routines are covered separately.


First we start with a message. The message is padded and the length of the message is added to the end. It is then split into blocks of 512 bits (Figure 2).


(Figure 2)

The blocks are then processed one at a time. Each block must be expanded and compressed. The value after each compression is added to a 160bit buffer called the current hash state. After the last block is processed the current hash state is returned as the final hash. A overview of this procedure can be seen in Figure 3.


Go to the article to read more


