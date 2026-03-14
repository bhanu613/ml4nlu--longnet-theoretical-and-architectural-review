# Comparative Table of Long-Context Transformer Architectures

This table accompanies **Appendix B** of the term paper.

| Model | Complexity | Max Context | Coverage Type | Key Limitation |
|---|---|---|---|---|
| Vanilla Transformer (Vaswani et al., 2017) | O(N²d) | ~2K–8K tokens | Dense, full self-attention | Quadratic cost in sequence length; cannot scale to very long documents. |
| Sparse Transformer (Child et al., 2019) | O(N^{3/2}·d) | ~16K–64K tokens | Fixed sparse patterns (local + strided) | Sparsity pattern is content-independent; some important long-range dependencies are never modelled directly. |
| Reformer (Kitaev et al., 2020) | O(N log N·d) | ~64K tokens | LSH-based approximate attention | LSH can separate semantically related tokens; attention is only approximate. |
| Longformer (Beltagy et al., 2020) | O(Nd) | ~16K–32K tokens | Sliding window + a few global tokens | A small set of global tokens acts as a bottleneck for global information flow. |
| Transformer-XL (Dai et al., 2019) | O(N²d) per segment | ~8K–16K tokens per segment | Dense attention within segments + cached recurrence | Still quadratic within each segment; distant information depends on compressed cache. |
| Memorizing Transformers (Wu et al., 2022) | O(Nd) + retrieval cost | ~262K tokens | Dense attention + kNN retrieval over external memory | Requires a large external memory and efficient retrieval index; performance depends on memory quality. |
| Recurrent Memory Transformer (Bulatov et al., 2022) | O(Nd) per segment | ~1M tokens | Attention over segment + learned recurrent memory slots | Finite memory slots can bottleneck information; very old content may be compressed or lost. |
| LongNet (Ding et al., 2023) | O(Nd) | ~1B tokens | Multi-scale dilated attention with head offsets | Evaluation focused on code only; open questions remain about NLU tasks and local resolution. |
