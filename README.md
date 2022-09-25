# Open Vote Network using zk-SNARKs
This is the proof of concept of our paper "[Dispute-free Scalable Open Vote Network using zk-SNARKs](https://eprint.iacr.org/2022/310)"

# Installation 
 1. Install [Nodejs](https://nodejs.org/)
 2. Install [Circom 2.0](https://docs.circom.io/getting-started/installation/)
 3. Install Truffle Framework:  `npm install -g truffle`
 4. Install Ganache-cli: `npm install -g ganache-cli`
 5. Clone this repository and change directory to its path
 6. Install the required packages `npm i`

# Development
Install docker, then build and run thedev  env with docker-compose
- `docker-compose run --rm dev`

# Execution
 - `cd build`
 - Run `./setup.sh -d [DESIGN_TO_BE_USED] -n [NUMBER_of_VOTERS]`
    where `[DESIGN_TO_BE_USED]` could be:
 
	 - `original`: Our original proposed design
	 - `sha256`: The first enhancement using Sha256
	 - `progressiveSha256`: The second enhancement using Sha256
	 - `progressivePoseidon`: The second enhancement using Poseidon

     For example `./setup.sh -d "original" -n 3`

 - Check the test code in the file `test/completeTest.js`
 - Run the local Ethereum node: `ganache-cli -l 30e6 -a [[NUMBER_of_VOTERS + 2]]` 
 - Run the command `truffle test` to view the result and the gas cost of each transaction

 # Notes
 - You may need to update the variable `powersOfTau` in `build/setup.sh` based on the number of constraints generated by the circuits.
 - You can find the suitable powerOfTau in https://github.com/iden3/snarkjs#7-prepare-phase-2(https://github.com/iden3/snarkjs#7-prepare-phase-2)

