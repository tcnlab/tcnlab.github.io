# Memory and prediction timeline
Tutorials and code examples for constructing a scale-free log-compressed memory timeline and from that  a scale-free log-compressed timeline of the estimated future. 

## Creating scale-free log-compressed memory timeline

For a very basic demo of a scale-free log-compressed memory timeline look into `compressed_memory.m`. The code provides an example for storing multiple repetitions of a single stimulus over 10000 time steps in 50 log-spaced buffers. 
The output figure illustrates how the input is compressed through a two-layer network. The output is characterized with logarithmically-spaced sequentially activated nodes ("time cells") that follow each stimulus presentation in a scale-invariant (width of the activation of each node scales with its peak time). At any moment in time the instantaneous firing rate of the sequentially activated neurons provides an estiamte of the recent past. 

![Compressed memory](/assets/images/zoran_1/compressed_memory.png)

A schematic of a neural netwrok implemented in `compressed_memory.m` is shown below (and it can be regenerated using `SITH_recurrent_network_tikz_figure.tex`.

![Compressed memory](/assets/images/zoran_1/SITH_recurrent_network_tikz_figure.png)

## Creating temporal associations 

A major utility of having acess to a compressed timeline is the ability to create temporal assocations. This is done through basic hebbing learning by binding the present input with presently active time cells. Each different stimulus has its own set of time cells, thus the association tensor (M) has three dimensions (it binds input stimulus with a past stimulus at specific lag determined with the presently active time cells). The associateve learning is implemented in `compressed_memory_temporal_associations_prediction.m`. 

![Temporal associations with compressed memory](/assets/images/zoran_1/M_heatmap.png)

## Computing a prediction of the future as a scale-free log-compressed memory

Probing the temporal associations tensor (M) with the present content of the memory timeline provides an estimate of future stimuli. This is also implemented in `compressed_memory_temporal_associations_prediction.m`. See `scale_free_prediction.mp4` for a video illustrating a simple example with four sequentially activated stimuli. 

## References 

Shankar, K.H., and Howard, M.W. (2012). A scale-invariant internal representation of time. Neural Computation, 24, 134-193.

Shankar, K.H. and Howard, M.W. (2013). Optimally fuzzy scale-free memory, Journal of Machine Learning Research, 14, 3753-3780.

Howard, M.W., MacDonald, C.J., Tiganj, Z., Shankar, K.H., Du, Q., Hasselmo, M.E., and Eichenbaum, H. (2014). A unified mathematical framework for coding time, space, and sequences in the hippocampal region. Journal of Neuroscience, 34, 4692-4707.

Tiganj, Z., Shankar, K. H. and Howard, M. W. (2017) Neural and computational arguments for memory as a compressed supported timeline. CogSci.