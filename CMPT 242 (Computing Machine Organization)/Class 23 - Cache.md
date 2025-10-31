### Cache
- **Note**: Paging can be thought of as a form of cache, and in the bets case can be reasonably fast (as if there were simply more memory)
	- Especially thunderbolt is nearly as fast
- **Note**: The cache mechanism reads (we hope) from cache but it must write back to both cache and main memory
	- Makes circuits more complex
#### Strategies
- Write through - uses parallel - does both simultaneously
- Write back - write first cache, sets a *dirty bit* and before purging the cache checks that bit and if set, writes to main memory.
#### Problems
1. Multiple processors may have independent caches only if the write-through strategy is used. But its still worth it.
2. Random access to cached data increases the likelihood of a miss.
3. The above problem does not happen when accessing instructions, except for large jumps (high locality).
- **Note**: Since each application has its own environment, including any cache, with an addressing space starting at 0 context switching (say to another app) usually involves:
	- Flush the current app cache before switching
	- Disambiguate the address space using some bits as identifiers to a  specific app - the rest is relative address.
- 