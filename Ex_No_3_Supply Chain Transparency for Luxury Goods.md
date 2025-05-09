### Ex_No_3_Supply Chain Transparency for Luxury Good

**Name : Tharun Sridhar**

**Reg No : 212223230230**

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
![image](https://github.com/user-attachments/assets/bca0d9e6-737d-4fc4-9450-a981da1f688f)


Ownership is transferred at every checkpoint.
![image](https://github.com/user-attachments/assets/424066f6-0b0a-4477-a416-fd1f45ac65e0)


Buyers can check the authenticity before purchasing.
![image](https://github.com/user-attachments/assets/00b0f724-1e0b-4690-8dad-2cfdc0f05e08)


# High-Level Overview:
Helps prevent counterfeit luxury goods.


Teaches real-world supply chain use cases.

# RESULT : 
Thus, we successfully developed a smart contract to track and verify the supply chain of luxury goods ensuring secure ownership transfer and product authenticity.
