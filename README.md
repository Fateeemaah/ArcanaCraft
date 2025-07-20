

## ArcanaCraft Gaming Platform Smart Contract

The `ArcanaCraft` smart contract powers asset ownership, trading, and character progression for a blockchain-based gaming platform. It ensures transparent management of in-game items and supports secure, decentralized trading of assets using the Stacks blockchain.

---

### 🚀 Features

* **In-Game Asset Management**

  * Mint individual or batches of game items.
  * Transfer ownership securely (individually or in batches).
  * Validate item metadata and trading eligibility.

* **Marketplace Integration**

  * List items for sale and purchase using STX.
  * Enforces ownership, price validity, and trade permissions.
  * Sellers can delist items anytime.

* **Character Progression**

  * Record and update experience and level for player characters.
  * Enforces caps on maximum experience and level.

---

### 🛠️ Admin Controls

* Only the platform administrator (`tx-sender` at deploy time) can create new items.
* Strict validations and permission checks prevent unauthorized operations.

---

### 🧾 Data Structures

* **Maps:**

  * `game-items`: Item ID → {owner, URI, tradable}
  * `item-market-values`: Item ID → {price}
  * `marketplace-item-listings`: Item ID → {seller, price, listing time}
  * `character-progression`: Character → {experience, level}

* **Variables:**

  * `total-item-count`: Tracks total minted items.

---

### 🧪 Public Functions Overview

| Function                       | Description                                |
| ------------------------------ | ------------------------------------------ |
| `create-item`                  | Create a single game item (admin-only)     |
| `batch-create-items`           | Create multiple items at once (admin-only) |
| `transfer-item`                | Transfer an item to another player         |
| `batch-transfer-items`         | Transfer multiple items                    |
| `list-item-for-sale`           | List owned item for sale                   |
| `purchase-item`                | Buy an item listed in the marketplace      |
| `delist-item`                  | Remove item from marketplace listing       |
| `update-character-progression` | Save character XP and level                |
| `get-item-details`             | View item data                             |
| `get-marketplace-listing`      | View current item listing                  |
| `get-character-progression`    | Get XP and level for a character           |
| `get-total-items`              | Get total minted item count                |

---

### ⚠️ Error Codes

* `u100`: Admin-only operation
* `u101`: Resource not found
* `u102`: Permission denied
* `u103`: Invalid parameters
* `u104`: Pricing or trade error

---

### 📜 Deployment Notes

* Ensure the deploying address is the intended `platform-admin`.
* All URI strings are capped at 256 bytes.
* Batch operations are limited to 10 items max.

---
