# Mappings

Maps are a key-value data structure used to store data within a smart contract. In Cairo they are implemented using the `Map` type. It's important to note that the `Map` type can only be used inside the `Storage` struct of a contract and that it can't be used elsewhere.

Here we demonstrate how to use the `Map` type within a Cairo contract, to map between a key of type `ContractAddress` and value of type `felt252`. The key-value types are specified within angular brackets <>. We write to the map by calling the `write()` method, passing in both the key and value. Similarly, we can read the value associated with a given key by calling the `read()` method and passing in the relevant key.

Some additional notes:

- More complex key-value mappings are possible, for example we could use `Map::<(ContractAddress, ContractAddress), felt252>` to create an allowance on an ERC20 token contract.

- In mappings, the address of the value at key $k_1,...,k_n$ is $\text{h}(...\text{h}(\text{h}(\text{sn\_keccak}(name),k_1),k_2),...,k_n)$ where $\text{h}$ is the Pedersen hash and the final value is taken $(\bmod {2^{251}} - 256~)$. You can learn more about the contract storage layout in the [Starknet Documentation](https://docs.starknet.io/documentation/architecture_and_concepts/Smart_Contracts/contract-storage/#storage_variables).

```cairo
// [!include ~/listings/getting-started/mappings/src/mappings.cairo:contract]
```
