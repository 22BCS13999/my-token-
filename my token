class MyToken {
    constructor() {
        // Public variables to store the details about the coin
        this.name = "MyToken";
        this.symbol = "MTK";
        this.totalSupply = 0;

        // Mapping to store the balances of addresses
        this.balances = new Map();
    }

    // Method to mint new tokens
    mint(address, value) {
        this.totalSupply += value;
        if (this.balances.has(address)) {
            this.balances.set(address, this.balances.get(address) + value);
        } else {
            this.balances.set(address, value);
        }
    }

    // Method to burn tokens
    burn(address, value) {
        if (!this.balances.has(address) || this.balances.get(address) < value) {
            throw new Error("Insufficient balance to burn");
        }

        this.totalSupply -= value;
        this.balances.set(address, this.balances.get(address) - value);
    }

    // Method to get the balance of an address
    balanceOf(address) {
        return this.balances.get(address) || 0;
    }
}

// Example usage:
const myToken = new MyToken();

// Minting tokens
myToken.mint("0x123", 100);
console.log(`Total Supply after minting: ${myToken.totalSupply}`); // Total Supply after minting: 100
console.log(`Balance of 0x123 after minting: ${myToken.balanceOf("0x123")}`); // Balance of 0x123 after minting: 100

// Burning tokens
myToken.burn("0x123", 50);
console.log(`Total Supply after burning: ${myToken.totalSupply}`); // Total Supply after burning: 50
console.log(`Balance of 0x123 after burning: ${myToken.balanceOf("0x123")}`); // Balance of 0x123 after burning: 50

// Attempting to burn more tokens than available balance (will throw an error)
try {
    myToken.burn("0x123", 100);
} catch (error) {
    console.error(error.message); // Insufficient balance to burn
}
