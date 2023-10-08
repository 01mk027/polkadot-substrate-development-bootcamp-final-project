# Introduction
This project is made for Polkadot Substrate Development Bootcamp which is held by RiseIn and Patika. (To prove my effort, I upload whole content to here).
# Tasks

Quoted from <a href="https://www.risein.com/bootcamp-details/polkadot-substrate-development-bootcamp/learner/submission/aoXAtGtG7eP9BSxkp">Rise In's webpage</a><br/>
```Share your Github repository for the Polkadot Rust & Substrate Bootcamp on the following four hands on projects:```

```1. Building a blockchain```<br/>
```2. Simulating a substrate network``` <br/>
```3. Adding trusted nodes to a network.``` <br/>
```8. Smart contracts  ``` <br/>
## Building a blockchain
I followed steps on <a href="https://docs.substrate.io/tutorials/build-a-blockchain/build-local-blockchain/">this website.</a> After compiling, I achieved to build my small blockchain. Screenshot for first launch is given below 
<img src="polkadot-substrate-readme-photos\after-launching-first-block.png" alt="alt text" width="320" height="180" style="margin-top: 20px; margin-bottom: 20px;">

And screenshot for the front-end template is given below.
<img src="polkadot-substrate-readme-photos\front-end-after-build-a-blockchain.png" alt="alt text" width="320" height="180" style="margin-top: 20px; margin-bottom: 20px;">

## Simulating a network

I followed steps on <a href="https://docs.substrate.io/tutorials/build-a-blockchain/simulate-network//">this website.</a>

In this section, we tried to simulate a block chain network. Also this part was easy, except some configurations for users. There are 2 virtual users which are named Alice and Bob. Screenshots for this part is listed below.

<img src="polkadot-substrate-readme-photos\simulate_network_alice.png" alt="alt text" width="320" height="180" style="margin-top: 20px; margin-bottom: 20px;">

<img src="polkadot-substrate-readme-photos\simulate_network_alice.png" alt="alt text" width="320" height="180" style="margin-top: 20px; margin-bottom: 20px;">

## Add trusted nodes
This was hardest task for this course, which I see. Again, to achieve this task I followed steps on <a href="https://docs.substrate.io/tutorials/build-a-blockchain/add-trusted-nodes/"> this tutorial</a>. Also <a href="https://youtu.be/d_SSgt_Ft5M?si=IGeg9v1J9veo7OuW">this</a> video helped me to achieve this task, and content for this task is almost completely based on relevant Youtube video.<br/>
<i>Note that, I didn't achieve this task by creating another ```sudo``` user for this task, second node didn't executed by second ```sudo``` user.</i><br/>

- ### Generating local keys
Given below, which are generated grandpa and aura keys for two nodes:
```
node01
(aura):
Secret phrase:       next gaze snap vault sleep rebuild duck panda genuine crane split slam
  Network ID:        substrate
  Secret seed:       0xa0db6f97984391781eac76b08dc8c3627f31064a66cc31ac45e20b6d892eb95a
  Public key (hex):  0x58af64a027767c61b040071921ad7c90298954dcee2a83be73062632e7c83b73
  Account ID:        0x58af64a027767c61b040071921ad7c90298954dcee2a83be73062632e7c83b73
  Public key (SS58): 5E4zB2NgpCTtqjvheWjPHzMkFjDvURShXSAMLyt6Xyqwa91S
  SS58 Address:      5E4zB2NgpCTtqjvheWjPHzMkFjDvURShXSAMLyt6Xyqwa91S
(grandpa):
Secret phrase:       next gaze snap vault sleep rebuild duck panda genuine crane split slam
  Network ID:        substrate
  Secret seed:       0xa0db6f97984391781eac76b08dc8c3627f31064a66cc31ac45e20b6d892eb95a
  Public key (hex):  0x90dbbe1b9d42c200f6f27bbe89398322b350d7ee1e545bb31a0d02fa591ab73c
  Account ID:        0x90dbbe1b9d42c200f6f27bbe89398322b350d7ee1e545bb31a0d02fa591ab73c
  Public key (SS58): 5FLe2gKmwcEWj5P1MQazuT7uaddBTx3FkboZmyQYWe1jYtC4
  SS58 Address:      5FLe2gKmwcEWj5P1MQazuT7uaddBTx3FkboZmyQYWe1jYtC4

node02
(aura):
Secret phrase:       silly usage bomb stamp cereal choice draft february shed jar pen change
  Network ID:        substrate
  Secret seed:       0x811402ebba3f6a0c1e37b4977a72da62f091f2538cc1352df0134b0f10fd3860
  Public key (hex):  0xdc54b0781fa9de9096d87f8269b594d83efef67f78d5845e4818abd322ef5076
  Account ID:        0xdc54b0781fa9de9096d87f8269b594d83efef67f78d5845e4818abd322ef5076
  Public key (SS58): 5H3bYqimMmanUg2vm6vLAwHnzcM5dxMp56dmcZV3JktLKh6K
  SS58 Address:      5H3bYqimMmanUg2vm6vLAwHnzcM5dxMp56dmcZV3JktLKh6K
(grandpa):
Secret phrase:       silly usage bomb stamp cereal choice draft february shed jar pen change
  Network ID:        substrate
  Secret seed:       0x811402ebba3f6a0c1e37b4977a72da62f091f2538cc1352df0134b0f10fd3860
  Public key (hex):  0x491037dfde2936fe9b42f6b36e0788dcc4fc7dc9e3b4347306510d1b796880f8
  Account ID:        0x491037dfde2936fe9b42f6b36e0788dcc4fc7dc9e3b4347306510d1b796880f8
  Public key (SS58): 5DiWAr4Z1PtueBrKamfSySpFDC7q3jrLdychrsua87HD7Enn
  SS58 Address:      5DiWAr4Z1PtueBrKamfSySpFDC7q3jrLdychrsua87HD7Enn

``` 
- ### Creating custom spec file and executing nodes
After that, I created custom spec file for relevant substrate <b>node</b> template


