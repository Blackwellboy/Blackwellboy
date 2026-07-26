# Blackwellboy

**Empirical performance engineering on DGX Spark (GB10).** I run a fleet of
five DGX Sparks (plus a 5090 box and an M-series Mac) and publish measured
numbers. Methodology, conditions, and raw data included, or it doesn't ship.

## The method

Every model that lands on the fleet gets the same battery:

1. **Speed**: short and sustained throughput benches, per-concurrency, TTFT at depth
2. **Intelligence**: a fixed 16-task suite, run in thinking-on and thinking-off arms
3. **Gate study**: a 10-condition grid measuring how prompt pressure suppresses
   or forces reasoning (dose-response, not vibes)
4. **Integrity probes**: does the model's stated reasoning match its behavior
5. **Soak**: long-duration sustained load with degradation detection

Honest-numbers rules: conditions beside every figure (image sha, model revision,
server flags, context, concurrency), negative results published, and protocols
that disagree get cited side by side, never averaged.

## Featured work

- **[laguna-s21-lab](https://github.com/Blackwellboy/laguna-s21-lab)**: the
  flagship. 20-cell serving sweep, 12h soak, thinking-gate dose-response study,
  cross-model head-to-head, and a quant-floor reference for Laguna S 2.1 on GB10
- **[Hy3-295B-NVFP4-MTP-Dual-DGX-Spark](https://github.com/Blackwellboy/Hy3-295B-NVFP4-MTP-Dual-DGX-Spark)**:
  serving a 295B MoE across two Sparks with NVFP4 and MTP, what works and what doesn't
- **[MiniMax-M3-2x-DGX-Spark-stock-driver](https://github.com/Blackwellboy/MiniMax-M3-2x-DGX-Spark-stock-driver)**:
  dual-node MiniMax-M3 on the stock driver, including the failure modes

## Support this work

If the numbers here saved you a week of trial and error on your own Spark:
GitHub Sponsors or Buy Me a Coffee (links in the sidebar). Sponsorship funds
lane-time for the next model in the queue.
