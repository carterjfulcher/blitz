# Blitz

A lightning fast blockchain, with capacity througput of 1 billion transactions per day.

If you have interest in collaborating on this project, comments, or questions, email me: `carter@dl.software` 

### Thesis
- Bitcoin does about 400k transactions per day. Visa & Mastercard do half a million transactions _per second._
- Blockchains are really just a large distributed compute problem. How far can a distributed KV over infiniband take us?
- Kafka write bandwidth is about 2 million messages per second. With partitions, we can distribute (in crypto terms- decentralize) consumers that write to a distrubted KV store


### A Transaction 
DDR4 2666MHz Memory in a six-channel configuration has bandwidth of 90GB/s. 

Say we store account balances in DDR4 memory in a KV store. A transaction could look like this:

```python3 
import numpy as np
transaction = np.dtype([
    ('account_number', np.int32),   # Assuming 32-bit integers are sufficient for account numbers
    ('operation', np.bool_),        # Using boolean for operation (True for increment, False for decrement)
    ('amount', np.float32)          # Using 32-bit float for amount
])
transaction = np.array((11231, True, 32.3), dtype=transaction)
```

`sizeof` transaction is 9 bytes, 600,000 of these each second would yield 5.4GB/s of bandwidth


### Other Ideas
- Stock exchanges handle volume with different tapes. Perhaps we could split transactions/accounts onto different tapes. Colocate accounts that have many transactions with each other with a special op for moving accounts to different tapes. 
- Blitz should NOT have it's own programming language. Blitz should support smart contracts. Maybe we can use C or C++ code, something optimized for speed
- Exchange trading on current blockchains is an after thought. DEX's are always a chain abstraction. Is there a way we can bake trading into the L1? We need a "decentralized" orderbook. What about US Securities Laws, though? Many legal questions. 
- In order to get the speed we want, we can't allow any type of machine to become a network node. Nodes should be in a datacenter with a 10G uplink. Network has to have some way of determining this.
- What proofing method? 
