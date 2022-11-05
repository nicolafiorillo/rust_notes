# Rust notes

### Enum

```rust
enum AccountingError {
    AccountNotFound(String),
    AccountUnderFunded(String, u64),
    AccountOverFunded(String, u64),
}

pub enum {
    Deposit { account: String, amount: u64 },
    Withdraw { account: String, amount: u64 },
}
```

### Struct

```rust
#[derive(Debug)]
struct Accounts {
    accounts: HashMap<String, u64>,
}
```

### Struct implementation

```rust
impl Accounts {
    pub fn new() -> Self {
        Accounts {
            accounts: Default::default(),
        }
    }

    pub fn deposit(&mut self, signer: &str, amount: u64) -> Result<Tx, AccountingError> { ... }
```
