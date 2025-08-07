# synapse_neurotransmitters

This repository includes curated synapses with confirmed gt_neurotransmitter profile. Both volumes are isotropic: 8nm(x) x 8nm(y) x 8nm(z) 

* MANC neurotransmitter profile from Lacin 2019. Source: funkelab
* Hemibrain neurotransmitter profile from Eckstein 2024.
* Tool: neuprint explorer 

## Curation Process 
### Hemibrain 

A. Replication of Eckstein Technique for Training Data
- Retrieve  neuron IDs from the immunolabelled chart in Eckstein.
- Neuron are used to import synapses from the hemibrain dataset via Neuprint.  
15 synapses from 20 neurons with the highest number of synapses from each classes are picked. 

B. Use of Synapse-Level Predictions from Eckstein (Filtered with Ground Truth)
- Individual predict nt synapses from the feather file are filtered: softmax scores must be in the upper quartile.
- Neurons associated with these synapses must be present in GT. 
15 synapses from 20 neurons with the highest number of synapses from each classes are picked. 

### MANC 
MANC Neuprint includes predicted neurotransmitter labels.
- Neuron bodyIDs were selected by matching these predictions (using max probability scores) with ground truth neurotransmitter identities from Lacin et al. (2019).
- For each neurotransmitter class, the top 20 bodyIDs with the highest predicted neurotransmitter probabilities were selected  
50 synapses from 20 neurons are picked

## Confidence filtering 

Synapse from both volumes are model predicted. Synapse confidence thresholds were adjusted per neurotransmitter class to ensure that each of the top 20 neurons contributed at least 15 synapses. Thresholds were pushed to its upper limit—retaining only the highest-confidence predictions across all selected neurons.

Hemibrain A method    
Dopamine=0.98
Octopamine=0.98
Serotonin=0.99
Glutamate=0.993
Gaba=0.993
Acetylcholine=0.994

MANC   
glutamate=0.9
gaba=0.95
acetylcholine=0.97 




## Data format 

Bounding boxes (bbox) are small cropped EM focused on the synapse features with sufficient surrounding context.  
* MANC: Bboxes are centered on pre-synaptic points and extend 65 pixels in all x,y and z. 
* Hemibrain: Bboxes are centered on pre-synaptic points and extend 15 pixels in all x,y and z.

Note: Both pre- and post-synaptic points are enclosed within the box; otherwise, it is flagged in the `any_out_of_range` column of the bbox CSV.

