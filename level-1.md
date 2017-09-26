* **Encoding**

  is for maintaining data _usability_

  and can be reversed by employing the same algorithm that encoded the content, i.e. no key is used.

* **Encryption**  
   is for maintaining data _confidentiality_  
   and requires the use of a key \(kept secret\) in order to return to plaintext.

* **Hashing**
   is for validating the _integrity_
   of content by detecting all modification thereof via obvious changes to the hash output.
* **Obfuscation**
   is used to _prevent people from understanding_
   the meaning of something, and is often used with computer code to help prevent successful reverse engineering and/or theft of a product’s functionality.
* **Salting**

  Passwords are often described as “hashed and salted”. Salting is simply the addition of a unique, random string of characters known only to the site to each password before it is hashed, typically this “salt” is placed in front of each password.

* **Peppering**

  Cryptographers like their seasonings. A “pepper” is similar to a salt - a value added to the password before being hashed - but typically placed at the end of the password.

One might ask when obfuscation would be used instead of encryption, and the answer is that obfuscation is used to make it harder for one entity to understand \(like a human\) while still being easy to consume for something else \(like a computer\). With encryption, neither a human or a computer could read the content without a key.

