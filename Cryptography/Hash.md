Hashing is a one way functionality (irreversible) to calculate a digest. Separate input into two block
Results must be idempotent (same for same input)
Digest size are always similar depending on the algorithm: MD5 -> 128 bits / SHA-256 -> 256 bits
If even one bit of information changes from the input (like an entire text), then the output must change considerably

Used to store data against leak (like database) or for integrity checks (data not corrupted). They should be fast but not instantaneous to prevent brute-force

### Salting

Used to prevent hash collisions (same password = same hash)

### Peppering
Used to prevent brute force by adding yet another value, but not stored in the database