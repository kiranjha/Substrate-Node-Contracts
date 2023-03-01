# Substrate-Node-Contracts
## After successfully installation of substrate-contract-node.
- Open Ubuntu terminal - 
1.  Start the contracts node in local development mode by running the following command:<br>
    **substrate-contracts-node --log info,runtime::contracts=debug 2>&1**<br>
    You should see output in the terminal similar to the following:<br>
    <img src="https://user-images.githubusercontent.com/55039934/222129868-80372325-e79e-416f-bdd5-ed1aaeeed158.png" width="500">

- Open another tab of Ubuntu terminal - 
2.  Test your contract by running the following command:<br>
    **cargo test** <br>
3.  Verify that you can build the WebAssembly for the contract by running the following command:<br>
    **cargo contract build** <br>
4.  Instantiate the contract using the new() constructor.<br>
    **cargo contract instantiate --constructor new --args 1_000_000 --suri //Alice --salt $(date +%s)**<br>
    <img src="https://user-images.githubusercontent.com/55039934/222131613-9a9a38f8-5260-4e95-9398-1cc0c85b9f6a.png" width="500"><br>
5.  Verify the total_supply by calling the total_supply() message. Don't forget to add the --dry-run flag since we only want to read from the chain state.<br>
    **cargo contract call --contract 5EmxJEdsmjaENQByQToSG4XP5bWXApDeixJZUT6BnYNTB5AR \
    --message total_supply --suri //Alice --dry-run** <br>
    <img src = "https://user-images.githubusercontent.com/55039934/222132404-f9236fb1-6461-4d18-b2dc-a525e53af8c6.png" width="600" height = "60"><br>
6.  Verify the amount of tokens Alice, the initial holder of all the tokens, has using balance_of().<br>
    **cargo contract call --contract 5EmxJEdsmjaENQByQToSG4XP5bWXApDeixJZUT6BnYNTB5AR \
    --message balance_of --args 5GrwvaEF5zXb26Fz9rcQpDWS57CtERHpNehXCPcNoHGKutQY \
    --suri //Alice --dry-run**<br>
    <img src = "https://user-images.githubusercontent.com/55039934/222133152-1cdaed60-53ac-4cb2-91da-3691f6e41724.png" width="600" height = "60"><br>
