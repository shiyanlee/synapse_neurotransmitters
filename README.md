# synapse_neurotransmitters

This repository includes curated synapses with confirmed gt_neurotransmitter profile. Both volumes are isotropic: 8nm(x) x 8nm(y) x 8nm(z) 

* MANC neurotransmitter profile from Lacin 2019. Source: funkelab
* Hemibrain neurotransmitter profile from Eckstein 2024.

## Curation Process 
### Hemibrain 

A. 
B. 

### MANC 

## Data format 

* MANC: Bboxes are centered on pre-synaptic points and extend 65 pixels in all directions. 
* Hemibrain: Bboxes are centered on pre-synaptic points and extend 15 pixels in all directions.

Note: Both pre- and post-synaptic points are enclosed within the box; otherwise, it is flagged in the `any_out_of_range` column of the bbox CSV.
