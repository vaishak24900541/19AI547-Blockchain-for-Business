# Aim:
To develop a smart contract that tracks the supply chain of luxury goods, ensuring authenticity.
# Algorithm:
The manufacturer records product creation details on-chain.


The product moves through different supply chain checkpoints.


The ownership of the product can be transferred securely.


Buyers can verify the product’s authenticity.


# Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract LuxurySupplyChain {
    struct Product {
        string name;
        address currentOwner;
        bool verified;
    }

    mapping(uint256 => Product) public products;

    event ProductRegistered(uint256 productId, string name);
    event OwnershipTransferred(uint256 productId, address newOwner);

    function registerProduct(uint256 productId, string memory name) public {
        require(products[productId].currentOwner == address(0), "Product already registered");
        products[productId] = Product(name, msg.sender, true);
        emit ProductRegistered(productId, name);
    }

    function transferOwnership(uint256 productId, address newOwner) public {
        require(products[productId].currentOwner == msg.sender, "Not the owner");
        products[productId].currentOwner = newOwner;
        emit OwnershipTransferred(productId, newOwner);
    }

    function verifyProduct(uint256 productId) public view returns (string memory, address, bool) {
        Product memory p = products[productId];
        return (p.name, p.currentOwner, p.verified);
    }
}
```
# Expected Output:
A luxury good (e.g., a Rolex watch) is registered on-chain.


Ownership is transferred at every checkpoint.


Buyers can check the authenticity before purchasing.


# High-Level Overview:
Helps prevent counterfeit luxury goods.


Teaches real-world supply chain use cases.

# Output :
![exp3](https://github.com/user-attachments/assets/1c784aeb-b6ce-481e-b55d-d1e96ac519e1)

![exp(1)](https://github.com/user-attachments/assets/9378661c-4785-4c18-b726-32d2534d9c58)

![exp(2)](https://github.com/user-attachments/assets/e33908ac-1bbc-472a-9e1b-c1f3d6f3f2dd)

![exp(3)](https://github.com/user-attachments/assets/151f0f7d-d6d9-4fcc-b50d-e1de1fb2a22c)

![exp(4)](https://github.com/user-attachments/assets/c879f76c-2495-4698-910e-74541de6bf00)



# RESULT : 
Thus, the program has been deployed and supplychain verified successfully
