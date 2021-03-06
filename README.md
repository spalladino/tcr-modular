# TCR-Modular EVM Package

#### *** DISCLAIMER: Current version contracts are not thoroughly tested or audited. Use at own risk ***

## About

This library aims to be a readable and modular library for registries and TCR's. Ideally developers can use these contracts to deploy their TCR or use these contracts as an extension onto their personalized registry contract.


## Setup
Install node modules:
```
$ npm install
```

Compile contracts:
```
$ npm run compile
```

Run tests:

```
$ npm run test
```

### Example Project

Example project using tcr-modular EVM package to deploy a TCR:
https://github.com/levelkdev/tcr-modular-example

## Contract Structure

### Registry Interface

`IRegistry.sol `

```
interface IRegistry {
  function add(bytes32 data) public;
  function remove(bytes32 data) public;
  function exists(bytes32 data) public view returns (bool item);
}
```

### Challenge Interface
`IChallengeFactory.sol`

```
interface IChallengeFactory {
  function create(address registry, address challenger, address applicant) returns (address challenge);
}
```

`IChallenge.sol`

```
interface IChallenge {
  // returns the address of the challenger
  function challenger() view returns (address);

  // returns true if the challenge has ended
  function close() public;

  // returns whether challenge has been officially closed
  function isClosed() public view returns (bool);

  // returns true if the challenge has passed
  // reverts if challenge has not been closed
  function passed() public view returns (bool);

  // @notice returns the amount of tokens the challenge must
  // obtain to carry out functionality
  function fundsRequired() public view returns (uint);

  // @dev returns amount to be rewarded to challenge winner
  function winnerReward() public view returns (uint);
}
```


## Code Review
* Notes on current state of this repository: https://docs.google.com/document/d/1vjaWW7izisc2QNlZEpti4BPh8yJTOGo3Wu9GNgaRI1A/
* Feel free to create an Issue with review, questions, or concerns.
