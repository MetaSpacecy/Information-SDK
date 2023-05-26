# Metaspacecy Information SDK

[![NPM Package Version][npm-image-version]][npm-url]
[![NPM Package Downloads][npm-image-downloads]][npm-url]
[![https://badges.frapsoft.com/os/mit/mit.svg?v=102](https://badges.frapsoft.com/os/mit/mit.svg?v=102)](https://opensource.org/licenses/MIT)

</br>
<div align="center">
  <img src="./assets/images/icon.png" alt="MetaSpacecy logo"/>
</div>
</br>

The Metaspacecy Information SDK is a powerful tool that lets you create an information market in the form of prediction or forecast about the future events or outcomes. It can be applied in multiple aspects of life such as election, financial indicators, and especially in competitive games, tournaments.

## Installation

Use the package manager _[npm](https://nodejs.org/en/download/)_ to install package.

```bash
npm install @metaspacecy/information-sdk
```

Use the package manager _[yarn](https://yarnpkg.com/getting-started/install)_ to install package.

```bash
yarn install @metaspacecy/information-sdk
```

## Quickstart
Integrate InformationSDK in EVM ecosystem.

```bash
import { InformationSDK, Network } from "@metaspacecy/information-sdk/evm";
import { ethers } from "ethers";

const provider = new ethers.providers.Web3Provider(window.ethereum);

const informationSDK = new InformationSDK(provider, Network.bnbTestnet);
```

Integrate InformationSDK in Move ecosystem.

```bash
// import SDK
import InformationSDK from "@metaspacecy/information-sdk/move";

// signAndSubmitTransaction is function of wallet adapter
// ChainID of the network used by the user
// The third parameter takes an array of values that the user wants to return after using the signAndSubmitTransaction function
// expamle ["hash"] => result {hash: ...}
const informationSDK = new InformationSDK(signAndSubmitTransaction, chainID, ["hash"]);
```

## Developer Docs and Demo
To get insight Metaspacecy Information SDK please checkout [Information SDK][doc-url]

## Semantic versioning

This project follows [semver](https://semver.org/) as closely as possible.

## Release process

To release a new version of the SDK do the following.

1. Check that the commit you're deploying from (likely just the latest commit of `main`) is green ln CI. Go to GitHub and make sure there is a green tick, specifically for the `sdk-release` release CI step. This ensures that the all tests, formatters, and linters passed, including server / client compatibility tests (within that commit) and tests to ensure the API, API spec, and client were all generated and match up.
2. Bump the version in `package.json` according to [semver](https://semver.org/).
3. Add an entry in the CHANGELOG for the version. We adhere to [Keep a Changelog](https://keepachangelog.com/en/1.0.0/). Generally this means changing the "Unreleased" section to a version and then making a new "Unreleased" section.
4. Once you're confident everything is correct, submit your PR. The CI will ensure that you have followed all the previous steps, specifically ensuring that the API, API spec, and SDK client are all compatible, that you've updated the changelog, that the tests pass, etc.
5. Land the PR into the main branch. Make sure this commit comes up green in CI too.
6. Check out the latest commit on main.
7. Get the auth token from our password manager. Search for "npmjs". It should look like similar to this: `npm_cccaCVg0bWaaR741D5Gdsd12T4JpQre444aaaa`.
8. Run `pnpm publish --dry-run`. From here, make some sanity checks:
    a. Look closely at the output of the command. {ay close attention to what is packaged. Make sure we're not including some files that were included accidentally. For example `.aptos`. Add those to .npmignore if needed.
    b. Compare the summary with the public npm package summary on npmjs. The number of files and sizes should not vary too much.
9. Run `NODE_AUTH_TOKEN=<token> pnpm checked-publish`
10. Double check that the release worked by visitng npmjs: https://www.npmjs.com/package/@metaspacecy/information-sdk


[examples]: https://github.com/MetaSpacecy/Information-SDK.git
[repo]: https://github.com/MetaSpacecy/Information-SDK.git
[npm-image-version]: https://img.shields.io/npm/v/pnpm.svg
[npm-image-downloads]: https://img.shields.io/npm/dm/aptos.svg
[npm-url]: https://github.com/MetaSpacecy/Information-SDK
[doc-url]: https://docs.metaspacecy.com/doc/metaspacecy-sdk/information-sdk
