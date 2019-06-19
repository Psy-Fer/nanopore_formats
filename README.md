# nanopore_formats
A place to track nanopore formats

Any format will do. If we can, perhaps we can add extra metadata with the basecaller and version to try and nail this stuff down.


## legacy

#### 1
    filename	read_id	run_id	channel	start_time	duration	num_events	template_start	num_events_template	template_duration	sequence_length_template	mean_qscore_template	strand_score_template

#### 2
    filename	read_id	run_id	channel	start_time	duration	num_events	passes_filtering	template_start	num_events_template	template_duration	sequence_length_template	mean_qscore_template	strand_score_template	median_template	mad_template



## multi_f5



#### 1
    filename_fastq	filename_fast5	read_id	run_id	channel	mux	start_time	duration	num_events	passes_filtering	template_start	num_events_template	template_duration	sequence_length_templatemean_qscore_template	strand_score_template	median_template	mad_template


#### 2
    filename_fastq	filename_fast5	read_id	run_id	channel	mux	start_time	duration	num_events	passes_filtering	template_start	num_events_template	template_duration	sequence_length_templatemean_qscore_template	strand_score_template	median_template	mad_template	pore_type	experiment_id	sample_id


## 1D^2

    filename1	filename2	read_id1	read_id2	run_id	channel	start_time1	start_time2	trimmed_duration1	trimmed_duration2	trimmed_events1	trimmed_events2	median1	median2	mad1	mad2	sequence_length	mean_qscore	strand_score
