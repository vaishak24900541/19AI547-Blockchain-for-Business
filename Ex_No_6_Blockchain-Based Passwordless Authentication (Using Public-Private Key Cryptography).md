# Experiment 6: Blockchain-Based Passwordless Authentication (Using Public-Private Key Cryptography)
# Aim:
To implement a secure passwordless authentication system using public-private key cryptography on Ethereum. This prevents phishing and password leaks.

# Algorithm:
Step 1: User Registration
A user registers with their Ethereum public key (instead of a password).


Step 2: Login Process
When logging in, the user signs a random challenge message using their private key.


The smart contract verifies the signature using the user’s public key.



# Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract PasswordlessAuth {
    mapping(address => bool) public registeredUsers;

    event UserRegistered(address user);
    event UserAuthenticated(address user);

    function registerUser() public {
        require(!registeredUsers[msg.sender], "Already registered");
        registeredUsers[msg.sender] = true;
        emit UserRegistered(msg.sender);
    }

    function authenticate(bytes32 hash, uint8 v, bytes32 r, bytes32 s) public view returns (bool) {
        require(registeredUsers[msg.sender], "User not registered");
        address signer = ecrecover(hash, v, r, s);
        return signer == msg.sender;
    }
}
```

# Expected Output:
Users can register without a password.


Users sign a challenge with their private key for authentication.


The smart contract verifies signatures to confirm identity.

![6(1)](https://github.com/user-attachments/assets/dd620863-0101-4371-a0e0-2aadf8ee4e37)

![6(2)](https://github.com/user-attachments/assets/375dc3ba-993d-44f4-8c01-d0fd4082089c)

![6(3)](https://github.com/user-attachments/assets/dfbf1fd2-65e8-42f7-b3bb-838375b9bdc9)

![6(4)](https://github.com/user-attachments/assets/29c4893f-66d1-4a4a-85f3-15a9e264e0e5)

![6(5)](https://github.com/user-attachments/assets/d5e94ac4-35e9-4ddd-b344-194a4f915140)

# High-Level Overview:
Eliminates password hacks & phishing attacks.


Uses Ethereum's built-in cryptographic functions.


Inspired by Web3 login solutions like MetaMask authentication.

# RESULT: 
