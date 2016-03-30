# casper_adc16

Ancillary files for CASPER ADC16 development

## installation

To install the ruby package, 

```
cd ruby
rake package
cd pkg/
gem install adc16
```

## Usage

Once the gem is installed, the following may be run from the command line.

### adc16_init.rb

```
Usage: adc16_init.rb [OPTIONS] HOSTNAME BOF

Programs HOSTNAME with ADC16-based design BOF and then calibrates
the serdes receivers.

Options:
    -d, --demux=D                    Set demux mode (1|2|4) [1]
    -g, --gain=G                     Set digital gain [1]
    -i, --iters=N                    Number of snaps per tap [1]
    -r, --reg=R1=V1[,R2=V2...]       Register addr=value pairs to set
    -v, --[no-]verbose               Display more info [false]
    -h, --help                       Show this message
```

### adc16_status.rb
```
Usage: adc16_status.rb [OPTIONS] ROACH2_NAME [...]

Shows ADC16 status for a running ADC16-based design.

Using the --cal option will verify SERDES calibration,
which will briefly switch in test patterns then revert
to analog inputs.  For cal status: "." = OK; "X" = BAD.

Options:
    -c, --[no-]cal                   Check SERDES calibration [false]
    -h, --help                       Show this message
    
```

### adc16_plot_taps.rb

```
Usage: adc16_plot_taps.rb [OPTIONS] ROACH2_NAME [BOF]

Plot error counts for various ADC16 delay tap settings.
Programs FPGA with BOF, if given.

Options:
    -c, --chips=C,C,...              Which chips to plot [all]
    -d, --device=DEV                 Plot device to use [/xs]
    -e, --expected=N                 Expected value of deskew pattern [42]
    -i, --iters=N                    Number of snaps per tap [1]
    -n, --nxy=NX,NY                  Controls subplot layout [auto]
    -v, --[no-]verbose               Display more info [false]
    -h, --help                       Show this message
```

### adc16_dump_chans.rb

```
Usage: adc16_dump_chans.rb [OPTIONS] ROACH2_NAME

Dump samples from ADC16 based design.
Lengths between 1025 and 65536 requires the adc16_test design.

Options:
    -l, --length=N                   Number of samples to dump per channel (1-65536) [1024]
    -r, --rms                        Output RMS of each channel instead of raw samples [false]
    -v, --[no-]verbose               Display more info [false]
    -h, --help                       Show this message
```
