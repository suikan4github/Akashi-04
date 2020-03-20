# Akashi-04
Audio board for Nucleo-G431RB

## Functionality
This board is designed to provide the audio functionality for the  STM32 series MCU. 
The connectors can be directly mounted on the Nucleo 64 series board and employs I2S interface of STM32 MCU.
This board supports following Nucleo :
- STM32F446RE
- STM32G431RB

The design can be retrieved from the [github](https://github.com/suikan4github/Akashi-04) repository.

![Image](docs/board.jpg)


These functionalities are tested with following codec board as with I2C control line. 
- [UMB-ADAU1361A](http://dsps.shop-pro.jp/?pid=82798273)

## Development
- [KiCad 5.1](http://kicad-pcb.org/blog/2019/03/KiCad-5.1.0-Release/)
- [Nucleo G431RB](https://www.st.com/en/evaluation-tools/nucleo-g431rb.html)
- [Nucleo F446RE](https://www.st.com/en/evaluation-tools/nucleo-f446re.html)


The schematics [can be downloaded](docs/Akashi-04.pdf) as PDF format. 

![Pin Configurations](docs/pin_assign.png)

The configuration of special ports are :
- I2S2 : Slave TX
- I2S3 : Slave RX
- PB7 : EXTI to detect the I2S WS edge. 
- PC9 : Open Drain output. To save the struggled I2C device.


## I2C address
By default, the I2C device address are configured as ***0x38*** ( 7bit address ). 
If you want to change, you should modify the short bridge as following : 

| JP1    | JP2    | Address |
---------|--------|---------|
| Closed | Closed | 0x38    |
| Open   | Closed | 0x39    |
| Closed | Open   | 0x3A    |
| Open   | Open   | 0x3B    |

Note that R3 and R4 are needed if JP1 and JP2 are cut, respectively

## Usage
To clone this project, follow :
```
git clone repository-of-this-project
git submodule update
```


The sample programs are published as [murasaki_samples_audio](https://github.com/suikan4github/murasaki_samples_audio) repositories. 

 To use these repository, follow the sequence :
 1. Clone the murasaki_samples_audio repository
 1. Import to CubeIDE

Caution : Because of the height of the capacitor, the stacked Arduino board may contact to the capacitor. 

## License
This PCB design is released under the [Creative Commons Attribution 4.0 International license](https://creativecommons.org/licenses/by/4.0/). 
You are welcome to use this design for commercial purposes. 
