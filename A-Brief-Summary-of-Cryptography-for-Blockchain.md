# A Brief Summary of Cryptography for Blockchain
Moonwon Lee @ berkeley.edu


## Development
1. Miracle : Public Key Encryption Scheme -> 
2. Problem : Impersonation Attack ->
3. Solution + Miracle : Digital Signature (which is basically based on Public Key Techniques or Public Key Encryption System) (But there is one based on Symmetric Key too)
4. Problem : Existential Forgery
5. Solution : TTP(Conditional for DS based on Public Key) and TTP(Unconditional for one based on Symmetric Key)


## Overview
* Cryptography System
  * Symmetric Cryptography System
    * Encryption Scheme
    * Digital Signature
  * Public Key Cryptography System 
    * Encryption Scheme
    * Digital Signature 
* Cryptography System
  * Encryption Scheme
    * Symmetric Key
    * Public Key
  * Digital Signature
    * Symmetric Key
    * Public Key


## Summary		



### 1. Security Objects
 1. Privacy 	= keeping information secret from all but those who are autho- rized to see it.
 2. Data integrity	 = ensuring information has not been altered by unauthorized or unknown means.
 3. Entity authentication or identification = corroboration of the identity of an entity (e.g., a person, a computer terminal, a credit card, etc.).
 4. Message authentication = corroborating the source of information; also known as data origin authentication.
 5. Signature 	= a means to bind information to an entity.
 6. Authorization = conveyance, to another entity, of official sanction to do or be something.
 7. Validation	 = a means to provide timeliness of authorization to use or ma- nipulate information or resources.
 8. Access control = restricting access to resources to privileged entities.
 9. Certification	 = endorsement of information by a trusted entity.
 10. Timestamping	 = recording the time of creation or existence of information.
 11. Witnessing 	= verifying the creation or existence of information by an entity other than the creator.
 12. Receipt	 = acknowledgement that information has been received.
 13. Confirmation	 = acknowledgement that services have been provided.
 14. Ownership	 = a means to provide an entity with the legal right to use or transfer a resource to others.
 15. Anonymity	 = concealing the identity of an entity involved in some process.
 16. Non-repudiation = preventing the denial of previous commitments or actions.
 17. Revocation 	= retraction of certification or authorization.
### 2. Encryption Scheme 
 1. Symmetric Key Encryption 
     1. (=Private Key)
     2. Figure 1.7: ‘Two-party communication using encryption, with a secure channel for key exchange’ 
     3. Problem = Key Distribution Problem (or Key Establishment): of symmetric-key systems is to find an efficient method to agree upon and exchange keys securely.   
 2. Public Key Encryption Scheme
     1. Figure 1.11 : ‘Two-party communication using Encryption, with unsecured channels for key exchange and ciphertext transmission  using public-key techniques’
     2. As a physical analogue : consider a metal box with the lid secured by a combination lock. The combination is known only to Bob. If the lock is left open and made publicly available then anyone can place a message inside and lock the lid. Only Bob can retrieve the message. Even the entity which placed the message into the box is unable to retrieve it 
     3. Problem : The necessity of authentication in public-key systems 
         1. Protocol Failure
             1. Impersonation Attack
                 1. In this scenario the adversary impersonates entity B by sending entity A a public key e′ which A assumes (incorrectly) to be the public key of B. The adversary intercepts encrypted messages from A to B, decrypts with its own private key d′, re-encrypts the message under B’s public key e, and sends it on to B. 			
                 2. This highlights the necessity to authenticate public keys to achieve data origin authentication of the public keys themselves. A must be convinced that she is encrypting under the legitimate public key of B. 
                 3. Fortunately, public-key techniques also allow an elegant solution to this problem 	 
                 4. Figure 1.13: An impersonation attack on a two-party communication. 
     4. A public-key encryption scheme of this type is called reversible
         1. Used for Digital Signature
         2. This type : Dd(Ee(m)) = Ee(Dd(m)) = m, for all m ∈ M. 
 3. (Private key vs. Secret key) : To avoid ambiguity, a common convention is to use the term private key in association with public-key cryptosystems, and secret key in association with symmetric-key cryptosystems. 		
     1. but none have been mathematically proven to be secure independent of qualifying assumptions. This is not unlike the symmetric-key case where the only system which has been proven secure is the one-time pad (§1.5.4). 
