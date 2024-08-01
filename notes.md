# 4 Puppy Raffle

- first run `git checkout e30d199697bbc822b646d76533b66b7d529b8ef5`
- solidity version 0.7.6
- to run **slither** => `slither .`
- `aderyn .` to run aderyn, this will create report 
- To update Aderyn to the latest version, you can run the cyfrinup: `cyfrinup`
- use `Solidity Metics` to see graph and which function call which one
- `forge inspect PuppyRaffle methods` this will print methods with function selector or signature ?? 

- DoS attacks put simply are - the denial of functions of a protocol. They can arise from multiple sources, but the end result is always a transaction failing to execute.

- DoS: 
  - By unbounded loop, by reaching the limit of block gas
  - An external call Failing and preventing the transaction from going to 

- DOS by external call ->
  - Force an External call to fail:
    - Sending Ether to a contract that doesnt accept it
    - calling a function that doesnt exist on contract and that contract does not have `fallback function`
    - The External call execution runs out of gas
    - Third-Party contract is simply malicious and reverts on purpose
  - By For loops (ask this questions):
    - Is the iterable entity bounded by size?
    - Can a user append arbitrary items to the list?
    - How much does it cost the user to do so?

- Reentrancy:
  - can be solve by CEI Method or [OpenZeppelin's ReentrancyGuard](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/ReentrancyGuard.sol)

- Methods to follow:
  - CEI = Checks Effects Interactions(with external contract or anything)
  - Checks - require statements, conditions
  - Effects - this is where you update the state of the contract
  - Interactions - any interaction with external contracts/addresses come last
  
  ```javascript
  function CEI() public {
    // checks

    // Effects

    // Interactions

  }
  // example :- simply doing this we can avoid reentracy attack
  function withdrawBalance() public {
    // Checks
        /*None*/
    //Effects
    uint256 balance = userBalance[msg.sender];
    userBalance[msg.sender] = 0;
    //Interactions
    (bool success,) = msg.sender.call{value: balance}("");
    if (!success) {
        revert();
    }
  }
  ```