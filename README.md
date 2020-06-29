# nanopore_formats
A place to track nanopore formats

Any format will do. If we can, perhaps we can add extra metadata with the basecaller and version to try and nail this stuff down.


## legacy

#### 1
    filename	read_id	run_id	channel	start_time	duration	num_events	template_start	num_events_template	template_duration	sequence_length_template	mean_qscore_template	strand_score_template


| Column   | **Description** |
| ------------- | ------------- |
| filename | fast5 filename |
| read_id | unique ID per read |
| read_id | unique ID per run |
| channel | channel reading the read |
| start_time | time of read sequencing since experiment start |
| duration | time taken to sequence read |
| num_events | number of events detected |
| template_start |  |
| num_events_template |  |
| template_duration |  |
| sequence_length_template | number of nucleotides in basecalled sequence |
| mean_qscore_template | average quality score of read |
| strand_score_template | |

#### 2
    filename	read_id	run_id	channel	start_time	duration	num_events	passes_filtering	template_start	num_events_template	template_duration	sequence_length_template	mean_qscore_template	strand_score_template	median_template	mad_template

| Column   | **Description** |
| ------------- | ------------- |
| filename | fast5 filename |
| read_id | unique ID per read |
| read_id | unique ID per run |
| channel | channel reading the read |
| start_time | time of read sequencing since experiment start |
| duration | time taken to sequence read |
| num_events | number of events detected |
| passes_filtering |  |
| template_start |  |
| num_events_template |  |
| template_duration |  |
| sequence_length_template | number of nucleotides in basecalled sequence |
| mean_qscore_template | average quality score of read |
| strand_score_template | |
| median_template |   |
| mad_template |  |

## multi_f5



#### 1
    filename_fastq	filename_fast5	read_id	run_id	channel	mux	start_time	duration	num_events	passes_filtering	template_start	num_events_template	template_duration	sequence_length_template mean_qscore_template	strand_score_template	median_template	mad_template


#### 2
    filename_fastq	filename_fast5	read_id	run_id	channel	mux	start_time	duration	num_events	passes_filtering	template_start	num_events_template	template_duration	sequence_length_template mean_qscore_template	strand_score_template	median_template	mad_template	pore_type	experiment_id	sample_id

#### 3
    filename	read_id	run_id	batch_id	channel	mux	start_time	duration	num_events	passes_filtering	template_start	num_events_template	template_duration	sequence_length_template	mean_qscore_template	strand_score_template	median_template	mad_template	calibration_strand_genome	calibration_strand_genome_start	calibration_strand_genome_end	calibration_strand_strand_start	calibration_strand_strand_end	calibration_strand_num_insertions	calibration_strand_num_deletions	calibration_strand_num_aligned	calibration_strand_num_correctcalibration_strand_identity	calibration_strand_accuracy	calibration_strand_score


## 1D^2

    filename1	filename2	read_id1	read_id2	run_id	channel	start_time1	start_time2	trimmed_duration1	trimmed_duration2	trimmed_events1	trimmed_events2	median1	median2	mad1	mad2	sequence_length	mean_qscore	strand_score

---

Latest update:

filename The name of the .fast5 file the read came from.
read_id The uuid that uniquely identifies this read.
run_id The uuid that uniquely identifies the sequencing run that this read came from.
batch_id Integer identifier of the batch that Guppy put this read in. See the --read_batch_size parameter and the --resume option.
channel The channel on the flow cell that the read came from.
mux The mux in the channel that the read came from.
start_time Start time of the read, in seconds since the beginning of the run.
duration Duration of the read, in seconds.
num_events Legacy field -- duration should be used instead.
passes_filtering Whether or not the read passed the qscore filter. See the --qscore_filtering flag and the --min_qscore parameter.
template_start Start time of the portion of the read that was sent to the basecaller after adapter trimming, in seconds since the beginning of the run. See the --trim_threshold, --trim_min_events, --max_search_len, --trim_strategy, and --dmean_win_size parameters.
num_events_template Legacy field -- template_duration should be used instead.
template_duration Duration of the portion of the read that was sent to the basecaller after adapter trimming, in seconds.
sequence_length_template Number of bases in the output sequence, taking into account any sequence trimming performed by options such as --trim_barcodes.
mean_qscore_template The qscore corresponding to the mean error rate of the sequence.
strand_score_template Legacy field - no longer populated reliably.
median_template The median current of the read, in pA.
mad_template The median absolute deviation of the current of the read, in pA.
scaling_median_template The "median_template" value used by the basecaller to scale incoming data. May be different than median_template if adapter scaling or scaling overrides are used. See the --scaling_med parameter.
scaling_mad_template The "mad_template" value used by the basecaller to scale incoming data. May be different than mad_template if adapter scaling or scaling overrides are used. See the --scaling_mad parameter.
If barcoding/demultiplexing is enabled via the --barcode_kits argument, then the following columns are added to the sequencing summary file:

