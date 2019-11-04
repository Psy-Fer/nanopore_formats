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

## Acknowledgements

Created from a history of complaining and a frustrated tweet. Thanks to [Wouter De Coster](https://twitter.com/wouter_decoster) and [Robert Lanfear](https://twitter.com/RobLanfear) for the suggestion to make it a repo and to  tell people about the format changes. I welcome anyone that wishes to add to this or format it.

## Contributers



## License

[The MIT License](https://opensource.org/licenses/MIT)
