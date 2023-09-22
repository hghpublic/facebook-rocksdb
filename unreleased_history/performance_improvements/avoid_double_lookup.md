During async_io, the Seek happens in 2 phases. Phase 1 starts an asynchronous read on a block cache miss, and phase 2 waits for it to complete and finishes the seek. In both phases, it tries to lookup the block cache for the data block first before looking in the prefetch buffer. It's optimized by doing the block cache lookup only in the first phase that would save some CPU.