# ess module

## cvrs_to_batch_totals
This routine creates a file for a single contest with vote totals by batch and candidate. User must give:
 * Required:
     * paths to two files (one with contest choices by cvr, one with batch info by cvr)
     * name of contest
     * path for output file
 * Optional:
     * columns for the join (default is "Cast Vote Record" for both files)
     * column with batch name (default is "Batch")

# scripts folder
## clearballot_to_coloradoRLA.py
- **clearballot_to_coloradoRLA.py** takes as input a single CVR export file from ClearBallot system (v1.4.3). For example, from the folder containing ```clearballot_sample_CVR.csv``` running
```python clearballot_to_coloradoRLA.py clearballot_sample_CVR.csv```
creates  (in the current folder) the file
```RLAclearballot_sample_CVR.csv``` suitable for upload to the ColoradoRLA
and creates (or updates) the file
```hashes.txt```
where the sha256 hash of the output file is stored.

Under construction:
- **cvr_conversion.py** takes as input a directory containing one or more CVR files. Every file in the directory with extension ```.csv```  will be processed. There are optional flags:
-h, --help            show this help message and exit
-i INPUT_CVR_FORMAT, --input_format=INPUT_CVR_FORMAT
use the specified input format, must be one of the
following: ess, clearballot
-o OUTPUT_CVR_FORMAT, --output_format=OUTPUT_CVR_FORMAT
use the specified output format, must be one of the
following: dominion
-f FILE, --file=FILE  write report to FILE
-q, --quiet           don't print status messages to stdout

Running
```python -i ess -o dominion cvr_conversion.py dirpath```
creates (in the directory *dirpath*) a file ```FreeFairRLAtool.input``` suitable for upload to the ColoradoRLA 
and creates (or updates) the file
```hashes.txt```
where the sha256 hash of the output file is stored.

    
In both cases the input CVR files must be scrubbed of any commas, quotes and apostrophes.