### 3. Public Key Crypto System
 1. RSA Public Key Crypto System
     1. Hardness of Factorization Problem
         1. Not proven to be NP-C. 
     2. Easiness of Primality Test 
         1. Logarithmic Polynomial 
### 4. Digital Signatures Schemes (Digital Signature Scheme with message recovery based on Public Key)	
 1. Purpose:  of a digital signature is to provide a means for an entity to bind its identity to a piece of information 		
 2. Digital Signature Scheme: The transformations SA and VA provide a digital signature scheme for A. 
     1. (=Digital Signature mechanism): Occasionally the term digital signature mechanism is used. 
 3. Digital signatures Scheme from reversible public-key encryption based on public-key encryption systems of a particular type			
     2. A public-key encryption scheme of this type is called reversible
         1. Used for Digital Signature
         2. This type : Dd(Ee(m)) = Ee(Dd(m)) = m, for all m ∈ M. 
     3. Figure 1.14 : A Digital Signature Scheme with message recovery 
 4. Digital Signature Scheme based on Symmetric key exists and needs TTP : Ch11
 5. Problem :  Existential Forgery
     1. Note that any entity B can select a random element s ∈ S as a signature and apply Ee to get u = Ee(s), since S = M and Ee is public knowledge. B may then take the message m = u and the signature on m to be s and transmits (m, s). It is easy to check that s will verify as a signature created by A for m but in which A has had no part. In this case B has forged a signature of A. 
 6. Limit : 	(digital signatures vs. confidentiality) Although digital signature schemes based on reversible public-key encryption are attractive, they require an encryption method as a primitive. There are situations where a digital signature mechanism is required but encryption is forbidden. In such cases these digital signature schemes are inappropriate. 
 7. Purpose then Problem(Limit) Again : 		 	 	 		
     1. The purpose of a digital signature (or any signature method) is to permit the resolution of disputes. For example, an entity A could at some point deny having signed a message or some other entity B could falsely claim that a signature on a message was produced by A. In order to overcome such problems a trusted third party (TTP) or judge is required. The TTP must be some entity which all parties involved agree upon in advance 
 8. Solution : TTP				
     1. The TTP must be some entity which all parties involved agree upon in advance. 
     2. The TTP has an authentic copy of VA.
     3. If A denies that a message m held by B was signed by A, then B should be able to present the signature sA for m to the TTP along with m. The TTP rules in favor of B if VA(m, sA) = true and in favor of A otherwise. B will accept the decision if B is confident that the TTP has the same verifying transformation VA as A does. A will accept the decision if A is confident that the TTP used VA and that SA has not been compromised. Therefore, fair resolution of disputes requires that the following criteria are met. 
 9. Conclusion : Requirements for resolution of disputed signatures				
     1. 1. SA and VA have properties (a) and (b) of page 23.
     2. 2. The TTP has an authentic copy of VA.
     3. 3. The signing transformation SA has been kept secret and remains secure. 
### 5. Symmetric Key Cryptography VS Public Key Cryptography				
 1. Key Length: 
     1. Private keys in public-key systems must be larger (e.g., 1024 bits for RSA) than secret keys in symmetric-key systems (e.g., 64 or 128 bits) 
     2. Reason : because whereas (for secure algorithms) the most efficient attack on symmetric- key systems is an exhaustive key search, all known public-key systems are subject to “short- cut” attacks (e.g., factoring) more efficient than exhaustive search 
### 6. Summary : Current cryptographic systems exploit the strengths of each. 	
 1. Public Key + Symmetric Key = Example : Public-key encryption techniques may be used to establish a key for a symmetric-key system being used by communicating entities A and B. In this scenario A and B can take advantage of the long term nature of the public/private keys of the public-key scheme and the performance efficiencies of the symmetric-key scheme. Since data encryption is frequently the most time consuming part of the encryption process, the public-key scheme for key establishment is a small fraction of the total encryption process between A and B. 
     1. Summary 
         1. Public-key cryptography facilitates efficient signatures (particularly non-repudiation) and key management 
         2. Symmetric-key cryptography is efficient for encryption and some data integrity applications.  	
         3. Performance Optimized! 