barcode_arrangement The normalized name of the barcode classification, without a kit (e.g. "barcode01"), or "unclassified" if no classification could be made.
barcode_full_arrangement The full name for the highest-scoring barcode match, including kit, variation, and direction (e.g. "RAB19_var2").
barcode_kit The kit name belonging to the highest-scoring barcode match (e.g. "RAB").
barcode_variant Which of the forward / reverse variants the highest-scoring barcode matched (e.g. "var1"), or "n/a" if no variants are available.
barcode_score The score for either the front or rear barcode, whichever is higher. The maximum score is 100, with no minimum.
barcode_front_id The full name for the barcode at the front of the strand, including direction (forward/reverse) and variant (1st/2nd) (e.g. "RAB19_2nd_FWD").
barcode_front_score The score for the barcode at the front of the strand.
barcode_front_refseq The reference sequence the barcode at the front of the strand was matched against.
barcode_front_foundseq The sequence of the barcode at the front of the strand that matched barcode_front_refseq.
barcode_front_foundseq_length The length of barcode_front_foundseq.
barcode_front_begin_index The position in the called sequence, counting from the beginning, that barcode_front_foundseq begins at.
barcode_rear_score The score for the barcode at the rear of the strand.
barcode_rear_refseq The reference sequence the barcode at the rear of the strand was matched against.
barcode_rear_foundseq The sequence of the barcode at the rear of the strand that matched barcode_rear_refseq.
barcode_rear_foundseq_length The length of barcode_rear_foundseq.
barcode_rear_end_index The position in the called sequence, counting backwards from the end, that barcode_rear_foundseq ends at.
If barcode trimming is enabled via the --trim_barcodes argument, then the following additional columns will also be present:

barcode_front_total_trimmed The number of bases removed from the front of the sequence as part of barcode trimming.
barcode_rear_total_trimmed The number of bases removed from the rear of the sequence as part of barcode trimming.
If dual barcoding is used the following additional columns will be present:

barcode_front_id_inner
barcode_front_score_inner
barcode_rear_id_inner
barcode_rear_score_inner
These columns have the same meaning as the standard "id" and "score" columns above, but apply only to the inner front and rear barcodes. The standard "id" and "score" columns now apply to the outer barcodes.

For further details on how barcoding works see the "How barcode demultiplexing works" section.

If alignment is enabled via the --align_ref argument, then the following colums are added to the sequencing summary file:

alignment_genome The name of the reference which the read aligned to, or "*" if no alignment was found.
alignment_genome_start The position in the reference where the alignment started, or -1 if no alignment was found.
alignment_genome_end The position in the reference where the alignment ended, or -1 if no alignment was found.
alignment_strand_start The position in the called sequence where the alignment started, or -1 if no alignment was found.
alignment_strand_end The position in the called sequence where the alignment ended, or -1 if no alignment was found.
alignment_num_insertions The number of insertions in the alignment, or -1 if no alignment was found.
alignment_num_deletions The number of deletions in the alignment, or -1 if no alignment was found.
alignment_num_aligned The number of bases in the called sequence which aligned to bases in the reference, or -1 if no alignment was found.
alignment_num_correct The number of aligned bases in the called sequence which match their corresponding reference base, or -1 if no alignment was found.
alignment_identity The percentage of aligned bases which correctly match their corresponding reference base (alignment_num_correct/alignment_num_aligned), or -1 if no alignment was found.
alignment_accuracy The percentage of all bases in the alignment which are correct (alignment_num_correct/(alignment_num_aligned + alignment_num_insertions + alignment_num_deletions)), or -1 if no alignment was found.
alignment_score The score returned by minimap2, or -1 if no alignment was found.
alignment_coverage The percentage of either the called sequence or the reference (whichever is shorter) that aligns (e.g. (alignment_strand_end - alignment_strand_start + 1)/(sequence_length_template), or -1 if no alignment was found.
alignment_direction The direction of the alignment, either forwards (+) or reverse (-), or "" if no alignment was found. Note that genome positions (e.g. **alignment_genome_start*) are always given in the forwards direction.


---

## Acknowledgements

Created from a history of complaining and a frustrated tweet. Thanks to [Wouter De Coster](https://twitter.com/wouter_decoster) and [Robert Lanfear](https://twitter.com/RobLanfear) for the suggestion to make it a repo and to  tell people about the format changes. I welcome anyone that wishes to add to this or format it.

## Contributers



## License

[The MIT License](https://opensource.org/licenses/MIT)
