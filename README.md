# Module-Eight-Journal

Questions and Answers:

* Briefly summarize your client, Artemis Financial, and its software requirements. Who was the client? What issue did the company want you to address?
    The Client was Artemis Financial, a financial services provider that manages sensitive client data, including personal and financial information.
    The main issue was the applications reliance on insecure and potentially non-compliant data handling, especially regarding data in transit and key management. the company required an indsutry standard, robust cryptographic solution to ensure the confidentiality and integrity of the client data during transfer and processing, as well as the refactoring of vulernable legacy SSL server code. I needed to implement and deploy a high assurance hybrid cryptographic system.
  
* What did you do well when you found your client’s software security vulnerabilities? Why is it important to code securely? What value does software security add to a company’s overall well-being?
    I excelled at designing and implementing a defense in depth cryptographic system. I went beyond simple encryption to a multi layered hybrid approach using AES-256 for bulk data encryption, RSA-2048 for secure key exchange, and SHA-256 for integrity verification. This strategic choice adheres to modern security standards and protects against multiple failure points. I also ensured that practices like using random intilization vectors for AES were applied to prevent repeated ciphertext, an important detail often overlooked in simple implementations.
  
* Which part of the vulnerability assessment was challenging or helpful to you?
    The hardest part was making sure the refactoring of existing Java SSL server code did not introduce subtle cryptographic misconfigurations. When working with SSL/TLS and complex ciphers like RSA and AES, a minor error in key handling, certificate validation, or IV generation can silently destroy the security of the channel. It took rigorous manual inspection of the refactored code to confirm the security logic was sound before deployment.
  
* How did you increase layers of security? In the future, what would you use to assess vulnerabilities and decide which mitigation techniques to use?
    I built security using defense in depth. This means a layered approach that allows layers to hold when others fall. Firstly I protected the data itself by using AES-256 encryption. Then I secured the secret key exchange using RSA-2048. Then I added SHA-256 checksum layer to create a unique fingerprint for the data, ensuring it wasnt changed during transfer. Other things were implemented as well like OWASP Dependency Check.
    
* How did you make certain the code and software application were functional and secure? After refactoring the code, how did you check to see whether you introduced new vulnerabilities?
    I first ran functional testing to confirm that the security changes still let the app process data correctly without crashing. Then, i ran the OWASP Dependency Check to verify that the dependency updates didnt bring in any new known vulnerabilities. After that, I performed code review.
    
* What resources, tools, or coding practices did you use that might be helpful in future assignments or tasks?
    The most important practices I used were the hybrid crypto model of combining AES and RSA for speed and secure key sharing. Also OWASP Dependency Check was crucial.

* Employers sometimes ask for examples of work that you have successfully completed to show your skills, knowledge, and experience. What might you show future employers from this assignment?
    I would show a future employer two main things to show my expertise. I would first should the Hybrid Cryptographic Model as previously mentioned as this would prove I can design and explain security solutions in a sturctured way. I would also present the before and after snapshots of the before and afters. Then I would show the OWASP Dependency Check report to prove my practicality in fixing critical security issues and following a secure development pipeline.
