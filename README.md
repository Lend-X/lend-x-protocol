# lend-x-protocol

## Architecture

The Lend-X Protocol provides a high degree of decoupling of Business Logic, Storage, and Access Control layers. Additional layers of abstraction are introduced to isolate specialized logic and storage which allows the protocol usage in a modular fashion in that non-core functionality can be easily removed or extended without impact to core functionality. This flexibility also provides a certain level of frictionless upgradeability to core contracts while preserving state and keeping redeployment gas costs to a minimum.

The Lend-X protocol is designed with considerable influence from the concepts used by the following projects and articles:
 
[OpenZeppelin & Aragon - Proxy Libraries in Solidity](https://blog.zeppelin.solutions/proxy-libraries-in-solidity-79fbe4b970fd)  
[Colony - Upgradeable Contracts](https://blog.colony.io/writing-upgradeable-contracts-in-solidity-6743f0eecc88)  
[CardStack - Upgradeable Contracts](https://medium.com/cardstack/upgradable-contracts-in-solidity-d5af87f0f913)  

## Contracts

### Resolver Layer

##### Resolver.sol
Versioning is handled through the resolver contract and changes are implemented by the multisig contract. 

### Access Control Layers

##### MultiSig.sol
The multisig contract is a temporary solution intended to allow for bug fixes and code changes in an expediated manner. At a point in the future when the community has determined the functionality to be stable, the multisig contract will be swapped out for a highly tested and proven DAO.

### Storage Layers

##### DebtStorage.sol
The primary storage for debt obligations. The Debt Storage contract is loosely defined data store with getters and setters for any data types without making assumptions about what the data represents. This means that as functionality changes, new debt orders can be stored with additional properties without the storage contract being changed.

##### TokenRegistry.sol
Specialized form of defined storage used for constraining the tokens that can be used within the protocol.

