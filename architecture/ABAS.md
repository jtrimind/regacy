## Table of Contents
- [Reference](#reference)

## Reference
[Attribute-Based Architectural Styles](https://resources.sei.cmu.edu/asset_files/TechnicalReport/1999_005_001_16781.pdf)

## Performance Characterization
```
Performance ┬ Stimuli ┬ Mode ┬ Regular
            │         │      └ Overload
            │         ├ Source ┬ Internal Event
            │         │        ├ Clock Interrupt
            │         │        └ External Event
            │         └ Frequency Regularity ┬ Periodic
            │                                └ Aperiodic ┬ Sporadic
            │                                            └ Random
            ├ Architectural Parameter ┬ Resource ┬ CPU Memory
            │                         │          ├ Network
            │                         │          └ Device & Sensors
            │                         ├ Resource Arbitration ┬ Queuing Policy
            │                         *TBD*
            └ Responses ┬ Latency ┬ Response Window
                        │         ├ Criticality
                       │         ├ Best/Avg/Worst Case
                       │         └ Jitter
                       ├ Throughput ┬ Criticality
                       │            ├ Best/Avg/Worst Case
                       │            └ Observation Window
                       └ Precedence ┬ Criticality
                                    └ Ordering ┬ Partial
                                             └ Total
```