### 7. Mechanism > Protocol 
### 8. Protocol (~=Mechanism)  	 	
 1. The Basic Primitives
     1. Examples
         1. the Symmetric-key Encryption Schemes
         2. the Public-key Encryption Schemes  	
 2. Protocol Failure	
     1. = occurs when a mechanism fails to meet the goals for which it was intended, in a manner whereby an adversary gains advantage not by breaking an underlying primitive such as an encryption algorithm directly, but by manipulating the protocol or mechanism itself. 
     2. Examples
         1. the inherent assumption that encryption provides data integrity is incorrect. 
         2. Forward Search Attack	
             1. Example : Suppose that in an electronic bank transaction the 32- bit field which records the value of the transaction is to be encrypted using a public-key scheme. This simple protocol is intended to provide privacy of the value field – but does it? An adversary could easily take all 232 possible entries that could be plaintext in this field and encrypt them using the public encryption function. (Remember that by the very nature of public-key encryption this function must be available to the adversary.) By comparing each of the 2^32 ciphertexts with the one which is actually encrypted in the transaction, the adversary can determine the plaintext. Here the public-key encryption function is not compromised, but rather the way it is used. A closely related attack which applies directly to authentication for access control purposes is the dictionary attack (see §10.2.2) 
### 9. Key Distribution (Ch12) 
 1. = Key Establishment + Key Management
 2. Key Establishment 
     1. = Key Agreement + Key Transport
     2. Def : any process whereby a shared secret key becomes available to two or more parties, for subsequent cryptographic use
     3. Key Agreement
     4. Key Transport
 3. Key Management
     5. Def : the set of processes and mechanisms which support key establishment and the maintenance of ongoing keying relationships between parties, including replacing older keys with new keys as necessary. 
 4. Problems
     1. Keying relationships in a simple 6-party network 
         1. Problem : 
             1. Key Establishment (exchange)  of So Many Keys
             2. Key Management 
 5. Solutions
     1. Key Management Through Symmetric Key Techniques
     2. Key Management Through Public Key Techniques
### 10. Key Management Techniques
 1. Key Management Through Symmetric Key Techniques		
     1. One solution : employs symmetric-key techniques involves an entity in the network which is trusted by all other entities. As in §1.8.3, this entity is referred to as a trusted third party (TTP). Each entity Ai shares a distinct symmetric key ki with the TTP. These keys are assumed to have been distributed over a secured channel. If two entities subsequently wish to communicate, the TTP generates a key k (sometimes called a session key) and sends it encrypted under each of the fixed keys as depicted in Figure 1.16 for entities A1 and A5. 			
     2. Figure 1.16: Key management using a trusted third party (TTP). 	
     3. Advantages of this approach include:
         1. It is easy to add and remove entities from the network. 
         2. Each entity needs to store only one long-term secret key.		
     4. Disadvantages include:				
         1. All communications require initial interaction with the TTP. 
         2. The TTP must store _n_ long-term secret keys. 
         3. The TTP can read all messages
         4. If the TTP compromised, all communications are insecure
 2. Key Management Through Public Key Techniques
     1. There are many ways (more in Ch13)
     2. One Simple Solution : 
         1. Each entity in the network has a public/private encryption key pair. The public key along with the identity of the entity is stored in a central repository called a public file. If an entity A1 wishes to send encrypted messages to entity A6, A1 retrieves the public key e6 of A6 from the public file, encrypts the message using this key, and sends the ciphertext to A6. Figure 1.17 depicts such a network. 
         2. Figure 1.17: Key management using public-key techniques. 
         3. Avantages
             1. No TTP 
             2. The  Public File could reside with any entity
             3. Only  n Public Keys need to be stored assuming the only  attack is by a passive adversary.
         4. Problem : Active adversary who alters the public file.
             1. Figure 1.18: An impersonation of A6 by an active adversary with public key e . 
             2. In the figure, the adversary alters the public file by replacing the public key e6 of entity A6 by the adversary’s public key e . Any message encrypted for A6 using the public key from the public file can be decrypted by only the adversary. Having decrypted and read the message, the adversary can now encrypt it using the public key of A6 and forward the ciphertext to A6. A1 however believes that only A6 can decrypt the ciphertext c. 
         5. Solution : TTP
     3. TTP (functionally trusted) = Solution to One Simple Solution 
         1. the entities may use a TTP to certify the public key of each entity. The TTP has a private signing algorithm ST and a verification algorithm VT (see §1.6) assumed to be known by all entities. The TTP carefully verifies the identity of each entity, and signs a message consisting of an identifier and the entity’s authentic public key. This is a simple example of a certificate, binding the identity of an entity to its public key (see §1.11.3). Figure 1.19 illustrates the network under these conditions. A1 uses the public key of A6 only if the certificate signature verifies successfully. 
         2. Figure 1.19: Authentication of public keys by a TTP. ∥ denotes concatenation. 		
         3. Advantages
             1. prevents an active adversary from impersonation 
             2. TTP cannot monitor communications
             3. Entities need trust the TTP only to bind identities to public keys properly.
             4. Per-communication interaction with the public file can be eliminated if entities store certificates locally. 
         4. Problems 
             1. If the signing key of the TTP is compromised, all communications become insecure
             2. All trust is placed with one entity, the TTP
