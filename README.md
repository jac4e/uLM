![uLM](https://raw.githubusercontent.com/jac4e/uLM/main/hardware/REV1_0/PCB.png)

# uLM

uLM is a lux meter for microcontrollers.

## Idea

The idea came from a physics experiment in which Malus' Law is verified using a smartphone app. Unfortunately in the original experiment, the smartphone app performed very poorly, so the uLM was designed as alternative with the hopes that it would perform better and eliminate the need for manually recording of the data.

## Goals

Three goals were set

- It should perform better than the smartphone app
- Data collection should be automatic, or nearly automatic
- and it should be relatively cheaper than consumer light meters

## Initial Design Considerations

From initial research, multiple ways of sensing light intensity were considered, but it was quickly determined that a photodiode with a low current input biased op-amp to use as a trans-impedance amplifier (TIA) would be the easiest way to sense light intensity accurately. Given that the experiment's light source was a computer monitor, the VTP9812FH was chosen as its spectral sensitivity is similar to that of human eyes. The LTC6268 was selected as the op-amp as it has a low input current bias and is advertised for this specific application. 

To convert the analog signal from the LTC6268, the ADS1100 was chosen as it offers programmable gain, up to 16 bits of resolution, and I already had exposure to I2C interfaces.

The final major design decision was the feedback resistance of the TIA. Initially, a resistance of 12.5MOhms was chosen, which corresponded to a max measurement of 400 Lux, sufficient for the application. However, due to part selection constraints, I went with a feedback resistance of 15MOhms which gives a max measurement of 333 Lux.
