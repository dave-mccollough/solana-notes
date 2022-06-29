# Solana Toolchain Setup for M1 Macs


## Install Rust  
1. To install Rust, open the terminal and run the following command.  
`curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh`  

2. Select the following installation option.  
`1) Proceed with installation (default)`  

3. After the installation is complete, run the following command to configure your shell.  
`source $HOME/.cargo/env`  

4. To verify the installation is complete, enter the following command.  
`rustup --version`  


## Install Rosetta  
Some packages of the Solana Toolchain require Rosetta be installed.  Run the following command to install Rosetta.  
`softwareupdate --install-rosetta`  


## Install Solana Tool Suite  

1. Verify the Mainnet version [here](https://docs.solana.com/cli/install-solana-cli-tools).  

2. Navigate to the folder you want to download the Solana source to via the command line.  

3. Run the following command to install Solana from the Git Repository.  
`git clone https://github.com/solana-labs/solana.git/`  

4. Change directory to the `solana` directory.  
`cd solana`  

5. Checkout the Mainnet version from step 1.  
`git checkout v1.10.27`  

6. Run this command to build the source.  
`./scripts/cargo-install-all.sh .`  

**Potential Errors**  

- `greadlink: command not found`  
    - This requires Homebrew.  If Homebrew is not installed, run the following command.  
    `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`  

    - Install Coreutils  
    `brew install coreutils`  

    - Run the following command to build the Solana source again.  
    `./scripts/cargo-install-all.sh .`  

- `error: failed to run custom build command for openssl-sys v0.9.67`  
    - Run the following command to install openssl  
    `brew install openssl@1.1`  

     - Run the following command to build the Solana source again.  
    `./scripts/cargo-install-all.sh .`  

- `toolchain '1.52.1-aarch64-apple-darwin' is not installed`  
    - Run the following commands.  
    `rustup toolchain uninstall stable`  
    `rustup toolchain install stable`  

    - Run the following command to build Solana source again.  
    `./scripts/cargo-install-all.sh .`  

7. Update the following command with username and folder location.  Run the following command.  
`export PATH="/Users/your-username/your-folder-location/solana"/bin:"$PATH"`  

8. Verify installation was successful, run the solana command.  
`solana`  


## Create the configuration file  
 
 1. Run command to create config file.  
 `solana config get`  

 2. Set config file to localhost  
 `solana config set --url localhost`  

 ## Install Mocha testing Framework  
 1. Verify Node and NPM is installed (minimum version v11.0.0)  
 `node --version`  

 2. If node and NPM are not installed, get them [here](https://nodejs.org/en/download/).  

 3. Install Mocha  
 `npm install -g mocha`  


## Install Anchor  
Anchor provides tooling for Solana developers.  Learn more [here](https://github.com/coral-xyz/anchor).  

1. Run command to install Anchor  
`cargo install --git https://github.com/project-serum/anchor anchor-cli --locked`  

2. Verify Anchor installation.  
`anchor --version`  

3. Install Anchor's npm module and Solana Web3 JS.  
`npm install @project-serum/anchor @solana/web3.js`  