### 11. TTP
 1. unconditionally trusted TTP : if trusted on all matters.
     1. Example: it may have access to the secret and private keys of  users.
 2. functionally trusted TTP : if the entity is assumed to be honest and fair but it does not have access to the secret of or private keys
 3. Public Key Certificate 
     1. The distribution of public keys is generally easier than that of symmetric keys, since secrecy is not required. However, the integrity (authenticity) of public keys is critical (recall §1.8.2). 
     2. = data part + signature part
     3. data part = consists of the name of an entity, the public key corresponding to that entity, possibly additional relevant information (e.g., the entity’s street or network address, a validity period for the public key, and various other attributes) 
     4. signature part = the signature of a TTP over the data part
     5. Process :
         1. In order for an entity B to verify the authenticity of the public key of an entity A, B must have an authentic copy of the public signature verification function of the TTP. For simplicity, assume that the authenticity of this verification function is provided to B by non- cryptographic means, for example by B obtaining it from the TTP in person. B can then carry out the following steps
             1. Acquire the public-key certificate of A over some unsecured channel, either from a central database of certificates, from A directly, or otherwise.
             2. Use the TTP’s verification function to verify the TTP’s signature on A’s certificate.
             3. If this signature verifies correctly, accept the public key in the certificate as A’s authentic public key; otherwise, assume the public key is invalid.	
 4. Before creating a public-key certificate for A, the TTP must take appropriate measures to verify the identity of A and the fact that the public key to be certificated actually belongs to A. One method is to require that A appear before the TTP with a conventional passport as proof of identity, and obtain A’s public key from A in person along with evidence that A knows the corresponding private key. Once the TTP creates a certificate for a party, the trust that all other entities have in the authenticity of the TTP’s public key can be used transitively to gain trust in the authenticity of that party’s public key, through acquisition and verification of the certificate. 
