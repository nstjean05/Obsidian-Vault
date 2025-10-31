### Cache
- **Note**: Paging can be thought of as a form of cache, and in the bets case can be reasonably fast (as if there were simply more memory)
	- Especially thunderbolt is nearly as fast
- **Note**: The cache mechanism reads (we hope) from cache but it must write back to both cache and main memory
	- Makes circuits more complex
#### Strategies
- Write through - uses parallel - does both simultaneously
- Write back does first cache, sets a *dirty bit* and before purging the cache checks that bit and if set, writes to main memory.
- 