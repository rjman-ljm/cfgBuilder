# cfgBuilder

## Config Builder

This is a simple CLI tool to help automate deployment of new relayers.

An input JSON config looks like this:

```json
{
    "relayerThreshold": "3",
    "ethchains": [
      {
        "name": "bsc_bnb",
        "chainId": "2",
        "endpoint": [
          "https://data-seed-prebsc-1-s3.binance.org:8545",
          "http://localhost:8545"
        ],
        "bridge": "0xeEc45984F86f35AF9F6489fd30a7f0aa655c08dB",
        "erc20Handler": "0x04c20C38e015e52685ba7DC34E839960a23C03CC",
        "internalAccount": "0x3DC0Ded73d906F64f466ef543E2f146b9Ae31454",
        "asset": "0x0F898bD1E62d72CA8C282AfE2E22aa0815fFC544",
        "http": "true",
        "networkId": "97",
        "relayers": [
          "0x3DC0Ded73d906F64f466ef543E2f146b9Ae31454",
          "0xBA6e8123fc49413CF11C23a3A90e73864d389ced",
          "0x8114B66d176B2BebB84729385709445166D7A463",
          "0xb742b10d22f30eEA9A7e338e79f0DB5D334E1197",
          "0x5B6D51affc88595aBc65d5c133C231cAFD69aA9E"
        ]
      },
      {
        "name": "kovan_eth",
        "chainId": "3",
        "endpoint": [
          "https://kovan.poa.network",
          "http://localhost:8546"
        ],
        "bridge": "0xf695b50c9C64e63b45A506909269D7B28B3a14Dc",
        "erc20Handler": "0x5c44C427D1DEEe2E9955c850c7a98014c4E557b4",
        "internalAccount": "0x3DC0Ded73d906F64f466ef543E2f146b9Ae31454",
        "asset": "0xcDb4d48Fc2646EdD51992e6e80792f1FFDf0A6c6",
        "http": "true",
        "networkId": "42",
        "relayers": [
          "0x3DC0Ded73d906F64f466ef543E2f146b9Ae31454",
          "0xBA6e8123fc49413CF11C23a3A90e73864d389ced",
          "0x8114B66d176B2BebB84729385709445166D7A463",
          "0xb742b10d22f30eEA9A7e338e79f0DB5D334E1197",
          "0x5B6D51affc88595aBc65d5c133C231cAFD69aA9E"
        ]
      },
      {
        "name": "heco_ht",
        "chainId": "4",
        "endpoint": [
          "https://http-testnet.hecochain.com",
          "http://localhost:8547"
        ],
        "bridge": "0x39b7FBbC38e4963A5cBCAd8d4A8ACbA21391CC55",
        "erc20Handler": "0xf0723e55127406FcAA17C6B2E5d2e68459cF40a6",
        "internalAccount": "0x3DC0Ded73d906F64f466ef543E2f146b9Ae31454",
        "asset": "0x89226933DF521856C64425206187a50D7F78f140",
        "http": "true",
        "networkId": "256",
        "relayers": [
          "0x3DC0Ded73d906F64f466ef543E2f146b9Ae31454",
          "0xBA6e8123fc49413CF11C23a3A90e73864d389ced",
          "0x8114B66d176B2BebB84729385709445166D7A463",
          "0xb742b10d22f30eEA9A7e338e79f0DB5D334E1197",
          "0x5B6D51affc88595aBc65d5c133C231cAFD69aA9E"
        ]
      }
    ],
    "subChains": [
      {
        "name":       "sherpax_asset_xasset",
        "chainId":    "101",
        "endpoint":   [
          "ws://localhost:9944"
        ],
        "relayers": [
          "5CHwt8bFyDLC3MyzPQugmmxZTGjShBW2kFMWiC2kSL5TuJxd",
          "5DtTcR48x8yWkSNwn6G1hjVnY61kCVT2SaGfKfU7WAHRvLKq",
          "5FNTYUQwxjrVE5zRRH1hKh6fZ72AosHB7ThVnNnq9Bv9BFjm",
          "5FnCTkAtgLinh6apZJwTX7n72H1A37MHE6xAXChZDbtUWMSg",
          "5HHGiHzTrdbAUFihSC1pgCER41qdrQSxiEBvDsJ2titfAof2"
        ]
      },
      {
        "name":       "kusama_kusama",
        "chainId":    "201",
        "endpoint":   [
          "ws://localhost:9945"
        ],
        "multiSigAddress": "FYzLbRnPh7ZRkgDf23oziUzFfpokQzwRqpM9Xc6gMt2i21o",
        "totalRelayer": "5",
        "multiSigThreshold": "3",
        "maxWeight": "22698000000",
        "resourceId": "0x0000000000000000000000000000000000000000000000000000000000000007",
        "relayers": [
          "5CHwt8bFyDLC3MyzPQugmmxZTGjShBW2kFMWiC2kSL5TuJxd",
          "5DtTcR48x8yWkSNwn6G1hjVnY61kCVT2SaGfKfU7WAHRvLKq",
          "5FNTYUQwxjrVE5zRRH1hKh6fZ72AosHB7ThVnNnq9Bv9BFjm",
          "5FnCTkAtgLinh6apZJwTX7n72H1A37MHE6xAXChZDbtUWMSg",
          "5HHGiHzTrdbAUFihSC1pgCER41qdrQSxiEBvDsJ2titfAof2"
        ]
      }
    ]
  }
```

This example would result in five configs, one for each relayer, with each containing the three provided chains.

## Build/Install

```shell
make build
```

OR

```shell
make install
```

## Usage

```shell
./build/cfgBuilder <input-file> <output-path>
# Example
mkdir ./relayers && ./build/cfgBuilder Example_HQSWY.json ./relayers
ls ./relayers
```

OR

```shell
cfgBuilder <input-file> <output-path>
```

## Clean

```shell
make clean
```
