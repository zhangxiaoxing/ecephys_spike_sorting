Noise Templates
==============
Identifies noise (putative non-neural) units in Kilosort outputs.

The most recent version uses a pre-trained [random forest classifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html) to identify noise templates. A pickle file containing the classifier object is included in this repository.

The classifier was trained on manually annotated templates assigned to one of five categories: 'good' units and four types of 'noise' units (see `images` sub-folder for examples). `template_classifier_app.py` can be used to generate new training data (requires PyQt5). Once the training data is available, `train_classifier.py` was used to create the classifier object. Because there are generally many more 'good' units than 'noise' units, we reduced the number of 'good' templates in the training set in order to lower the false positive rate. In this iteration, the classifier performs with a hit rate of 99.2% ('good' units correctly identified) and a false positive rate of 12.3% ('noise' units identified as 'good'). False positives may be filtered out at a later step based on the metrics calculated by the `mean_waveforms` module. 

Running
-------
```
python -m ecephys_spike_sorting.modules.noise_templates --input_json <path to input json> --output_json <path to output json>
```
See the schema file for detailed information about input json contents.


Input data
----------
- **Kilosort outputs** : includes spike times, spike clusters, templates, etc.


Output data
-----------
- **cluster_group.tsv** : labels for each cluster in spike_clusters.npy