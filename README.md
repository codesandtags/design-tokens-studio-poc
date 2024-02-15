# Design Tokens Studio PoC

This PoC is because I was inspired by my friend Jyrmid, so I wanted to create the PoC by myself and also share a functional approach with the world.

## Motivation

Nowadays the [Design Tokens](https://thedesignsystem.guide/design-tokens) are very common within the UI/UX design and Frontend Community to have a standard way for naming components and UI/UX elements. However, keeping a unique source of truth is difficult and we do not want to make difficult the cognitive load for UI/UX designer nor developers.

## Goal

Define a simple approach to sync the `Design Tokens` created with Tokens Studio in **Figma**. These tokens can be used by developers and other designers.

## Key Considerations

- Designer should not download any tool / local development environment.
- Tokens should be centralized to keep a unique source of information shared between designers and developers
- The [schema used by Tokens Studio](https://schemas.tokens.studio/latest/tokens-schema.json) should be the same used by the REST API.

## Proposal

### Using JSON Server to store the tokens

- Using `json-server` to create a simple REST API to store the tokens in a JSON file.
- Using a [Generic Versioned Storage Sync](https://docs.tokens.studio/sync/generic-storage) to sync the values from Figma to the REST API.
- Tokens should be stored in a JSON file when `Apply to selection` button is clicked in Figma.

### Using Figma Tokens Generic Storage example repository

- Using the [Figma Tokens Generic Storage](https://github.com/SorsOps/figma-tokens-generic-storage-example/tree/main) repository to create a simple example to sync the tokens from Figma to the REST API.

## Results

### Using JSON Server to store the tokens

#### Pros

- Using this options is quite easy to create a simple REST API to store the tokens in a JSON file.

#### Cons

- One drawback is that if the path is not defined from the begining, the `json-server` will not be able to store the tokens in the JSON file.
- There are some errors when trying to sync the tokens from Figma to the REST API.
- Data is easily lost if the server is restarted.
- Data is stored with spaces which it takes more space in the JSON file.

### Using Figma Tokens Generic Storage example repository

#### Pros

- This approach uses a db in SQLite to store the tokens.
- Data is persisted if the server is restarted.

#### Cons

- The `figma-tokens-generic-storage-example` repository is not updated and it requires some changes with the latest version of the `tokens-schema` and dependencies.

## Conclusion

The PoC was successful, however, the `json-server` approach is not the best option to store the tokens. The `figma-tokens-generic-storage-example` repository is a better option to store the tokens, but it requires some changes to work with the latest version of the `tokens-schema` and dependencies.

## Next Steps

- [ ] Create a Docker Image with the changes to expose the REST API to store the tokens.
- [ ] Create a deployment pipeline to deploy the REST API to store the tokens in a - cloud provider.
- [ ] Document the steps to sync the tokens from Figma to the REST API.
- [ ] Write a proper article to share this approach with the world.

## References

- https://tokens.studio/
- https://configurator.tokens.studio/
- https://medium.com/@ian.lawton/a-simple-design-token-storage-server-for-figma-token-studio-3a9ba74aefb5
