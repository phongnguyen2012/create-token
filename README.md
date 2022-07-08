
## Create-token
  Fungible Token 
  Example implementation of a Fungible Token contract which uses near-contract-standards and simulation tests. This is a contract-only example.
<sup>
    #### 1. Prerequisites Install Rust

    Building ./build.sh

    #### 2. Using this contract : Deloy contract

    near deploy --wasmFile out/create-token.wasm --accountId $ID

    Fungiable Token contract should be initialized before usage. You can read more about metadata at 'nomicon.io'. Modify the parameters and create a         token:

    near call $ID new '{"owner_id": "'$ID'", "total_supply": "1000000000000000", "metadata": { "spec": "ft-1.0.0", "name": "Example Token Name",             "symbol":

      "EXLT", "decimals": 8 }}' --accountId $ID


    Get metadata: near view $ID ft_metadata

    #### 3. Transfer Example

    near create-account teo.$ID --masterAccount $ID --initialBalance 5

    Add storage deposit for teo's account:

    near call $ID storage_deposit '' --accountId teo.$ID --amount 0.2

    Check balance of teo's account

    near view $ID ft_balance_of '{"account_id": "'teo.$ID'"}'

    Transfer tokens to teo from the contract that minted these fungible tokens, exactly 1 yoctoNEAR of deposit should be attached:

    near call $ID ft_transfer '{"receiver_id": "'teo.$ID'", "amount": "1"}' --accountId $ID --amount 0.000000000000000000000001

    #### 4. Test

    cargo test
  
</sup>