```./target/release/node-template build-spec --disable-default-bootnode --chain local > customSpec.json```

and I've opened template in my favourite text editor by typing ```code .``` :)

I've changed required parts of customSpec.json. Then i executed 
```./target/release/node-template build-spec --chain=customSpec.json --raw --disable-default-bootnode > customSpecRaw.json ```
command to create customSpecRaw.json.
And I've started first node and added keys into store for nodes. (I've done it for two nodes <i>node01</i> and <i>node02</i> with respective suri keys). And ı typed the commands to restart all the nodes. (It can be checked from customSpec.json file)

<b><u>node01:</u></b>
```
./target/release/node-template \
  --base-path /tmp/node01 \
  --chain ./customSpecRaw.json \
  --port 30333 \
  --rpc-port 9945 \
  --telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
  --validator \
  --rpc-methods Unsafe \
  --name MyNode01 \
  --password-interactive
```
<b><u>node02:</u></b>
```
sudo ./target/release/node-template \
  --base-path /tmp/node02 \
  --chain ./customSpecRaw.json \
  --port 30334 \
  --rpc-port 9946 \
  --telemetry-url 'wss://telemetry.polkadot.io/submit/ 0' \
  --validator \
  --rpc-methods Unsafe \
  --name MyNode02 \
  --bootnodes /ip4/127.0.0.1/tcp/30333/p2p/{current_local_identity_for_node01} \
  --password-interactive 
  ```
  After launching first node

  <img src="polkadot-substrate-readme-photos\add-trusted-nodes-after-launching-node01.png" alt="alt text" width="320" height="180" style="margin-top: 20px; margin-bottom: 20px;"><br>

After launching second node:
  <img src="polkadot-substrate-readme-photos\add-trusted-nodes-after-launching-node02.png" alt="alt text" width="320" height="180" style="margin-top: 20px; margin-bottom: 20px;"><br>
Please take attention to target local identity on picture.

# Smart Contracts
 To achieve this task, I followed also <a href="https://docs.substrate.io/tutorials/smart-contracts/prepare-your-first-contract/">this</a> documentation.

   <img src="polkadot-substrate-readme-photos\smart-contract-get.png" alt="alt text" width="320" height="180" style="margin-top: 20px; margin-bottom: 20px;"><br>

  <i>After executing```  cargo contract call --contract 5DibxvMvKRtdnNo9g3oucbKtgZfhGEhohGgxdAHZgNjK9hCv --message get --execute --gas 200000000000 --proof-size 100000000000 --suri //Alice --skip-dry-run``` command. My subssystem route me to select --skip-dry-run flag, why I don't know</i>



   <img src="polkadot-substrate-readme-photos\smart-contract-flip.png" alt="alt text" width="320" height="180" style="margin-top: 20px; margin-bottom: 20px;"><br>

  <i>After executing ```cargo contract call --contract 5DibxvMvKRtdnNo9g3oucbKtgZfhGEhohGgxdAHZgNjK9hCv --message flip --suri //Alice``` command.</i>

  # Conclusion
  By help of this course, I've learnt existence of Substrate. Its CLI, looks like Shopify's CLI and robust. Selecting Rust as an official progamming language is very good idea. And also, I've learnt a bit about Polkadot. And finally, I've learnt about Rust programming language, its flex syntax and its speed. Thanks for this course 


  




