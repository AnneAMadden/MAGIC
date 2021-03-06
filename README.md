#READ ME
Marker Gene to Hierarchical Classifier Database Solution
MAGIC-DS

This software reformats and filters entries from a database and formats them in a custom
database for use in retraining the naive Baysian hierarchical classifier, such 
as RDP. The current version is appropriate for use with a subset of entries from the 
Bar Code of Life database.

Input
The input required for this software is obtained from the Bar Code of Life Database public
database. <insert website> A taxonomic selection is input such as "Mammals." When records 
are returned, download the "Complete File" as a .tsv file (Tab separated values.) 

Output
The output appropriate for classifiers such as RDP is a taxonomy file, which will have a 
unique ID (the "Process ID"-without hyphens stipulated by BOLD) 
attached to each taxonomic string. The second file is a sequence file, that is a
fasta file with the unique ID paired with the corresponding nucleotide sequence.

This software is written in Python 2.7 and is appropriate for the BOLD database v.3. 

The script first parses the database by what taxonomic string is of interest
(User input levels) and then performs filtering to remove sequences that contain ambiguous 
base calls, no sequence information, or the desired taxonomic resolution.

User defined parameters:
-b	limit to standard barcode region? 
	BOLD specific option
	(default: FALSE)
	Limit to the CO1-5P portion of the COI gene?
	
-n	number of taxa. 
	(default: 7)
	Options: 1-7
	Number of taxonomic levels to include in string. Note: older versions of RDP require
	fewer levels.

-t 	taxa to include in string
	(Required if -n is not default)
	Options: -Phylum, Order, Class, Family, Subfamily, Genus, Species
	
-l Sequence length to exclude 
	(Default: <50)
	Options: 1-9999
	Note: RDP is not recommended for sequences <50 basepairs long.

-i input filepath 
	(Required)

-o output filepath 
	(Required)
	Will return two files. One is a taxa file (ending in .txt), one is a fasta file
	ending in .fasta.

-d dereplicate redundant entries?
	default: False
	Note, dereplicating entries can increase the processing speed of the RDP classifier.
	This will only dereplicate if the nucleotide sequence and taxonomic string are identical

-r finest taxonomic resolution to include
	(default: Phylum)
	options: Phylum, Order, Class, Family, Subfamily, Genus, Species
	This will filter out those sequences where the taxonomy is not resolved to the desired
	level.
	
-x Initial database
	(default: BOLD)
	options: BOLD, GenBank...?
	
Example Call:
MAGIC-DS -i /Users/JaneSmith/bold_2.tsv -o /Users/JaneSmith/ -n 6 -t Phylum, Order, Class, 
Family, Subfamily, Genus -d -r Genus 

Licensed to Madden, Leff, Barberan....et al.

This software is licensed under......

Disclaimer. This parser and filter is designed to work with the data from the BOLD repository
While every effort is made to check for errors that will not allow for use in the RDP classifer,
this software does not check the validity of the data within the repository. User beware.

Add references for RDP

Add references for BOLD

How to cite this software...

Include wrapper for standalone RDP?
