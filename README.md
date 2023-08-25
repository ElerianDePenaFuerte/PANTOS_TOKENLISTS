# @ElerianDePenaFuerte/PANTOS_TOKENLISTS (Uniswap Tokenlist Specification)

![version](https://img.shields.io/badge/version-1.0.0-blue)

This package includes a JSON schema for token lists according the UNISWAP specifications (https://github.com/Uniswap/token-lists).

The JSON schema represents the technical specification for a token list which can be used in a dApp interface, such as the Uniswap Interface.

## Content

The JSON schema includes all current PANDAS token of the PANTOS Multichain protocol (https://pantos.io/) including IPFS links to logos for
- Wrapped Pandas tokens
- Custom Pandas tokens created manually
- Custom Pandas tokens created using the PANDAS multichain token creator (https://creator.testnet.pantos.io/)

## What are token lists?

Uniswap Token Lists is a specification for lists of token metadata (e.g. address, decimals, ...) that can be used by any dApp interfaces that needs one or more lists of tokens.

Anyone can create and maintain a token list, as long as they follow the specification.

Specifically an instance of a token list is a [JSON](https://www.json.org/json-en.html) blob that contains a list of 
[ERC20](https://github.com/ethereum/eips/issues/20) token metadata for use in dApp user interfaces.
Token list JSON must validate against the [JSON schema](https://json-schema.org/) in order to be used in the Uniswap Interface.
Tokens on token lists, and token lists themselves, are tagged so that users can easily find tokens.

## JSON Schema $id

The JSON schema ID is [https://uniswap.org/tokenlist.schema.json](https://uniswap.org/tokenlist.schema.json)

## Validating token lists

This package does not include code for token list validation. You can easily do this by including a library such as 
[ajv](https://ajv.js.org/) to perform the validation against the JSON schema. The schema is exported from the package
for ease of use.

## Semantic versioning

Lists include a `version` field, which follows [semantic versioning](https://semver.org/).

List versions must follow the rules:

- Increment major version when tokens are removed
- Increment minor version when tokens are added
- Increment patch version when tokens already on the list have minor details changed (name, symbol, logo URL, decimals)

Changing a token address or chain ID is considered both a remove and an add, and should be a major version update.

Note that list versioning is used to improve the user experience, but not for security, i.e. list versions are not meant
to provide protection against malicious updates to a token list; i.e. the list semver is used as a lossy compression
of the diff of list updates. List updates may still be diffed in the client dApp.



