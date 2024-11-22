// SPDX-License-Identifier: MIT
// Specifying the software license under which the code is distributed.
// Ensuing the compliance with open-source lisensing norms.

pragma solidity ^0.8.0;
// Specifies the Solidity compiler version
// Prevents use of older or potentially insecure versions of the Solidity compiler

// Defining a smart contract of any variable name
contract Logging_the_message 
{
    event MessageLogged(address indexed user, string message);
    // Event allows logging off data on the blockchain. Listened to by off-chain applications.
    // user: The address of the user logging the message and message: The message being logged.
    // Indexed: Enables filtering of the event log by the user address.

    mapping(address => bool) private hasLogged;
    // Data structure for key-value pairs.
    // Maps each address to a bool indicating whether the user has logged a message.
    // Private: Limits the visibility of the mapping to the contract itself, meaning external contracts or users cannot access it directly.

    function storing_message(string calldata content) external 
    // A block of code that performs a specific task.
    // calldata: A temporary, non-modifiable area where function arguments are stored.
    // External: The function can be called only from outside the contract (by users or other contracts).
    {
        require(bytes(content).length <= 100, "Message exceeds 100 characters.");
        // Require: Used to enforce conditions. If the condition fails, the transaction is reverted, and an error message is returned.
        // Ensures the input message is no longer than 100 characters.
        // bytes(content).length converts the string to a byte array to check its length.

        require(!hasLogged[msg.sender], "User has already logged a message.");
        // Ensures the user has not already logged a message.
        // msg.sender: A global variable representing the address of the caller.
        // hasLogged[msg.sender]: Checks the mapping to see if msg.sender has logged a message.

        emit MessageLogged(msg.sender, content);
        // Triggers the MessageLogged event, recording the user's address and message.
        // Emit: A keyword used to call events.

        hasLogged[msg.sender] = true;
        // Marks the user as having logged a message by updating the mapping.
        // This ensures the user cannot log another message due to the require statement above.
    }

    function message_is_logged_or_not() external view returns (bool)
    // Defining a function to check if a user has logged a message.
    // View: Indicates that the function reads data but does not modify the blockchain state.
    // Returns (bool) returns a boolean value.
    {
        return hasLogged[msg.sender];
        // Returns true if the user has logged a message, otherwise false.
    }
}  
