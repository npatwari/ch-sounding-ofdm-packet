# Channel Sounding OFDM Packet Generation

This is a repo with code to generate pilots for an OFDM signal with a low peak-to-average power ratio (PAPR). The code saves two files:

- An IQ file with the samples for just one symbol (256 samples)
- An IQ file with the samples for a packet of `repetitions` number (1000) of the symbol, one after another. 

The goal is to generate an all-pilot chnanel OFDM symbol that is perfectly known and repetitive so that it can be used for channel frequency response estimation.
But we want to minimize the PAPR so that we can send as high of signal power as possible without clipping the transmitted signal.

Because each symbol repeats, there is no need for the cyclic prefix.

The code shows that you can reduce the PAPR by a factor of about 65 compared to straightforward 
methods to pick pilot values for the pilots, for example, using the same pilot value for all pilot subcarriers.
If you randomly pick a (complex) unit-amplitude pilot value, you can see a range of PAPR with a maximum PAPR that's 
5 times higher than the minimum PAPR.

This code randomly generates 10,000 random pilot value vectors, and then chooses the best (lowest PAPR) one.
