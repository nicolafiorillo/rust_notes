# Rust notes

### Enum

Examples:

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

`struct` example

```rust
#[derive(Debug)]
struct Accounts {
    accounts: HashMap<String, u64>,
}
```

### Struct implementation

Struct `impl` example:

```rust
impl Accounts {
    pub fn new() -> Self {
        Accounts {
            accounts: Default::default(),
        }
    }

    pub fn deposit(&mut self, signer: &str, amount: u64) -> Result<Tx, AccountingError> { ... }
}
```

### Question ? operator

Container function must return a `Result<.., AccountingError>` type.

Expression like

```rust
  let sender_tx = self.withdraw(sender, amount)?;
```

is equal to

```rust
  let sender_tx = match self.withdraw(sender, amount) {
      Ok(tx) => tx,
      Err(err) => return Err(err),
  };
```