### 12. Suite B
 1. AES
 2. Secure Hash Algorithm
 3. Elliptic Curve Cryptography		
     1. ED25519 **Edwards-curve Digital Signature Algorithm** (**EdDSA**) is a [digital signature](https://en.wikipedia.org/wiki/Digital_signature) scheme using a variant of [Schnorr signature](https://en.wikipedia.org/wiki/Schnorr_signature) based on [Twisted Edwards curves](https://en.wikipedia.org/wiki/Twisted_Edwards_curve) [100].
     2. Curve25519
         1.   is an [elliptic curve](https://en.wikipedia.org/wiki/Elliptic_curve_cryptography) offering 128 bits of security and designed for use with the [elliptic curve Diffie–Hellman](https://en.wikipedia.org/wiki/Elliptic_curve_Diffie%E2%80%93Hellman) (ECDH) key agreement scheme. It is one of the fastest ECC curves and is not covered by any known patents [101]<sup><a href="https://en.wikipedia.org/wiki/Curve25519#cite_note-:1-1">]</a></sup> 
         2. The curve is [birationally equivalent](https://en.wikipedia.org/wiki/Birational_geometry) to a [twisted Edwards curve](https://en.wikipedia.org/wiki/Twisted_Edwards_curve) used in [Ed25519[7][8]](https://en.wikipedia.org/wiki/Ed25519) signature scheme.<sup><a href="https://en.wikipedia.org/wiki/Curve25519#cite_note-9">[9]</a></sup>	
### 13. Communication Between Two Different Blockchains
반대편 블록체인의 validator들의 공개키를  가지고 있어야 한다. 왜냐하면 Relayer가 메세지랑 Proof를 보내는데, Proof안에  그 메세지가 담겨있었던 블록에 있던 정보를 보내주는데, 특히 거기안에  그 블록에 옳다고 투표한(최소 2f+1개) validator들의 투표가 들어있다. 그 투표가 validator들의 private key라고 생각하면 된다. 그럼 내게는 Verifier가 상대편 Relayer가 보낸 메세지랑 그 투표들을 보고 투표들에다가 내가 가지고 있는 그 투표들을 싸인한 validator들의 public key를 가지고 그 투표들을 체크한다. 맞으면, 믿는다. 그럼 이말은 즉슨 계속해서 저쪽 블록체인의 validator들의 publickey를 최신본으로 가지고 있어야 한다는 소리인데, 그러려면 상대방 블록체인에서 생기는 새로운 블록을 계속 전달받아야 한다. 왜냐하면 그 블록안에 그쪽 validator들의 hash값(Rep hash)이 적혀있기 때문이다. 내가 가지고 있는 publickey가 맞는지도 확인해야 하기 때문이다. so 내가 가지고 있는 publicKey에 해쉬를 해서 그쪽 가장 최신블록의 Rep hash랑 값이 같은지 확인해서 같으면 내 퍼블릭 키를 믿는다. 근데 문제는 전달되온 가장 최근 그쪽 블록이 진짜인지도 확인해야 한다는 거다. 그러려면 그쪽의 모든 블록체인을 다 받아야 한다. 그래야 가장 최근 블록이 맞는 블록인지 확인하기 때문이다. 여기서 모든 문제가 생긴다. 그쪽의 모든 블록을 다 가지고 있어야 한다는 거다. 당연히 새로생기는 블록도 실시간으로 받아와야한다. gg. 이 짓을 안하려면 TTP가 퍼블릭키를 전달해줘야 하는데 문제를 풀려다 문제를 받아들인 셈이 되는 것. 

### Reference


    [Alfred J. Menezes](http://cacr.uwaterloo.ca/hac/authors/ajm.html), [Paul C. van Oorschot](http://cacr.uwaterloo.ca/hac/authors/pvo.html) and [Scott A. Vanstone](http://cacr.uwaterloo.ca/hac/authors/sav.html), “[Handbook of Applied Cryptography](http://cacr.uwaterloo.ca/hac/)”, 1996


[100] Josefsson, S.; Liusvaara, I. (January 2017). _[Edwards-Curve Digital Signature Algorithm (EdDSA)](https://tools.ietf.org/html/rfc8032)_. [Internet Engineering Task Force](https://en.wikipedia.org/wiki/Internet_Engineering_Task_Force). [doi](https://en.wikipedia.org/wiki/Digital_object_identifier):[10.17487/RFC8032](https://doi.org/10.17487%2FRFC8032). [ISSN](https://en.wikipedia.org/wiki/International_Standard_Serial_Number) [2070-1721](https://www.worldcat.org/issn/2070-1721). RFC 8032. Retrieved 2017-07-31.


    [101]  Bernstein. ["Irrelevant patents on elliptic-curve cryptography"](https://cr.yp.to/ecdh/patents.html). _cr.yp.to_. Retrieved 2016-02-08.



*   [7] Daniel J. Bernstein, Niels Duif, Tanja Lange, Peter Schwabe, Bo-Yin Yang (2017-01-22). ["Ed25519: high-speed high-security signatures"](http://ed25519.cr.yp.to/). Retrieved 2019-11-09.
*   [8][^](https://en.wikipedia.org/wiki/Curve25519#cite_ref-8) Daniel J. Bernstein, Niels Duif, Tanja Lange, Peter Schwabe, Bo-Yin Yang (2011-09-26). ["High-speed high-security signatures"](http://ed25519.cr.yp.to/ed25519-20110926.pdf)(PDF). Retrieved 2019-11-09.
*   [9][^](https://en.wikipedia.org/wiki/Curve25519#cite_ref-9) [Bernstein, Daniel J.](https://en.wikipedia.org/wiki/Daniel_J._Bernstein); Lange, Tanja (2007). Kurosawa, Kaoru (ed.). [Faster addition and doubling on elliptic curves](https://eprint.iacr.org/2007/286). Advances in cryptology—ASIACRYPT. Lecture Notes in Computer Science. 4833. Berlin: Springer. pp. 29–50. [doi](https://en.wikipedia.org/wiki/Digital_object_identifier):[10.1007/978-3-540-76900-2_3](https://doi.org/10.1007%2F978-3-540-76900-2_3). [ISBN](https://en.wikipedia.org/wiki/International_Standard_Book_Number) [978-3-540-76899-9](https://en.wikipedia.org/wiki/Special:BookSources/978-3-540-76899-9). [MR](https://en.wikipedia.org/wiki/Mathematical_Reviews) [2565722](https://www.ams.org/mathscinet-getitem?mr=2565722).

<!-- Docs to Markdown version 1.0β17 -->
