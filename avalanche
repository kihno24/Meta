# Meta
metacraft
// SPDX-License-Identifier: MIT
pragma solidity >=0.6.12 <0.9.0;

contract Payment {
    uint public balance;
    uint public constant MAX_UINT = 2 ** 256 - 1;

    function deposit(uint _amount) public {
        // Use require to ensure that the deposit doesn't cause overflow
        uint oldBalance = balance;
        uint newBalance = balance + _amount;
        require(newBalance >= oldBalance, "Overflow");

        balance = newBalance;

        // Use assert to ensure that the balance is correctly updated
        assert(balance >= oldBalance);
    }

    function withdraw(uint _amount) public {
        // Ensure that the withdrawal doesn't cause underflow
        require(balance >= _amount, "Insufficient balance");
        
        // Safe subtraction to prevent underflow
        balance -= _amount;

        // Assert to ensure that the balance is correctly updated
        assert(balance <= MAX_UINT);

        // Add a revert statement if the withdrawal amount exceeds the contract's balance
        if (balance < _amount) {
            revert("The amount withdrawal exceeds to the balance");
        }
    }
}
