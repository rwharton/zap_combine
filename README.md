# zap_combine
Bandpass correct, RFI zap, and combine two pols 

## Requirements 

This requires the python package `your`:  https://github.com/thepetabyteproject/your


## Usage
    
    usage: zap_combine.py [-h] [-tel TELESCOPE_ID] [-m MACHINE_ID]
                          [-src SOURCE_NAME] -o OUTBASE [-ez EDGEZAP]
                          [-dthresh DTHRESH] [-nwin CHANWIN]
                          infile1 infile2
    
    BP correct, zap, and combine pols (can also change some header 
    vals if you want)
    
    positional arguments:
      infile1               Pol 1 fil file
      infile2               Pol 2 fil file
    
    optional arguments:
      -h, --help            show this help message and exit
      -tel TELESCOPE_ID, --telescope_id TELESCOPE_ID
                            Telescope ID Number
      -m MACHINE_ID, --machine_id MACHINE_ID
                            Machine ID Number
      -src SOURCE_NAME, --source_name SOURCE_NAME
                            Source Name
      -o OUTBASE, --outbase OUTBASE
                            Output file basename (no suffix)
      -ez EDGEZAP, --edgezap EDGEZAP
                            Fraction of band to zap at edges
      -dthresh DTHRESH, --dthresh DTHRESH
                            Fractional diff threshold for bp flagging
      -nwin CHANWIN, --chanwin CHANWIN
                            Window size for bandpass flagging (chans)


## Example

    python zap_combine.py xlcp-p0000_n0100.fil xrcp-p0000_n0100.fil 
           -ez 0.1 -dthresh 0.25 -nwin 5 -o test

In this example we take in two files (`xlcp-p0000_n0100.fil` and `xlcp-p0000_n0100.fil`), zap 10% of the band at the edges, search for and flag channels that have a fraction difference of 25% from a running median bandpass made with a window of 5 channels, then write the combined data to a file called `test.fil`.  This will also produce two plots of the bandpasses of each input file with flagged channels indicated.  These will be named the same as the input files but appended with `_bp.png`.


