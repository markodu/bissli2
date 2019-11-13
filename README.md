# bissli2
Map Bisulfite Converted Reads

## bissli2-align.pl
Align bisulfite converted reads to a reference genome using bowtie2:

```bash
bissli2-align.pl  [OPTIONS]  -g <genome>  -x <index>  {-1 <m1> -2 <m2> | -U <r>}
```

Arguments:

    ebwt
        The basename of the index to be searched. The index is created using
        bissli2-build.

    input-file
        Input FASTQ file holding reads. Note that other input file formats
        are unsupported.

    output-file
        Output SAM file that will hold aligned reads. Note that output file
        must always be in SAM format.

Options:

    -h, --help
        Show this help message and exit.

    -1 <m1> -2 <m2>
        Files containing paired-end reads. <m1> and <m2> are comma-separated
        lists of filenames containing read 1 and read 2 respectively.

    --bowtie2 <path>
        Path to the bowtie2 executable. [bowtie2]

    --ct
        Assume that the reads to be aligned underwent C->T conversion. If
        paired-end reads are aligned, then assume read 1 underwent C->T
        conversion while read 2 underwent G->A conversion. The --ct and --ga
        options are mutually exclusive.

    -g <dir>
        A directory holding the reference genome, one FASTA file per
        chromosome.

    --ga
        Assume that the reads to be aligned underwent G->A conversion. If
        paired-end reads are aligned, then assume read 1 underwent G->A
        conversion while read 2 underwent C->T conversion. The --ct and --ga
        options are mutually exclusive.

    --keep-tmp
        Don't remove temporary directory once the run complete. For debug
        purposes only.

    -S <filename>
        Name of output SAM file. If this option is not set, output will be
        written to stdout in SAM format.

    --tmp-dir <dir>
        Directorhy for storing temporary files. If this option is not set,
        temporary files will be stored under /tmp.

    -U <r>
        Files containing single-end reads. <r> is a comma-separated list of
        filenames.

    bowtie2 Options
        Any unknown options are passed transparently to bowtie2. Note that
        the following bowtie2 options are always applied: -q --quiet
        --reorder.

## bissli2-build.pl
Create an bowtie2 index for a bisulfite converted genome:

```bash
bissli2-build.pl  [OPTIONS]  <reference>  <idx_base>
```
     
