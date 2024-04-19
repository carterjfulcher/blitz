# Blitz

A lightning fast blockchain, with capacity througput of 1 billion transactions per day.

### Thesis
- Bitcoin does about 400k transactions per day. Visa & Mastercard do half a million transactions _per second._
- Blockchains are really just a large distributed compute problem. How far can a distributed KV over infiniband take us?
- Kafka write bandwidth is about 2 million messages per second. With partitions, we can distribute (in crypto terms- decentralize) consumers that write to a distrubted KV store
