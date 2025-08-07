# synapse_neurotransmitters

This repository includes curated synapses with confirmed gt_neurotransmitter profile. Both volumes are isotropic: 8nm(x) x 8nm(y) x 8nm(z) 

* MANC neurotransmitter profile from Lacin 2019. Source: funkelab
* Hemibrain neurotransmitter profile from Eckstein 2024.

## Curation Process 
### Hemibrain 

A. Replication of Eckstein Technique for Training Data
- Retrieve hemibrain neuron IDs from the immunolabelled chart in Eckstein (ground truth).
- Neuron types from step 1 are used to import synapses from the hemibrain dataset via Neuprint.  
15 synapses from 20 neurons with the highest number of synapses from each classes are picked. 

B. Use of Synapse-Level Predictions from Eckstein (Filtered with Ground Truth)
- Individual synapses from the feather file are filtered: softmax scores from each neurotransmitter must be in the upper quartile.
- Neurons associated with these synapses must be present in the ground truth set to be included.
- Synapse coordinates are used (double-check this step for correctness).  
15 synapses from 20 neurons with the highest number of synapses from each classes are picked. 


### MANC 


## Data format 

Bounding boxes (bbox) are small cropped EM focused on the synapse features with sufficient surrounding context.  
* MANC: Bboxes are centered on pre-synaptic points and extend 65 pixels in all x,y and z. 
* Hemibrain: Bboxes are centered on pre-synaptic points and extend 15 pixels in all x,y and z.

Note: Both pre- and post-synaptic points are enclosed within the box; otherwise, it is flagged in the `any_out_of_range` column of the bbox CSV.
