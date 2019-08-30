===================================================
> LRG.rnc version 1.10 Release notes   2019-08-24 <
===================================================

# FIXED_ANNOTATION section:

- New optional tag "superceded_by" to indicate if a LRG has been deprecated and superceded by an other LRG.


# UPDATABLE_ANNOTATION section:

- Additional values ('novel_patch' and 'fix_patch') allowed for the attribute "type" in the "mapping" tag.

- Additional values ('MANE-select' and 'MANE-plus') allowed for the attribute "source" in the "db_xref" tag.


==================================================
> LRG.rnc version 1.9 Release notes   2014-10-01 <
==================================================

# FIXED_ANNOTATION section:

- New tag "creation_date" for the new transcripts in the fixed section, if the transcripts have been added after the LRG has been made public.

- Move or duplicate requester information to the updatable section: we will keep the requester information in the fixed section for the public LRGs and for the pending LRG, the requester information will be only in the updatable section, as an annotation set with the type "requester".

- Allow LRG without transcripts: change the constraint on the "transcript" tag.


# UPDATABLE_ANNOTATION section:

- New attribute "type" in the "annotation_set" tag to indicate the type of annotation set, i.e. 'lrg', 'ncbi', 'ensembl', 'requester', 'community', 'lsdb'.

- New attribute "type" in the "mapping" tag to indicate the type of sequence aligned against the LRG sequence, i.e. 'main assembly', 'other assembly', 'patch', 'haplotype', 'transcript'.

- New attribute "other_id_syn" in the "mapping" tag to add a synonym of the "other_name" or "other_id "  attributes (e.g. the INSDC identifier of the chromosome).

- New optional "note" tag, mainly designed for the community annotation set.

- Move or duplicate requester information to the updatable section: we will keep the requester information in the fixed section for the public LRGs and for the pending LRG, the requester information will be only in the updatable section, as an annotation set with the type "requester".


==================================================
> LRG.rnc version 1.8 Release notes   2013-08-28 <
==================================================

# FIXED_ANNOTATION section:

- New attribute "label" in the "exon" tags, to store the specific LRG number of each exon.

- New optional tag "hgnc_id" which can contains the HGNC identifier corresponding to the LRG gene name.

- Change the pattern of the LRG transcript and protein coordinate systems (i.e. the attribute "coord_system" in the tag "coordinates") 
  by removing the character "_" between the LRG name and the transcript and protein name, e.g.:
    - LRG_1t1 instead of LRG_1_t1
    - LRG_1p1 instead of LRG_1_p1


# UPDATABLE_ANNOTATION section:

- Changes for the tag "symbol":
    - Now, only one tag "symbol" is allowed per "gene"
    - The symbol name has been moved from the content of the tag "symbol" to a new attribute "name".
    - The tag "synonym" (0 to many) has been added as a child of the tag "symbol".
    - Moved up the tag "symbol" at the top position in the tag "gene".

- Added optional tags "url" and "comment" in both tags "other_exon_naming" and "alternate_amino_acid_numbering"

- Remove the tag "comment" in the tag "fixed_transcript_annotation" (i.e. moved into "other_exon_naming" and "alternate_amino_acid_numbering").

- The "other_exon_naming" and "alternate_amino_acid_numbering" data are now stored exclusively in the "Community" annotation set.
  If there is no data for at least one of these 2 tags, there won't be a "Community" annotation set for the LRG.



==================================================
> LRG.rnc version 1.7 Release notes   2012-07-31 <
==================================================

## FIXED_ANNOTATION section:

- Added sequence_source which contains the accession number of the RefSeqGene with exact alignment to the LRG

- The translation of multiple protein products from a single transcript is now supported

- The tag <translation_exception> has been added. This tag will contain information on non-canonical codon translation and read-through codons. This replaces elements 'selenocysteine' and 'pyrrolysine'

==== Patched the "2012-10-01" ====
- Add an optional "comment" tag in the fixed annotation section

==== Patched the "2013-03-27" ====
- Add an optional "comment" tag for transcript


## UPDATABLE_ANNOTATION section:

- Added mapping information for all transcripts encoded by the gene specified in <lrg_locus>. The mapping is by sequence alignment and includes information on differences between the transcript and LRG.

- Removed most_recent attribute

 

==================================================
>  LRG.rnc version 1.6 Release notes  2010-03-17 <
==================================================
## FIXED_ANNOTATION section:

- Required initial exon are now followed by optional intron-exon blocks

- Specification of selenocysteine codons are now done as elements below coding_region element

- Added support for pyrrolysine codon

## UPDATABLE_ANNOTATION section:

- Added Rfam, miRBase and pseudogene.org to list of allowed xref databases

- Re-arranged schema to be more modular



=====================================
> LRG.rnc version 1.5 Release notes <
=====================================

## UPDATABLE_ANNOTATION section:

- most_recent attribute, indicating if the assembly is the most recent available,
  added to mapping element

- lrg_gene_name element added to hold the HGNC gene identifier (optional)

- fixed_id attribute added to transcript element to link the updatable annotation
  to a transcript in the fixed annotation section (optional)

- alternative_amino_acid_numbering element is now optional

- other_exon_naming element is now optional

- features element is now optional



=====================================
> LRG.rnc version 1.4 Release notes <
=====================================

## FIXED_ANNOTATION section:

- exons being followed by an intron now has an element denoting intron phase



=====================================
> LRG.rnc version 1.3 Release notes <
=====================================

## FIXED_ANNOTATION section:

- minor modification of intron phase representation



=====================================
> LRG.rnc version 1.2 Release notes <
=====================================

## FIXED_ANNOTATION section:

- multiple contacts now permitted in source section.

- transcript elements now have start and end attributes.

- multiple transcript elements now permitted.

- cdna element containing sequence moved to be first element in transcript.

- coding_region element now has start, end and optional codon_start and
  codon_selenocysteine attributes.

- exon elements now follow coding_region element, rather than being contained
  within them.
  
- exons are no longer explicitly numbered in the fixed layer. Legacy
  naming/numbering can be added in the updatable layer using other_exon_naming.

- exons now have three elements within them; lrg_coords, cdna_coords and
  peptide_coords. These represent exon coordinates in three systems, and each
  have start and end attributes. The peptide_coords elements have start_phase
  and end_phase attributes with values of '0', '1' or '2' to represent the phase
  of the exon/intron boundary.


## UPDATABLE_ANNOTATION section:

- now contains one or more annotation_set elements to allow for sets of
  annotation from multiple sources (e.g. NCBI, EMBL-EBI).

- amino_acid_mapping element renamed alternate_amino_acid_numbering.

- alternate_amino_acid_numbering and other_exon_naming elements now have a
  transcript element with name attribute within them, to allow for
  transcript-specific annotation.

- mapping element has been completely reworked. It has chr_name, chr_start and
  chr_end attributes to represent the total region covered by the mapped LRG
  sequence. It then contains one or more mapping_span elements that represent a
  contiguous block of the LRG sequence aligned to the genome. Each mapping_span
  element may contain one or more diff elements that describe short sequence
  differences between the LRG sequence and the reference genome - these have a
  type attribute that can be 'mismatch', 'lrg_ins' or 'genomic_ins'. This new
  element configuration allows for a complete description of how the LRG
  sequence relates to and differs from the reference seqeunce.

- cds elements in features have been renamed transcript, and now occur within
  their respective gene elements. The transcript elements have start and end
  attributes to bring them in line with their equivalents in the fixed
  annotation layer.

- protein_product elements have cds_start and cds_end attributes to represent
  the coordinates of the coding sequence.

- the aforementioned gene, transcript and protein_product elements may now
  contain a partial element that indicates if the feature in question partially
  overlaps the 5' or 3' end of the LRG sequence (i.e. the feature is not fully
  contained within the LRG).
